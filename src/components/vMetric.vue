<template>
  <li class="metric">
    <div class="metric__item">
      <input
        @click="chooseMetric()"
        class="item__checkbox"
        :id="'metric-' + li.id"
        type="checkbox"
        :checked="li.checked"
      /><label class="item__label" :for="'metric-' + li.id"
        ><input class="item__label-input" type="text" v-model="name" :disabled="isDisable" />
      </label>
    </div>

    <div class="metric__buttons">
      <div class="metric__buttons-edit">
        <button @click="editNameMetric" class="edit-btn">
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
    li: Object,
  },
  data() {
    return {
      checked: this.li.checked,
      isDisable: true,
      name: this.li.name
    };
  },
  methods: {
    // editNameMetric() {
    //   this.isDisable = !this.isDisable
    //   this.$emit("editNameMetric", {
    //     id: this.id,
    //     name: this.name
    //   })
    // },
    chooseMetric() {
      if (this.li.checked) {
        this.checked = false;
      } else {
        this.checked = true;
      }
      this.$emit("chooseMetric", {
        id: this.li.id,
        isChecked: this.checked,
      });
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
  &__label {
    &-input:disabled {
      border: none;
      width: 100%;
      outline: none;
      background-color: inherit;
      font-family: inherit;
      color: inherit;
    }
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
