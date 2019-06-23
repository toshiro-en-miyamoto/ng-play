## Key Router Terms

Ref : https://angular.io/guide/router

The application has a configured router (1).
The shell component has a `RouterOutlet` where it can
display views produced by the router (2).
It has `RouterLink`s that users can click
to navigate via the router (3).

(1)
```typescript
// app.module.ts
import { RouterModule, Routes } from '@angular/router';
const routes: Routes = [                                        1
  { path: 'crisis-center', component: CrisisListComponent   },
  { path: 'hero/:id',      component: HeroDetailComponent   },
  { path: '',              component: HeroListComponent     },
  { path: '**',            component: PageNotFoundComponent }
];
@NgModule({
  imports: [
    RouterModule.forRoot(routes)                                1
  ]
})
export class AppModule {}
```

(2)
```html
<!-- app.component.html -->
<h1>Angular Router</h1>
<nav>
  <a routerLink="/crisis-center">Crisis Center</a>              2
  <a routerLink="/heros">Heros</a>                              2
</nav>
<router-outlet></router-outlet>                                 3
```

## Summary

<dl>
<dt>Router
<dd>Displays the application component for the active URL.
    Manages navigation from one component to the next.
<dt>RouterModule
<dd>A seperate NgModule that provides the necessary service providers
    and directives for navigating through application view.
<dt>Routes
<dd>Defines an array of <code>Route</code>s,
    each mapping a URL path to a component.
<dt>Route
<dd>Defines how the router should navigate to a component based on a
    URL pattern. Most routes consist of a path and a component type.
<dt>RouterOutlet
<dd>The directive (<code>&lt;router-outlet&gt;</code>) that marks
    where the router displays a view.
<dt>RouterLink
<dd>The directive for binding a clickable HTML element to a route.
    Clicking an element with a <code>routerLink</code> directive
    that is bound to a <i>string</i> or a <i>link parameters array</i>
    triggers a navigation.
<dt>RouterLinkActive
<dd>The directive for adding/removing classes from an HTML element
    when an associated <code>routerLink</code> contained on or inside
    the element becomes active/inactive.
<dt>ActivatedRoute
<dd>A service that is provided to each route component that contains
    route specific information such as route parameters, static data,
    resolve data, global query params, and the global fragment.
<dt>RouteState
<dd>The current state of the router including a tree of the currently
    activated routes together with convenience methods for traversing
    the route tree.
<dt>Link parameter arrays
<dd>An array that the router interprets as a routing instruction.
    You can bind that array to a <code>routerLink</code> or pass the
    array as an argument to the <code>Router.navigate</code> method.
<dt>Routing component
<dd>An Angular component with a <code>RouterOutlet</code> that
    displays views based on router navigations.
</dl>
