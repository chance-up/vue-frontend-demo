<template>
  <div>
    <button type="button" @click="loadData()">load</button>
    <ul>
      <li v-for="(name,idx) in names" :key="idx">{{name}}</li>
    </ul>

  </div>
</template>

<script>
import {ref,onMounted} from 'vue'
import axios from 'axios'

export default {
  setup () {
    async function loadData(){
      const result = await axios.get('https://jsonplaceholder.typicode.com/posts/1/comments');
      console.log(result.data);
      names.value = result.data.map(item => item.name); 
    }
    onMounted(loadData);
    const names = ref(['John','Jane','Joe']);
    

    return {
      names,loadData
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
