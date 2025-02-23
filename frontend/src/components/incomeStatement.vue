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
    totalIncome() {
      return this.salary + this.otherInc;
    },
    incomeAfterTax() {
      return (this.salary + this.otherInc) * (1 - this.formData.taxBracket);
    },
    individualExpenses() {
      return [
        Number(this.formData.expOne),
        Number(this.formData.expTwo),
        Number(this.formData.expThree),
        Number(this.formData.expFour),
        Number(this.formData.expFive),
        Number(this.formData.expSix),
        Number(this.formData.expSeven),
        Number(this.formData.expEight),
      ]
    },
    totalExpenses() {
      return this.individualExpenses.reduce((acc, curr) => acc + curr, 0)
    },
    variableExp() {
      return [
        Number(this.formData.varExpOne),
        Number(this.formData.varExpTwo),
        Number(this.formData.varExpThree),
        Number(this.formData.varExpFour),
        Number(this.formData.varExpFive),
        Number(this.formData.varExpSix),
        Number(this.formData.varExpSeven),
      ]
    },
    totalVariableExpenses() {
      return this.variableExp.reduce((acc, curr) => acc + curr, 0)
    }
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

    <div class="main-content">
      <!-- <h3 class="side-title">Monthly P/L</h3> -->
      <table>
        <thead>
          <tr>
            <th style="width: 25%;"></th>
            <th style="width: 75%;">Income</th>
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
            <td class="table-label-cell">Earnings Before Taxes</td>
            <td>
              <CurrencyDisplay :value="salary + otherInc" />
            </td>
          </tr>
          <tr>
            <td class="table-label-cell">Income After Taxes</td>
            <td>
              <CurrencyDisplay class="net-income" :value="incomeAfterTax" />
            </td>
          </tr>
        </tbody>
      </table>
      <table>
        <thead>
          <th style="width: 25%;"></th>
          <th style="width: 75%;">Fixed Costs</th>
        </thead>
        <tbody>
          <tr>
            <td class="table-label-cell">Housing Costs</td>
            <td>
              <CurrencyDisplay :value="individualExpenses[0]" />
            </td>
          </tr>
          <tr>
            <td class="table-label-cell">Internet</td>
            <td>
              <CurrencyDisplay :value="individualExpenses[1]" />
            </td>
          </tr>
          <tr>
            <td class="table-label-cell">Cell Phone</td>
            <td>
              <CurrencyDisplay :value="individualExpenses[2]" />
            </td>
          </tr>
          <tr>
            <td class="table-label-cell">Car Payment</td>
            <td>
              <CurrencyDisplay :value="individualExpenses[3]" />
            </td>
          </tr>
          <tr>
            <td class="table-label-cell">Car Insurance</td>
            <td>
              <CurrencyDisplay :value="individualExpenses[4]" />
            </td>
          </tr>
          <tr>
            <td class="table-label-cell">Other Expenses</td>
            <td>
              <CurrencyDisplay :value="individualExpenses[5]" />
            </td>
          </tr>
          <tr>
            <td class="table-label-cell">Total Fixed Expenses</td>
            <td>
              <CurrencyDisplay class="net-income" :value="totalExpenses" />
            </td>
          </tr>
        </tbody>
      </table>
      <table>
        <thead>
          <th style="width: 25%;"></th>
          <th style="width: 75%;">Variable Expenses</th>
        </thead>
        <tbody>
          <tr>
            <td class="table-label-cell">Electric Bill</td>
              <td >
                <CurrencyDisplay :value="variableExp[0]" />
              </td>
          </tr>
          <tr>
            <td class="table-label-cell">Water, Sewer, & Other Utilities</td>
              <td >
                <CurrencyDisplay :value="variableExp[1]" />
              </td>
          </tr>
          <tr>
            <td class="table-label-cell">Clothing</td>
              <td >
                <CurrencyDisplay :value="variableExp[2]" />
              </td>
          </tr>
          <tr>
            <td class="table-label-cell">Groceries</td>
              <td >
                <CurrencyDisplay :value="variableExp[3]" />
              </td>
          </tr>
          <tr>
            <td class="table-label-cell">Transportation</td>
              <td >
                <CurrencyDisplay :value="variableExp[4]" />
              </td>
          </tr>
          <tr>
            <td class="table-label-cell">Debt Payments</td>
              <td >
                <CurrencyDisplay :value="variableExp[5]" />
              </td>
          </tr>
          <tr>
            <td class="table-label-cell">Miscellaneous</td>
              <td>
                <CurrencyDisplay :value="variableExp[6]" />
              </td>
          </tr>
          <tr>
            <td class="table-label-cell">Total Variable Expenses</td>
              <td>
                <CurrencyDisplay class="net-income" :value="totalVariableExpenses" />
              </td>
          </tr>
        </tbody>
      </table>
      <table>
        <thead>
          <th style="width: 25%;"></th>
          <th style="width: 75%;">Net Cash Flow</th>
        </thead>
        <tbody>
          <tr>
            <td class="table-label-cell">Total Income</td>
              <td>
                <CurrencyDisplay :value="incomeAfterTax" />
              </td>
          </tr>
          <tr>
            <td class="table-label-cell">Total Expenses</td>
              <td>
                <CurrencyDisplay :value="totalExpenses + totalVariableExpenses" />
              </td>
          </tr>
          <tr>
            <td class="table-label-cell">Net Cash Flow</td>
              <td>
                <CurrencyDisplay class="net-income" :value="incomeAfterTax - (totalExpenses + totalVariableExpenses)" />
              </td>
          </tr>
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
