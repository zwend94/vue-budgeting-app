<script>
export default {
  name: 'VariableExpenses',
  props: {
    formData: {
      type: Object,
      required: true,
      default: () => ({
        varExpOne: '',
        varExpTwo: '',
        varExpThree: '',
        varExpFour: '',
        varExpFive: '',
        varExpSix: '',
        varExpSeven: '',
      }),
    },
  },
  data() {
    return {
      localData: {
        ...this.formData,
      },
    };
  },
  methods: {
    handleSubmit() {
      this.$emit('update-form', this.localData);
      this.$emit('next-page');
    },
  },
};
</script>
<template>
  <div class="page">
    <form method="post" @submit.prevent="handleSubmit">
      <fieldset>
        <legend>Variable Expenses</legend>
        <div class="input-row">
          <label>Electric Bill</label>
          <input
            v-model="localData.varExpOne"
            type="text"
            placeholder="Enter amount."
          />
        </div>
        <div class="input-row">
          <label>Water, Sewer, & Other Utilities</label>
          <input
            v-model="localData.varExpTwo"
            type="text"
            placeholder="Enter amount."
          />
        </div>
        <div class="input-row">
          <label>Transportation Costs <p>(Fuel, ride-share, etc.)</p></label>
          <input
            v-model="localData.varExpThree"
            type="text"
            placeholder="Enter amount."
          />
        </div>
        <div class="input-row">
          <label>Clothing</label>
          <input
            v-model="localData.varExpFour"
            type="text"
            placeholder="Enter amount."
          />
        </div>
        <div class="input-row">
          <label>Groceries</label>
          <input
            v-model="localData.varExpSix"
            type="text"
            placeholder="Enter amount."
          />
        </div>
        <div class="input-row">
          <label>Debt Payments <p>(Student Loans, Credit Card fees, etc.)</p></label>
          <input
            v-model="localData.varExpFive"
            type="text"
            placeholder="Enter amount."
          />
        </div>
        <div class="input-row">
          <label>Other <p>(Childcare expenses, Alimony, etc.)</p></label>
          <input
            v-model="localData.varExpSeven"
            type="text"
            placeholder="Enter amount."
          />
        </div>
      </fieldset>
      <div class="button-group">
        <button type="button" @click="$emit('prev-page')">Back</button>
        <button type="submit">Submit</button>
      </div>
    </form>
  </div>
</template>
<style>

p {
    font-style: italic;
    font-weight: normal;
}

</style>
