<template>
    <span :class="{ 'text-red-500': isNegative }">
      {{ formattedValue }}
    </span>
  </template>
  
  <script>
  export default {
    name: 'PercentDisplay',
    props: {
      value: {
        type: [Number, String],
        required: true,
        validator: function (value) {
          return !isNaN(Number(value));
        },
      },
      showPercentSign: {
        type: Boolean,
        default: true,
      },
      decimals: {
        type: Number,
        default: 2,
        validator: function (value) {
          return value >= 0;
        },
      },
      useGrouping: {
        type: Boolean,
        default: true,
      },
    },
    computed: {
      numericValue() {
        return Number(this.value);
      },
      isNegative() {
        return this.numericValue < 0;
      },
      formattedValue() {
        if (isNaN(this.numericValue)) {
          return '0%';
        }
  
        const formatter = new Intl.NumberFormat('en-US', {
          minimumFractionDigits: this.decimals,
          maximumFractionDigits: this.decimals,
          useGrouping: this.useGrouping,
          style: 'decimal',
        });
  
        const formatted = formatter.format(this.numericValue);
        return this.showPercentSign ? `${formatted * 100}%` : formatted;
      },
    },
  };
  </script>
  
