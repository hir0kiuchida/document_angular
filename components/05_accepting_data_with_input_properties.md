
## Accepting data with input properties

> [!NOTE]
> When **extending** a component class, inputs are inherited by the child class.

### Required inputs

```ts
@Component({...})
export class CustomSlider {
  @Input({required: true}) value = 0;
}
```

### Input transforms

```ts
@Component({
  selector: 'custom-slider',
  ...
})
export class CustomSlider {
  @Input({transform: trimString}) label = '';

  trimString(value: string | undefined) {
    return value?.trim() ?? '';
  }
}
```
```ts
<custom-slider [label]="systemVolume" />
```

The most common use-case for input transforms is to accept a wider range of value types in templates,  
often including *null* and *undefined*.

> [!CAUTION]
> 以下意味がわからない

When you specify an input transform, the type of the transform function's parameter determines the types of values that can be set to the input in a template.

```ts
@Component({...})
export class CustomSlider {
  @Input({transform: appendPx}) widthPx: string = '';
}
function appendPx(value: number) {
  return `${value}px`;
}
```
In the example above, the `widthPx` input accepts a `number` while the property on the class is a `string`


> [!CAUTION]
> わからん

Angular includes two built-in transform functions for the two most common scenarios:
coercing values to boolean and numbers.

```ts
import {Component, Input, booleanAttribute, numberAttribute} from '@angular/core';
@Component({...})
export class CustomSlider {
  @Input({transform: booleanAttribute}) disabled = false;
  @Input({transform: numberAttribute}) number = 0;
}
```

### Inputs with getters and setters

> [!CAUTION]
> わからん

A property implemented with a getter and setter can be an input
```ts
export class CustomSlider {
  @Input()
  get value(): number {
    return this.internalValue;
  }
  set value(newValue: number) {
    this.internalValue = newValue;
  }
  private internalValue = 0;
}
```

**Prefer using input transforms instead of getters and setters if possible.**

### Specify inputs in the @Component decorator
This can be useful when a component inherits a property from a base class
```ts
// `CustomSlider` inherits the `disabled` property from `BaseSlider`.
@Component({
  ...,
  inputs: ['disabled'],
})
export class CustomSlider extends BaseSlider { }
```

---

## Coming Soon...
```ts
@Component(...)
export class MyComponent {
  // default: undefined
  optionalInput = input<number>();  

  // default: 5
  optionalInputWithDefaultValue = input<number>(5);           
  
  
  // parent must pass value trough input
  requiredInput = input.required<number>();    
  
  // ERROR - setting initial value to required input is not allowed
  requiredInputWithDefaultValue = input.required<number>(5);  
}
```
