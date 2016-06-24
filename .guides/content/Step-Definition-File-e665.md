The first distinct part of a Calabash test is the feature file, and the second distinct part is the **step definition** file. 

Step definitions are like code-behind for the scenarios defined in Gherkin. They provide the glue that makes them runnable in the application. Their sole function is to translate the Gherkin into runnable actions.

The image below shows a feature file with scenarios:
![](.guides/img/ScenarioExample.png)

The following image shows the step definitions that are required to run the tests for credit card validation in the second scenario listed above:
![](.guides/img/ScenarioStepExample.png)

The step definitions make use of the methods in the Calabash API such as touch and query. These methods take queries that tell Calabash how to locate views on the screen. 



