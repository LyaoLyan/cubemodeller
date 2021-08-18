<script>
import { Area } from "vue-chartjs";
export default {
  extends: Area,
  props: {
    chartdata: {
      type: Object,
      default: null,
    },
    options: {
      type: Object,
      default: null,
    }
  },
  mounted() {
    this.renderChart(this.chartdata, this.options)
  },
};
</script>
