## Inheritance

### Extending other components and directives
```ts
@Component({
  selector: 'base-listbox',
  host: {'(keydown)': 'handleKey($event)'},
})
export class ListboxBase {
  @Input() value: string;
  handleKey(event: KeyboardEvent) { }
}
```

```ts
@Component({
  selector: 'custom-listbox',
  host: {'(click)': 'focusActiveOption()'},
})
export class CustomListbox extends ListboxBase {
  @Input() disabled = false;
  focusActiveOption() { }
}
```
`CustomListbox` inherits all the information associated with `ListboxBase`, overriding the selector and template with its own values. 
`CustomListbox` has two inputs (`value` and `disabled`) and two event listeners (`keydown` and `click`).

### Forwarding injected dependencies
```ts
@Component({ ... })
export class ListboxBase {
  constructor(private element: ElementRef) { }
}

@Component({ ... })
export class CustomListbox extends ListboxBase {
  constructor(element: ElementRef) {
    super(element);
  }
}
```

### overriding lifecycle methods
```ts
@Component({ ... })
export class ListboxBase {
  protected isInitialized = false;
  ngOnInit() {
    this.isInitialized = true;
  }
}
@Component({ ... })
export class CustomListbox extends ListboxBase {
  override ngOnInit() {
    super.ngOnInit();
    /* ... */
  }
}
```
