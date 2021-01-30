Targeting Angular 7

Following https://v7.angular.io/guide/quickstart#prerequisites with a little help from https://stackoverflow.com/questions/43344600/installing-a-specific-version-of-angular-with-angular-cli.

`> npm uninstall -g @angular/cli`
`> npm cache clean`
`> npm i -g npm`
`> npm cache verify`
`> npm install -g @angular/cli@7`
`> ng new seven`
(yes to angular routing, selected SASS)

ng serve works just fine, though there are some warnings about vulnerabilities. 

Starting with the above and then initing the repo via GitKraken hit an error where it was treating the seven directory as a file. Creating the repo on github and then repeating the ng new worked just fine.

Making changes while ng serve is running doesn't seem to auto update. Ghost in the machine, needed to restart a few times.

Working to convert seven into the tour of heroes via the tutorial. 

1. The Hero Editor

`>ng generate component heroes`

I actually made a typo here and needed to delete the component. There seems to be no cli command to destroy a component, so what I did was delete the folder under src/app and then modify app.modules.ts to remove references to the destroyed component (two places but highlighted due to missing directory).

2. Displaying a List

`*ngFor` is known as the *repeater directive*.

`(click)="~~~"` is an example of [event binding](https://v7.angular.io/guide/template-syntax#event-binding) syntax.

As part of adding the new 'selectedHero' display, when I put it above the list it breaks spectacularly. The tutorial intends for this to be placed below in which case it fails the expected way. Some sort of top-to-bottom cascade must be going on.

`[class.selected]="hero === selectedHero"` is known as [class binding](https://v7.angular.io/guide/template-syntax#class-binding).

3. Master/Detail Components

`>ng generate component hero-detail`

(@Input decorator)[https://v7.angular.io/guide/template-syntax#inputs-outputs]

`[hero]="selectedHero"` is an Angular [property binding](https://v7.angular.io/guide/template-syntax#property-binding).