<template>
  <div id="app">
    <button v-on:click="openModal()">Open modal</button>

    <div class="modal__off" :class="{ modal__on: toCreate }">
      <v-modal />
    </div>
  </div>
</template>

<script>
import vModal from "./components/vModal.vue";

export default {
  name: "App",
  components: {
    vModal,
  },
  data() {
    return {
      toCreate: false,
    };
  },
  methods: {
    openModal() {
      if (this.toCreate) {
        this.toCreate = false;
      } else {
        this.toCreate = true;
      }
    },
  },
};
</script>

<style lang="scss">
.modal {
  &__off {
    display: flex;
    align-items: center;
    position: fixed;
    left: 0;
    width: 100%;
    height: 100%;
    opacity: 0;
    pointer-events: none;
    background: rgba(0, 0, 0, 0.5);
    top: 0;
  }
  &__on {
    opacity: 1;
    pointer-events: auto;
  }
}
.container {
  width: 330px;
  margin-left: 16px;
  
  &-header {
    width: inherit;
    height: 50px;
    background-color: #ffffff;
    box-sizing: border-box;
    border-radius: 13px 13px 0 0;
    border: 1px solid #EBEBEB;
  }
  &-body {
    background-color: #eef1fa;
    height: 25vh;
  }
  &-footer {
    border-radius: 0 0 13px 13px;
    height: 5vh;
    background: #ffffff;
    border: 1px solid #EBEBEB;
  }
}
.header {
  &-row {
    height: 100%;
    padding: 0px 5px;
    display: flex;
    padding: 0px 21px;
    justify-content: space-between;
    // padding: 12px;
    align-items: center;
    
  }
}
button {
  border: none;
  background: none;
  padding: 0px;
  padding-top: 5px;
  margin: 0px;
}
</style>
