# Stop Rewriting DAX: User-Defined Functions \& the DAX Lib Ecosystem

Presentation materials for a talk on DAX User-Defined Functions (UDFs) and the DAX Lib open-source ecosystem.

## What's In This Repo

|File|Description|
|-|-|
|`Stop Rewriting DAX User-Defined Functions \& the DAX Lib Ecosystem.pptx`|Slide deck — section dividers, code examples, comparison cards, resources|
|`DAXUDFDemoQueries.dax`|All demo DAX queries, validated and ready to paste into DAX Query View|

## About the Talk

DAX has been a functional language that ironically didn't let you define your own functions — until September 2025. User-Defined Functions bring parameterized, reusable logic to DAX for the first time, and DAX Lib (daxlib.org) provides an open-source repository of 30+ community-built function packages you can import into any model.

This session covers:

* **UDF fundamentals** — syntax, parameter types, naming conventions
* **VAL vs. EXPR** — the critical parameter-passing concept that will make or break your functions
* **DAX Lib ecosystem** — browsing, importing, and using community function libraries
* **Practical examples** — ranking functions, YoY refactoring, model-dependent wrappers

## Demo Setup

The demos use the **SQLBI Contoso Data Generator V2** sample dataset (10K version). Download it from the [Contoso Data Generator releases page](https://github.com/sql-bi/Contoso-Data-Generator-V2-Data/releases).

### Prerequisites

* Power BI Desktop (September 2025 or later)
* "User-Defined DAX Functions" preview feature enabled (File → Options → Preview features)
* Contoso 10K .pbix open with data loaded

### Demo Queries

The `DAX\_UDF\_Demo\_Queries.dax` file contains 7 self-contained demos, each with a `DEFINE FUNCTION` block and an `EVALUATE` statement. Paste them individually into DAX Query View.

|Demo|What It Shows|Key Takeaway|
|-|-|-|
|1 — First Function|`SumTwoNumbers` basic syntax|Function anatomy: name, params, `=>`, body|
|2 — Type Casting|`INT64` parameters with decimals|Params are cast individually before the function runs|
|3a/3b — ComputeForRed|VAL (broken) vs. EXPR (fixed)|VAL pre-evaluates; EXPR evaluates inside the function|
|4a/4b/4c — BestCustomers|Measure ref → raw SUMX → CALCULATE fix|Always wrap EXPR params in CALCULATE for context transition|
|5 — RankByMetric|Reusable ranking with TABLE + EXPR params|One function, swap the metric, get different rankings|
|6 — YoY Refactoring|Old duplicated measures vs. new function|Identical results, fraction of the code|
|7 — Model-Dependent Wrapper|Generic function → model-specific one-liner|`Local.` prefix pattern for model-specific functions|

### Pre-Built Measures

The Contoso model includes four pre-built "before" measures in the **YoY Metrics** display folder for the refactoring demo:

* `Revenue YoY %`
* `Cost YoY %`
* `Margin YoY %`
* `Quantity YoY %`

Demo 6 defines a `Local.YoYChange` function and compares its output against these measures side by side — the old and new columns match exactly.

## Resources

|Resource|Link|
|-|-|
|DAX Lib|[daxlib.org](https://daxlib.org)|
|DAX Lib Documentation|[docs.daxlib.org](https://docs.daxlib.org)|
|DAX Lib GitHub|[github.com/daxlib](https://github.com/daxlib)|
|SQLBI: Introducing UDFs in DAX|[sqlbi.com/articles/introducing-user-defined-functions-in-dax](https://www.sqlbi.com/articles/introducing-user-defined-functions-in-dax/)|
|SQLBI: Model-dependent vs. independent UDFs|[sqlbi.com/articles/model-dependent-and-model-independent-user-defined-functions-in-dax](https://www.sqlbi.com/articles/model-dependent-and-model-independent-user-defined-functions-in-dax/)|
|SQLBI: Introducing DAX Lib (video)|[sqlbi.com/tv/introducing-dax-lib](https://www.sqlbi.com/tv/introducing-dax-lib/)|
|Contoso Data Generator V2|[github.com/sql-bi/Contoso-Data-Generator-V2-Data](https://github.com/sql-bi/Contoso-Data-Generator-V2-Data/releases)|
|Tabular Editor: DAX Package Manager|[docs.tabulareditor.com/te3/tutorials/udfs.html](https://docs.tabulareditor.com/te3/tutorials/udfs.html)|
|DaxLib.SVG Documentation|[evaluationcontext.github.io/daxlib.svg](https://evaluationcontext.github.io/daxlib.svg/)|

## License

Presentation materials are shared for community use. The Contoso dataset is provided by SQLBI under the MIT License.

