<template>
  <div class="content">
    <div class="content-body">
      <v-line-chart
        v-if="choosenChart == 'line'"
        :chartdata="chartdata"
        :options="options"
        class="chart"
      />
      <v-bar-chart
        v-if="choosenChart == 'bar'"
        :chartdata="chartdata"
        :options="options"
        class="chart"
      />
      <v-radar-chart
        v-if="choosenChart == 'radar'"
        :chartdata="chartdata"
        :options="options"
        class="chart"
      />
      <v-scatter-chart
        v-if="choosenChart == 'scatter'"
        :chartdata="chartdata"
        :options="options"
        class="chart"
      />
      <v-bubble-chart
        v-if="choosenChart == 'bubble'"
        :chartdata="chartdata"
        :options="options"
        class="chart"
      />
    </div>
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
            v-for="item in choosenMetric"
            :key="Number(Object.keys(item)[0])"
            :item="item"
          ></v-choosen-metric>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import vChoosenMetric from "./vChoosenMetric.vue";
import vLineChart from "./charts/vLineChart.vue";
import vBarChart from "./charts/vBarChart.vue";
import vRadarChart from "./charts/vRadarChart.vue";
import vBubbleChart from "./charts/vBubbleChart.vue";
import vScatterChart from "./charts/vScatterChart.vue";

export default {
  components: {
    vChoosenMetric,
    vLineChart,
    vBarChart,
    vRadarChart,
    vBubbleChart,
    vScatterChart,
  },
  data() {
    return {
      chartdata: {
        labels: [
          "January",
          "February",
          "March",
          "April",
          "May",
          "June",
          "July",
          "August",
          "September",
          "October",
          "November",
          "December",
        ],
        datasets: [
          {
            label: "Data One",
            data: [40, 20, 12, 39, 10, 40, 39, 80, 40, 20, 12, 11],
          },
        ],
      },
      options: {
        responsive: true,
        maintainAspectRatio: false,
      },
    };
  },
  props: {
    choosenMetric: Array,
    choosenChart: String,
  },
  mounted() {},
  methods: {},
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
    display: flex;
    align-items: center;
    justify-content: center;
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
.chart {
  height: 20vh;
  width: 20vw;
  background: #ffffff;
  box-shadow: 4px 4px 25px rgba(207, 212, 255, 0.5);
  border-radius: 9px;
}
</style>