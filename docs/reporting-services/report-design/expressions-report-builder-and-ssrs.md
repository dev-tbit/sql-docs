---
title: "Expressions in a paginated report | Microsoft Docs"
description: Control the content, design, and interactivity of your paginated report with expressions that enable you to retrieve, display, filter, and format data in Report Builder.
ms.date: 09/06/2016
ms.service: reporting-services
ms.subservice: report-design


ms.topic: conceptual
ms.assetid: 76d3ac86-650c-46fe-8086-8b3edcea3882
author: maggiesMSFT
ms.author: maggies
---
# Expressions in a paginated report (Report Builder)

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-ssrs-rb](../../includes/ssrs-appliesto-ssrs-rb.md)] [!INCLUDE [ssrs-appliesto-pbi-rb](../../includes/ssrs-appliesto-pbi-rb.md)] [!INCLUDE [ssrb-applies-to-ssdt-yes](../../includes/ssrb-applies-to-ssdt-yes.md)]

  Expressions are widely used throughout paginated reports to retrieve, calculate, display, group, sort, filter, parameterize, and format data. 
  
  Many report item properties can be set to an expression. Expressions help you control the content, design, and interactivity of your report. Expressions are written in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], saved in the report definition, and evaluated by the report processor when you run the report.  
  
 Unlike applications such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel where you work with data directly in a worksheet, in a report, you work with expressions that are placeholders for data. To see the actual data from the evaluated expressions, you must preview the report. When you run the report, the report processor evaluates each expression as it combines report data and report layout elements such as tables and charts.  
  
 As you design a report, many expressions for report items are set for you. For example, when you drag a field from the data pane to a table cell on the report design surface, the text box value is set to a simple expression for the field. In the following figure, the Report Data pane displays the dataset fields ID, Name, SalesTerritory, Code, and Sales. Three fields have been added to the table: [Name], [Code], and [Sales]. The notation [Name] on the design surface represents the underlying expression `=Fields!Name.Value`.  
  
 ![rs_DataDesignandPreview](../../reporting-services/report-data/media/rs-datadesignandpreview.gif "rs_DataDesignandPreview")  
  
 When you preview the report, the report processor combines the table data region with the actual data from the data connection and displays a row in the table for every row in the result set.  
  
 To enter expressions manually, select an item on the design surface, and use shortcut menus and dialog boxes to set the properties of the item. When you see the ***(fx)*** button or the value `<Expression>` in a drop-down list, you know that you can set the property to an expression. For more information, see [Add an Expression &#40;Report Builder and SSRS&#41;](../../reporting-services/report-design/add-an-expression-report-builder-and-ssrs.md).  
  
 To develop complex expressions or expressions that use custom code or custom assemblies, we recommend that you use Report Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. For more information, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="Types"></a> Understanding Simple and Complex Expressions  
 Expressions begin with an equal sign (=) and are written in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]. Expressions can include a combination of constants, operators, and references to built-in values (fields, collections, and functions), and to external or custom code.  
  
 You can use expressions to specify the value of many report item properties. The most common properties are values for text boxes and placeholder text. Typically, if a text box contains only one expression, the expression is the value of the text box property. If a text box contains multiple expressions, each expression is the value of placeholder text in the text box.  
  
 By default, expressions appear on the report design surface as *simple* or *complex expressions*.  
  
-   **Simple** A simple expression contains a reference to a single item in a built-in collection, for example, a dataset field, a parameter, or a built-in field. On the design surface, a simple expression appears in brackets. For example, `[FieldName]` corresponds to the underlying expression `=Fields!FieldName.Value`. Simple expressions are created for you automatically as you create the report layout and drag items from the Report Data pane to the design surface. For more information about the symbols that represent different built-in collections, see [Understanding Prefix Symbols for Simple Expressions](#DisplayText).  
  
-   **Complex** A complex expression contains references to multiple built-in references, operators, and function calls. A complex expression appears as <\<Expr>> when the expression value includes more than a simple reference. To view the expression, hover over it and use the tooltip. To edit the expression, open it in the **Expression** dialog box.  
  
 The following figure shows typical simple and complex expressions for both text boxes and placeholder text.  
  
 ![rs_ExpressionDefaultFormat](../../reporting-services/report-design/media/rs-expressiondefaultformat.gif "rs_ExpressionDefaultFormat")  
  
 To display sample values instead of text for expressions, apply formatting to the text box or placeholder text. The following figure shows the report design surface toggled to show sample values:  
  
 ![rs_ExpressionSampleValuesFormat](../../reporting-services/report-design/media/rs-expressionsamplevaluesformat.gif "rs_ExpressionSampleValuesFormat")  
  
 For more information, see [Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](../../reporting-services/report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md).  
  
## <a name="DisplayText"></a> Understanding Prefix Symbols in Simple Expressions  

Simple expressions use symbols to indicate whether the reference is to a field, a parameter, a built-in collection, or the ReportItems collection. The following table shows examples of display and expression text:  
  
|Item|Display text example|Expression text example|  
|----------|--------------------------|-----------------------------|  
|Dataset fields|`[Sales]`<br /><br /> `[SUM(Sales)]`<br /><br /> `[FIRST(Store)]`|`=Fields!Sales.Value`<br /><br /> `=Sum(Fields!Sales.Value)`<br /><br /> `=First(Fields!Store.Value)`|  
|Report parameters|`[@Param]`<br /><br /> `[@Param.Label]`|`=Parameters!Param.Value`<br /><br /> `=Parameters!Param.Label`|  
|Built-in fields|`[&ReportName]`|`=Globals!ReportName.Value`|  
|Literal characters used for display text|`\[Sales\]`|`[Sales]`|  
  
##  <a name="References"></a> Writing Complex Expressions  
 Expressions can include references to functions, operators, constants, fields, parameters, items from built-in collections, and to embedded custom code or custom assemblies.  
  
> [!NOTE]
>  To develop complex expressions or expressions that use custom code or custom assemblies, we recommend that you use Report Designer in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. For more information, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
 The following table lists the kinds of references you can include in an expression:  
  
|References|Description|Example|  
|----------------|-----------------|-------------|  
|[Constants](../../reporting-services/report-design/constants-in-expressions-report-builder-and-ssrs.md)|Describes the constants you can access interactively for properties that require constant values, such as font colors.|`="Blue"`|  
|[Operators](../../reporting-services/report-design/operators-in-expressions-report-builder-and-ssrs.md)|Describes the operators you can use to combine references in an expression. For example, the **&** operator is used for concatenating strings.|`="The report ran at: " & Globals!ExecutionTime & "."`|  
|[Built-in Collections](../../reporting-services/report-design/built-in-collections-in-expressions-report-builder.md)|Describes the built-in collections that you can include in an expression, such as `Fields`, `Parameters`, and `Variables`.|`=Fields!Sales.Value`<br /><br /> `=Parameters!Store.Value`<br /><br /> `=Variables!MyCalculation.Value`|  
|[Built-in Report and Aggregate Functions](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md)|Describes the built-in functions, such as `Sum` or `Previous`, that you can access from an expression.|`=Previous(Sum(Fields!Sales.Value))`|  
|[Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)|Describes how you can access the built-in CLR classes <xref:System.Math> and <xref:System.Convert>, other CLR classes, [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] run-time library functions, or methods from an external assembly.<br /><br /> Describes how you can access custom code that is embedded in your report, or that you compile and install as a custom assembly on both the report client and the report server.|`=Sum(Fields!Sales.Value)`<br /><br /> `=CDate(Fields!SalesDate.Value)`<br /><br /> `=DateAdd("d",3,Fields!BirthDate.Value)`<br /><br /> `=Code.ToUSD(Fields!StandardCost.Value)`|  
   
##  <a name="Valid"></a> Validating Expressions  
 When you create an expression for a specific report item property, the references that you can include in an expression depend on the values that the report item property can accept and the scope in which the property is evaluated. For example:  
  
-   By default, the expression [Sum] calculates the sum of data that is in scope at the time the expression is evaluated. For a table cell, the scope depends on row and column group memberships. For more information, see [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
-   For the value for a Font property, the value must evaluate to the name of a font.  
  
-   Expression syntax is validated at design time. Expression scope validation occurs when you publish the report. For validation that depends on the actual data, errors can only be detected at run-time. Some of these expressions produce #Error as an error message in the rendered report. To help determine the issues for this kind of error, you must use Report Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Report Designer provides an Output window that provides more information about these errors.  
  
 For more information, see [Expression Reference &#40;Report Builder and SSRS&#41;](../../reporting-services/report-design/expression-reference-report-builder-and-ssrs.md).  
  
##  <a name="Section"></a> In This Section  
 [Add an Expression &#40;Report Builder and SSRS&#41;](../../reporting-services/report-design/add-an-expression-report-builder-and-ssrs.md)  
  
 [Expression Uses in Reports &#40;Report Builder and SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)  
  
 [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
 [Expression Reference &#40;Report Builder and SSRS&#41;](../../reporting-services/report-design/expression-reference-report-builder-and-ssrs.md)  

## See Also
 For more information and examples, see the following topics:  
  
-   [Expression Uses in Reports &#40;Report Builder and SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)  
-   [Expression Examples &#40;Report Builder and SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)  
-   [Filter Equation Examples &#40;Report Builder and SSRS&#41;](../../reporting-services/report-design/filter-equation-examples-report-builder-and-ssrs.md)  
-   [Group Expression Examples &#40;Report Builder and SSRS&#41;](../../reporting-services/report-design/group-expression-examples-report-builder-and-ssrs.md)  
-   [Tutorial: Introducing Expressions](../tutorial-introducing-expressions.md)
-   [Report Samples (Report Builder and SSRS)](https://go.microsoft.com/fwlink/?LinkId=198283)  
  
