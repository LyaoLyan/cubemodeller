<template>
  <div class="footer">
    <div class="footer__add">
      <button class="add-btn"><img src="../assets/add.svg" alt="" /></button>
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
          <!-- USE SELECT -->
        <input
          class="footer__formula__place-input"
          type="text"
          placeholder="Formula"
          v-model="formula"
        />
      </div>
      <!-- <v-search v-for="(item, index) in metricsList_n" :key="index"></v-search> -->
      <!-- {{metricsList_n}} -->
      <div
        class="footer__formula__search focus_no"
        :class="{ focus_yes: formula }"
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
export default {
  components: {
    vSearch,
  },
  data() {
    return {
      metricaName: "",
      formula: "",
      choosen: false,
    };
  },
  props: {
    metrics: Array,
  },
  mounted() {
    
    $('.js-example-basic-multiple').select2();

  },
  methods: {
    searched(data) {
      this.choosen = data.choosen;
      this.formula = data.item;
    },
  },
  computed: {
    metricsList_n() {
      let obj = this.metrics;
      let newArray = [];
      const serach = this.formula.toLowerCase();
      obj.forEach((element) => {
        if (
          element[Number(Object.keys(element)[0])].name
            .toLowerCase()
            .indexOf(serach) == 0
        )
          newArray.push(element[Number(Object.keys(element)[0])].name);
      });
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
