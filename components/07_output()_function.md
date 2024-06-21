## Function-based-outputs

```ts
import {Component, output} from '@angular/core';
@Component({...})
export class MyComp {
  onNameChange = output<string>()    // OutputEmitterRef<string>
  setNewName(newName: string) {
    this.onNameChange.emit(newName);
  }
}
```

### Subscribing
Consumers may create your component dynamically with a reference to a ComponentRef.  
In those cases, parents can subscribe to outputs by directly accessing the property of type OutputRef.
```ts
const myComp = viewContainerRef.createComponent(...);
myComp.instance.onNameChange.subscribe(newName => {
  console.log(newName);
});
```

> [!CAUTION]
> わからん

### Using RsJS observables as source
The outputFromObservable function is a compiler primitive, similar to the output() function,　 
and declares outputs that are driven by RxJS observables.
```ts
import {Directive} from '@angular/core';
import {outputFromObservable} from '@angular/core/rxjs-interop';
@Directive(...)
class MyDir {
  nameChange$ = this.dataService.get(); // Observable<Data>
  nameChange = outputFromObservable(this.nameChange$);
}
```

### Converting an output to an observable
```ts
import {outputToObservable} from '@angular/core/rxjs-interop';
@Component(...)
class MyComp {
  onNameChange = output<string>();
}
// Instance reference to `MyComp`.
const myComp: MyComp;
outputToObservable(this.myComp.instance.onNameChange) // Observable<string>
  .pipe(...)
  .subscribe(...);
```
