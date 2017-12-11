<template>
  <div class="inputs">
    <b-row v-for="item in items" :key="item.key">
      <b-form-text
        size="lg"
      >{{item.label}}</b-form-text>
      <b-form-checkbox
        style="margin-left: 10px"
        v-if="item.type === 'checkbox'"
        v-model="item.value"
      ></b-form-checkbox>
      <b-form-input
        v-else
        v-model="item.value"
      ></b-form-input>
    </b-row>
  </div>
</template>

<script>
export default {
  name: 'inputs',
  props: ['value'],
  data() {
    return {
      items: [
        { key: 'text', label: 'Text', value: '' },
        { key: 'link', label: 'Link', value: '' },
        { key: 'badge', label: 'Badge', value: '' },
        { key: 'alert', label: 'Alert', value: false, type: 'checkbox' },
      ],
    };
  },
  computed: {
    modelStatus() {
      return this.items.reduce((memo, item) => {
        if (item.value) {
          // eslint-disable-next-line
          memo[item.key] = item.value;
        }
        return memo;
      }, {});
    },
  },
  watch: {
    modelStatus(ms) {
      this.$emit('input', ms);
    },
  },
};
</script>
<<style>
div.inputs {
  padding: 10px;
}
</style>
