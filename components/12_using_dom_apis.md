## Using DOM APIs

```ts
@Component({...})
export class ProfilePhoto {
  constructor(elementRef: ElementRef) {
    afterRender(() => {
      // Focus the first input element in this component.
      elementRef.nativeElement.querySelector('input')?.focus();
    });
  }
}
```
> [!IMPORTANT]
> `afterRender` and `afterNextRender` must be called in an injection context, typically a component's constructor.
> **Avoid direct DOM manipulation whenever possible.**
> **Render callbacks never run during server-side rendering or build-time pre-rendering.**
> **Never directly manipulate the DOM inside of other Angular lifecycle hooks.**

### When to use DOM APIs
- Managing element focus
- Measuring element geometry, such as with `getBoundingClientRect`
- Reading an element's text content
- Setting up native observers such as `MutationObserver`, `ResizeObserver`, or `IntersectionObserver`.

> [!CAUTION]
> never directly set an element's `innerHTML` property
