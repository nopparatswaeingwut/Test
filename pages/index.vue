<template>
  <div class="dashboard">
    <table>
      <thead>
        <tr>
          <th colspan="2">Factory Dashboard</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td class="machine-details">
            <h2>Machine Details Area</h2>
            <div v-if="this.dataSets.length > 0">
            <img src="/product.jpg" class="imageProduct" alt="Product Image">
            <GaugeChart  class="Chart" :data="[randomNumber]" />
            <p><strong>Label:</strong> {{ machine.Tagname }}</p>

            <p><strong> Gauge Speed:</strong>  {{ randomNumber }}</p>
            <p class="Detail">Details</p>
            <div >
              <p><strong>OrderNumber:</strong> {{ machine.OrderNumber }}</p>
              <p><strong>SemiBatch:</strong> {{ machine.SemiBatch }}</p>
              <!-- <p><strong>Act_Weight:</strong> {{ machine.Act_Weight }}</p> -->
              <p><strong>DateTime:</strong> {{ machine.DateTime }}</p>
            </div>
            </div>
            <div v-else>
              <p>No data</p>
            </div>
          </td>
          <td class="storage-area">
            <h2>Storage Area</h2>
            <div v-if="this.dataSets.length > 0">
            <GaugeChartArea  :dataArea="machine.Material" :actWeight="machine.Act_Weight" />
            </div>
            <div v-else>
              <p>No data</p>
            </div>
          </td>
        </tr>
      </tbody>
    </table>

  </div>
</template>

<script>
import GaugeChart from '../components/GaugeChart'
import GaugeChartArea from '../components/GaugeChartArea'
export default {
  components: {
    GaugeChart,
    GaugeChartArea
  },
  data() {
    return {
      machine: {},
      dataSets: [
        [{ "0": 1, "Id_pk": 1, "1": "X", "OrderNumber": "X", "2": "2440006", "SemiBatch": "2440006", "3": "SESHE06", "Material": "SESHE06", "4": "LD2FST01", "Tagname": "LD2FST01", "5": 0, "Act_Inv": 0, "6": 10365.056640625, "Act_Weight": 10365.056640625, "7": "Jul 10 2024 11:02:29:000AM", "DateTime": "Jul 10 2024 11:02:29:000AM" },
        { "0": 2, "Id_pk": 2, "1": "X", "OrderNumber": "X", "2": "2440078", "SemiBatch": "2440078", "3": "SESDM21", "Material": "SESDM21", "4": "LD2FST02", "Tagname": "LD2FST02", "5": 0, "Act_Inv": 0, "6": 4477.3969726562, "Act_Weight": 4477.3969726562, "7": "Jul 10 2024 11:02:29:000AM", "DateTime": "Jul 10 2024 11:02:29:000AM" },
        { "0": 3, "Id_pk": 3, "1": "X", "OrderNumber": "X", "2": "2440061", "SemiBatch": "2440061", "3": "SESDG28", "Material": "SESDG28", "4": "LD2FST03", "Tagname": "LD2FST03", "5": 0, "Act_Inv": 0, "6": 19403.16796875, "Act_Weight": 19403.16796875, "7": "Jul 10 2024 11:02:29:000AM", "DateTime": "Jul 10 2024 11:02:29:000AM" }
        ],
        [{ "0": 1, "Id_pk": 1, "1": "X", "OrderNumber": "X", "2": "2440006", "SemiBatch": "2440006", "3": "SESHE06", "Material": "SESHE06", "4": "LD2FST01", "Tagname": "LD2FST01", "5": 0, "Act_Inv": 0, "6": 10366.4765625, "Act_Weight": 10366.4765625, "7": "Jul 10 2024 01:09:31:000PM", "DateTime": "Jul 10 2024 01:09:31:000PM" },
        { "0": 2, "Id_pk": 2, "1": "X", "OrderNumber": "X", "2": "2440078", "SemiBatch": "2440078", "3": "SESDM21", "Material": "SESDM21", "4": "LD2FST02", "Tagname": "LD2FST02", "5": 0, "Act_Inv": 0, "6": 471.34725952148, "Act_Weight": 471.34725952148, "7": "Jul 10 2024 01:09:31:000PM", "DateTime": "Jul 10 2024 01:09:31:000PM" },
        { "0": 3, "Id_pk": 3, "1": "X", "OrderNumber": "X", "2": "2440061", "SemiBatch": "2440061", "3": "SESDG28", "Material": "SESDG28", "4": "LD2FST03", "Tagname": "LD2FST03", "5": 0, "Act_Inv": 0, "6": 13340.837890625, "Act_Weight": 13340.837890625, "7": "Jul 10 2024 01:09:31:000PM", "DateTime": "Jul 10 2024 01:09:31:000PM" }
        ],
        [{ "0": 1, "Id_pk": 1, "1": "X", "OrderNumber": "X", "2": "2440006", "SemiBatch": "2440006", "3": "SESHE06", "Material": "SESHE06", "4": "LD2FST01", "Tagname": "LD2FST01", "5": 0, "Act_Inv": 0, "6": 10365.766601562, "Act_Weight": 10365.766601562, "7": "Jul 10 2024 03:04:32:000PM", "DateTime": "Jul 10 2024 03:04:32:000PM" },
        { "0": 2, "Id_pk": 2, "1": "X", "OrderNumber": "X", "2": "2440078", "SemiBatch": "2440078", "3": "SESDM21", "Material": "SESDM21", "4": "LD2FST02", "Tagname": "LD2FST02", "5": 0, "Act_Inv": 0, "6":   376.91082763672, "Act_Weight": 376.91082763672, "7": "Jul 10 2024 03:04:32:000PM", "DateTime": "Jul 10 2024 03:04:32:000PM" },
        { "0": 3, "Id_pk": 3, "1": "X", "OrderNumber": "X", "2": "2440061", "SemiBatch": "2440061", "3": "SESDG28", "Material": "SESDG28", "4": "LD2FST03", "Tagname": "LD2FST03", "5": 0, "Act_Inv": 0, "6": 10065.418945312, "Act_Weight": 10065.418945312, "7": "Jul 10 2024 03:04:32:000PM", "DateTime": "Jul 10 2024 03:04:32:000PM" }
        ],
        [{ "0": 1, "Id_pk": 1, "1": "X", "OrderNumber": "X", "2": "2440006", "SemiBatch": "2440006", "3": "SESHE06", "Material": "SESHE06", "4": "LD2FST01", "Tagname": "LD2FST01", "5": 0, "Act_Inv": 0, "6": 10365.766601562, "Act_Weight": 10365.766601562, "7": "Jul 10 2024 03:49:33:000PM", "DateTime": "Jul 10 2024 03:49:33:000PM" },
        { "0": 2, "Id_pk": 2, "1": "X", "OrderNumber": "X", "2": "2440078", "SemiBatch": "2440078", "3": "SESDM21", "Material": "SESDM21", "4": "LD2FST02", "Tagname": "LD2FST02", "5": 0, "Act_Inv": 0, "6": 379.04138183594, "Act_Weight": 379.04138183594, "7": "Jul 10 2024 03:49:33:000PM", "DateTime": "Jul 10 2024 03:49:33:000PM" },
        { "0": 3, "Id_pk": 3, "1": "X", "OrderNumber": "X", "2": "2440061", "SemiBatch": "2440061", "3": "SESDG28", "Material": "SESDG28", "4": "LD2FST03", "Tagname": "LD2FST03", "5": 0, "Act_Inv": 0, "6": 7225.255859375, "Act_Weight": 7225.255859375, "7": "Jul 10 2024 03:49:33:000PM", "DateTime": "Jul 10 2024 03:49:33:000PM" }
        ],
        [{ "0": 1, "Id_pk": 1, "1": "X", "OrderNumber": "X", "2": "2440006", "SemiBatch": "2440006", "3": "SESHE06", "Material": "SESHE06", "4": "LD2FST01", "Tagname": "LD2FST01", "5": 0, "Act_Inv": 0, "6": 10365.766601562, "Act_Weight": 11914.821601562, "7": "Jul 10 2024 04:23:33:000PM", "DateTime": "Jul 10 2024 04:23:33:000PM" },
        { "0": 2, "Id_pk": 2, "1": "X", "OrderNumber": "X", "2": "2440078", "SemiBatch": "2440078", "3": "SESDM21", "Material": "SESDM21", "4": "LD2FST02", "Tagname": "LD2FST02", "5": 0, "Act_Inv": 0, "6": 379.04138183594, "Act_Weight": 611.04238183594, "7": "Jul 10 2024 04:23:33:000PM", "DateTime": "Jul 10 2024 04:23:33:000PM" },
        { "0": 3, "Id_pk": 3, "1": "X", "OrderNumber": "X", "2": "2440061", "SemiBatch": "2440061", "3": "SESDG28", "Material": "SESDG28", "4": "LD2FST03", "Tagname": "LD2FST03", "5": 0, "Act_Inv": 0, "6": 7225.255859375, "Act_Weight": 6425.255859375, "7": "Jul 10 2024 04:23:33:000PM", "DateTime": "Jul 10 2024 04:23:33:000PM" }
        ],
        [{ "0": 1, "Id_pk": 1, "1": "X", "OrderNumber": "X", "2": "2440006", "SemiBatch": "2440006", "3": "SESHE06", "Material": "SESHE06", "4": "LD2FST01", "Tagname": "LD2FST01", "5": 0, "Act_Inv": 0, "6": 7336.0224609375, "Act_Weight": 7336.0224609375, "7": "Jul 11 2024 09:17:44:000AM", "DateTime": "Jul 11 2024 09:17:44:000AM" },
        { "0": 2, "Id_pk": 2, "1": "X", "OrderNumber": "X", "2": "2440078", "SemiBatch": "2440078", "3": "SESDM21", "Material": "SESDM21", "4": "LD2FST02", "Tagname": "LD2FST02", "5": 0, "Act_Inv": 0, "6": 58.102722167969, "Act_Weight": 58.102722167969, "7": "Jul 11 2024 09:17:44:000AM", "DateTime": "Jul 11 2024 09:17:44:000AM" },
        { "0": 3, "Id_pk": 3, "1": "X", "OrderNumber": "X", "2": "2440061", "SemiBatch": "2440061", "3": "SESDG28", "Material": "SESDG28", "4": "LD2FST03", "Tagname": "LD2FST03", "5": 0, "Act_Inv": 0, "6": 222.83312988281, "Act_Weight": 222.83312988281, "7": "Jul 11 2024 09:17:44:000AM", "DateTime": "Jul 11 2024 09:17:44:000AM" }
        ],
        [{ "0": 1, "Id_pk": 1, "1": "X", "OrderNumber": "X", "2": "2440006", "SemiBatch": "2440006", "3": "SESHE06", "Material": "SESHE06", "4": "LD2FST01", "Tagname": "LD2FST01", "5": 0, "Act_Inv": 0, "6": -39.882751464844, "Act_Weight": -39.882751464844, "7": "Jul 12 2024 08:48:00:000AM", "DateTime": "Jul 12 2024 08:48:00:000AM" },
        { "0": 2, "Id_pk": 2, "1": "X", "OrderNumber": "X", "2": "2440078", "SemiBatch": "2440078", "3": "SESDM21", "Material": "SESDM21", "4": "LD2FST02", "Tagname": "LD2FST02", "5": 0, "Act_Inv": 0, "6": 67.334136962891, "Act_Weight": 67.334136962891, "7": "Jul 12 2024 08:48:00:000AM", "DateTime": "Jul 12 2024 08:48:00:000AM" },
        { "0": 3, "Id_pk": 3, "1": "X", "OrderNumber": "X", "2": "2440061", "SemiBatch": "2440061", "3": "SESDG28", "Material": "SESDG28", "4": "LD2FST03", "Tagname": "LD2FST03", "5": 0, "Act_Inv": 0, "6": 239.87329101562, "Act_Weight": 239.87329101562, "7": "Jul 12 2024 08:48:00:000AM", "DateTime": "Jul 12 2024 08:48:00:000AM" }
        ]
      ],
      currentDataSetIndex: 0,
      randomNumber: null
    }
  },
  computed: {

    data() {
      return this.dataSets[this.currentDataSetIndex];
    },
  },
  methods: {
    updateDashboard() {
      if (this.dataSets.length > 0) {
      const randomIndex = Math.floor(Math.random() * this.data.length);
      this.machine = this.data[randomIndex];
      this.generateRandomSpeed();
      }
      else{
      }

    },
    updateDataSet() {
      if (this.dataSets.length > 0) {
      this.currentDataSetIndex = (this.currentDataSetIndex + 1) % this.dataSets.length;
      this.updateDashboard();
      }
      else{

      }
    },
    generateRandomSpeed() {
      this.randomNumber = Math.floor(Math.random() * (100 - 50 + 1)) + 50;
    }
  },
  mounted() {
    this.updateDashboard();
    setInterval(this.updateDataSet, 5000);
  }
}
</script>

<style scoped>
body {
  font-family: Arial, sans-serif;
}

.dashboard {
  margin: 20px;
  background-color: #cccccc48;
}

table {
  width: 100%;
  border-collapse: collapse;
}

th {
  background-color: #c40b0b;
  text-align: center;
  font-size: 1.5em;
  padding: 10px;
  color: #fff;
}

td {
  border: 1px solid #ccc;
  vertical-align: top;
  padding: 20px;
}

.imageProduct {
  width: 16vw; /* ใช้ vw แทน % */
  height: auto;
}

.Chart {
  width: 35%;
  height: auto;
}

.storage-area {
  width: 40%;
  height: auto;
}

h2 {
  text-align: center;
  color: #000000;
}

.machine-details, .storage-area {
  background-color: #fff;
  color: #000000;
}

.Detail {
  font-weight: bold;
  font-size: 1.5em;
  margin-bottom: 15px;
}

/* Responsive Design */
@media (max-width: 768px) {
  table {
    width: 100%;
  }

  thead {
    display: block;
    width: 100%;
  }

  th {
    display: block;
    text-align: center;
    padding: 10px;
    background-color: #c40b0b;
    color: #fff;
    font-size: 1.5em;
  }

  tr {
    display: block;
  }

  td {
    display: block;
    width: 100%;
    box-sizing: border-box;
  }

  .imageProduct {
    width: 100%;
    max-width: 400px;
    height: auto;
    margin-bottom: 20px;
  }

  .Chart {
    width: 100%;
    max-width: 400px;
    height: auto;
    margin-bottom: 20px;
  }

  .machine-details, .storage-area {
    width: 100%;
    display: block;
  }
}
</style>

