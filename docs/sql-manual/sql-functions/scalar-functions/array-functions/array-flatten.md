---
{
    "title": "ARRAY_FLATTEN",
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

Flatten a multidimensional array into one dimension.

## Syntax

```sql
array_flatten(<a>)
```

## Parameters

| Parameter | Description | 
| --- | --- |
| `<a>` | ARRAY array |

## Return Value

Returns the flattened array

## Example

```sql
mysql> select array_flatten([[1,2,3],[4,5]]);
+--------------------------------+
| array_flatten([[1,2,3],[4,5]]) |
+--------------------------------+
| [1, 2, 3, 4, 5]                |
+--------------------------------+
1 row in set (0.01 sec)

mysql> select array_flatten([[[[[[1,2,3,4,5],[6,7],[8,9],[10,11],[12]],[[13]]],[[[14]]]]]]);
+-------------------------------------------------------------------------------+
| array_flatten([[[[[[1,2,3,4,5],[6,7],[8,9],[10,11],[12]],[[13]]],[[[14]]]]]]) |
+-------------------------------------------------------------------------------+
| [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]                               |
+-------------------------------------------------------------------------------+
1 row in set (0.02 sec)
```
