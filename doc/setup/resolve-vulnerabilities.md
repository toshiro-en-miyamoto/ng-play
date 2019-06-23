# Resolve Vulnerabilities

When you create a new application (`ng new my-app` or `ng g app my-app`),
it is not uncommon that the newly installed dependencies have vulunerabilities.
Resolve it by `ng update` and `npm audt`.

## Update Angular Packages

```
$ cd my-app
$ ng update
    We analyzed your package.json, there are some packages to update:
     Name                               Version                  Command to update
     --------------------------------------------------------------------------------
      @angular/cli                       7.1.4 -> 8.0.2           ng update @angular/cli
      @angular/core                      7.1.4 -> 8.0.0           ng update @angular/core
      rxjs                               6.3.3 -> 6.5.2           ng update rxjs

$ ng update @angular/cli
$ ng update
    We analyzed your package.json, there are some packages to update:
      Name                               Version                  Command to update
     --------------------------------------------------------------------------------
      @angular/core                      7.1.4 -> 8.0.0           ng update @angular/core
      rxjs                               6.3.3 -> 6.5.2           ng update rxjs

$ ng update @angular/core --allow-dirty
$ ng update
    We analyzed your package.json and everything seems to be in order. Good work!
$
```

## Audit NPM Packages

```
$ npm audit
                       === npm audit security report ===
# Run  npm install --save-dev karma@4.1.0  to resolve 1 vulnerability

found 1 low severity vulnerability in 18834 scanned packages
  1 vulnerability requires semver-major dependency updates.
$
$ npm install --save-dev karma@4.1.0
$ npm audit
                                                                                
                       === npm audit security report ===                        
                                                                                
found 0 vulnerabilities
 in 19011 scanned packages
$
```
