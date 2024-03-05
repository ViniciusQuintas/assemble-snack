<template>
    <div>
        <img :src="pao[0]" alt="pão superior">
        <img :src="alface" alt="alface">
        <img :src="ketchup" alt="molho">
        <img :src="mostarda" alt="molho">
        <img :src="maionese" alt="molho">
        <img :src="hamburguer" alt="hamburguer">
        <img :src="pao[1]" alt="pão inferior">
    </div>
</template>

<script>


export default {
    props: {
        choices: Object,
    },
    computed: {
        pao() {
            if (this.choices.pao === 'gergelim')
                return ['/src/img/pao_gergelim_superior.png', '/src/img/pao_gergelim_inferior.png',];
            else if (this.choices.pao === 'australiano')
                return ['/src/img/pao_australiano_superior.png', '/src/img/pao_australiano_inferior.png'];
            else
                return ['/src/img/padrao/pao_superior.png', '/src/img/padrao/pao_inferior.png'];
        },
        alface() {
            if (this.choices.alface === true)
                return '/src/img/alface.png';
            else
                return '/src/img/padrao/alface.png';
        },
        ketchup() {
            if (this.choices.molho && this.choices.molho.includes('ketchup'))
                return '/src/img/ketchup.png';
            else
                return '/src/img/padrao/molho.png';
        },
        maionese() {
            if (this.choices.molho && this.choices.molho.includes('maionese'))
                return '/src/img/maionese.png';
            else
                return '/src/img/padrao/molho.png';
        },
        mostarda() {
            if (this.choices.molho && this.choices.molho.includes('mostarda'))
                return '/src/img/mostarda.png';
            else
                return '/src/img/padrao/molho.png';
        },
        hamburguer() {
            if (this.choices.hamburguer === 'bovino')
                return '/src/img/bovino.png';
            else if (this.choices.hamburguer === 'frango')
                return '/src/img/frango.png';
            else if (this.choices.hamburguer === 'soja')
                return '/src/img/soja.png';
            else
                return '/src/img/padrao/hamburguer.png';
        },
    },

}

</script>
