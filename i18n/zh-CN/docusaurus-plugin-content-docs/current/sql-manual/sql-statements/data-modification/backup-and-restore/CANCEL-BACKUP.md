---
{
"title": "CANCEL BACKUP",
"language": "zh-CN"
}
---

<!--
Licensed to the Apache Software Foundation (ASF) under one
or more contributor license agreements.  See the NOTICE file
distributed with this work for additional information
regarding copyright ownership.  The ASF licenses this file
to you under the Apache License, Version 2.0 (the
"License"); you may not use this file except in compliance
with the License.  You may obtain a copy of the License at

  http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing,
software distributed under the License is distributed on an
"AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
KIND, either express or implied.  See the License for the
specific language governing permissions and limitations
under the License.
-->

## 描述

该语句用于取消一个正在进行的 BACKUP 任务。

## 语法

```sql
CANCEL BACKUP FROM <db_name>;
```

## 参数

**1.`<db_name>`**

备份任务所属数据库名。

## 示例

1. 取消 example_db 下的 BACKUP 任务。

```sql
CANCEL BACKUP FROM example_db;
```

