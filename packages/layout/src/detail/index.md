---
title: 详情布局 - DetailLayout
nav:
  title: 布局
  path: /layout
  order: 2
group:
  title: layout
  path: /layout
---

## 基础表现

```tsx
/**
 * title: 详情布局组件
 * desc: 基础使用
 */
import React from 'react';
import { BlIcon } from '@blacklake-web/component';
import { DetailLayout, DetailLayoutInfoBlock } from '@blacklake-web/layout';

export default () => {
  const dataSource = {
    warehouseName: 'warehouseNametest超长的仓库名称释义的就是这样的长度',
    warehouseCode: 'warehouseCode',
    parentName: 'parentName',
    parentCode: 'parentCode',
    name: 'name',
    code: 'code',
  };

  const baseMenu = [
    {
      key: 'edit',
      onClick: () => {},
      icon: <BlIcon type="iconqiyong" />,
    },
    {
      key: 'refresh',
      onClick: () => {},
      icon: <BlIcon type="iconshuaxin" />
    }
  ];

  const detailInfo: DetailLayoutInfoBlock = {
    title: '仓库信息',
    items: [
      {
        label: '仓库名称',
        dataIndex: 'warehouseName',
        render: (warehouseName) => warehouseName ?? '-',
      },
      {
        label: '仓库编号',
        dataIndex: 'warehouseCode',
        render: (warehouseCode) => warehouseCode ?? '-',
      },
      {
        label: '仓库编号',
        dataIndex: 'warehouseCode',
        render: (warehouseCode) => warehouseCode ?? '-',
      },
      {
        label: '仓库编号',
        dataIndex: 'warehouseCode',
        render: (warehouseCode) => warehouseCode ?? '-',
      },
      {
        label: '仓库编号',
        dataIndex: 'warehouseCode',
        render: (warehouseCode) => warehouseCode ?? '-',
      },
      {
        label: '上级区域名称',
        dataIndex: 'parentName',
        render: (parentName) => parentName ?? '-',
      },
      {
        label: '上级区域编号',
        dataIndex: 'parentCode',
        render: (parentCode) => parentCode ?? '-',
      },
      { label: '区域名称', dataIndex: 'name' },
      { label: '区域编号', dataIndex: 'code' },
    ],
    column: 2,
  };

  const materialInfo: DetailLayoutInfoBlock = {
    title: '物料信息',
    items: [
      {
        label: '投入物料',
        dataIndex: 'warehouseName',
        desc: '投入生产的物料',
        render: (warehouseName) => warehouseName ?? '-',
      },
      {
        label: '产出物料',
        dataIndex: 'warehouseCode',
        render: (warehouseCode) => warehouseCode ?? '-',
      }
    ],
    column: 2,
  };

    const otherInfo: DetailLayoutInfoBlock = {
    title: '其他信息',
    items: [
      {
        label: '附件',
        dataIndex: 'warehouseName',
        isFullLine: true,
        render: (warehouseName) => warehouseName ?? '-',
      },
      {
        label: '备注',
        dataIndex: 'warehouseCode',
        render: (warehouseCode) => warehouseCode ?? '-',
      }
    ],
    column: 2,
  };

  return (
    <div style={{ border: '1px solid #d8d8d8' }}>
      <DetailLayout title="详情" info={[detailInfo, materialInfo, otherInfo]} dataSource={dataSource} baseMenu={baseMenu} />
    </div>
  );
};
```

## modal,drawer 配套

```tsx
/**
 * title: modal，drawer
 * desc: 配合 DetailLayoutForModal 或 DetailLayoutForDrawer 定制使用
 */
import React, { useState } from 'react';
import { Button } from 'antd';
import {
  DetailLayout,
  DetailLayoutForModal,
  DetailLayoutForDrawer,
  DetailLayoutInfoBlock,
} from '@blacklake-web/layout';
import { BlIcon } from '@blacklake-web/component';

export default () => {
  const [visibleType, setVisibleType] = useState('');

  const dataSource = {
    warehouseName: 'warehouseName',
    warehouseCode: 'warehouseCode',
    parentName: 'parentName',
    parentCode: 'parentCode',
    name: 'name',
    code: 'code',
  };

  const baseMenu = [
    {
      key: 'edit',
      onClick: () => {},
      title: '转移',
    },
    {
      key: 'delate',
      onClick: () => {},
      title: '刷新',
    }
  ];

  const detailInfo: DetailLayoutInfoBlock = {
    title: '仓库信息',
    items: [
      {
        label: '仓库名称',
        dataIndex: 'warehouseName',
        render: (warehouseName) => warehouseName ?? '-',
      },
      {
        label: '仓库编号',
        dataIndex: 'warehouseCode',
        render: (warehouseCode) => warehouseCode ?? '-',
      },
      {
        label: '上级区域名称',
        dataIndex: 'parentName',
        render: (parentName) => parentName ?? '-',
      },
      {
        label: '上级区域编号',
        dataIndex: 'parentCode',
        render: (parentCode) => parentCode ?? '-',
      },
      { label: '区域名称', dataIndex: 'name' },
      { label: '区域编号', dataIndex: 'code' },
    ],
    column: 2,
  };

  const onCancel = () => {
    setVisibleType('');
  };

  return (
    <div>
      <Button
        onClick={() => {
          setVisibleType('modal');
        }}
      >
        open modal
      </Button>
      <Button
        onClick={() => {
          setVisibleType('drawer');
        }}
      >
        open drawer
      </Button>
      <DetailLayoutForModal
        visible={visibleType === 'modal'}
        onClose={onCancel}
        width={800}
        content={<DetailLayout title="详情" info={[detailInfo]} dataSource={dataSource} />}
      />
      <DetailLayoutForDrawer
        visible={visibleType === 'drawer'}
        onClose={onCancel}
        width={800}
        content={
          <DetailLayout
            title="详情"
            info={[detailInfo]}
            dataSource={dataSource}
            baseMenu={baseMenu}
          />
        }
      />
    </div>
  );
};
```

<API src="/detailLayout.tsx"/>

## DetailLayoutInfoBlock

| 参数   | 说明               | 类型                     | 默认值 |
| ------ | ------------------ | ------------------------ | ------ |
| title  | 标题，不填不显示   | `ReactNode`              | -      |
| extra  | 标题右边拓展内容， | `ReactNode`              | -      |
| column | 每行的列数量       | `number`                 | 1      |
| items  | 当前标题下内容     | `DetailLayoutInfoItem[]` |        |

## DetailLayoutInfoItem

| 参数      | 说明                  | 类型                | 默认值 |
| --------- | --------------------- | ------------------- | ------ |
| label     | 名称 label            | `string`            | -      |
| dataIndex | 你懂的                | `string[] / string` | -      |
| span      | 当前占几列            | `number`            | 1      |
| render    | FormItem 内的输入组件 | `() => ReactNode`   | -      |
| toggle    | 支持展开、收起        | `boolean`           | false  |
