<template>
        <div class="filter-box">
            <div class="selected-condations">
                <div class="left-title ">已选条件：</div>
                <div class="right-area aa">
                    <p class="selected-item" v-if="selected_range_item !='不限'">{{selected_range_item}}<span class="clear-selected" @click="clearRange">×</span></p>
                    <p class="selected-item" v-if="selected_area_item !='不限'">{{selected_area_item}}<span class="clear-selected" @click="clearArea">×</span></p>
                </div>
            </div>
            <div class="condations-box">
                <div class="major-range ">
                    <div class="left-title ">专业层次：</div>
                    <div class="right-area "></div>
                </div>
                <school-range :school-range-list="$store.state.school_range_obj"></school-range>
                <school-area :school-area-list="$store.state.school_area_obj"></school-area>
            </div>
            <school-subject :colleges-data-list="$store.state.colleges_data_obj" :colleges-name-list="$store.state.colleges_name_obj"></school-subject>
        </div>
</template>
<script>

import axios from '../axios/axios';
import school_range from '../components/school_range';
import school_area from '../components/school_area';
import school_subject from '../components/subject _analysis';
export default {
    name:'overall',
    components:{
        "school-range": school_range,
        "school-area":school_area,
        "school-subject":school_subject
    },
    computed:{
        "selected_range_item":function () {
            return  this.$store.getters.selected_range
        },
        "selected_area_item":function () {
            return  this.$store.getters.selected_area
        },
        
    },
    mounted:function(){
        console.log(this.$store.state.colleges_data_obj)
    },
    created:function(){
        let vm = this; 
        this.$http('src/data/school_range.json').then(function (res) {
            let range_data = res.data.list.map((val,index) => {
                return index == 0 ? {value:val,selected:true} : {value:val,selected:false}
            })
            vm.$store.commit("update_range",range_data)
        });     
        this.$http('src/data/school_area.json').then(function (res) {
            let area_data = res.data.list.map((val,index) => {
                return index == 0 ? {value:val,selected:true} : {value:val,selected:false}
            })
            vm.$store.commit("update_area",area_data)
        });
        this.$http('src/data/高校检索.json').then(function (res) {
            vm.$store.commit("colleges_data",res.data.result)
        });
        this.$http('src/data/学校方式聚合.json').then(function (res) {
            console.log(res)
            vm.$store.commit("colleges_name_data",res.data.result)
        });

    },
 
    methods:{
        clearRange:function () {
             this.$store.commit('clear_range')
        },
        clearArea:function () {
             this.$store.commit('clear_area')
        }
    }
}
</script>
<style >
    .selected-condations{
            line-height: 40px;
            padding:5px 0;
            text-indent: 10px;
    } 
    .left-title, .right-area{
        float: left;
    }
    .condations-box{
        border:1px solid #ccc;
        padding:10px;
    }
    .selected-condations, .major-range{
        overflow: hidden;
    }
    .selected-item{
        margin:0;
        display:inline-block;
        border:1px solid #ccc;
        line-height: 30px;
        padding:2px 8px;
    }
    .aa{
        line-height: 50px;
    }
    .filter-item{
        display: inline-block;
        min-width: 70px;
        padding: 0 5px;
        height: 35px;
        color: #333333;
        text-align: center;
        line-height: 35px;
        margin: 5px;
        cursor: pointer;
    }
    .filter-item.selected{
        background: rgba(0, 160, 92, 1);
        color: #fff;
    }
    .filter-item:hover{
        background: rgba(0, 160, 92, 1);
        color: #fff;
    }
    .left-title{
        margin: 5px 0;
        text-indent: 10px;
        width: 10%;
    }
    .right-area{
        width: 90%;
    }
    .clear-selected{
        cursor: pointer;
    }
</style>


