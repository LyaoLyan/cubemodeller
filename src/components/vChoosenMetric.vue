<template>
  <div class="metric">
    <div class="metric__name">{{ metric.name }}</div>
    <div class="metric__axis">
      <!-- <input class="metric__axis-list" type="list" list="axis" /> -->
      <select class="metric__axis-list" name="select">
        <option class="metric__axis-option" selected value="s1">x</option>
        <option class="metric__axis-option" value="s2">y</option>
      </select>
    </div>
    <div class="metric__statistic">
      <select class="metric__statistic-list" name="select">
        <option class="metric__statistic-option" selected value="s1">
          sum
        </option>
        <option class="metric__statistic-option" value="s2">
          average
        </option>
      </select>
    </div>
    <div class="metric__period">
      <select class="metric__period-list" name="select">
        <option selected value="s1">5 min</option>
        <option value="s2">10 min</option>
        <option value="s3">15 min</option>
      </select>
    </div>
    <div class="metric__delete">
      <button class="delete-btn">
        <img class="delete-img" src="../assets/delete.svg" alt="" />
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    metric: Object,
  },
};
</script>

<style lang="scss" scoped>
.metric {
  color: #4f4f4f;
  font-size: 14px;
  display: flex;
  width: 100%;
  border-bottom: 0.6px solid #dfe0eb;
  padding-bottom: 7px;
  padding-top: 7px;
  padding-left: 10px;
  &:hover {
    background: #ffffff;
    box-shadow: 0px 2px 15px rgba(68, 68, 79, 0.1);
    border-radius: 9px;

    .metric__axis-list,
    .metric__statistic-list,
    .metric__period-list {
      border: 1px solid #ece9f1;
      padding: 0px 0px 0px 5px;
      background: url("../assets/opened.svg") no-repeat 90% center;
      background-size: 10px 10px;
    }
  }
  &__axis-list,
  &__statistic-list,
  &__period-list {
    width: 80%;
    font-size: 12px;
    border: none;
    box-sizing: border-box;
    border-radius: 5px;
    height: 1.8em;
    padding: 0px 0px 0px 6px;
    appearance: none;
  }
  &__name {
    flex-grow: 1;
  }
  &__axis {
    flex-basis: 10%;
    &-list {
      color: #ffaa00;
      font-family: inherit;
    }
    &:active {
        color: #ffaa00;
    }
    &-option {
      &:focus{
        color: #ffaa00;
      }
    }
  }
  &__statistic {
    &-list {
      color: #ff0099;
      font-family: inherit;
    }
    flex-basis: 12%;
  }
  &__period {
    &-list {
      color: #4262fe;
      font-family: inherit;
    }
    flex-basis: 15%;
  }
  &__delete {
    flex-basis: 5%;
  }
}
.delete-img {
  color: red;
}
</style>
