<template>
  <span
    class="element"
    v-on:click="removeFromFormula()"
    :class="{ element__sign: isSign }"
  >
    {{ element.name }}
  </span>
</template>

<script>
export default {
  props: {
    element: Object,
  },
  methods: {
    removeFromFormula() {
      this.$emit("removeFromFormula", {
        id: this.element.id,
      });
    },
  },
  computed: {
    isSign() {
      const sign = /[\-\[\]\/\\\{\}\(\)\*\+\?\.\^\$\|]/;
      const num = /^[+-]?([0-9]*[.])?[0-9]+$/;
      return !!(sign.test(this.element.name) || num.test(this.element.name));
    },
  },
};
</script>

<style lang="scss" scoped>
.element {
  margin-left: 5px;
  padding: 3px 7px 3px 10px;
  text-align: center;
  font-size: 14px;
  color: #22a447;
  background: rgba(36, 255, 0, 0.2);
  border-radius: 9px;
  &__sign {
    background: none;
    color: black;
    padding: 0;
  }
}
</style>

