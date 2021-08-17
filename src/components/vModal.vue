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
    <div class="modal-footer">
      <div class="footer__add">
        <button class="add-btn"><img src="../assets/add.svg" alt=""></button>
      </div>
      <div class="footer__metrica">
        <input class="footer__metrica-input" type="text" placeholder="Metrica" />
      </div>
      <div class="footer__formula">
        <input class="footer__formula-input" type="text" placeholder="Formula" />
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
  width: 61%;
  height: 67%;
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
      width: 46%;
      display: flex;
      align-items: center;
      &-edit {
        margin-right: 7px;
        margin-left: 7px;
      }
    }
    &-buttons {
      display: flex;
      width: 36%;
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
  &-footer {
    margin-top: 10px;
    border-radius: 0px 0px 13px 13px;
    flex-basis: 6%;
    background: #eef1fa;
    display: flex;
    border-top: 1.5px solid #dfe0eb;
  }
}
.footer {
  &__add {
    flex-basis: 4%;
    display: flex;
justify-content: center;
  }
  &__metrica {
    flex-basis: 50%;
    border-right: 1.5px solid #dfe0eb;
    border-left: 1.5px solid #dfe0eb;
    &-input {
      width: 100%;
      height: 100%;
      background: none;
      border: none;
      padding: 0px;
      margin: 0px;
      padding-left: 10px;
      font-family: 'Inter', sans-serif;
      letter-spacing: 2px;


      &:focus {
        outline: none;
// border: #33A3FA05 1px solid;
      }
      &::placeholder {
        color: #11263C;
        opacity: 0.2;
        // font-family: 'Inter', sans-serif;
      }
    }
  }
  &__formula {
    flex-basis: 45%;
    &-input {
      width: 100%;
      height: 100%;
      background: none;
      border: none;
      padding: 0px;
      margin: 0px;
      padding-left: 10px;
      font-family: 'Inter', sans-serif;
      letter-spacing: 2px;


      &::placeholder {
        color: #11263C;
        opacity: 0.2;
        // font-family: 'Inter', sans-serif;
      }
      &:focus {
        outline: none;

border-radius: 0px 0px 13px 0px;
      }
    }
  }
}
.modal__content {
  display: flex;
  height: 85%;
}
.content {
  display: flex;
  &__select {
    display: flex;
    flex-basis: 20%;
    height: 100%;
    flex-direction: column;
    &-widget {
      margin-bottom: 10px;
      flex-basis: 40%;
    }
    &-metrics {
      flex-basis: 60%;
    }
  }
  &__localtest {
    margin-left: 30px;
    margin-right: 16px;
    flex-grow: 1;
  }
}

</style>
