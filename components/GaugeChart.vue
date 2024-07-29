<!-- <template>
  <div v-if="this.randomNumber">
    <GaugeChart :data="[this.randomNumber]" />
  </div>
</template> -->

<script>
import { Doughnut } from 'vue-chartjs';
import Chart from 'chart.js';

export default {
  name: 'GaugeChart',
  extends: Doughnut,
  props: {
    data: {
      type: Array,
      required: true
    }
  },
  watch: {
    data(newVal) {
      this.updateChart(newVal[0]);
    }
  },
  mounted() {
    this.renderChart({
      datasets: [{
        data: [this.data[0], 100 - this.data[0]],
        backgroundColor: ['#00FF66', '#ddd'],
        borderWidth: 2
      }]
    }, {
      circumference: Math.PI,
      rotation: Math.PI,
      cutoutPercentage: 80,
      tooltips: {
        callbacks: {
          label: function(tooltipItem, data) {
            return `Speed: ${data.datasets[0].data[tooltipItem.index]}%`;
          }
        }
      }
    });
  },
  methods: {
    updateChart(value) {
      this.renderChart({
        datasets: [{
          data: [value, 100 - value],
          backgroundColor: ['#00FF66', '#ddd'],
          borderWidth: 2
        }]
      }, {
        circumference: Math.PI,
        rotation: Math.PI,
        cutoutPercentage: 80,
        tooltips: {
          callbacks: {
            label: function(tooltipItem, data) {
              return `Speed: ${data.datasets[0].data[tooltipItem.index]}%`;
            }
          }
        }
      });
    }
  }
};
</script>

<style scoped>
canvas {
  width: 75% !important;
  height: auto !important;
}
</style>
