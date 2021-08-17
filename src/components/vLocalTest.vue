<template>
  <div class="content">
    <div class="content-body"></div>
    <div class="content-info">
      <div class="info__about">
        <div class="info__about__title">Selected Metrics</div>
        <div class="info__about__alert">
          <button class="alert-btn">
            <img src="../assets/alert-circle.svg" alt="" />
          </button>
        </div>
      </div>
      <div class="info__table">
        <div class="info__table-title">
          <div class="info__table-title__name">Name</div>
          <div class="info__table-title__axis">Axis</div>
          <div class="info__table-title__statistic">Statistic</div>
          <div class="info__table-title__period">Period</div>
          <div class="info__table-title__delete"></div>
        </div>
        <div class="info__table-rows">
          <v-choosen-metric
            v-for="metric in choosenMetrics"
            :key="metric.id"
            :metric="metric"
          ></v-choosen-metric>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import vChoosenMetric from "./vChoosenMetric.vue";

export default {
  components: {
    vChoosenMetric,
  },
  data() {
    return {
      choosenMetrics: [
        { id: 0, name: "Metrica 1" },
        { id: 1, name: "Metrica 2" },
      ],
    };
  },
};
</script>

<style scoped lang="scss">
.content {
  display: flex;
  flex-direction: column;
  width: 100%;
  height: 100%;
  background: #ffffff;
  /* stroke */

  box-sizing: border-box;
  border-radius: 13px;
  border: 1px solid #ebebeb;
  &-body {
    flex-basis: 56%;
    background-color: #eef1fa;
    border-radius: 13px 13px 0 0;
  }
  &-info {
    display: flex;
    flex-direction: column;
    // align-items: center;
    padding: 10px 20px;
  }
}
.info {
  &__about {
    display: flex;
    align-items: center;
    &__title {
    }
    &__alert {
      margin-right: 7px;
      margin-left: 7px;
    }
  }
  &__table {
    display: flex;
    flex-direction: column;
    &-title {
      display: flex;
      width: 100%;
      color: #919699;
      font-size: 12px;
      &__name {
        flex-grow: 1;
        padding-left: 10px;
      }
      &__axis {
        flex-basis: 10%;
      }
      &__statistic {
        flex-basis: 12%;
      }
      &__period {
        flex-basis: 15%;
      }
      &__delete {
        flex-basis: 5%;
      }
    }
  }
}
</style>