<template>
  <li class="metric">
    <div class="metric__item">
      <input
        class="item__checkbox"
        :id="'metric-' + index"
        type="checkbox"
         @click="chooseMetric()"
      /><label class="item__label" :for="'metric-' + index">{{
        li.name
      }}</label>
    </div>

    <div class="metric__buttons">
      <div class="metric__buttons-edit">
        <button class="edit-btn">
          <img src="../assets/edit.svg" alt="" />
        </button>
      </div>

      <div class="metric__buttons-delete">
        <button class="delete-btn">
          <img class="delete-img" src="../assets/delete.svg" alt="" />
        </button>
      </div>
    </div>
  </li>
</template>

<script>
export default {
  name: "vMetric",
  props: {
    index: Number,
    li: Object,
  },
  data() {
    return {
      choosenMetric: [],
      choosen: false,
    };
  },
  methods: {
    chooseMetric() {
    //   if (this.choosen == false) {
    //     this.choosenMetric.push(this.li);
    //   } else {
    //     function checkIndex(element) {
    //       return element.index == this.choosenMetric.index;
    //     }
    //     this.choosenMetric.splice(this.choosenMetric.findIndex(checkIndex), 1);
    //     this.choosen = true;
    //   }
    this.$emit("chooseMetric", {
        item: this.li
    })
    },
  },
};
</script>

<style lang="scss" scoped>
.item {
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
.metric {
  width: 90%;
  display: flex;
  justify-content: space-between;
  border-left: 1px solid #adb5bd;
  &__item {
    display: flex;
    color: #4f4f4f;
    list-style-type: none;

    margin-left: 15px;
  }
  &:hover {
    background: #ffffff;
    box-shadow: 0px 2px 15px rgba(68, 68, 79, 0.1);
    border-radius: 9px;
    .metric__buttons {
      opacity: 1;
    }
  }
  &__buttons {
    display: flex;
    opacity: 0;
    user-select: none;
    &-edit,
    &-delete {
      padding: 0 5px;
    }
  }
}
</style>
