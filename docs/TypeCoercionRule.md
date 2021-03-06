# TypeCoercionRule -- Type Coercion Rules

`TypeCoercionRule` is the <<contract, contract>> of <<implementations, logical rules>> to <<coerceTypes, coerce>> and <<propagateTypes, propagate>> types in <<spark-sql-LogicalPlan.md#, logical plans>>.

[[contract]]
[source, scala]
----
package org.apache.spark.sql.catalyst.analysis

trait TypeCoercionRule extends Rule[LogicalPlan] {
  // only required methods that have no implementation
  // the others follow
  def coerceTypes(plan: LogicalPlan): LogicalPlan
}
----

.(Subset of) TypeCoercionRule Contract
[cols="1m,2",options="header",width="100%"]
|===
| Method
| Description

| coerceTypes
| [[coerceTypes]] Coerce types in a <<spark-sql-LogicalPlan.md#, logical plan>>

Used exclusively when `TypeCoercionRule` is <<apply, executed>>
|===

`TypeCoercionRule` is simply a <<catalyst/Rule.md#, Catalyst rule>> for transforming <<spark-sql-LogicalPlan.md#, logical plans>>, i.e. `Rule[LogicalPlan]`.

[[implementations]]
.TypeCoercionRules
[cols="1,2",options="header",width="100%"]
|===
| TypeCoercionRule
| Description

| CaseWhenCoercion
| [[CaseWhenCoercion]]

| ConcatCoercion
| [[ConcatCoercion]]

| DecimalPrecision
| [[DecimalPrecision]]

| Division
| [[Division]]

| EltCoercion
| [[EltCoercion]]

| FunctionArgumentConversion
| [[FunctionArgumentConversion]]

| IfCoercion
| [[IfCoercion]]

| ImplicitTypeCasts
| [[ImplicitTypeCasts]]

| [InConversion](logical-analysis-rules/InConversion.md)
| [[InConversion]]

| PromoteStrings
| [[PromoteStrings]]

| StackCoercion
| [[StackCoercion]]

| [WindowFrameCoercion](logical-analysis-rules/WindowFrameCoercion.md)
| [[WindowFrameCoercion]]
|===

## <span id="apply"> Executing Rule

```scala
apply(plan: LogicalPlan): LogicalPlan
```

`apply` <<coerceTypes, coerceTypes>> in the input <<spark-sql-LogicalPlan.md#, LogicalPlan>> and returns the following:

* The input <<spark-sql-LogicalPlan.md#, LogicalPlan>> itself if [matches](catalyst/TreeNode.md#fastEquals) the coerced plan

* The plan after <<propagateTypes, propagateTypes>> on the coerced plan

`apply` is part of the [Rule](catalyst/Rule.md#apply) abstraction.

=== [[propagateTypes]] `propagateTypes` Internal Method

[source, scala]
----
propagateTypes(plan: LogicalPlan): LogicalPlan
----

`propagateTypes`...FIXME

NOTE: `propagateTypes` is used exclusively when `TypeCoercionRule` is <<apply, executed>>.
