<template>
  <div class="days">
    <h3 class="card right">{{ $route.params.operationID }}</h3>
    <div class="table-wrapper card center ">
      <table class="fl-table">
        <thead>
          <tr>
            <th>Time</th>
            <th>Temp</th>
            <th>Humidity</th>
            <th>Lux</th>
            <th>Is Raining</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="data in data" :key="data.timestamp">
            <td>{{ data.timestamp }}</td>
            <td>{{ data.temperature }}</td>
            <td>{{ data.humidity }}</td>
            <td>{{ data.lux }}</td>
            <td>{{ data.isRaining }}</td>
          </tr>
        </tbody>
      </table>
    </div>
    <div class="graphs card center">
      <Linechart
        :chart-data="
          createGraphData(this.labels, this.temperature, 'temperature')
        "
      />
      <Linechart
        :chart-data="createGraphData(this.labels, this.humidity, 'humidity')"
      />
      <Linechart :chart-data="createGraphData(this.labels, this.lux, 'lux')" />
    </div>
  </div>
</template>

<script>
import Linechart from "@/components/Linechart.vue";
export default {
  name: "Day",
  data: () => ({
    days: Array,
    data: [],
    labels: [],
    temperature: [],
    humidity: [],
    lux: [],
    renderGraphs: false
  }),
  components: {
    Linechart
  },
  mounted() {
    /*fetch(
      `http://localhost:3000/sentinels/data/findByOperationID/${this.$route.params.operationID}`
    )
      .then(response => response.json())
      .then(result => {
        this.days = result;
        this.days.forEach(x => {
          x.Data.forEach(y => {
            this.data.push(y);
            this.labels.push(y.timestamp);
            this.temperature.push(y.temperature);
            this.humidity.push(y.humidity);
            this.lux.push(y.lux);
          });
        });
      });*/
    this.getData(
      `http://localhost:3000/sentinels/data/findByOperationID/${this.$route.params.operationID}`
    );
  },
  methods: {
    getData: async function(url) {
      let response = [];
      let result = [];
      response = await fetch(url);
      result = await response.json();

      console.log(response);
      console.log(result);

      this.days = result;
      this.days.forEach(x => {
        x.Data.forEach(y => {
          this.data.push(y);
          this.labels.push(y.timestamp);
          this.temperature.push(y.temperature);
          this.humidity.push(y.humidity);
          this.lux.push(y.lux);
        });
      });
    },
    createGraphData: function(labels, data, name) {
      return {
        labels: labels,
        datasets: [
          {
            label: name,
            data: data,
            backgroundColor: "transparent",
            borderColor: "rgba(1, 116, 188, 0.50)",
            pointBackgroundColor: "rgba(171, 71, 188, 1)"
          }
        ]
      };
    }
  }
};
</script>

<style>
.card {
  border: 1px, solid, #fff;
  width: auto;
  height: auto;
  backdrop-filter: blur(20px);
  background-color: rgba(255, 255, 255, 0.1);
  box-shadow: 2px 3px 18px #333;
  border-radius: 10px;
  padding: 10px;
  color: white;
  text-decoration: none;
}

.right {
  align-self: flex-start;
}

.center {
  align-self: center;
}
.days {
  display: flex;
  justify-content: center;
  flex-direction: column;
}
.table-wrapper {
  margin: 10px 40px 40px;
  box-shadow: 0px 35px 50px rgba(0, 0, 0, 0.2);
  width: 75%;
  height: 100%;
}

.fl-table {
  border-radius: 5px;
  font-size: 12px;
  font-weight: normal;
  border: none;
  border-collapse: collapse;
  width: 100%;
  max-width: 100%;
  white-space: nowrap;
  background-color: white;
  color: black;
}

.fl-table td,
.fl-table th {
  text-align: center;
  padding: 8px;
}

.fl-table td {
  border-right: 1px solid #f8f8f8;
  font-size: 12px;
}

.fl-table thead th {
  color: #ffffff;
  background: #4fc3a1;
}

.fl-table thead th:nth-child(odd) {
  color: #ffffff;
  background: #324960;
}

.fl-table tr:nth-child(even) {
  background: #f8f8f8;
}

.graph {
  width: 50%;
  height: auto;
}
</style>
