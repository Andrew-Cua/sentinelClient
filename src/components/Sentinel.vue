<template>
  <router-link :to="'/jobs/' + sentinelData._id" class="sentinel">
    <div>
      <h3>{{ sentinelData._id }}</h3>
      <hr />
      <p>Operation: {{ sentinelData.CurrentOperationID }}</p>
      <p>Last Update: {{ sentinelData.LastReportDate }}</p>
    </div>
  </router-link>
</template>

<script>
export default {
  name: "Sentinel",
  data: () => ({
    sentinel: {
      _id: "",
      CurrentOperationID: Number,
      LastReportDate: Date
    }
  }),
  props: {
    sentinelData: Object
  }
};
</script>

<style scoped>
.sentinel {
  border: 1px, solid, #fff;
  width: 15%;
  height: 5%;
  backdrop-filter: blur(20px);
  background-color: rgba(255, 255, 255, 0.1);
  box-shadow: 2px 3px 18px #333;
  border-radius: 10px;
  padding: 10px;
  margin: 20px;
  color: white;
  text-decoration: none;
}
</style>
