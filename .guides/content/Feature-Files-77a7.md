In Cucumber and Calabash, acceptance tests are known as **features**. Features are text files with the *.feature* extension that are written in plain language understood by developers and business users alike. 
A feature is used to test one particular function of an application. Features are broken down into one or more **scenarios**. 
A scenario describes a test that describes when some functionality of an application has been properly implemented. It exists within the context of the feature. A scenario is in turn subdivided into **steps** – a list of sentences that describe the pre-conditions for the scenario, the actions a user would take, and the expected results of the user’s actions. Each step is matched to a **step definition** - a piece of Ruby code that executes when the test runs.

![](.guides/img/FeatureDiagram.png)

