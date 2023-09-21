<template>
  <div class="app">
    <header>
      <div class="order">
        <button @click="handleClick('title')">Order By Title</button>
        <button @click="handleClick('salary')">Order By Salary</button>
        <button @click="handleClick('location')">Order By Location</button>
      </div>
    </header>
  <JobList :jobs="jobs" :order="order" /> 
</div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import Job from './types/Jobs'
import OrderTerm from './types/OrderTerm'
import JobList from './components/JobList.vue'


export default defineComponent({
  name: 'App',
  components: { JobList },
  setup() {
    const jobs = ref<Job[]>([
      { title: 'Farm Worker', location: 'Lon Lon Ranch', salary: 3000, id: '1'},
      { title: 'Quarryman', location: 'Death Mountain', salary: 4000, id: '2'},
      { title: 'Flute Player', location: 'The Lost Woods', salary: 35000, id: '3'},
      { title: 'Fisherman', location: 'Lake Hylia', salary: 21000, id: '4'},
      { title: 'Prison Guard', location: 'Gerudo Valley', salary: 32000, id: '5'},
    ])
    const order = ref<OrderTerm>('title')

    const handleClick = (term: OrderTerm) => {
      order.value = term
    }

    return { jobs, handleClick, order }
  }});
   
</script>

<style>
  header {
    text-align: center;
  }
  header .order {
    margin-top: 20px;
  }
  button {
    margin: 0 10px;
    color: #1195c9;
    border: 3px solid #1195c9;
    background: #d5f0ff;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: bold;
  }
</style>