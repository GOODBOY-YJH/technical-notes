## a-table 如何给行设置样式



```
<a-table :columns="columns"
                   :showTitle="false"
                   :data-source="tableData"
                   :pagination="pagination"
                   tableLayout="fixed"
                   @change="onTableChange"
                   :customRow="customRow"
                   :rowClassName="rowClassName"
                   rowKey="id"
          >
          </table>
          
          
    // 监测到行被点击
    customRow(record, index){
      return {
        on: {
          click: () => {
            this.pageData = record;
          }
        }
      }
    },
    // 给对应id的行设置样式
    rowClassName(record, index){
      return record.id === this.pageData.id ? 'rowClass' : '';
    },
```

使用 :customRow="customRow" :rowClassName="rowClassName"