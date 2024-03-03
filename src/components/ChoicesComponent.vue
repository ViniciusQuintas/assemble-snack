
<template>
    <div class="pb-5md:pb-2">
        <div class="px-4 mt-9 md:mt-2 md:mb-9">
            <h2 class="font-semibold text-xl">Pão</h2>
            <div class="flex px-4 md:mt-0">
                <div>
                    <input type="radio" name="pao" id="gergelim" class="mr-1 accent-red-600" value="gergelim" v-model="input_pao">
                    <label for="gergelim">Gergelim</label>
                </div>
                <div class="mx-2">
                    <input type="radio" name="pao" id="australiano" class="mr-1 accent-red-600" value="australiano" v-model="input_pao">
                    <label for="australiano">Australiano</label>
                </div>
            </div>
        </div>
        <div class="px-4 mt-4 md:mb-9">
            <h2 class="font-semibold text-xl">Saladas</h2>
                <div class="flex px-4 mt-2 md:mt-0">
                    <div>
                        {{ input_alface }}
                        <input type="checkbox" name="alface" id="alface" class="mr-1 accent-red-600" value="alface" v-model="input_alface">
                        <label for="">Alface</label>
                    </div>
                </div>
        </div>
        <div class="px-4 mt-4 md:mb-9">
            <h2 class="font-semibold text-xl">Molhos</h2>
            <div class="flex px-4 mt-2 md:mt-0">
                <div>
                    <input type="checkbox" name="ketchup" id="ketchup" class="mr-1 accent-red-600" value="ketchup" v-model="input_molho">
                    <label for="ketchup">Ketchup</label>
                </div>
                <div class="mx-2">
                    <input type="checkbox" name="mostarda" id="mostarda" value="mostarda" class="mr-1 accent-red-600" v-model="input_molho">
                    <label for="mostarda">Mostarda</label>
                </div>
                <div class="mx-2">
                    <input type="checkbox" name="maionese" id="maionese" value="maionose" class="mr-1 accent-red-600" v-model="input_molho">
                    <label for="maionese">Maionese</label>
                </div>
            </div>
        </div>
        <div class="px-4 mt-4">
            <h2 class="font-semibold text-xl">Bife</h2>
            <div class="flex px-4 mt-2 md:mt-0">
                <div>
                    <input type="radio" name="hamburguer" id="bovino" value="bovino" v-model="input_hamburguer" class="mr-1 accent-red-600">
                    <label for="bovino">Bovino</label>
                </div>
                <div class="mx-2">
                    <input type="radio" name="hamburguer" id="frango" value="frango" v-model="input_hamburguer" class="mr-1 accent-red-600">
                    <label for="frango">Frango</label>
                </div>
                <div class="mx-2">
                    <input type="radio" name="hamburguer" id="soja" value="soja" v-model="input_hamburguer" class="mr-1 accent-red-600">
                    <label for="soja">Soja</label>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                input_pao: '',
                input_alface: '',
                input_molho: [],
                input_hamburguer: '',
                data: ''
            }
        },
        watch: {
            sendData: {
                handler() {
                    this.emitData();
                },
                deep: true
            }
        },
        computed: {
            sendData() {
                return {
                    'pao': this.input_pao ? this.input_pao : '',
                    'alface': this.input_alface ? this.input_alface : '',
                    'molho': this.input_molho.length > 0 ? this.input_molho : '',
                    'hamburguer': this.input_hamburguer ? this.input_hamburguer : '',
                };
            }
        },
        methods: {
            emitData() {
                this.$emit('recebe-data', this.sendData);
            }
        },

    }
</script>