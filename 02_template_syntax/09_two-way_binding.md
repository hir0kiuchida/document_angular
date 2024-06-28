## Two-way binding

For two-way data binding to work, the `@Output()` property must use the pattern, inputChange,  
where `input` is the name of the `@Input()` property. For example, if the `@Input()` property is 
`size`, the `@Output()` property must be `sizeChange`.
