# Work with lists of objects 

To show how a list of related objects is processed or evaluate an operation on a list of items, put the entire list of items into a table or a bullet or numbered list, and use it as an argument of a normal text step by including directly below the step.

Tables and lists that follow an executable text step are passed to the related step execution function as a single argument, rather than evaluated line-by-line. You can then use the list of objects to pre-populate a database, or compare lists to expectations. DaSpec will report missing, additional and matching items in a way that is easy to read and understand.

[Example: Tables As Lists Of Objects](../examples/tables_as_lists_of_objects.md)

## Step implementation

To implement a matching step, define a matcher for the entire table header row (column titles). The assigned step processor will be called for all table data rows, from top to bottom. The arguments to the step processor will be cell values, in sequence from left to right. If the regular expression for the table header has matching groups, they will be passed to the processor after the cell values. 

# Writing tips 

There are no specific requirements from DaSpec for naming organising table information, but the following writing tips will help your readers get the most out of the specification: 

* When objects in the list have several important properties, tables can visually group the related information together nicely.
* If you only want to show a single property (such as the item name), use lists instead. 
* If you want to show a list where order is important, use numbered lists. If the order is not important, use bullet-lists.
* It's a good practice to formulate the steps so that it is clear if the lists are inputs or expected outputs. For example, use past tense to show inputs, and future tense to show outputs. Alternatively, formulate the example as Given _some inputs_, ... Then _some outputs_.
* When using tables, make the first column something that readers can easily use to identify the entire row -- for example the item name, or unique ID. This will make it easier to understand and troubleshoot examples. In the future, DaSpec will also use partial matching from left to right, so it will be able to report on single attribute differences better than failing an entire row.