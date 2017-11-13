<template>
     <div class="subject">
         <span class="subject_title" >选考科目分析</span>
         <p class="subject_proportion">科目比例：要求所选选考科目的专业总数/条件范围内专业总数。以专业为例：经济统计学专业历史所占比例为66.7%，意为选考历史，66.7%的经济统计学专业均可报考。</p>
         <div class="table1_box">
              <table-item :table_list ="this.collegesDataList.analysisData" class="aa"> </table-item>
              <table-item :table_list ="this.collegesDataList.analysisData" class="aa"> </table-item>
         </div>
         <table2-item :table2_list ="this.collegesNameList" ></table2-item>
     </div>  
</template>
<script>
import table_item from './table_item';
import table2_item from './table2_item'
export default {
     props:["collegesDataList","collegesNameList"],
     components:{
        "table-item":table_item,
        "table2-item":table2_item
     }
}
</script>
<style>
   .subject_proportion{
       font-size: 14px;
       color: red;
       border-top:1px solid #ccc;
       line-height: 30px;
   }
   .subject{
       margin-top:15px;
   }
    .subject_form{
       border:1px solid #ccc;
   }
   .table1_box .aa{
     display:inline-block;
   }
   .table tr{
      
       color:#00A15C;
      
   }
   .thead tr td{
        background:#00A15C;
        color:#fff;
   }
   .table td{
       border:1px solid #ccc;
       width: 142px;
        height: 50px;
       color:#000;
       text-align: center;
   }
</style>

