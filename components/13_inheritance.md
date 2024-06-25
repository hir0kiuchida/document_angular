## Inheritance

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
