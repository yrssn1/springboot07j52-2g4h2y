# 基于web的网上摄影工作室的开发与实现

## 简介

本代码仅供学习参考使用

加QQ(**3055269939**)获取完整项目和论文

## 主要内容

### 数据库设计表

网上摄影工作室需要后台数据库，下面介绍数据库中的各个表的详细信息：

表4.1 摄影作品评论表

| 字段      | 类型         | 空   | 默认              | 注释     |
| --------- | ------------ | ---- | ----------------- | -------- |
| id (主键) | bigint(20)   | 否   |                   | 主键     |
| addtime   | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间 |
| refid     | bigint(20)   | 否   |                   | 关联表id |
| userid    | bigint(20)   | 否   |                   | 用户id   |
| nickname  | varchar(200) | 是   | NULL              | 用户名   |
| content   | longtext     | 否   |                   | 评论内容 |
| reply     | longtext     | 是   | NULL              | 回复内容 |

表4.2 摄影圈

| 字段      | 类型         | 空   | 默认              | 注释     |
| --------- | ------------ | ---- | ----------------- | -------- |
| id (主键) | bigint(20)   | 否   |                   | 主键     |
| addtime   | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间 |
| title     | varchar(200) | 是   | NULL              | 帖子标题 |
| content   | longtext     | 否   |                   | 帖子内容 |
| parentid  | bigint(20)   | 是   | NULL              | 父节点id |
| userid    | bigint(20)   | 否   |                   | 用户id   |
| username  | varchar(200) | 是   | NULL              | 用户名   |
| isdone    | varchar(200) | 是   | NULL              | 状态     |

表4.3 系统公告

| 字段         | 类型         | 空   | 默认              | 注释     |
| ------------ | ------------ | ---- | ----------------- | -------- |
| id (主键)    | bigint(20)   | 否   |                   | 主键     |
| addtime      | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间 |
| title        | varchar(200) | 否   |                   | 标题     |
| introduction | longtext     | 是   | NULL              | 简介     |
| picture      | varchar(200) | 否   |                   | 图片     |
| content      | longtext     | 否   |                   | 内容     |

表4.4 摄影作品

| 字段            | 类型         | 空   | 默认              | 注释         |
| --------------- | ------------ | ---- | ----------------- | ------------ |
| id (主键)       | bigint(20)   | 否   |                   | 主键         |
| addtime         | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间     |
| zuopinmingcheng | varchar(200) | 是   | NULL              | 作品名称     |
| zuopinfenlei    | varchar(200) | 是   | NULL              | 作品分类     |
| zuopinfengmian  | varchar(200) | 是   | NULL              | 作品封面     |
| zuopinjianjie   | longtext     | 是   | NULL              | 作品简介     |
| zuopinneirong   | longtext     | 是   | NULL              | 作品内容     |
| faburiqi        | date         | 是   | NULL              | 发布日期     |
| yonghuming      | varchar(200) | 是   | NULL              | 用户名       |
| nicheng         | varchar(200) | 是   | NULL              | 昵称         |
| thumbsupnum     | int(11)      | 是   | 0                 | 赞           |
| crazilynum      | int(11)      | 是   | 0                 | 踩           |
| clicktime       | datetime     | 是   | NULL              | 最近点击时间 |
| clicknum        | int(11)      | 是   | 0                 | 点击次数     |

表4.5 收藏表

| 字段      | 类型         | 空   | 默认              | 注释     |
| --------- | ------------ | ---- | ----------------- | -------- |
| id (主键) | bigint(20)   | 否   |                   | 主键     |
| addtime   | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间 |
| userid    | bigint(20)   | 否   |                   | 用户id   |
| refid     | bigint(20)   | 是   | NULL              | 收藏id   |
| tablename | varchar(200) | 是   | NULL              | 表名     |
| name      | varchar(200) | 否   |                   | 收藏名称 |
| picture   | varchar(200) | 否   |                   | 收藏图片 |

表4.6 管理员表

| 字段      | 类型         | 空   | 默认              | 注释     |
| --------- | ------------ | ---- | ----------------- | -------- |
| id (主键) | bigint(20)   | 否   |                   | 主键     |
| username  | varchar(100) | 否   |                   | 用户名   |
| password  | varchar(100) | 否   |                   | 密码     |
| role      | varchar(100) | 是   | 管理员            | 角色     |
| addtime   | timestamp    | 否   | CURRENT_TIMESTAMP | 新增时间 |

表4.7 用户

| 字段          | 类型         | 空   | 默认              | 注释     |
| ------------- | ------------ | ---- | ----------------- | -------- |
| id (主键)     | bigint(20)   | 否   |                   | 主键     |
| addtime       | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间 |
| yonghuming    | varchar(200) | 否   |                   | 用户名   |
| mima          | varchar(200) | 否   |                   | 密码     |
| xingming      | varchar(200) | 是   | NULL              | 姓名     |
| touxiang      | varchar(200) | 是   | NULL              | 头像     |
| nicheng       | varchar(200) | 是   | NULL              | 昵称     |
| xingbie       | varchar(200) | 是   | NULL              | 性别     |
| nianling      | int(11)      | 是   | NULL              | 年龄     |
| lianxidianhua | varchar(200) | 是   | NULL              | 联系电话 |

表4.8 作品分类

| 字段         | 类型         | 空   | 默认              | 注释     |
| ------------ | ------------ | ---- | ----------------- | -------- |
| id (主键)    | bigint(20)   | 否   |                   | 主键     |
| addtime      | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间 |
| zuopinfenlei | varchar(200) | 否   |                   | 作品分类 |