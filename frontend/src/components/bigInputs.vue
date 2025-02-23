<script>
export default {
  name: 'IncomeInputs',
  props: {
    formData: {
      type: Object,
      required: true,
      default: () => ({
        monthlySalary: '',
        taxBracket: '',
        housingCost: '',
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
        <legend>Monthly Inputs</legend>
        <div class="input-row">
          <label>Monthly Salary</label>
          <input
            v-model="localData.monthlySalary"
            type="text"
            placeholder="Enter whole number."
            name="loss_cost_per_exposure"
          />
        </div>
        <div class="input-row">
          <label>Tax Bracket</label>
          <select v-model="localData.taxBracket">
            <option
              v-for="(value, index) in [
                0.1, 0.12, 0.22, 0.24, 0.32, 0.35, 0.37,
              ]"
              :key="index"
              :value="value"
              name="loss_cost_trend"
            >
              {{ value * 100 }}%
            </option>
          </select>
        </div>
        <div class="input-row">
          <label>Other Income</label>
          <input
            v-model="localData.otherIncome"
            type="text"
            placeholder="Enter decimal number."
          />
        </div>

        <!-- <div class="input-row">
        <label>Adverse Loss Ratio</label>
        <input
          v-model="localData.adverseLossRatio"
          type="text"
          placeholder="Enter decimal number."
        />
      </div> -->
      </fieldset>
      <div class="button-group">
        <button type="button" @click="$emit('prev-page')">Back</button>
        <button type="submit">Next</button>
      </div>
    </form>
  </div>
</template>
