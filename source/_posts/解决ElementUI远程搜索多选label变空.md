---
title: 解决ElementUI多选远程搜索时label变空
date: 2020-02-14 12:00:53
tags: ElementUI
categories: 前端
---

> 在 ElementUI 中使用 el-select 多选，option 的 value 值为 object 类型，远程搜索时，label 显示变空，效果如下图

![Element](/images/select.jpeg)

这是因为，再次搜索时，下拉选项里没有之前选中的内容，所以无法显示数据。那么，解决方法，就是在搜索时，把之前的选中内容加到下拉列表里。

#### 页面布局

```
  <el-select
    v-model="value"
    placeholder="请选择"
    multiple
    filterable
    remote
    :remote-method="multiSearch"
    @change="updateValue"
    @remove-tag="doRemoveTag"
    value-key="id" <!-- value为object时必加value-key -->
  >
    <el-option
      v-for="item in options"
      :key="item.id"
      :value="item"
      :label="item.name"
    >
      <div>{{ item.name }}({{ item.otherInfo }})</div>
    </el-option>
  </el-select>
```

<!-- more -->

#### 搜索结果回来时

```
getOptions.search(searchStr).then(list => {
  // 在返回的列表里查找是否和选中项有重复的，没有的话加进去
  this.value.map(v => {
    if (!list.find(l => l.id === v.id)) {
      list.push(v);
    }
  });
  this.options = list;
})
.catch(err => {
  console.error(err);
});
```

#### 删除选项时

```
// 下拉列表为空时则等同于已选内容列表，需要浅拷贝，防止数据错乱
doRemoveTag() {
  this.options = [].concat(this.value);
}
```

#### delect 键删除选项时

```
updateValue() {
  if (this.options.length === 0) {
    this.options = [].concat(this.value);
  }
}
```

但是这种解决方法还有 bug：在用 delect 键删除时，第一次无法监听，label 变空。第二次删除因为触发了 change 事件，会恢复正常。大家有什么好的解决方法，欢迎讨论交流。
