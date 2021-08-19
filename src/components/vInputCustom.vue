<template>
  <div class="footer">
    <div class="footer__add">
      <button v-on:click="addMetrica()" class="add-btn"><img src="../assets/add.svg" alt="" /></button>
    </div>
    <div class="footer__metrica">
      <input
        class="footer__metrica-input"
        type="text"
        placeholder="Metrica"
        v-model="metricaName"
      />
    </div>
    <div class="footer__formula">
      <div class="footer__formula__place">
        <v-input-custom-formula
          v-for="element in formula"
          :key="element.id"
          :element="element"
          @removeFromFormula="removeFromFormula"
        ></v-input-custom-formula>

        <input
          :style="style"
          class="footer__formula__place-input"
          type="text"
          placeholder="Formula"
          v-model="input"
        />

        <!-- <span class="footer__formula__place" v-model="formula" contenteditable="true"></span> -->
      </div>
      <!-- <v-search v-for="(item, index) in metricsList_n" :key="index"></v-search> -->
      <!-- {{metricsList_n}} -->
      <div
        class="footer__formula__search focus_no"
        :class="{ focus_yes: input }"
      >
        <v-search
          v-for="(item, index) in metricsList_n"
          :key="index"
          :item="item"
          @searched="searched"
        ></v-search>
      </div>
    </div>
  </div>
</template>

<script>
import vSearch from "./vSearch.vue";
import vInputCustomFormula from "./vInputCustomFormula";
export default {
  components: {
    vSearch,
    vInputCustomFormula,
  },
  data() {
    return {
      metricaName: "",
      input: "",
      choosen: false,
      formula: [],
      signs: [],
      idElementFormula: 0,
      idMetrica: this.lastId
    };
  },
  props: {
    metrics: Array,
    lastId: Number
  },
  mounted() {},
  methods: {
    addMetrica() {
      let customMetrica = {
        id: ++this.idMetrica,
        name: this.metricaName,
        checked: false,
        formula: this.formula
      }
      this.$emit("addCustom", {
        item: customMetrica
      })
      this.idElementFormula++;
      this.formula = []
      this.metricaName = ""
      this.input = ""

    },
    removeFromFormula(data) {
      function checkIndex(element) {
        return element.id == data.id;
      }
      this.formula.splice(this.formula.findIndex(checkIndex), 1);
      console.log(this.formula);
    },
    searched(data) {
      this.choosen = data.choosen;
      if (data.isNumber) {
        this.formula.push({ id: this.idElementFormula, name: this.input });
      } else {
        this.formula.push({ id: this.idElementFormula, name: data.item });
      }

      this.idElementFormula++;
      this.input = "";
      console.log(this.formula);
    },
  },
  computed: {
    style() {
      return { width: "30%" };
    },
    metricsList_n() {
      let re = /^[+-]?([0-9]*[.])?[0-9]+$/;
      var names = [];
      for (let x in this.metrics) {
        names.push(this.metrics[x].name);
      }

      let signs = ["+", "-", "/", "*"];

      let obj = [...names, ...signs];

      // let obj = this.metrics;
      let newArray = [];
      const serach = this.input.toLowerCase();
      obj.forEach((element) => {
        if (element.toLowerCase().indexOf(serach) == 0) {
          newArray.push(element);
        }
      });
      if (re.test(this.input)) {
        newArray.push("Number");
      }
      return newArray;
      //   for (obj in this.metrics) {
      //     // el = obj[key];
      //     // if (el.name.toLowerCase().indexOf(serach) != -1) newArray.push(el);
      //     console.log(obj);
      //   }
      //   console.log(newArray);
      //   return newArray;
    },
  },
};
</script>

<style lang="scss" scoped>
.focus {
  &_no {
    display: none;
    position: relative;
  }
  &_yes {
    display: block;
  }
}
.footer {
  margin-top: 10px;
  border-radius: 0px 0px 13px 13px;
  flex-basis: 6%;
  background: #eef1fa;
  display: flex;
  border-top: 1.5px solid #dfe0eb;
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
      font-family: "Inter", sans-serif;
      letter-spacing: 2px;

      &:focus {
        outline: none;
        // border: #33A3FA05 1px solid;
      }
      &::placeholder {
        color: #11263c;
        opacity: 0.2;
        // font-family: 'Inter', sans-serif;
      }
    }
  }
  &__formula {
    flex-basis: 45%;
    display: flex;
    flex-direction: column;
    &__search {
      margin-top: 36px;
      position: absolute;
      background: #eef1fa;
      border-radius: 0px 0px 13px 13px;
      padding: 10px;
    }
    &__place {
      height: 100%;
      &-input {
        width: 100%;
        height: 100%;
        background: none;
        border: none;
        padding: 0px;
        margin: 0px;
        padding-left: 10px;
        font-family: "Inter", sans-serif;
        letter-spacing: 2px;

        &::placeholder {
          color: #11263c;
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
}
</style>
