<script>
import { Doughnut, mixins } from 'vue-chartjs';
import Chart from 'chart.js';
const { reactiveProp } = mixins;

Chart.pluginService.register({
  beforeDraw: function (chart) {

  }
});

export default {
  name: 'GaugeChart',
  extends: Doughnut,
  mixins: [reactiveProp],
  props: {
    data: {
      type: Array,
      required: true
    },
    chartData: {
      type: Object,
      default() {
        return {
          datasets: [{
            data: [0, 100],
            backgroundColor: ['#00FF66', '#ddd'],
            borderColor: '#000',
            borderWidth: 1
          }]
        };
      }
    },
    options: {
      type: Object,
      default() {
        return {
          circumference: Math.PI,
          rotation: Math.PI,
          cutoutPercentage: 80,
          responsive: true,
          maintainAspectRatio: false,
          tooltips: {
            callbacks: {
              label: function(tooltipItem, data) {
                return `Speed: ${data.datasets[0].data[tooltipItem.index]}`;
              }
            }
          }
        };
      }
    }
  },
  watch: {
    data(newVal) {
      this.updateChart(newVal[0]);
    }
  },
  mounted() {
    this.renderChart(this.chartData, this.options);
  },
  methods: {
    updateChart(value) {
      this.chartData.datasets[0].data = [value, 100 - value];
      this.$data._chart.update();
    }
  }
};
</script>

<style scoped>
canvas {
  width: 100% !important;
  height: auto !important;

}
</style>
