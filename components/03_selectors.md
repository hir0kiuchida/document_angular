## Components Selector
**Angular matches selectors statically at compile-time.**  
Changing the DOM at run-time, either via Angular bindings or with DOM APIs, does not affect the components rendered.

### The :not pseudo-class
You can append this pseudo-class to any other selector to narrow which elements a component's selector matches.  
For example, you could define a [dropzone] attribute selector and prevent matching textarea elements:
```ts
@Component({
  selector: '[dropzone]:not(textarea)',
  ...
})
export class DropZone { }  
```

Angular does not support any other pseudo-classes or pseudo-elements in component selectors.

### Combining selectors
You can combine multiple selectors by concatenating them.  
For example, you can match `<button>` elements that specify `type="reset"`
```ts
@Component({
  selector: 'button[type="reset"]',
  ...
})
export class ResetButton { }
```

You can also define multiple selectors with a comma
```ts
@Component({
  selector: 'drop-zone, [dropzone]',
  ...
})
export class DropZone { }
```

### Selector prefixes
**The Angular team recommends using a short, consistent prefix for all the custom components defined inside your project.**  
For example, if you were to build YouTube with Angular, you might prefix your components with `yt-`, with components like `yt-menu`, `yt-player`, etc. 
Namespacing your selectors like this makes it immediately clear where a particular component comes from. 
By default, the Angular CLI uses `app-`.

### When to use an attribute selector
You should consider an attribute selector when you want to create a component on a standard native element.  
For example, if you want to create a custom button component, you can take advantage 
of the standard `<button>` element by using an attribute selector
```ts
@Component({
  selector: 'button[yt-upload]',
   ...
})
export class YouTubeUploadButton { }
```


Components that define attribute selectors should use lowercase, dash-case attributes.  
You can follow the same prefixing recommendation described above.

