### Node.JS Commands

Verifica installazione:
```javascript
node -e "console.log('Hello World');"
```

Verifica versione
```javascript
node -v
```

Creazione prima app
```javascript
ex.1: ng new my-first-app --prefix mac
ex.2: ng new mastering-angular-components --prefix=mac
```


Run dell'applicazione
```javascript
cd my-first-app
ng serve
```
You can now launch your favourite browser and open up the address http://localhost:4200, where you should see the message welcome to mac.


### Angular View Encapsulation
Angular has three ways to handle view encapsulation and each way has its own pros and cons. Let's look at the different settings:

- ViewEncapsulation.Emulated
> it will emulate style encapsulation by attaching the generated attributes to the component element and modifying CSS selectors to include these attribute selectors

- ViewEncapsulation.Native
> It makes use of Shadow DOM, to create an isolated DOM for the whole component. This mode depends on the browser to support Shadow DOM natively, and therefore, can't always be used. It's also important to note that global styles will no longer be respected and local styles need to be placed within the component in inline style tags (or use the styles property on the component annotation).

- ViewEncapsulation.None
> This mode tells Angular not to provide any template or style encapsulation. Within our application, we rely on styles coming from a global CSS; therefore, we use this mode for most of the components. Neither Shadow DOM, nor attributes will be used to create style encapsulation; we can simply use the classes specified within our global CSS file.


### src/main.ts

This is the main entry file of our TypeScript project code. It contains all the necessary code to start Angular and bootstrap our main application module.

### Bootstrapping
The starting point of our project is located within the src/main.ts file. This file is responsible for bootstrapping the Angular framework and starting our applications main module.
In order to bootstrap an Angular module, we first need to create a platform. There are many ways for different platforms and environments to create a platform. If you'd like to create a browser platform, which is the default platform for browser environments, we need to import the platform factory function platformBrowserDynamic from the @angular/platform-browser-dynamic module. Simply by calling the platform factory function, we will receive an instance of the newly created platform. On the platform instance, we can then call the bootstrapModule function, passing our main application module as a parameter:

```
import {platformBrowserDynamic} from '@angular/platform-browser-dynamic';
import {AppModule} from './app/app.module';

platformBrowserDynamic().bootstrapModule(AppModule)
  .catch(err => console.log(err));
```

### Generate Component Options
> Using the --spec false option while generating our component, we can skip creating test specifications.

>Using the -ve none parameter, we can tell Angular to create the component using ViewEncapsulation.None as a default encapsulation setting.

Example
````
ng generate component --spec false -ve none tasks/task-list
````

### @Input()

If we're using property binding on a regular DOM property, Angular will create a binding of the expression directly to the element's DOM property. We're using such a type of binding to bind the task completed flag to the checked property of the checkbox's input element.

### Local View Reference
This template consists of an input field as well as a button to enter a new task. If you take a closer look at the input field, you can see that we've added a special attribute called #titleInput. This is called a local view reference and we can use this reference within the current component view, or query for the element within our component code.

### @Output
Using the @Output decorator to create an event emitter. The output properties need to be instance properties that hold an event emitter within the component. On the component's host element, we can then use event bindings to capture any events emitted. This gives us a great flexibility that we can use to create a clean application design, where we glue components together through the binding within the view.
