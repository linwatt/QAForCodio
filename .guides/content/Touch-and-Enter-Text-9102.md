As usual, anything you can query, you can touch (but the element must be visible to be found).

```
touch("EditText id:'email_edittext'")
```

<h2>Enter Text</h2>
iOS and Android handle entering text differently.

**iOS**
On iOS the method takes a single parameter: the text that will be input into the view. It is assumed that the view **already has focus and is visible on the screen**:
```
tap_mark 'editable_view'
keyboard_enter_text "Words to enter"
```

**Android**
On Android the method takes 2 parameters: 
1) A Calabash query to locate the view
2) A string with the text to enter
```
enter_text("id:'editable_field'", "Words to enter")
```

