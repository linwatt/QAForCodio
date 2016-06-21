<h2>Scenario Outlines</h2>
**Scenario Outlines** allow us to separate out the small tables of example data used in the Scenario from the description of steps in the Scenario and thereby run it with multiple sets of data. 
This is very useful for situations when yo have a single path through the application that you wish to run with different sets of example data. These different examples might test different subtle behaviors 
in the code. Scenario outlines reuse the same test code, but substituting different rows of example data for each test execution.

![](.guides/img/ScenarioOutline.png)

![](.guides/img/ScenarioOutlineElements.png)

<h2>Background Statements</h2>
Sometimes you have a setup that repeats for most of the scenarios in a feature. Duplication is an unavoidable circumstance when writing scenarios. A way of sharing setup among all of the scenarios in a feature is to use a **Background statement**. The Background statement is performed before each of the scenarios in a feature. This guarantees that each scenario has a fresh set of data to operate upon.

![](.guides/img/Backgroundstatement.png)
