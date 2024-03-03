<template>
    <div>
        <img :src="pao[0]" alt="pão superior">
        <img src="../img/padrao/alface.png" alt="alface">
        <img src="../img/padrao/molho.png" alt="molho">
        <img src="../img/padrao/molho.png" alt="molho">
        <img src="../img/padrao/molho.png" alt="molho">
        <img src="../img/padrao/hamburguer.png" alt="hamburguer">
        <img :src="pao[1]" alt="pão inferior">
    </div>
</template>

<script>
    export default{
        props: {
            choices: Object
        },
        data(){
            return {
                data: {}
            }
        },
        created() {
            this.data = { ...this.choices }; 
        },
        watch: {
            choices: {
                handler(newData) {
                    this.data = { ...newData };
                    console.log('data', this.data); // Moveu o console.log para o watch handler
                },
                deep: true // Observação profunda para objetos e matrizes
            }
        },
        computed: {
            pao(){
                console.log('choice22', this.choices.pao)
                if (this.choices.pao && this.choices.pao === 'gergelim')
                    return ['../img/pao_gergelim_superior.png', '../img/pao_gergelim_inferior.png']
                else if (this.choices.pao && this.choices.pao === 'australiano')
                    return ['../img/pao_australiano_superior.png', '../img/pao_australiano_inferior.png']
                else 
                    return ['../img/padrao/pao_superior.png', '../img/padrao/pao_inferior.png'];
            }
        },
        
    }

</script>
