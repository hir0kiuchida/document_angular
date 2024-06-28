## Built-in control flow

### Referencing the conditional expression's result
```html
@if (users$ | async; as users) {
  {{ users.length }}
}
```

### `@for` block
#### track
Inside `@for` contents, several implicit variables are always available:

| Variable | Meaning |
---- | ----
| $count | Number of items in a collection iterated over |
| $index | Index of the current row |
| $first | Whether the current row is the first row |
| $last | Whether the current row is the last row |
| $even | Whether the current row index is even |
| $odd | Whether the current row index is odd |

### `@empty` block
You can optionally include an `@empty` section immediately after the `@for` block content.  
The content of the `@empty` block displays when there are no items:

```html
@for (item of items; track item.name) {
  <li> {{ item.name }}</li>
} @empty {
  <li> There are no items.</li>
}
```
