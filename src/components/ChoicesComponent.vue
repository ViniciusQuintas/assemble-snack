<template>
	<div v-if="etapa === 1">
		<div
			class="px-5 py-10 mt-14 mb-10 md:mt-0 bg-[#6c757d] rounded-2xl md:p-12"
		>
			<div class="mb-6">
				<h1 class="font-bold text-slate-100 text-xl md:text-3xl">
					Escolha seus ingredientes:
				</h1>
			</div>
			<div class="px-4 mt-9 md:mt-2 md:mb-9">
				<h2 class="font-semibold text-xl text-slate-100">Pão</h2>
				<div class="flex px-4 md:mt-0">
					<div>
						<input
							required
							type="radio"
							name="pao"
							id="gergelim"
							class="mr-1 accent-[#863e57]"
							value="gergelim"
							v-model="input_pao"
						/>
						<label class="text-slate-100" for="gergelim">Gergelim</label>
					</div>
					<div class="mx-2">
						<input
							required
							type="radio"
							name="pao"
							id="australiano"
							class="mr-1 accent-[#863e57]"
							value="australiano"
							v-model="input_pao"
						/>
						<label class="text-slate-100" for="australiano">Australiano</label>
					</div>
				</div>
			</div>
			<div class="px-4 mt-4 md:mb-9">
				<h2 class="font-semibold text-xl text-slate-100">Saladas</h2>
				<div class="flex px-4 mt-2 md:mt-0">
					<div>
						<input
							type="checkbox"
							name="alface"
							id="alface"
							class="mr-1 accent-[#863e57]"
							value="alface"
							v-model="input_alface"
						/>
						<label class="text-slate-100" for="alface">Alface</label>
					</div>
				</div>
			</div>
			<div class="px-4 mt-4 md:mb-9">
				<h2 class="font-semibold text-xl text-slate-100">Molhos</h2>
				<div class="flex px-4 mt-2 md:mt-0">
					<div>
						<input
							type="checkbox"
							name="ketchup"
							id="ketchup"
							class="mr-1 accent-[#863e57]"
							value="ketchup"
							v-model="input_molho"
						/>
						<label class="text-slate-100" for="ketchup">Ketchup</label>
					</div>
					<div class="mx-2">
						<input
							type="checkbox"
							name="mostarda"
							id="mostarda"
							value="mostarda"
							class="mr-1 accent-[#863e57]"
							v-model="input_molho"
						/>
						<label class="text-slate-100" for="mostarda">Mostarda</label>
					</div>
					<div class="mx-2">
						<input
							type="checkbox"
							name="maionese"
							id="maionese"
							value="maionese"
							class="mr-1 accent-[#863e57]"
							v-model="input_molho"
						/>
						<label class="text-slate-100" for="maionese">Maionese</label>
					</div>
				</div>
			</div>
			<div class="px-4 mt-4">
				<h2 class="font-semibold text-xl text-slate-100">Bife</h2>
				<div class="flex px-4 mt-2 md:mt-0">
					<div>
						<input
							type="radio"
							name="hamburguer"
							id="bovino"
							value="bovino"
							v-model="input_hamburguer"
							class="mr-1 accent-[#863e57]"
						/>
						<label class="text-slate-100" for="bovino">Bovino</label>
					</div>
					<div class="mx-2">
						<input
							type="radio"
							name="hamburguer"
							id="frango"
							value="frango"
							v-model="input_hamburguer"
							class="mr-1 accent-[#863e57]"
						/>
						<label class="text-slate-100" for="frango">Frango</label>
					</div>
					<div class="mx-2">
						<input
							type="radio"
							name="hamburguer"
							id="soja"
							value="soja"
							v-model="input_hamburguer"
							class="mr-1 accent-[#863e57]"
						/>
						<label class="text-slate-100" for="soja">Soja</label>
					</div>
				</div>
			</div>
		</div>
		<div class="text-center md:text-right">
			<button
				@click="makeOrder"
				class="bg-[#275d8b] text-slate-100 px-8 py-2 rounded-md"
			>
				Fazer pedido
			</button>
		</div>
	</div>
	<div v-if="etapa === 2">
		<FinishOrderComponentVue @mudar-etapa="toBack" @reset="reset" />
	</div>
</template>

<script>
import FinishOrderComponentVue from "./FinishOrderComponent.vue";
export default {
	components: {
		FinishOrderComponentVue,
	},
	data() {
		return {
			input_pao: "",
			input_alface: "",
			input_molho: [],
			input_hamburguer: "",
			data: "",
			etapa: 1,
		};
	},
	watch: {
		sendData: {
			handler() {
				this.emitData();
			},
			deep: true,
		},
	},
	computed: {
		sendData() {
			return {
				pao: this.input_pao ? this.input_pao : "",
				alface: this.input_alface ? this.input_alface : "",
				molho: this.input_molho.length > 0 ? this.input_molho : "",
				hamburguer: this.input_hamburguer ? this.input_hamburguer : "",
			};
		},
	},
	methods: {
		emitData() {
			this.$emit("recebe-data", this.sendData);
		},
		makeOrder() {
			if (this.input_hamburguer && this.input_pao) this.etapa = 2;
			else alert("Escolha pelo menos um tipo de pão e um hamburguer");
		},
		toBack(etapa) {
			this.etapa = etapa;
		},
		reset(data){
			this.input_pao = data.input_pao;
			this.input_alface = data.input_alface;
			this.input_molho = data.input_molho;
			this.input_hamburguer = data.input_hamburguer;
		}
	},
};
</script>
