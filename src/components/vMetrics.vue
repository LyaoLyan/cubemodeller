<template>
  <div class="container">
    <div class="container-header">
      <div class="header-row">
        <div class="header-row-title">Metrics</div>
        <div class="header-row-alert">
          <button>
            <img src="../assets/alert-circle.svg" alt="" />
          </button>
        </div>
        <div class="header-row-search">
          <span class="search-icon"
            ><img src="../assets/search.svg" alt=""
          /></span>
          <input class="search-input" type="search" />
        </div>
        <div class="header-row-add">
          <button class="add-btn">
            <img src="../assets/add.svg" alt="" />
          </button>
        </div>
      </div>
    </div>
    <div class="container-body">
      <ul class="options">
        <li class="options__item">
          <details class="options__item-details">
            <summary class="options__item-details-summary">Templates</summary>
            <ul class="options__item-details-list">
              <v-metric
                v-for="li in ul"
                :key="Number(Object.keys(li)[0])"
                :li="li"
                @chooseMetric="chooseMetric"
              ></v-metric>
            </ul>
          </details>
        </li>
        <li class="options__item">
          <details class="options__item-details">
            <summary class="options__item-details-summary">Data pool</summary>
            <li></li>
            <li></li>
            <li></li>
          </details>
        </li>
        <li class="options__item">
          <details class="options__item-details">
            <summary class="options__item-details-summary">Custom</summary>
            <li></li>
            <li></li>
            <li></li>
          </details>
        </li>
      </ul>
    </div>
    <div class="container-footer"></div>
  </div>
</template>

<script>
import vMetric from "./vMetric.vue";
export default {
  components: {
    vMetric,
  },
  data() {
    return {
     
      choosenMetric: [],
    };
  },
  props: {
    ul: Array
  },
  methods: {
    chooseMetric(data) {
      if (data.push) {
        this.choosenMetric.push(data.item);
      } else {
        function checkIndex(element) {
          return Number(Object.keys(element)[0]) == data.id
        }
        this.choosenMetric.splice(this.choosenMetric.findIndex(checkIndex), 1)
      }
      console.log(this.choosenMetric);
      this.$emit("chooseMetric", {
        choosenMetric: this.choosenMetric})
    },
  },
};
</script>

<style lang="scss" scoped>
.header-row-search {
  position: relative;
  vertical-align: middle;
  white-space: nowrap;
}
.search {
  &-input {
    background: #ffffff;
    padding-left: 20px;
    border: 1.23597px solid #ece9f1;
    box-sizing: border-box;
    border-radius: 9px;
    &:-moz-placeholder {
      color: #65737e;
    }
    &::-webkit-search-cancel-button {
      -webkit-appearance: none;
    }
    &::-webkit-search-results-button {
      -webkit-appearance: none;
    }
  }
  &-icon {
    position: absolute;
    z-index: 1;
    margin-left: 5px;
    margin-top: 2px;
  }
}
.container {
  height: 100%;
}
.container-body {
  // height: 100%;
  .options {
    margin: 0px;
    padding-top: 13px;
    &__item {
      color: rgba(116, 89, 217, 1);
      font-size: 14px;
      padding-bottom: 5px;
      list-style-type: none;

      &-details {
        &-summary {
          list-style-type: none;
          &::-webkit-details-marker {
            display: none;
          }
          &::marker {
            display: none;
          }
          &::before {
            padding-right: 5px;
            content: url("../assets/open.svg");
          }
        }
        &[open] > summary::before {
          padding-right: 0px;
          content: url("../assets/opened.svg");
        }

        &-list {
          padding-left: 6px;
          &-item {
            color: #4f4f4f;
            list-style-type: none;
            &__checkbox {
              position: absolute;
              z-index: -1;
              opacity: 0;
            }
            &__checkbox + &__label {
              display: inline-flex;
              align-items: center;
              user-select: none;
            }
            &__checkbox + label::before {
              content: "";
              display: inline-block;
              width: 1em;
              height: 1em;
              flex-shrink: 0;
              flex-grow: 0;
              border: 1px solid #adb5bd;
              border-radius: 0.25em;
              margin-right: 0.5em;
              background-repeat: no-repeat;
              background-position: center center;
              background-size: 50% 50%;
            }
            &__checkbox:checked + label::before {
              border-color: #7459d9;
              background-color: #7459d9;
              background-size: 80%;
              background-image: url("../assets/checkmark.svg");
            }
          }
        }
      }
    }
  }
}
</style>