<template>
    <main>
      <div>
        <component
          :is="currentPage"
          :form-data="formData"
          @update-form="updateForm"
          @next-page="nextPage"
          @prev-page="prevPage"
        />
      </div>
    </main>
  </template>
  
  <script>
  import { ref } from 'vue';
  import IncomeInputs from './components/bigInputs.vue';
  import FixedExpenses from './components/fixedExpenses.vue';
  import VariableExpenses from './components/variableExpenses.vue';
  import IncomeStatement from './components/incomeStatement.vue';
  
  export default {
    name: 'App',
    components: {
      IncomeInputs,
      FixedExpenses,
      VariableExpenses,
      IncomeStatement,
    },
    data() {
      return {
        currentPageIndex: 0,
        pages: ['IncomeInputs', 'FixedExpenses', 'VariableExpenses', 'IncomeStatement'],
        formData: {
          monthlySalary: '',
          taxBracket: '',
          otherIncome: '',
          expOne: '',
          expTwo: '',
          expThree: '',
          expFour: '',
          expFive: '',
          expSix: '',
          expSeven: '',
          expEight: '',

        },
      };
    },
    computed: {
      currentPage() {
        return this.pages[this.currentPageIndex];
      },
    },
    methods: {
      updateForm(data) {
        this.formData = { ...this.formData, ...data };
      },
      nextPage() {
        if (this.currentPageIndex < this.pages.length - 1) {
          this.currentPageIndex++;
        }
      },
      prevPage() {
        if (this.currentPageIndex > 0) {
          this.currentPageIndex--;
        }
      },
    },
  };
  </script>
  <style></style>
  
