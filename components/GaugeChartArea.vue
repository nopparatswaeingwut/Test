<script>
import { Pie } from 'vue-chartjs';
import Chart from 'chart.js';

export default {
  name: 'GaugeChartArea',
  extends: Pie,
  props: {
    dataArea: {
      type: String,
      required: true
    }
  },
  data() {
    return {
      chartData: {
        labels: [],
        datasets: [{
          data: [],
          backgroundColor: ['#00FF66', '#00BFFF', '#FF6347'],
          borderWidth: 2
        }]
      }
    };
  },
  watch: {
    dataArea(newVal) {
      this.updateChart(newVal);
    }
  },
  mounted() {
    this.renderChart(this.chartData, {
      plugins: {
        legend: {
          labels: {
            color: 'white' // Change legend label color to white
          }
        },
        tooltip: {
          callbacks: {
            label: function(tooltipItem, data) {
              let label = data.labels[tooltipItem.index] || '';
              let value = data.datasets[0].data[tooltipItem.index];
              return `${label}: ${value}`;
            }
          },
          // Change tooltip text color to white
          bodyColor: 'white',
          titleColor: 'white'
        }
      },
      // Option for customizing chart appearance
      responsive: true,
      maintainAspectRatio: false,
      elements: {
        arc: {
          borderColor: 'transparent' // Optionally set border color if needed
        }
      }
    });
  },
  methods: {
    updateChart(newData) {
      const index = this.chartData.labels.indexOf(newData);

      if (index !== -1) {
        this.chartData.datasets[0].data[index] += 1;
      } else {
        this.chartData.labels.push(newData);
        this.chartData.datasets[0].data.push(1);
      }

      this.renderChart(this.chartData, {
        plugins: {
          legend: {
            labels: {
              color: 'white' // Change legend label color to white
            }
          },
          tooltip: {
            callbacks: {
              label: function(tooltipItem, data) {
                let label = data.labels[tooltipItem.index] || '';
                let value = data.datasets[0].data[tooltipItem.index];
                return `${label}: ${value}`;
              }
            },
            // Change tooltip text color to white
            bodyColor: 'white',
            titleColor: 'white'
          }
        },
        responsive: true,
        maintainAspectRatio: false,
        elements: {
          arc: {
            borderColor: 'transparent' // Optionally set border color if needed
          }
        }
      });
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
