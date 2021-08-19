<template>
  <div>
    <button @click="searched()">
      {{ item }}
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  props: {
    item: String,
  },
  methods: {
    searched() {
      let isNumber = false;
      console.log("ddddd");
      if (this.item == "Number") {
        isNumber = true;
      }
      this.$emit("searched", {
        choosen: true,
        item: this.item,
        isNumber: isNumber,
      });
    },
  },
};
</script>
