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
          <v-widget @chooseChart="chooseChart"></v-widget>
        </div>
        <div class="content__select-metrics">
          <v-metrics @chooseMetric="chooseMetric" :ul="ul"></v-metrics>
        </div>
      </div>
      <div class="content__localtest">
        <v-local-test 
          :choosenMetric="choosenMetric"
          :choosenChart="choosenChart"
        ></v-local-test>
      </div>
    </div>
    <v-custom :metrics="ul"></v-custom>
  </div>
</template>

<script>
import vWidget from "./vWidget.vue";
import vMetrics from "./vMetrics.vue";
import vLocalTest from "./vLocalTest.vue";
import vCustom from "./vCustom.vue";
export default {
  name: "vModal",
  components: {
    vWidget,
    vMetrics,
    vLocalTest,
    vCustom,
  },
  data() {
    return {
      choosenMetric: [],
      choosenChart: "",
       ul: [
        {0: { name: "Metrica 1" }},
        {1: { name: "Metrica 2" }},
        {2: { name: "Metrica 3" }},
      ],
    };
  },
  methods: {
    chooseMetric(data) {
      this.choosenMetric = data.choosenMetric;
    },
    chooseChart(data) {
      this.choosenChart = data.choosenChart;
    },
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
