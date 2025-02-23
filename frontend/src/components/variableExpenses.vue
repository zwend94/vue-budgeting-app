<script>
export default {
  name: 'VariableExpenses',
  props: {
    formData: {
      type: Object,
      required: true,
      default: () => ({
        expOne: '',
        expTwo: '',
        expThree: '',
        expFour: '',
        expFive: '',
        expSix: '',
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
        <legend>Fixed Expenses</legend>
        <div class="input-row">
          <label>Housing Payment</label>
          <input
            v-model="localData.expOne"
            type="text"
            placeholder="Enter amount."
          />
        </div>
        <div class="input-row">
          <label>Internet</label>
          <input
            v-model="localData.expTwo"
            type="text"
            placeholder="Enter amount."
          />
        </div>
        <div class="input-row">
          <label>Cell Phone</label>
          <input
            v-model="localData.expThree"
            type="text"
            placeholder="Enter amount."
          />
        </div>
        <div class="input-row">
          <label>Car Payment</label>
          <input
            v-model="localData.expFour"
            type="text"
            placeholder="Enter amount."
          />
        </div>
        <div class="input-row">
          <label>Car Insurance</label>
          <input
            v-model="localData.expFive"
            type="text"
            placeholder="Enter amount."
          />
        </div>
        <div class="input-row">
          <label>Other</label>
          <input
            v-model="localData.expSix"
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
