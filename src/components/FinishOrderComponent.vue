<template>
	<form action="">
		<h2 class="mb-14 mt-4 md:mt-0 text-xl md:text-3xl font-bold">
			Informe seus dados
		</h2>

		<div class="mb-2">
			<input
				class="min-w-96 bg-slate-200 rounded-md outline-1 outline-[#863e57] py-2 pl-4"
				type="text"
				v-model="nome"
				placeholder="Nome"
			/>
		</div>
		<div class="mb-14">
			<input
				class="min-w-96 bg-slate-200 rounded-md outline-1 outline-[#863e57] py-2 pl-4"
				type="text"
				v-model="endereco"
				placeholder="Endereço"
			/>
		</div>

		<section class="flex justify-between items-center">
			<button
				@click="emitDataBack"
				class="bg-[#275d8b] text-slate-100 px-8 py-2 rounded-md"
			>
				Voltar
			</button>
			<button
				@click.prevent="emitDataFinally"
				class="bg-[#e09f3e] text-slate-100 px-8 py-2 rounded-md"
			>
				Finalizar
			</button>
		</section>
	</form>
</template>

<script>
export default {
	data() {
    return {
      nome: "",
      endereco: "",
    };
  },
	methods: {
		emitDataBack() {
			this.$emit("mudar-etapa", 1);
		},
		emitDataFinally() {
			if (this.nome.trim() === "" || this.endereco.trim() === "") {
				alert("Por favor, preencha os campos de nome e endereço.");
			} else {
				const data = {
					input_pao: "",
					input_alface: "",
					input_molho: [],
					input_hamburguer: "",
				};
				alert("Pedido finalizado com sucesso");
				this.$emit("mudar-etapa", 1);
				this.$emit("reset", data);
			}
		},
		makeOrder() {
			if (this.input_hamburguer && this.input_pao) this.etapa = 2;
			else alert("Escolha pelo menos um tipo de pão e um hamburguer");
		},
	},
};
</script>
