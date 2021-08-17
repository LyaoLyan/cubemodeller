<template>
  <div class="modal">
    <div class="modal__panel">
      <div class="modal__panel-title">
        <div class="title-row"></div>
        Cube modeler
        <button>
          <img
            class="modal__panel-title-alert"
            src="../assets/alert-circle.svg"
            alt=""
          />
        </button>
      </div>
      <div class="modal__panel-test">
        <img class="modal__panel-test-edit" src="../assets/edit.svg" alt="" />
        Local test
      </div>
      <div class="modal__panel-buttons">
        <div class="modal__panel-buttons-chat">
          <button class="modal__panel-buttons-chat-btn">
            <img
              class="modal__panel-buttons-chat-img"
              src="../assets/chat.svg"
              alt=""
            />
          </button>
        </div>
        <div class="modal__panel-buttons-load">
          <button class="modal__panel-buttons-load-btn">
            <img
              class="modal__panel-buttons-load-img"
              src="../assets/load.svg"
              alt=""
            />
          </button>
        </div>
        <div class="modal__panel-buttons-save">
          <button class="modal__panel-buttons-save-btn">Save</button>
        </div>
        <div class="modal__panel-buttons-exit">
          <button class="modal__panel-buttons-exit-btn">
            <img src="../assets/exit.svg" alt="" />
          </button>
        </div>
      </div>
    </div>
    <div class="modal__content">
      <div class="content__select">
        <div class="content__select-widget">
          <v-widget></v-widget>
        </div>
        <div class="content__select-metrics">
          <v-metrics></v-metrics>
        </div>
      </div>
      <div class="content__localtest">
        <v-local-test></v-local-test>
      </div>
    </div>
  </div>
</template>

<script>
import vWidget from "./vWidget.vue";
import vMetrics from "./vMetrics.vue";
import vLocalTest from "./vLocalTest.vue";
export default {
  name: "vModal",
  components: {
    vWidget,
    vMetrics,
    vLocalTest,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@400;500&display=swap");
.modal {
  width: 1200px;
  height: 620px;
  background-color: #f9f9f9;
  flex-direction: column;
  margin-left: auto;
  margin-right: auto;
  border: 1, 27px solid;
  font-family: "Poppins", sans-serif;
  border-image-source: linear-gradient(0deg, #ece9f1, #ece9f1),
    linear-gradient(0deg, #ebebeb, #ebebeb);
  border-radius: 13px;
  display: flex;
  &__panel {
    display: flex;
    margin: 10px 30px;
    // width: 100%;
    justify-content: space-between;
    &-title {
      width: 330px;
      display: flex;
      align-items: center;
      &-alert {
        margin-right: 7px;
        margin-left: 7px;
      }
    }
    &-test {
      width: 33%;
      display: flex;
      align-items: center;
      &-edit {
        margin-right: 7px;
        margin-left: 7px;
      }
    }
    &-buttons {
      display: flex;
      width: 25%;
      justify-content: space-between;
      align-items: center;
      &-chat {
        &-btn {
          border: none;
          background: none;
        }
      }
      &-load {
        &-btn {
          background: #ffffff;
          border: none;
          box-shadow: 0px 2px 15px rgba(68, 68, 79, 0.1);
          border-radius: 7.45301px;
          padding: 7px 13px;
        }
      }
      &-save {
        &-btn {
          background: #22a447;
          border-radius: 9px;
          padding: 7px 45px;
          border: none;
          color: white;
        }
      }
      &-exit {
        &-btn {
          border: none;
          background: none;
        }
      }
    }
  }
}
.modal__content {
  display: flex;
  
}
.content {
  &__select {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    &-widget {
      margin-bottom: 10px;
    }
  }
  &__localtest {
    margin-left:10px;
    width: 100%;
    height: 100%;
  }
}
</style>
