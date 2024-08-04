<script>
import { Bar } from 'vue-chartjs';
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js';

export default {
  name: 'GaugeChartArea',
  extends: Bar,
  props: {
    dataArea: {
      type: String,
      required: true
    },
    actWeight: {
      type: Number,
      required: true
    }
  },
  data() {
    return {
      chartData: {
        labels: [],
        datasets: [{
          label: 'Act_Weight',
          data: [],
          backgroundColor: ['#00FF66', '#00BFFF', '#FF6347'],
          borderColor: '#000',
          borderWidth: 1
        }]
      },
      options: {
        plugins: {
          legend: {
            labels: {
              color: 'white'
            }
          },
          tooltip: {
            callbacks: {
              label: function(tooltipItem) {
                let label = tooltipItem.label || '';
                let value = tooltipItem.raw;
                return `${label}: ${value}`;
              }
            },
            bodyColor: 'white',
            titleColor: 'white'
          }
        },
        responsive: true,
        maintainAspectRatio: false,
        scales: {
          x: {
            ticks: {
              color: 'white'
            },
            grid: {
              color: 'rgba(255, 255, 255, 0.1)'
            }
          },
          y: {
            ticks: {
              color: 'white'
            },
            grid: {
              color: 'rgba(255, 255, 255, 0.1)'
            }
          }
        }
      }
    };
  },
  watch: {
    dataArea(newVal) {
      this.updateChart(newVal, this.actWeight);
    },
  },
  mounted() {
    this.renderChart(this.chartData, this.options);
  },
  methods: {
    updateChart(newData, weight) {
      const label = newData.toString();
      const index = this.chartData.labels.indexOf(label);

      if (index !== -1) {
        this.chartData.datasets[0].data[index] = weight;
      } else {
        this.chartData.labels.push(label);
        this.chartData.datasets[0].data.push(weight);
      }

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
