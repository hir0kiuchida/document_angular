## Styling components

### Style scoping
Every component has a **view encapsulation** setting that determines how the framework scopes a component's styles.  
There are three view encapsulation modes: `Emulated`, `ShadowDom`, and `None`. 
You can specify the mode in the @Component decorator:
```ts
@Component({
  ...,
  encapsulation: ViewEncapsulation.None,
})
export class ProfilePhoto { }
```

By default, Angular uses emulated encapsulation.
