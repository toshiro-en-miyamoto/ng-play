# The Main ARtificats of an Angular App

This chapter covers:

- Understanding components, directives, services, modules, and pipes
- Looking at Angular data bindings

## Services ($2.2)

For cleaner code separation, we usually don't use a component for code that fetches or manipulates data. An injectable service is the right place for handling data. A component may depend on one or more services.

## Modules ($2.5)

An Angular module is a container for a group of related components, services, directives, and pipes. You can think of a module as a package that implements certain functionality from the business domain of your application, such as a shipping or billing module.

All elements of a small application can be located in one module (the **root module**), whereas large apps may have more than one module (**feature modules**). All apps must have at least a root module that's bootstrapped during app launch.

## Data Binding ($2.6)

Four types of data binding:
- unidirectional data binding (from NgComponent to DOM)
- unidirectional property binding (from NgComponent to DOM)
- unidirectional event binding (from DOM to NgComponent)
- two-way (between NgComponent and DOM)

### Unidirectional data binding (from NgComponent to DOM)

With **double curly braces**, a value of a class variable (HelloComponent.name) is **interpolated** in a text node.

```javascript
@Component({
  template: `<p>Hello {{name}}</p>`,
  ....
})
export class HelloComponent ... {
  name: string;
}
```

### Unidirectional property binding (from NgComponent to DOM)

With **square brackets**, the value of a class variable (HelloComponent.isValid) is **bound to a property** of an HTML element.

```javascript
@Component({
  template: `<span [hidden]="isValid">This field is required</span>`,
  ....
})
export class HelloComponent ... {
  isValid: boolean;
}
```

### Unidirectional event binding (from DOM to NgComponent)

With **parentheses**, an event of an HTML element is **bound to an event handler** of an NgComponent. When the event specified in parentheses is triggered, the expression in double quotes is reevaluated. In the following listing, the expression is a function, so it is invoked each time the corresponding event is triggered.

```javascript
@Component({
  template: `<button (click)="onClick()">Get Products</button>`,
  ....
})
export class HelloComponent ... {
  function onClick() : void { ... }
}
```

### Two-way binding (between NgComponent and DOM)

Remember, **square brackets** represent property binding, and **parentheses** represent event binding. To denote two-way binding, surround a template element’s **ngModel** with both square brackets and parentheses. In the following code, you instruct Angular to update the name variable as soon as the value in the input field changes, and update the value of the input field as soon when the value of the name variable changes. This is what the two-way binding means.

```javascript
@Component({
  template: `
    <input type='text'  [(ngModel)]="name">
    <button (click)="clearName()'">Clear</button>
    `,
  ....
})
export class AppComponent {
  name: string;
  function clearName(): void { name = ''; }
}
```
