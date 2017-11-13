<template>
     <table class="table">
            <thead class="thead">
                <tr>
                   <td v-for="(value,index) in table2_list.title" :key="index" >{{value}}</td>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(value,ind) in table2_list.rows" :key="ind">
                    <td  v-for="(value,index) in table2_list.rows[ind]" :key="index" v-if="index<=8">{{value}}</td>
                </tr>
            </tbody>
        </table>
</template>
<script>
export default {
     props:["table2_list"],
     mounted:function() {
         console.log(this)
     }
}
</script>

