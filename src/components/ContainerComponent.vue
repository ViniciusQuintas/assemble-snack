<script>
import SnackComponentVue from './SnackComponent.vue';
import ChoicesComponentVue from './ChoicesComponent.vue';

export default {
    components: {
        SnackComponentVue, ChoicesComponentVue
    },
}
</script>

<template>
    <div class="mt-16 flex flex-col items-center md:flex-row md:container md:mx-auto md:justify-around">
        <SnackComponentVue />
        <ChoicesComponentVue />
    </div>
</template>
