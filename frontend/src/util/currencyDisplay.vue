<template>
  <span>{{ formattedValue }}</span>
</template>

<script>
export default {
  name: 'CurrencyDisplay',
  props: {
    value: {
      type: [Number, String],
      required: true,
    },
    showDollarSign: {
      type: Boolean,
      default: true,
    },
  },
  computed: {
    formattedValue() {
      const numValue = Number(this.value);
      if (isNaN(numValue)) return this.value;
      else {
        const formatted = numValue.toLocaleString('en-US');

        return this.showDollarSign ? `$${formatted}` : formatted;
      }
    },
  },
};
</script>
