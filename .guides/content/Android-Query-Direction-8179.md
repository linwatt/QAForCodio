In the previous example all the queries were applied to the **descendants** of the previous query. However, this behavior can be modified with the **direction** element of Calabash.
The following directions are supported:
1) **Descendant**: all the descendants of an element (meaning all the children and the children's children, etc)
2) **Child**: only the direct children
3) **Parent**: all the ancestors (parents and their parents)
4) **Sibling**: all the elements which are on the same hierarchy level

<h2>Descendant vs Child</h2>
**Descendant** is the default direction, so if you don't specify anything the descendant direction applies. The following two lines mean the same thing:
```
query("RelativeLayout TextView")
query("RelativeLayout descendant TextView")
```
![](.guides/img/DescendantVChild.png)
The difference between descendant and **child** is the *depth*: the child looks *only* at the direct children where the descendant gets *all* the indirect children as well.
![](.guides/img/Descendantvchild2.png)
Let's try using child instead of descendant from the previous query:
```
query("RelativeLayout child Textview")
```
You get back an empty result because the RelativeLayout doesn't have any direct TextView children, only two LinearLayouts.

<h2>Sibling</h2>
**Sibling** means all the other children views which are inside the same container and are on the same level.
![](.guides/img/Sibling.png)
For example the sibling of the *email_label TextView* is the *email_edittext EditText* 
They are both direct children of email_container and they are on the same level.

This gives back all the siblings of email_label:
```
query("TextView id:'email_label' sibling *")
```

What's the result of the following query?
```
query("Button id:'login_button' sibling TextView")
```
We want to have all the TextView siblings of the login_button. 
The result is only the title view. The email_label and robot_question_label are TextViews but are much deeper on the hierarchy not on the same level as login_button.

<h2>Parent</h2>
The last direction is the **parent**. We've seen that the descendant and children moved down the hierarchy, the sibling moved on the same level and parent will move up.
![](.guides/img/Parent.png)
The parent of email_label 'TextView' is the email_container 'LinearLayout'. The parent of email_container is the login_form_container 'RelativeLayout'. The parent direction runs the query on all the parent views.

Example of a parent query with 2 parts:
```
query("LinearLayout id:'email_container' parent RelativeLayout")
```
1) LinearLayout id:'email_container' 
The first part finds the email_container 'LinearLayout'
2) parent RelativeLayout 
The second part searches all the parents of email_container and finds the RelativeLayouts.

To get a list of all the parents of the 
EditText id:'email_edittext' view, run the following query:
```
query("EditText id:'email_edittext' parent *")
```
You get a list of all the ancestors of email_edittext. Its direct parent (email_container) is the first result, the parent's parent (login_form_container) is the second result and so on.

If you want to get only the direct parent just select the first result:
```
query("EditText id:'email_edittext' parent * index:0")
```
This is one of the few places where using index is completely acceptable. Typically, using index can create brittle tests, as they will fail when elements get moved around. 

As a last example, what will be the result of the following query?
```
query("* id:'email_label' parent * index:1 child LinearLayout descendant TextView")
```
This is a complex query but it follows the same logic:
1) *id:'email_label' 
Finds the email_label TextView
2) parent * index:1
Finds all of its parents and gives the second ancestor (parent's parent) which is the login_form_container RelativeLayout
3) child LinearLayout 
All direct children of login_form_containers which are two LinearLayouts
4) descendant TextView 
Finally we have the two LinearLayouts and we are looking for all TextViews that are inside these (email_label and robot_question_label)
 


