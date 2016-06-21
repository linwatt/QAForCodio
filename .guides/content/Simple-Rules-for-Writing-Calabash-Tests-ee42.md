1) Stability - Your first priority has to be stability. Try to make your tests as stable and as resilient as possible. Brittle tests will kill the automation effort. If the tests are brittle, you will find that most of your time will be spent updating or fixing the automated test rather than actual testing. If the tests are constantly failing, the failures won't be taken seriously, your frustration will increase and you will likely abandon the automated tests effort.

2) Sleeping is bad - Never, Never, Never use the sleep statement! Hoping that you guessed the right number of seconds to sleep in order for the expected element to appear is a disaster waiting to happen. Randomly these tests will fail, usually when you least expect it! Adding extra time is not the answer and ultimately will affect the Stability of the automated suite. So if Sleep statements are bad, what is good?

3) Wait is good - Most failures happen because the element that you want to interact with or assert has not appeared on the screen. Mobile applications with a lot of networking or animations will fall victim to not being able to find/interact with the desired element. Here are two rules to follow for wait statements:
   - wait **before** you interact with any element
    - wait **after** every action to finish
    
4) id is better than text - For stability sake use id rather than text to identify elements on the screen. If the id doesn't exist let the developers know how important it is to be able to interact with the various elements by their id.

5) Page Object Model - Sometimes referred to as the Screen Object Model. This concept is not just for Cross platform applications, but in general it is a good practice to get into the habit of doing. It allows for the reuse of code which is why it is popular when the application being developed crosses platforms. It also beneficial in organizing the automated test code base, because when the UI changes for the application you only have one place to change your code.

6) Be pragmatic - Verify only the important things at the beginning! Don't verify every possible element on the screen when you are writing your tests from scratch. More verification can be added later when the application stabilize and mature. When in doubt start with the Happy Path first!

**There should be one feature file per screen**