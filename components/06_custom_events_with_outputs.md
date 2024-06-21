## Custom events with outputs

> [!NOTE]
> When **extending** a component class, outputs are inherited by the child class.

### Specify outputs in the @Component decorator
In addition to the `@Output` decorator, you can also specify a component's outputs  
with the `outputs` property in the `@Component` decorator. This can be useful  
when a component inherits a property from a base class

```ts
// `CustomSlider` inherits the `valueChanged` property from `BaseSlider`.
@Component({
  ...,
  outputs: ['valueChanged'],
})
export class CustomSlider extends BaseSlider {}
```
