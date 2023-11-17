### 设置a-table的body滚动条自适应时，header也自适应

当使用

```
设置table :scroll="{x:1000, y:550}"
和样式
/deep/.ant-table-body{
    overflow: auto !important;
  }
```

方式设置表格滚动条自适应时，由于表头header无法自适应产生滚动条对应的宽度，会导致表格body内容与表头相差一个滚动条的宽度。

针对性解决方案：

把表格滚动条出现的高度，设置为固定行数数据的高度（比如10行数据的高度为500px，高度偏差在一行数据之内都可以，即 ```500px - 550px``` ），然后通过查询所得的数据行数动态添加class样式，动态取消表头的滚动条

```
示例代码
<a-table :columns="columns"
         :data-source="tableData"
         :scroll="{x:1000, y:500}"
         :class="{'haveHeaderScroll':this.tableData.length <= 10}"
>
</a-table>
                
上面550px是刚好十条数据的高度，然后当数据条数大于10条时添加class样式，
或者可以通过行数计算高度，当数据高度达到多少时添加class
比如 (this.tableData.length * 50) - XXpx <= 500 
可以更精细的控何时添加class


.myTable{
  /deep/.ant-table-body{
    overflow: auto !important;
  }
  .haveHeaderScroll{
    /deep/.ant-table-header {
      overflow-y: hidden !important;
    }
  }
}
```

