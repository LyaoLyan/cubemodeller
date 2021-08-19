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
        
        <input class="modal__panel-test-input" type="text" v-model="name">
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
          <v-metrics
            @chooseMetric="chooseMetric"
            @chooseCustomMetric="chooseCustomMetric"
            :ul="ul"
            :customMetrics="customMetrics"
          ></v-metrics>
        </div>
      </div>
      <div class="content__localtest">
        <v-local-test
          :choosenMetric="checkedMetric"
          :choosenCustomMetric="checkedCustomMetric"
          :choosenChart="choosenChart"
          @removeFromChoosenMetric="removeFromChoosenMetric"
        ></v-local-test>
      </div>
    </div>
    <v-input-custom
      :metrics="ul"
      :lastId="ul[ul.length-1].id"
      @addCustom="addCustom"
    ></v-input-custom>
  </div>
</template>

<script>
import vWidget from "./vWidget.vue";
import vMetrics from "./vMetrics.vue";
import vLocalTest from "./vLocalTest.vue";
import vInputCustom from "./vInputCustom.vue";
export default {
  name: "vModal",
  components: {
    vWidget,
    vMetrics,
    vLocalTest,
    vInputCustom,
  },
  data() {
    return {
      choosenChart: "",
      ul: [
        { id: 0, name: "Metrica 1", checked: false },
        { id: 1, name: "Metrica 2", checked: false },
        { id: 2, name: "Metrica 3", checked: false },
        { id: 3, name: "Metrica 4", checked: false },
        { id: 4, name: "Metrica 5", checked: false },
        { id: 5, name: "Metrica 6", checked: false },
        { id: 6, name: "Metrica 7", checked: false },
      ],
      customMetrics: [],
      // id здесь сделано статичным, надо бы привязать к последнему id ul
      id: 6,
      name: "Local Test"
    };
  },
  methods: {
    addCustom(data) {
      this.customMetrics.push(data.item);
    },
    chooseMetric(data) {
      this.ul[data.id].checked = data.isChecked;
    },
    chooseCustomMetric(data) {
      this.customMetrics[data.id-this.id-1].checked = data.isChecked;
    },
    chooseChart(data) {
      this.choosenChart = data.choosenChart;
    },
    removeFromChoosenMetric(data) {
      this.ul[data.id].checked = false;
    },
  },
  // created() {
  //   if (this.customMetrics.length) {
  //     // console.log("CUSTOMMETRIC IS NOT NULL", Number(this.customMetrics[this.customMetrics.length-1].id + 1));
  //     this.id = Number(
  //       this.customMetrics[this.customMetrics.length - 1].id + 2
  //     );
  //   } else {
  //     this.id = Number(this.ul[this.ul.length - 1].id + 1);
  //   }
  // },
  created() {
    // this.id = ;
  },
  computed: {
    
    checkedMetric() {
      var arr = [];
      this.ul.forEach((element) => {
        if (element.checked) {
          arr.push(element);
        }
      });
      console.log(arr);
      return arr;
    },
    checkedCustomMetric() {
      var arr = [];
      this.customMetrics.forEach((element) => {
        if (element.checked) {
          arr.push(element);
        }
      });
      console.log(arr);
      return arr;
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
      &-input {
        background-color: inherit;
        outline: none;
        border: none;
        border-bottom: 1px solid #DFE0EB;
        font-size: inherit;
        font-family: inherit;
        width: 5vw;
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
