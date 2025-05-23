---
{
    "title": "BITMAP_OR_COUNT",
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

Computes the union of two or more input Bitmaps and returns the count of elements in the union.

## Syntax

```sql
BITMAP_OR_COUNT(<bitmap1>, <bitmap2>, ..., <bitmapN>)
```

## Parameters

| Parameter   | Description    |
|-------------|----------------|
| `<bitmap1>` | The first Bitmap   |
| `<bitmap2>` | The second Bitmap  |
| ...         | ...            |
| `<bitmapN>` | The N-th Bitmap   |

## Return Value

The count of elements in the union of multiple Bitmaps.  
Returns `NULL` if any of the Bitmaps is `NULL`.

## Examples

To compute the count of elements in the union of a non-empty Bitmap and an empty Bitmap:

```sql
select bitmap_or_count(bitmap_from_string('1,2,3'), bitmap_empty());
```

The result will be:

```text
+--------------------------------------------------------------+
| bitmap_or_count(bitmap_from_string('1,2,3'), bitmap_empty()) |
+--------------------------------------------------------------+
|                                                            3 |
+--------------------------------------------------------------+
```

To compute the count of elements in the union of two identical Bitmaps:

```sql
select bitmap_or_count(bitmap_from_string('1,2,3'), bitmap_from_string('1,2,3'));
```

The result will be:

```text
+---------------------------------------------------------------------------+
| bitmap_or_count(bitmap_from_string('1,2,3'), bitmap_from_string('1,2,3')) |
+---------------------------------------------------------------------------+
|                                                                         3 |
+---------------------------------------------------------------------------+
```

To compute the count of elements in the union of two different Bitmaps:

```sql
select bitmap_or_count(bitmap_from_string('1,2,3'), bitmap_from_string('3,4,5'));
```

The result will be:

```text
+---------------------------------------------------------------------------+
| bitmap_or_count(bitmap_from_string('1,2,3'), bitmap_from_string('3,4,5')) |
+---------------------------------------------------------------------------+
|                                                                         5 |
+---------------------------------------------------------------------------+
```

To compute the count of elements in the union of multiple Bitmaps, including an empty Bitmap:

```sql
select bitmap_or_count(bitmap_from_string('1,2,3'), bitmap_from_string('3,4,5'), to_bitmap(100), bitmap_empty());
```

The result will be:

```text
+-----------------------------------------------------------------------------------------------------------+
| bitmap_or_count(bitmap_from_string('1,2,3'), bitmap_from_string('3,4,5'), to_bitmap(100), bitmap_empty()) |
+-----------------------------------------------------------------------------------------------------------+
|                                                                                                         6 |
+-----------------------------------------------------------------------------------------------------------+
```

To compute the count of elements in the union of multiple Bitmaps, including a `NULL` value:

```sql
select bitmap_or_count(bitmap_from_string('1,2,3'), bitmap_from_string('3,4,5'), to_bitmap(100), NULL);
```

The result will be:

```text
+-------------------------------------------------------------------------------------------------+
| bitmap_or_count(bitmap_from_string('1,2,3'), bitmap_from_string('3,4,5'), to_bitmap(100), NULL) |
+-------------------------------------------------------------------------------------------------+
|                                                                                            NULL |
+-------------------------------------------------------------------------------------------------+
```
