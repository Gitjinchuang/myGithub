<template>
    <table class="table">
            <thead class="thead">
                <tr>
                   <td >选考科目</td>
                   <td >高校数</td>
                   <td >专业(类)数</td>
                   <td >科目比例</td>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(value,index) in table_list" v-if="index<=15" :key="index">
                   <td >{{value.subject}}</td>
                   <td >{{value.majorCount}}</td>
                   <td >{{value.collegesCount}}</td>
                   <td >{{value.rate}}</td>
                </tr>
            </tbody>
        </table>
</template>
<script>
export default {
  props:["table_list"],
  mounted:function(){
      //console.log(this)
  }
}
</script>
<style>

</style>


