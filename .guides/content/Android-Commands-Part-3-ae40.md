**Text Property**
Of course id is not the only property that you can filter on. Another commonly used one is the **text** property. This is the label of the view which is visible on the screen.
```
query("* text:'Next'")
```
This will find the view on the screen which has a text Next. The result is exactly the same as before - the next button.

It is easy to use the text attribute when exploring the UI, since you see the text on the screen. One the desired element is located, id is used in the to produce more stable tests. Labels tend to change more frequently than ids. It also eliminates all the translations and localization problems.

What if a view doesn't have an id? 
Ask for one to be added!

**Other Properties**
So far the items that have searched were string properties. Let's try now something different: the **enabled** property. If this is true the view is enabled, otherwise the view is disabled. In our examples the next button is disabled until you type something in the email field. Let's try to find all of the disabled buttons.
```
query("* enabled:false")
```
Notice that while we used single quotes for sting parameters we're not using anything here for false. 
![](.guides/img/FilterEnabled.png)
**Integer parameters**
Another type of parameter is the integer parameter (numbers). One example is the width parameter:
```
query("* width:656")
```
This gives you all the views that are exactly 656 pixel wide. Notice that we are not using the single quotes to define the value.
**Combining Filters**
You can also combine the filters using multiple criteria. Let's get all the view which are enabled and they are 96 pixel high.
```
query(enabled:true height:96")
```
**Returning Specific Properties**
Sometimes you are only interested in certain properties not the full result. Let's say you want to get all of id's on the screen:
```
query("*", :id)
```
![](.guides/img/FilterIdsOnly.png)
As you can see a result is an array of strings where only the ids are shown. You can put any property as the second argument of query to get the data you're interested in. Another example to get all the labels for the enabled views:
```
query("* enabled:true", :text)
```
<h2>General Syntax for Filtering</h2>
The general syntax for property filtering is the following:
```
prop:value
```
The prop is the name of the property and the value is either a string, a boolean or an integer value.
We've already used a couple of the properties like id, text, enabled and width. There are a lot more.. For Starters you can use all the attributes that you see in the query results. But that's not everything.

Every view object supports a set of methods - you can find all the supported methods on the view's documentation. 

For example, the View Class has an isEnabled() method. When Calabash tries to resolve the property it finds the following methods on the view prop(), getPrope(), and isProp() in this order.

So for the enabled property it tries to find the enabled(), getEnabled(), or isEnabled() methods.

If Calabash does find a method it calls it and compares the return value with the value you specified. If it doesn't match it gets rid of that view. It also discards the view if it can't find the appropriate methods.

<h2>Other Useful Things</h2>
**Marked**
The marked keyword is a shorthand for identifying an element by it's name. It's a convenience method to filter by id, text or contentDescription properties.
```
query("button marked:'next_button'")
```
**Index**
he query language also supports the index keyword. The index is very similar to using the array indexing - it gives you the element at a given index:
```
query("* index:0")
```
This is usually used with lists and other collection views. Often you will just want to click on the first element on a list. Be warned though: you should only use index if you really need it. Using index to identify elements in the layout is usually not a good idea - it leads to brittle tests and hard to diagnose problems.

Use ids, text and other identifiers and don't rely on the ordering of the items!