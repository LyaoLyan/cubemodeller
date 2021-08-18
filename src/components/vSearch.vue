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
          console.log("ddddd");
          this.$emit("searched", {
              choosen: true,
              item: this.item
          })
      }
  }
};
</script>
