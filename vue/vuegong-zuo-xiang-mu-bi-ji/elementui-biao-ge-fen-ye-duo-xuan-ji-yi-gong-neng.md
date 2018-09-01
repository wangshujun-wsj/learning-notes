# 需求: 
多选框表格数据在翻页时,显示当前页选中的项
第一页选中3条,切换到第二页再选中2条数据,当再次切换回第一页时,将本页当前选中的项勾选上.

# 大概思路
1. questions: []  分页时从后台获取的本页面数据
2. multipleSelection: []  当前页选中的项
3. allSelecteds: [] 所有选中的项
4. 翻页的时候将questions的数据在allSelecteds判断是否存在,存在就设置为选中

使用到的elementUI提供的事件或方法


|  事件名或方法名  |  说明  | 参数 |
| --- | --- | ---|
|  select  |  当用户手动勾选数据行的 Checkbox 时触发的事件  |  selection, row |
|  select-all |  当用户手动勾选全选 Checkbox 时触发的事件  |  selection  |
|  clearSelection |  用于多选表格，清空用户的选择  |    |
|  toggleRowSelection |  用于多选表格，切换某一行的选中状态，如果使用了第二个参数，则是设置这一行选中与否（selected 为 true 则选中）  |  row, selected  |

## 主要方法
翻页方法

```
	this.multipleSelection = [];
        let len = this.allSelecteds.length;
        // 需要在表格el-table上添加 ref="multipleTable"
        this.$refs.multipleTable.clearSelection();
        setTimeout(() => {
          for (let i = 0; i < len; i++) {
            for(let j = 0;j<this.questions.length;j++) {
              // 判断数据是否选中
              if (this.allSelecteds[i].id === this.questions[j].id) {
                this.$refs.multipleTable.toggleRowSelection(this.questions[j]);
                this.multipleSelection.push(this.questions[i]);
                break;
              }
            }
          }
        }, 100);
```
select事件触发的方法
```
// 当用户手动勾选数据行的 Checkbox 时触发的事件
      handleSelection(selection, row) {
        if (this.checkScore(row)) {
          this.select(selection, row);
        } else {
          this.$refs.multipleTable.toggleRowSelection(row);
        }
        return false;
      },
```
select-all 事件触发的方法
```
// 当用户手动勾选全选 Checkbox 时触发的事件
      handleSelectionAll(selection) {
        for (let i = selection.length - 1; i >= 0; i--) {
          if (!this.checkScore(selection[i])) {
            this.$refs.multipleTable.clearSelection();
          }
        }
        this.select(selection);
      },
```

select 事件和select-all 事件公有部分
```
select(selection, row) {
        let isSave = false;
        let selectionLength = selection.length;
        if (this.allSelecteds.length < 1) {
          this.allSelecteds = this.allSelecteds.concat(selection);
        } else {
          //select 事件
          if (row) {
            // 点击选中试题
            if (JSON.stringify(selection).indexOf(JSON.stringify(row)) !== -1) {
              this.delOrSaveSeleted(row, true);
            } else {
              // 从全部选中试题里把取消的这条数据删除
              this.delOrSaveSeleted(row);
            }
            //select-all 事件
          } else { 
            // 点击全选全部选中本页
            if (selectionLength > 0) {
              isSave = true;
            } else {
              // 点击全选取消选中本页的试题
              isSave = false;
              selection =  this.multipleSelection;
            }
            for (let i = 0; i < selection.length; i++) {
              this.delOrSaveSeleted(selection[i], isSave);
            }
          }
        }
        if(selectionLength>0) {
          this.multipleSelection = selection;
        } else {
          this.multipleSelection = [];
        }
      },
     
```
删除或添加全部选中的试题
```
 // 删除或添加全部选中的试题
      delOrSaveSeleted(row, isSave) {
        let len = this.allSelecteds.length;
        for (let i = 0; i < len; i++) {
          if (this.allSelecteds[i].id === row.id) {
            if(!isSave) {
              this.allSelecteds.splice(i, 1);
            }
            return;
          }
        }
        if(isSave ) {
          this.allSelecteds.push(row);
        }
      },
```

参考[https://blog.csdn.net/github_36327470/article/details/72652518](https://blog.csdn.net/github_36327470/article/details/72652518)