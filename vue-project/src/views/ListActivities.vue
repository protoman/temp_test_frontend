<template>
  <div class="activityList">
    <h1>Activities</h1>
    <h3>
      <ul>
        <li v-for="item in items" :key="item.id">{{ item.id }} - {{ item.name }}</li>
      </ul>
    </h3>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .activityList {
    min-height: 100vh;
    align-items: center;
  }
}
</style>

<script>
import axios from 'axios'

const items = ref([{ id: 1, name: 'Foo' }, { id: 2, name: 'Bar' }])

export default {
  name: 'activityList',
  data() {
    return {
      activityList: []
    }
  },
  created() {
    this.getActivityList()
  },
  methods: {
    getActivityList() {
      axios
        .get('http://localhost:8080/api/v1.0/practice/activity')
        .then((res) => {
          this.activityList = res.data
        })
        .catch((error) => {
          console.log(error)
        })
    }
  }
}
</script>
