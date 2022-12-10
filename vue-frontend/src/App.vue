<script>
import {ref,onMounted} from 'vue'
export default {
 setup() {
  const languages = ref([])
  onMounted(() => {
      getResponse()
    })
  
   const getResponse = async () => {
    fetch('http://localhost:4000/') 
    .then((res) => res.json())
    .then(data => {
      languages.value = data;
      console.log(languages.value)
    })
    .catch(err => console.log(err.message)) }
   return {getResponse, languages}
 }
}
</script>

<template>
  <div>
    <table>
      <tr>
        <th>LANGUAGE</th>
        <th>USES</th>
        <th>YEAR OF INVENTION</th>
      </tr>
      <tr v-for="language in languages" :key="language.id" >
        <td>{{language.language}}</td>
        <td>{{language.use}}</td>
        <td>{{language.invented}}</td>
      </tr>
    </table>
  </div>
</template>



<style scoped>
div{
  margin: auto;
  width: 1000px;
}
table {
  margin: 0% auto;
  width: 100%;
}
th{
  font-weight: bolder;
}
td{
  width: 150px;
}
th, td {
  border-bottom: 1px solid #ddd;
  padding: 7px;
}
</style> 
