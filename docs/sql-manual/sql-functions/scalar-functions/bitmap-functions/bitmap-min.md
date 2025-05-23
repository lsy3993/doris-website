---
{
    "title": "BITMAP_MIN",
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

Computes and returns the minimum value in a Bitmap.

## Syntax

```sql
BITMAP_MIN(<bitmap>)
```

## Parameters

| Parameter  | Description                     |
|------------|---------------------------------|
| `<bitmap>` | A Bitmap type column or expression |

## Return Value

The minimum value in the Bitmap.  
Returns `NULL` if the Bitmap is empty.

## Examples

To compute the minimum value in an empty Bitmap:

```sql
select bitmap_min(bitmap_from_string('')) value;
```

The result will be:

```text
+-------+
| value |
+-------+
|  NULL |
+-------+
```

To compute the minimum value in a Bitmap with multiple elements:

```sql
select bitmap_min(bitmap_from_string('1,9999999999')) value;
```

The result will be:

```text
+-------+
| value |
+-------+
|     1 |
+-------+
```
