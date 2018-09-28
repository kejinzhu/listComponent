<template>
  <el-container class="wrap">
      <el-header>
            <el-row v-for="(data,index) in listData" :key="index" :gutter="20" v-show="data.flag">
                <el-col :span="6">
                    <el-select v-model="value5" placeholder="请选择">
                        <el-option
                        v-for="item in fieldList"
                        :key="item.value"
                        :label="item.label"
                        :value="item.value"
                        :type="item.type">
                        </el-option>
                    </el-select>
                </el-col>
                <el-col :span="6">
                    <el-select
                        v-model="value11"
                        collapse-tags
                        style="margin-left: 20px;"
                        placeholder="请选择">
                        <el-option
                            v-for="item in operatorMap.text"
                            :key="item.value"
                            :label="item.label"
                            :value="item.value">
                        </el-option>
                    </el-select>
                </el-col>
                <el-col :span="6">
                    <el-input placeholder="请输入内容" v-model="data.input" clearable>
                    </el-input></el-col>
                <el-col :span="2"><button @click="deleteData(index)">&times;</button></el-col>
            </el-row>
            <el-row>
                <a href="javascript:void(0)" @click="add">+ 添加筛选条件</a> 
            </el-row>
      </el-header>
      <!-- <el-footer>
          <a href="javascript:void(0)">+ 添加筛选条件</a> 
      </el-footer> -->
  </el-container>
</template>

<script>
export default {
    name: 'List',
    data() {
      return {
        listData:[{
            flag:true,
            input:""
        }],  
        fieldList: [{
            type:'text',  
            value: 'text1',
            label: '陈列上报编号'
        }, 
        {
            type:'text',
            value:'text2',
            label:'负责人'
        },
        {
            type:'text',
            value:'text3',
            label:'负责人所在部门'
        },
        {
            type:'text',
            value:'text4',
            label:'产品'
        },
        {
            type:'number',
            value:'num1',
            label:'排面数'
        },
        {
            type:'number',  
            value: 'num2',
            label: '割箱数'
        },
        {
            type:'number',
            value:'num3',
            label:'整箱数'
        },{
            type:'number',
            value:'num4',
            label:'堆头数'
        }
        ],
        value5: [],
        value11: [],
        operatorMap:{
            text: [
                {
                value: "include",
                label: "包含"
                },
                {
                value: "uninclude",
                label: "不包含"
                },
                {
                value: "equal",
                label: "等于"
                },
                {
                value: "notEqual",
                label: "不等于"
                },
                {
                value: "null",
                label: "为空(未填写)"    
                },
                {
                value: "fill",
                label: "不为空" 
                }
            ]    
        }
      }
    },
    methods: {
        deleteData(idx){
            this.listData = this.listData.filter((item,index)=>index!==idx);
        },
        add(){
            this.listData.push({
                flag:true
            })
        }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" scoped>
.wrap{
    margin: 20px auto;
    text-align: center;
    display: flex;
    align-items: center;
    justify-content: center;
}
.el-row {
    margin-bottom: 20px;
    overflow: hidden;
    &:last-child {
      margin-bottom: 0;
    }
    a{
        float: left;
        text-decoration: none;
    }
}
.el-col {
    border-radius: 4px;
}

button{
    width:28px;
    height:28px;
    border-radius: 50%;
    background: #ccc;
    border: none;
    outline: none;
    color: #fff;
    font-size: 18px;
    margin-top: 5px;
    cursor: pointer;
}
</style>


  
