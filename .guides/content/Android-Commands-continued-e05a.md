<h2>Filtering by Class</h2>
The goal is usually to find a *single element* to check it or to interact with it. The search starts will all the elements on the screen then gradually filtering down by different criteria until only one remains. The first criteria is filtering by class.

**Simple Class Name**
Filtering by class means that we only want to look at certain types of views. This is what we've done before when we were searching for Buttons or TextViews:
```
irb(main):002:0> query("Button")
```
Will return:
![](.guides/img/FilterClassName.png)
This is called filtering by simple name. The result shows you that the full class name is **android.widget.Button**: this is what we call *fully qualified class name* and the **android.widget** part is called *package name*.
When you query with simple name Calabash only looks at the last bit of the name. This is also case insensitive, so Button, button or bUtTOn is the same in this context.

**Fully Qualified Class Name**
You can also use the fully qualified class name in the query:
```
irb(main):003:0> query("android.widget.Button")
```
This will pick out all views in the input which have class android.widget.Button or which inherit from android.widget.Button.

<h2>Filtering by Property</h2>
Usually there are several buttons, textviews and edit texts on the screen so filtering by class is not enough to identify a single element. In the query results you get back a set of properties for each view like id, text, class.

Calabash allows you to filter on these properties. The most used property is the id. On Android every view can have an id, which is an invisible string identifier. The id is not necessarily unique and also not every view has one. Even with these restrictions using id is the most reliable way to find views.

**id property**
![](.guides/img/FilterIdProp.png)
Let's try to find the Next button by id:
```
query("* id:'next_button'")
```
The first part of the query is the class filtering * means give me all the views. The second part is the property filtering id: 'next_button' means find the view that has the id next_button
The filtering happens on the result of the first part of the query string. Previously we used "*" so the filtering was applied to all of the views. But we could have used a different class. Let's see what happens if we use TextView:
```
query("TextView id:'next_button'")
```
The result is empty. In the first part we filter for TextViews and then we try to find the id amongst these TextViews. Because the next button is not a TextView the result will be empty.