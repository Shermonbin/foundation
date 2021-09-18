---
title: 单选级联 - Cascader
nav:
  title: 组件
  path: /component
  order: 1
group:
  title: Bl
  path: /Bl
---

# Cascader

单选级联选择框

### 何时使用

- 需要从一组相关联的数据集合进行选择，例如省市区，公司层级，事物分类等。

- 从一个较大的数据集合中进行选择时，用多级分类进行分隔，方便选择。

- 比起 Select 组件，可以在同一个浮层中完成选择，有较好的体验。

### 基本使用

- [请参考 Antd](https://ant.design/components/cascader-cn/#API)
- 该组件默认输入、输出都是全路径数据结构

```
  value:(string | number)[] = ['zhejiang1', 'hangzhou1', 'xihu1']
```

- 树结构为

```typescript
  options: CascaderOptionType[] = [
    {
      value: 'zhejiang1',
      label: 'Zhejiang',
      children: [
        {
          value: 'hangzhou1',
          label: 'Hangzhou',
          children: [
            {
              value: 'xihu1',
              label: 'West Lake',
            },
            {
              value: 'xiasha1',
              label: 'Xia Sha',
              disabled: true,
            },
          ],
        },
      ],
    },
  ]
```

### 是否只显示叶子节点的 label

输入框的回显，默认显示全路径

#### 代码演示

<code src="./demo/demo1/index.tsx"></code>

### 自定义显示

自定义分隔符，默认用 `/` 分割

#### 代码演示

<code src="./demo/demo2/index.tsx"></code>

### 是否只能选择叶子节点

默认为 true，只能选择到最后一级的节点。

<code src="./demo/demo3/index.tsx"></code>

### 动态加载选项

> 通常用来解决数据量巨大的情况
> 注意：① loadData 模式 与 showSearch 一起使用，只能搜索已动态加载过的数据。
> ② loadData 模式存在默认值时，未动态全部选项，所以在菜单展开时无法自动定位。
> 因此，动态加载选项还需要另外一套搜索、菜单渲染逻辑

1. 初始化 ：默认值，获取默认值的 options 塞到下拉菜单中
2. 搜索请求后端，重新返回所有的 option，搜索关键字清空后重置
   <code src="./demo/demo4/index.tsx"></code>

### 与 Form 表单一起使用

#### 代码演示

<API />
