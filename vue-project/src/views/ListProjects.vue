<template>
  <div class="projectList">
    <h1>Project List goes here</h1>
    <h3>
      <ul>
        <li>{{ projectList.id }}</li>
        <li>{{ projectList.name }}</li>
      </ul>
    </h3>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .projectList {
    min-height: 100vh;
    align-items: center;
  }
}
</style>

<script>
import axios from 'axios'

export default {
  name: 'projectList',
  data() {
    return {
      projectList: {}
    }
  },
  created() {
    this.getProjectList()
  },
  methods: {
    getProjectList() {
      axios
        .get('http://localhost:8080/api/v1.0/practice/client/id/1')
        .then((res) => {
          this.projectList = res.data
        })
        .catch((error) => {
          console.log(error)
        })
    }
  }
}
</script>
