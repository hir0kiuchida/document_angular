## Standalone Components
A standalone component is a component that sets `standalone true` in its component metadata.  
Standalone components directly import other components, directives, and pipes used in their templates:
```ts
@Component({
  standalone: true,
  selector: 'profile-photo',
})
export class ProfilePhoto { }

@Component({
  standalone: true,
  imports: [ProfilePhoto],
  template: `<profile-photo />`
})
export class UserProfile { }
```
