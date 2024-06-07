---
categories: [个人笔记]
attachments: [Clipboard_2022-09-09-22-20-12.png, Clipboard_2022-09-09-22-26-08.png, Clipboard_2022-09-09-22-35-33.png, Clipboard_2022-09-09-22-37-06.png, Clipboard_2022-09-09-22-37-42.png, Clipboard_2022-09-09-22-38-20.png, Clipboard_2022-09-09-22-39-01.png, Clipboard_2022-09-09-22-50-19.png, Clipboard_2022-09-09-22-55-07.png, Clipboard_2022-09-09-22-55-23.png, Clipboard_2022-09-09-22-59-12.png, Clipboard_2022-09-09-23-05-04.png, Clipboard_2022-09-09-23-06-54.png, Clipboard_2022-09-09-23-07-31.png, Clipboard_2022-09-09-23-08-13.png, Clipboard_2022-09-09-23-16-24.png, Clipboard_2022-09-09-23-16-42.png, Clipboard_2022-09-09-23-17-28.png, Clipboard_2022-09-09-23-18-34.png, Clipboard_2022-09-09-23-19-05.png, Clipboard_2022-09-09-23-20-58.png, Clipboard_2022-09-09-23-24-14.png, Clipboard_2022-09-10-15-07-16.png, Clipboard_2022-09-10-15-07-50.png, Clipboard_2022-09-10-15-09-09.png, Clipboard_2022-09-10-15-11-13.png, Clipboard_2022-09-10-15-15-26.png, Clipboard_2022-09-10-15-19-04.png, Clipboard_2022-09-10-15-19-15.png, Clipboard_2022-09-11-16-59-02.png, Clipboard_2022-09-11-16-59-11.png, Clipboard_2022-09-11-16-59-21.png, Clipboard_2022-09-11-16-59-31.png, Clipboard_2022-09-11-17-06-47.png, Clipboard_2022-09-11-17-08-07.png, Clipboard_2022-09-11-17-08-50.png, Clipboard_2022-09-11-17-10-30.png, Clipboard_2022-09-11-17-11-28.png, Clipboard_2022-09-11-17-11-58.png, Clipboard_2022-09-11-17-12-10.png, Clipboard_2022-09-11-17-15-04.png, Clipboard_2022-09-11-17-16-42.png, Clipboard_2022-09-11-17-16-51.png, Clipboard_2022-09-11-17-17-29.png, Clipboard_2022-09-11-17-18-37.png, Clipboard_2022-09-11-17-18-39.png, Clipboard_2022-09-11-17-18-53.png, Clipboard_2022-09-11-17-20-19.png, Clipboard_2022-09-11-17-21-51.png, Clipboard_2022-09-11-17-23-27.png, Clipboard_2022-09-11-17-25-00.png, Clipboard_2022-09-11-17-26-19.png, Clipboard_2022-09-11-17-43-01.png, Clipboard_2022-09-11-18-14-24.png, Clipboard_2022-09-11-18-15-25.png, Clipboard_2022-09-11-18-15-50.png, Clipboard_2022-09-11-18-16-11.png, Clipboard_2022-09-11-18-17-15.png, Clipboard_2022-09-11-18-18-36.png, Clipboard_2022-09-11-18-18-50.png, Clipboard_2022-09-11-18-19-03.png, Clipboard_2022-09-11-18-19-29.png, Clipboard_2022-09-11-18-19-57.png, Clipboard_2022-09-11-18-20-41.png, Clipboard_2022-09-11-18-21-02.png, Clipboard_2022-09-11-18-21-24.png, Clipboard_2022-09-11-18-37-52.png, Clipboard_2022-09-11-19-39-56.png]
tags: [个人笔记]
title: KT-Cloud-Management
date: '2022-09-06T08:15:38.208Z'
lastmod: '2024-05-08T11:16:12.670Z'
---

# KT-Cloud-Management

## 文件结构

### 自建rancher api 密钥

```
Bearer token-7dtp2:jlmd8csggxwtlz7zgj2m55r6zkxz8rg5znbzrxjbpdxrd6jjtnjwcn
// 服务器地址 192.168.131.138
```

### public

- assets
  **图片...**

- css-***reset.css***
  **重置全局样式**

- ***index.html***
  **根DOM**

### src

- api
    - ***ajax.js***
      **封装axiosAPI请求**

    - ***index.js***
      **ajax请求**
    
- components
    - Base
        - selfdefined-card
          只含一个redio单选框，传送数据格式参下

          ```
          options={[
              { number: 1, key: 8, value: 'op', label: 'okkk' },
              { number: 1, key: 7, value: 'op', label: 'okkk' },
              { number: 1, key: 6, value: 'op', label: 'okkk' },
              { number: 1, key: 5, value: 'op', label: 'okkk' },
              { number: 1, key: 4, value: 'op', label: 'okkk' }
          ]}
          ```

        - selfdefined-cardpanel
          ![](/images/attachments/Clipboard_2022-09-09-22-26-08.png)
          数据格式：

          ```
            clusterInfo={{
                title: '集群title',
                status: '集群状态',
                tatol: '总量',
                version: '版本',
                createtime: '创建时间'
            }}
          ```

        - selfdefined-panel
          ![](/images/attachments/Clipboard_2022-09-09-22-35-33.png)
          
          ```
            <Com panelInfo={{
                ifKnowledges: [{key: 'key'}, {key: 'key0'}],
                panelIcon: 'icon',
                title: 'title',
                description: '描述'
            }}
          ```

        - selfdefined-radio
          ![](/images/attachments/Clipboard_2022-09-09-22-20-12.png)

        - selfdefined-table
          ![](/images/attachments/Clipboard_2022-09-09-22-37-06.png)

        - selfdefined-table-manage
          ![](/images/attachments/Clipboard_2022-09-09-22-38-20.png)

        - selfdefined-table-member
          ![](/images/attachments/Clipboard_2022-09-09-22-37-42.png)

        - selfdefined-table-sorce-show
          ![](/images/attachments/Clipboard_2022-09-09-22-39-01.png)

    - DefinedTable
        - ***DefinedTable.jsx***
          ![](/images/attachments/Clipboard_2022-09-09-22-50-19.png)
          ```
            <Com
                columns={[{ title: 'title', dataIndex: 'dataIndex', sorter: 'sorter' },
                { title: 'title', dataIndex: 'dataIndex', sorter: 'sorter' },
                { title: 'title', dataIndex: 'dataIndex', sorter: 'sorter' }]}
                data={[{ key: 'ok' },{ key: 'ok1' },{ key: 'ok2' },{ key: 'ok3' }, ]}
                needRowSelection={() => { }}
                rowSelectCbk={() => { }}
                needSearch={() => { }}
                needOperation={() => { }}
                operationCbks={() => { }}
            />
          ```
        - ***DefinedTable.less***
        - ***TableContainer.jsx***
          connect容器，看代码是一个redux reducer
    - footer
        - ***index.jsx***
          还没有写
    - header
        - ***index.css***
        - ***index.jsx***
          ![](/images/attachments/Clipboard_2022-09-09-22-55-07.png)
          ![](/images/attachments/Clipboard_2022-09-09-22-55-23.png)
        - ***index.less***
    - Input
        - ***DefinedInput.jsx***
          ![](/images/attachments/Clipboard_2022-09-09-22-59-12.png)
          ```
            const {
              inputTitle = 'unkownTitle',
              suffixText = '',
              placeholder = '请输入',
              required = true
            } = props;
          ```
        - ***DefinedInput.less***

        - ***DefinedSelect.css***
        - ***DefinedSelect.jsx***
          ![](/images/attachments/Clipboard_2022-09-09-23-05-04.png)
          ```
            const { inputTitle = 'unkownTitle' } = props;
            const { selectOptions=[2, 4, 5], onChange=()=>{} } = props
          ```
        - ***DefinedSelect.less***

        - ***DefinedTextArea.jsx***
          ![](/images/attachments/Clipboard_2022-09-09-23-06-54.png)
        - ***DefinedTextArea.less***

        - ***FormInput.jsx***
          ![](/images/attachments/Clipboard_2022-09-09-23-07-31.png)
        - ***StepInput.less***
        - ***StepInput.jsx***
          ![](/images/attachments/Clipboard_2022-09-09-23-08-13.png)
    - left-nav
        - ***index.css***
        - ***index.jsx***
        ![](/images/attachments/Clipboard_2022-09-09-23-16-24.png)
        ![](/images/attachments/Clipboard_2022-09-09-23-16-42.png)
        - ***index.less***
    - Modal
        - AddClusterUser
          ![](/images/attachments/Clipboard_2022-09-09-23-18-34.png)
        - ThreeStepModal
          ![](/images/attachments/Clipboard_2022-09-09-23-19-05.png)
        - ***Test.css***
        - ***Test.jsx***
          ![](/images/attachments/Clipboard_2022-09-09-23-17-28.png)
    - Select
        - ***DefinedSelect.jsx***
          ![](/images/attachments/Clipboard_2022-09-09-23-20-58.png)
          ```
            const { selectTitle='def', nameSpaces=[1,2,3], placeholder='ph' } = props
          ```
        - ***DefinedSelect.less***
    - YAMLEditor
        - ***DiffYAMLEditor.jsx***
          ![](/images/attachments/Clipboard_2022-09-09-23-24-14.png)
        - ***DiffYAMLEditor.less***
        - ***NormalYAMLDisplayer.jsx***
          只有展示的yaml编辑器
        - ***NormalYAMLEditor.jsx***
          可以修改的yaml编辑器，需要传回调函数onchange
        - ***YAMLValidatorExample.js***
          JS对yaml文件的验错插件实例

- config
    - ***menuConfig.js***
      左导航栏菜单的配置

- mock （伪造API）
    - clustermanage
    - ***index.js***
    - ***table.js***

- pages
    - admin
        - create
          ***Hypform***
          ![](/images/attachments/Clipboard_2022-09-10-15-09-09.png)
          ***clusterform***
          ![](/images/attachments/Clipboard_2022-09-10-15-11-13.png)
          ***hyptable***
          ![](/images/attachments/Clipboard_2022-09-10-15-15-26.png)
        - platformInfo
          ![](/images/attachments/Clipboard_2022-09-10-15-19-15.png)
        - userInfo
          ![](/images/attachments/Clipboard_2022-09-10-15-19-04.png)
        - ***admin.css***
        - ***admin.jsx***
          ![](/images/attachments/Clipboard_2022-09-10-15-07-50.png)
        - ***admin.less***
    - clustermanage
        - applications
          - deployment
          ![](/images/attachments/Clipboard_2022-09-11-17-10-30.png)
          - daemonSets
          ![](/images/attachments/Clipboard_2022-09-11-17-11-28.png)
          - statefulSets
          ![](/images/attachments/Clipboard_2022-09-11-17-11-58.png)
          - pods
          ![](/images/attachments/Clipboard_2022-09-11-17-12-10.png)

        - components

        - monitor
          ![](/images/attachments/Clipboard_2022-09-11-17-23-27.png)

        - namespace
          index:
          ![](/images/attachments/Clipboard_2022-09-11-17-08-07.png)
          namespaceConfigure
          ![](/images/attachments/Clipboard_2022-09-11-17-26-19.png)

        - nodes
          index:
          ![](/images/attachments/Clipboard_2022-09-11-17-08-50.png)
          nodeConfigure:
          ![](/images/attachments/Clipboard_2022-09-11-17-25-00.png)

        - overview
          ![](/images/attachments/Clipboard_2022-09-11-17-06-47.png)

        - service
          ![](/images/attachments/Clipboard_2022-09-11-17-20-19.png)

        - serviceCreate
          ![](/images/attachments/Clipboard_2022-09-11-17-21-51.png)

        - ServiceFrom
          没东西

        - storage
          - PV
            index:
            ![](/images/attachments/Clipboard_2022-09-11-17-17-29.png)
            create:
            ![](/images/attachments/Clipboard_2022-09-11-17-16-51.png)
            YAMLconf:
            ![](/images/attachments/Clipboard_2022-09-11-17-18-37.png)
          - PVC
            index:
            ![](/images/attachments/Clipboard_2022-09-11-17-15-04.png)
            create:
            ![](/images/attachments/Clipboard_2022-09-11-17-18-53.png)
            YAMLconf:
            ![](/images/attachments/Clipboard_2022-09-11-17-18-39.png)

        - store
          `combineReducer(/overview/store)`

        - yaml
          应用负载与服务管理页面的编辑YAML选项页面：
          ![](/images/attachments/Clipboard_2022-09-11-17-43-01.png)

        - ***index.jsx***
          一大堆路由

    - clusternodes
        - deploymentStatus
          ![](/images/attachments/Clipboard_2022-09-11-18-20-41.png)

        - events
          ![](/images/attachments/Clipboard_2022-09-11-18-19-03.png)

        - label
          ![](/images/attachments/Clipboard_2022-09-11-18-19-29.png)

        - log
          ![](/images/attachments/Clipboard_2022-09-11-18-19-57.png)

        - monitors
          ![](/images/attachments/Clipboard_2022-09-11-18-15-50.png)

        - nodeimg
          ![](/images/attachments/Clipboard_2022-09-11-18-18-50.png)

        - pods
          ![](/images/attachments/Clipboard_2022-09-11-18-18-36.png)

        - podsstatus
          ![](/images/attachments/Clipboard_2022-09-11-18-21-02.png)

        - resource
          ![](/images/attachments/Clipboard_2022-09-11-18-17-15.png)

        - servicestatus
          ！！！貌似location.state有问题载入的是deploymentstate的页面
          （已解决，在clusternodes/index中，optionsCfg[123行]，默认为deploymentStatus）
          ![](/images/attachments/Clipboard_2022-09-11-18-21-24.png)
          以下为真实页面
          ![](/images/attachments/Clipboard_2022-09-11-19-39-56.png)

        - status
          ![](/images/attachments/Clipboard_2022-09-11-18-37-52.png)
          
        - store
          redux reducer

        - yaml
          ![](/images/attachments/Clipboard_2022-09-11-18-15-25.png)

        - ***index.css***
        - ***index.jsx***
        拥有首页多个状态的子页面：
        ![](/images/attachments/Clipboard_2022-09-11-18-16-11.png)
        - ***index.less***

    - login
        - images
        - ***login.css***
        - ***login.jsx***
          登录界面
          ![](/images/attachments/Clipboard_2022-09-10-15-07-16.png)
        - ***login.less***

    - pod
        - events
          ![](/images/attachments/Clipboard_2022-09-11-16-59-31.png)
        - resource-status
          ![](/images/attachments/Clipboard_2022-09-11-16-59-02.png)
        - schedule
          ![](/images/attachments/Clipboard_2022-09-11-16-59-21.png)
        - ***index.css***
        - ***index.jsx***
          ![](/images/attachments/Clipboard_2022-09-11-16-59-11.png)
        - ***index.less***

- store
    - ***index.js***
      redux store 以及使用异步中间件
    - ***reducer.js***
      combine reducers 主要是 集群管理 与 集群节点 两个大页面的状态管理
- utils
    - ***constant.js***
      颜色16进制常量们
    - ***downloadUtils.js***
      下载yaml文件的函数，blob二进制数据
    - ***json2yaml.js***
      json To yaml
    - ***memoryUtils.js***
      在内存保存数据的模块
    - ***storageUtils.js***
      在浏览器storege里存储
    - ***YAMLUtils.js***
      保证yaml文件属性不变
- ***app.jsx***
- ***index.jsx***

## API

- rancher api server

### redux reducer 结构

clusterManage/overview/store `combinedTo` clusterManage/store

clusterNodes

## 技术栈

### frontend

- craco
- react & react-dom & react-router-dom
- redux & react-redux & redux-thunk
- axios
- mockjs
- kube-design/components
- echarts
- js-cookie

### backend

- docker
- kubernetes
- rancher
