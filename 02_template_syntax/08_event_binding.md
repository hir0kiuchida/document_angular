## Event binding

### Binding to keyboard events
The following example shows how to bind a keyboard event to `keydown.shift.t`.
```html
<input (keydown.shift.t)="onKeydown($event)" />
```

If you bind to `keydown.shift.alt.t`, on macOS, that combination produces a `ˇ` character  
instead of a `t`, which doesn't match the binding and won't trigger your event handler.  
To bind to `keydown.shift.alt.t` on macOS, use the code keyboard event field 
to get the correct behavior, such as `keydown.code.shiftleft.altleft.keyt` shown in this example.
```html
<input (keydown.code.shiftleft.altleft.keyt)="onKeydown($event)" />
````
