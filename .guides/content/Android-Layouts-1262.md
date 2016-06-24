Enter the following command in the calabash-android console:
```
query("*")
```
There are a lot of visible views that you're familiar with: TextViews, Buttons, CheckBoxes and so on. You may also notice that there are some items that don't show up on the screen with strange class names like LinearLayout and RelativeLayout

Theses views are **containers**: they hold other views inside them. They are usually invisible and they help position the view that are inside them. Because of this they are often called layouts. Although these view are invisible they can have ids so they can be identified. On the screenshot below you can see all the layout views and their ids:
![](.guides/img/RoboBook.png)
The Linerlayout (id: email_container) contains a TextView ("Email address") and an EditText. These two views are called the **children** of the LinerLayout.

Similarly, the children of the other LinerLayout (id: robot_question_container) are a TextView ("Are you a robot?") and a CheckBox.

There is also a RelativeLayout which contains both LinerLayout and consequently all 4 views.
![](.guides/img/Relationship_Hierarchy.png)
Every view that contains other views is a class of ViewGroup. You get all of the ViewGroups on the screen by running this command:
```
query("android.view.ViewGroup")
```
<h2>Query Chaining</h2>
What if I want to get all the views inside email_container? Calabash allows you to do that with the following command:
```
query("LinearLayout id:'email_container' *")
```
The query has 2 parts:
1) LinearLayout id:'email_container'
The first part means find the LinearLayout with the specified id email_container
2) " * "
The second part means find all the elements inside the previously found LinerLayout.

**Chaining queries** means that you run multiple queries after each other. Each query runs on the results of the previous query, refining the results further. So if the first query filters down the result to 4 views the next part will only run on those 4 views.

Another 2 queries chained together:
```
query("RelativeLayout LinearLayout")
```
1) ReleativeLayout 
The first one gives us all the RelativeLayouts (only one is present on the screen)
2) LinearLayout 
The second finds all the LinearLayouts inside that ReleativeLayout. The result is both the email_container and the robot_questions_container layouts.

This example is a little more complex because it's chaining more queries but it follows the same logic:
```
query("LinearLayout id:'main_layout' RelativeLayout enabled:true LinearLayout id:'email_container' TextView")
```
1) LinearLayout id:'main_layout 
The first query gets the LinearLayout with the id "main_layout'( -> one result)
2) RelativeLayout enabled:true 
The second query finds all the enabled RelativeLayouts inside the 'main_layout'( -> one result)
3) LinearLayout id:'email_container' 
The third query looks inside the RelativeLayout and finds the LinearLayout with id 'email_container' ( -> one result)
4) TextView 
The fourth query looks inside the 'email_container' and finds all the TextViews ( -> only one TextView is inside the 'email_container')

Another Example:
```
query("RelativeLayout TextView")
```
The logic is similar: 
1) The first query gets the RelativeLayout 
2) The second finds all the TextViews inside it. 

Although the RelativeLayout doesn't have any direct TextViews as children, the result contains both the 'email_label' and the 'robot_question_label' views. This is because chaining by default looks at the **descendants**: not just the direct children but the children of those children.