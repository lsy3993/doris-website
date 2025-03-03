---
{
  "title": "SHOW TRASH",
  "language": "en"
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



## Description

This statement is used to view the space occupied by garbage data in backend.

## Syntax

```sql
SHOW TRASH [ON ("<be_host>:<be_heartbeat_port>" [, ...])];
```

## Optional Parameters

**1. `[ON ("<be_host>:<be_heartbeat_port>" [, ...])]`**

Specify the backend that you want to view. If you do not add ON, all backend is displayed by default.


## Access Control Requirements

Users executing this SQL command must have at least the following privileges:


| Privilege  | Object | Notes                                        |
| :--------- | :----- | :------------------------------------------- |
| ADMIN_PRIV or NODE_PRIV | User or Role  | Only users or roles with the ADMIN_PRIV or NODE_PRIV privilege can perform the SHOW TRASH operation. |


## Examples

1. View the garbage data usage of all be nodes.


```sql
SHOW TRASH;
```

2. View the junk data usage of '192.168.0.1:9050' (disk information is displayed).


```sql
SHOW TRASH ON "192.168.0.1:9050";
```