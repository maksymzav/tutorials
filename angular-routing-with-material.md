This tutorial will help you to create a basic Angular app, that will use Angular Router to navigate between pages.
We will also use Angular Material to add side navigation for the application.

### Prerequisites

Before working with this tutorial you should work on the [Using Angular routes in a single-page application](https://angular.dev/guide/routing/router-tutorial) tutorial.
The tutorial assumes you generate application without routing preinstalled. You will configure the routing by yourself.
But the tutorial has an error, when generating a new application instead of 
`ng new angular-router-sample` you should use `ng new angular-routing-sample --routing false` command.

### Create a new Angular app

Create a new Angular app using the Angular CLI.
In the tutorial above you configured the routing manually after the app has been created.
We will use the Angular CLI to add routing to our app. So when running the `ng new` command, you don't need to add the `--routing false` flag.
This way Angular will do several things for you:

1. create an app.routes.ts file
2. will add `provideRouter(routes)` to the app.config.ts file
3. will generate a <router-outlet> tag in the app.component.html file

### Locate things above Angular generated to support routing

find the app.routes.ts file, inspect the app.config.ts file to find the `provideRouter(routes)` function and find the <router-outlet> tag in the app.component.html file.

### Clean up the app.component.ts file

By default, the app.component.ts file contains a lot of code that we don't need. So let's clean it up.
1. Remove everything from the app.component.html file and leave only the following:

```angular2html
<router-outlet></router-outlet>
```

2. Remove the `title` property from the app.component.ts file.

**Commit the changes. Create a repo for this tutorial and push the changes to the repo.**

### Add @angular/material to the project

1. Install @angular/material using npm:

There is no good tutorial to install the Angular Material using Angular 17. So I'll go with you step by step.

```bash
ng add @angular/material
```

The ng add command will install Angular Material, and ask you the following questions to determine which features to include:

1. Choose a prebuilt theme name, or "custom" for a custom theme.
Choose one of prebuilt themes from the list.
2. Set up global Angular Material typography styles.
Choose N.
3. Include the Angular animations module?
Choose Include and enable animations.

The Angular Material should now be installed.

**Coommit your application with the Angular Material installed.**

### Add a side navigation to the application

Update the app.component.html file to contain side navigation:

```angular2html
<mat-sidenav-container >
    <mat-sidenav opened mode="side" [fixedInViewport]="true">
        <mat-nav-list>
            <a mat-list-item>Page 1</a>
            <a mat-list-item>Page 2</a>
        </mat-nav-list>
    </mat-sidenav>

    <mat-sidenav-content>
        <router-outlet></router-outlet>
    </mat-sidenav-content>
</mat-sidenav-container>

```

Update your app.component.ts with the following imports:
```typescript
MatSidenavModule,
MatListModule
```

At this moment you should have a side navigation with two links in it.
Note, the links are not working yet.

**Commit your changes.**

### Generate Page 1 and Page 2 components

1. Generate components for Page 1 and Page 2 views.
2. Add any content to the Page 1 and Page 2 components.

### Configure the routes

1. Update the app.routes.ts file so when you:
- navigate to /page-1 the Page 1 component is displayed
- navigate to /page-2 the Page 2 component is displayed

2. Update the app.component.html file so when you click on the Page 1 link the Page 1 component is displayed and when you click on the Page 2 link the Page 2 component is displayed.

**Commit your changes.**
