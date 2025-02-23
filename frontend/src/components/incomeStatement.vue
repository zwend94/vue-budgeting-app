<script>
import PercentDisplay from '../util/percentDisplay.vue';
import CurrencyDisplay from '../util/currencyDisplay.vue';

export default {
  name: 'IncomeStatement',
  components: {
    PercentDisplay,
    CurrencyDisplay,
  },
  props: {
    formData: {
      type: Object,
      required: true,
    },
  },
  computed: {
    years() {
      return ['Year 1', 'Year 2'];
    },
    salary() {
      return Number(this.formData.monthlySalary);
    },
    otherInc() {
      return Number(this.formData.otherIncome);
    },
  },
};
</script>

<template>
  <div class="container">
    <!-- Top text section  -->
    <header class="top-section">
      <div class="header-grid">
        <div class="header-column"></div>
        <div class="header-column-one"></div>
      </div>
    </header>

    <!-- Pro Forma Table  -->
    <div class="main-content">
      <h3 class="side-title">Monthly P/L</h3>
      <table>
        <thead>
          <tr>
            <th></th>
            <th></th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td class="table-label-cell">Gross Income</td>
            <td>
              <CurrencyDisplay :value="salary" />
            </td>
          </tr>
          <tr>
            <td class="table-label-cell">Other Income</td>
            <td><CurrencyDisplay :value="otherInc" /></td>
          </tr>
          <tr>
            <td class="table-label-cell">Total Income</td>
            <td>
              <CurrencyDisplay class="net-income" :value="salary + otherInc" />
            </td>
          </tr>
          <!-- Add calculation for total Income
    Add expenses -->
        </tbody>
      </table>
    </div>

    <!-- Right screen text section -->
    <aside class="right-section">
      <div></div>
    </aside>
    <div class="button-group">
      <button type="button" @click="$emit('prev-page')">Back</button>
    </div>
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
/* Formatting for right-hand section  */
p {
  margin-top: 5px;
}

h6 {
  text-align: center;
  font-weight: normal;
  font-style: italic;
  font-size: 12px;
}

th {
  font-size: 14px;
}

.side-title {
  margin-left: 335px;
  margin-bottom: 10px;
  margin-top: -10px;
}
</style>
