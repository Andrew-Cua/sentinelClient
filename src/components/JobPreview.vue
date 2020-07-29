<template>
  <router-link :to="'/days/' + jobData._id" class="job">
    <div>
      <h3>{{ jobData._id }}</h3>
      <hr />
      <p>Start: {{ jobData.StartDate }}</p>
      <p>End: {{ jobData.EndDate }}</p>
    </div>
  </router-link>
</template>

<script>
export default {
  name: "JobPreview",
  props: {
    jobData: Object
  }
};
</script>

<style lang="scss" scoped>
.job {
  border: #fff, 1px, solid;
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
