---
order: 16
title:
  en-US: Tree data
  zh-CN: 树形数据展示
---

## zh-CN

表格支持树形数据的展示，可以通过设置 `indentSize` 以控制每一层的缩进宽度。

> 注：暂不支持父子数据递归关联选择。

## en-US

Display tree structure data in Table, control the indent width by setting `indentSize`.

> Note, no support for recursive selection of tree structure data table yet.

````jsx
import { Table } from 'antd';

const columns = [{
  title: '应用',
  dataIndex: 'app',
  key: 'app',
}, {
  title: '时间',
  dataIndex: 'time',
  key: 'time',
  width: '12%',
}, {
  title: '总访问量',
  dataIndex: 'pv_all',
  width: '30%',
  key: 'address',
}];

const data = [{
  key: 1,
  app: '全部',
  age: '2018-06-26',
  pv_all: 36,551,452,
  children: [{
      key: 11,
      app: '应用系统01',
      age: '2018-06-26',
      pv_all: 36,551,452
  }, {
    key: 12,
    app: '应用系统02',
    age: '2018-06-26',
    pv_all: 36,551,452
  }]
}, {
  key: 2,
  app: '全部',
  age: '2018-06-22',
  pv_all: 36,551,452,
}];

// rowSelection objects indicates the need for row selection
const rowSelection = {
  onChange: (selectedRowKeys, selectedRows) => {
    console.log(`selectedRowKeys: ${selectedRowKeys}`, 'selectedRows: ', selectedRows);
  },
  onSelect: (record, selected, selectedRows) => {
    console.log(record, selected, selectedRows);
  },
  onSelectAll: (selected, selectedRows, changeRows) => {
    console.log(selected, selectedRows, changeRows);
  },
};

ReactDOM.render(
  <Table columns={columns} rowSelection={rowSelection} dataSource={data} />
, mountNode);
````
