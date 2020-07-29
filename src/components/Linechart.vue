<script>
import { Line, mixins } from "vue-chartjs";
const { reactiveProp } = mixins;
export default {
  extends: Line,
  props: {
    data: Array,
    labels: Array,
    name: String,
    render: Boolean
  },
  mixins: [reactiveProp],
  mounted() {
    this.renderChart(this.chartData);
  }
};
</script>
