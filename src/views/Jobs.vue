<template>
  <div class="jobs">
    <JobPreview v-for="job in jobs" :key="job._id" :jobData="job" />
  </div>
</template>

<script>
import JobPreview from "@/components/JobPreview.vue";
export default {
  name: "Jobs",
  components: {
    JobPreview
  },
  data: () => ({
    jobs: []
  }),
  mounted() {
    fetch(
      `http://localhost:3000/jobs/findBySentinelID/${this.$route.params.sentinelID}`
    )
      .then(response => response.json())
      .then(result => {
        this.jobs = result;
      });
  }
};
</script>

<style scoped>
.jobs {
  display: flex;
  flex-direction: row;
}
</style>
