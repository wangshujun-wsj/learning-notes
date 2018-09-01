[CSDN原文](https://blog.csdn.net/xuxu_qkz/article/details/80166442)
```
<el-table
     :data="tableData" 
     v-loading="loading"   
     :height="height"       
     style="width: 100%;"
     :row-key="getRowKeys"
     @row-click="rowClick"
     @expand-change="showDetail"
     :expand-row-keys="expands"
   >
     <el-table-column
       label="点击展开"
       width="100"
       type="expand"
     >  
       <template slot-scope="props"> 
       </template>
     </el-table-column>
     <el-table-column
       prop="alarmTypeName"
       label="事件"
       min-width="150"
     >
       <template slot-scope="scope">
         <span :style="colorStyle(scope.row.alarmLevel)" style="width:10px;height:12px;display:inline-block;margin-right:10px;"></span><span>{{scope.row.alarmTypeName}}</span>
       </template>
     </el-table-column>

  </el-table>
    data(){
      expands: [],
      tableData:[]
},
methods:{
        rowClick(data, event, column){
              // console.log('点击行出发','column',column.label)
              if(column.label !== '点击展开'){
                this.expands=[];
              }
            },
        //点击展开列表详细数据
    showDetail(data,expandedRows) {
      //控制只显示当前行
      if (expandedRows.length) {
         this.expands = []; 
        if (data) {
          this.expands.push(data.id);
        } 
      }else{
        this.expands = [];
      }
    },
    getRowKeys(row) {
      return row.id;
    },
}
```