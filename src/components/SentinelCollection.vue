<template>
  <div class="sentinelCollection">
    <Sentinel
      v-for="sentinel in sentinels"
      :key="sentinel._id"
      v-bind:sentinelData="sentinel"
    />
  </div>
</template>

<script>
import Sentinel from "@/components/Sentinel.vue";
export default {
  name: "SentinelCollection",
  components: {
    Sentinel
  },
  data: () => ({
    sentinel: {
      _id: "",
      CurrentOperationID: Number,
      LastReportDate: Date
    },
    sentinels: []
  }),
  mounted() {
    fetch("http://localhost:3000/sentinels")
      .then(response => response.json())
      .then(result => {
        this.sentinels = result;
      });
  }
};
</script>

<style scoped>
.sentinelCollection {
  display: flex;
  flex-direction: row;
}
</style>
