# ColumnVector &mdash; In-Memory Columnar Data

`ColumnVector` is the <<contract, contract>> of <<implementations, in-memory columnar data>> (of a <<type, DataType>>).

[[contract]]
.ColumnVector Contract (Abstract Methods Only)
[cols="1m,3",options="header",width="100%"]
|===
| Method
| Description

| getArray
a| [[getArray]]

[source, java]
----
ColumnarArray getArray(int rowId)
----

Used when...FIXME

| getBinary
a| [[getBinary]]

[source, java]
----
byte[] getBinary(int rowId)
----

Used when...FIXME

| getBoolean
a| [[getBoolean]]

[source, java]
----
boolean getBoolean(int rowId)
----

Used when...FIXME

| getByte
a| [[getByte]]

[source, java]
----
byte getByte(int rowId)
----

Used when...FIXME

| getChild
a| [[getChild]]

[source, java]
----
ColumnVector getChild(int ordinal)
----

Used when...FIXME

| getDecimal
a| [[getDecimal]]

[source, java]
----
Decimal getDecimal(
  int rowId,
  int precision,
  int scale)
----

Used when...FIXME

| getDouble
a| [[getDouble]]

[source, java]
----
double getDouble(int rowId)
----

Used when...FIXME

| getFloat
a| [[getFloat]]

[source, java]
----
float getFloat(int rowId)
----

Used when...FIXME

| getInt
a| [[getInt]]

[source, java]
----
int getInt(int rowId)
----

Used when...FIXME

| getLong
a| [[getLong]]

[source, java]
----
long getLong(int rowId)
----

Used when...FIXME

| getMap
a| [[getMap]]

[source, java]
----
ColumnarMap getMap(int ordinal)
----

Used when...FIXME

| getShort
a| [[getShort]]

[source, java]
----
short getShort(int rowId)
----

Used when...FIXME

| getUTF8String
a| [[getUTF8String]]

[source, java]
----
UTF8String getUTF8String(int rowId)
----

Used when...FIXME

| hasNull
a| [[hasNull]]

[source, java]
----
boolean hasNull()
----

Used when [OffHeapColumnVector](OffHeapColumnVector.md) and [OnHeapColumnVector](OnHeapColumnVector.md) are requested to `putNotNulls`

| isNullAt
a| [[isNullAt]]

[source, java]
----
boolean isNullAt(int rowId)
----

Used in many places

| numNulls
a| [[numNulls]]

[source, java]
----
int numNulls()
----

Used for testing purposes only

|===

[[implementations]]
.ColumnVectors (Direct Implementations and Extensions)
[cols="1,3",options="header",width="100%"]
|===
| ColumnVector
| Description

| `ArrowColumnVector`
| [[ArrowColumnVector]]

| `OrcColumnVector`
| [[OrcColumnVector]]

| [WritableColumnVector](WritableColumnVector.md)
| [[WritableColumnVector]] Writable column vectors with [off-heap](OffHeapColumnVector.md) and [on-heap](OnHeapColumnVector.md) memory variants

|===

[[creating-instance]]
[[type]]
[[dataType]]
`ColumnVector` takes a [DataType](DataType.md) of the column to be created.

NOTE: `ColumnVector` is a Java abstract class and cannot be <<creating-instance, created>> directly. It is created indirectly for the <<implementations, concrete ColumnVectors>>.

[NOTE]
====
`ColumnVector` is an `Evolving` contract that is evolving towards becoming a stable API, but is not a stable API yet and can change from one feature release to another release.

In other words, using the contract is as treading on thin ice.
====

=== [[getInterval]] `getInterval` Final Method

[source, java]
----
CalendarInterval getInterval(int rowId)
----

`getInterval`...FIXME

NOTE: `getInterval` is used when...FIXME

=== [[getStruct]] `getStruct` Final Method

[source, java]
----
ColumnarRow getStruct(int rowId)
----

`getStruct`...FIXME

NOTE: `getStruct` is used when...FIXME
