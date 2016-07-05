<h2>Start the Console</h2>
To open the console enter the following on the command line: 
```
calabash-android console <path to apk>
```
You will need to restart the application using the "test server" that is created at the time the console was launched. This command is necessary each time you want to query the elements within the application. To start the test server, enter the following on the command line:
```
start_test_server_in_background
```

When querying a screen that is in the interior of the application, you must first run the start_test_server_in_background command and then navigate to the screen that you want to query.

<h2>Query Basics</h2>
On Android, every application is built of components called views. Buttons, labels, and check boxes are all just views on the screen.

The **Query** command allows you to find views on the current screen. 
To get a list of all elements on the screen, open the command line and type:
```
query("*")
```
and all element details will be displayed. The "*" is known as a wildcard search.

Opening the command line and typing:
```
query("Button")
```
will find all views that contains the word "Button" in the various elements: id, class, text. The returned results will be displayed like this:
![](.guides/img/FilterClassName.png)
It found one view (the next button) and it returned some data about the button inside the curly braces. The result is a set of key, value pairs which in Ruby is called a **hash**. The button's **text** property is 'Next' (this is the visible text on the button), and its **id** is 'next_button'.