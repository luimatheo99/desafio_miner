<script setup lang="ts">
import InputText from "primevue/inputtext";
import Button from "primevue/button";
import InputNumber from "primevue/inputnumber";
import InputMask from "primevue/inputmask";
</script>

<script lang="ts">
export default {
  data() {
    return {
      name: "",
      weight: null,
      height: null,
    };
  },
  methods: {
    calculate() {
      if (!this.name) {
        this.$toast.add({
          severity: "warn",
          summary: "Atenção",
          detail: "Informe seu nome",
          life: 5000,
        });
        return;
      }

      if (!this.weight) {
        this.$toast.add({
          severity: "warn",
          summary: "Atenção",
          detail: "Informe seu peso",
          life: 5000,
        });
        return;
      }

      if (!this.height) {
        this.$toast.add({
          severity: "warn",
          summary: "Atenção",
          detail: "Informe sua altura",
          life: 5000,
        });
        return;
      }

      const imc = this.weight / (this.height * this.height);

      if (imc > 30) {
        this.$toast.add({
          severity: "info",
          summary: "Atenção",
          detail: `Olá ${this.name}, você está acima da linha da obesidade!`,
          life: 5000,
        });
      } else {
        this.$toast.add({
          severity: "info",
          summary: "Atenção",
          detail: `Olá ${this.name}, você está abaixo da linha da obesidade!`,
          life: 5000,
        });
      }

      this.name = "";
      this.height = null;
      this.weight = null;
    },
  },
};
</script>

<template>
  <main>
    <div class="align-items-center text-center">
      <p class="text-3xl font-medium pb-5">Calcular IMC</p>
      <div class="field">
        <span class="p-float-label">
          <InputText id="name" type="text" v-model="name" />
          <label for="name">Nome</label>
        </span>
      </div>

      <div class="field pt-2">
        <span class="p-float-label">
          <InputNumber
            v-model="weight"
            mode="decimal"
            id="weight"
            :minFractionDigits="2"
            :maxFractionDigits="2"
            suffix=" kg"
          />
          <label for="weight">Peso</label>
        </span>
      </div>

      <div class="field pt-2">
        <span class="p-float-label">
          <InputNumber
            v-model="height"
            mode="decimal"
            id="height"
            :minFractionDigits="2"
            :maxFractionDigits="2"
            suffix=" m"
          />
          <label for="height">Altura</label>
        </span>
      </div>

      <div class="py-2">
        <Button
          @click="calculate"
          label="Calcular"
          class="p-button-success w-full"
        />
      </div>
    </div>
  </main>
</template>
