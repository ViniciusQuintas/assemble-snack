
<template>
    <div class="mt-14 flex flex-col items-center md:flex-row md:container md:mx-auto md:justify-around">
        <SnackComponentVue :choices="choices" />
        <ChoicesComponentVue @recebe-data="recebeDados" />
    </div>
</template>

<script>
    import SnackComponentVue from './SnackComponent.vue';
    import ChoicesComponentVue from './ChoicesComponent.vue';
    
    export default {
        components: {
            SnackComponentVue, ChoicesComponentVue
        },
        data() {
            return {
                choices: ''
            }
        },
        methods: {
            recebeDados(data) {
                this.choices = data;
            }
        }
    }
</script>