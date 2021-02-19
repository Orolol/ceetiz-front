<template lang="pug">
    .form
        select.select-type.formElement(v-model="form.TypeId")
            option(:value="null") Please select a enterprise type
            option(:value="t.ID" v-for="t in types") {{t.Name}}
        input.formElement(v-model="form.Denomination" placeholder="Denomination") 
        input.formElement(v-model="form.Siret" placeholder="Siret") 
        input.formElement(v-model="form.Adress" placeholder="Adress") 
        input.formElement(type="number" v-model.number="form.Revenue" placeholder="Revenue") 
        button.formElement(@click="estimate") Estimate
        span.formElement Tax estimated : {{tax}}
</template>
<script>
export default {
  name: "FormEnt",
  data() {
    return {
      form: {
        Denomination: "",
        Siret: "",
        Adress: "",
        Revenue: 0,
        TypeId: null
      },
      types: [],
      tax: 0
    }
  },
  async mounted() {
    const res = await fetch("http://localhost:3010/types")
    const data = await res.json()
    this.types = data
  },
  methods: {
    async estimate() {
      const { form } = this
      const res = await fetch("http://localhost:3010/estimate", {
        method: "post",
        body: JSON.stringify(form)
      })
      const data = await res.json()
      this.tax = data
    }
  }
}
</script>
<style lang="scss">
.form {
  width: 50%;
  padding: 25%;
  display: flex;
  flex-direction: column;
  .formElement {
    margin-bottom: 10px;
  }
}
</style>
