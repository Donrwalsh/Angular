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

[@Input decorator](https://v7.angular.io/guide/template-syntax#inputs-outputs)

`[hero]="selectedHero"` is an Angular [property binding](https://v7.angular.io/guide/template-syntax#property-binding).

4. Services

"Components shouldn't fetch or save data directly and they certainly shouldn't knowingly present fake data. They should focus on presenting data and delegate data access to a service." <- This seems pretty critical.

`>ng generate service hero`

Oooh here comes [dependency injection](https://v7.angular.io/guide/dependency-injection).

A [provider](https://v7.angular.io/guide/providers) is something that can create or deliver a service.

Constructor gets a declaration of the service (dependency injection) but the call to retrieve the list of heroes belongs inside ngOnInit.

The way this is set up to retrieve mock heroes is helpful in tutorial-world, but a more realistic application will have to deal with the fact that the 'getHeroes()' method may not immediately deliver data. I named this method 'getHeroesSynchronous()' since midway through the tutorial we implement a fake asynchronous version. 

Second go at this uses the RxJS Observable library. This new version waits for the `Observable` to emit the array of heroes. Then `subscribe` passes the emitted array to the callback, which sets the component's `heroes` property.

Angular only binds to *public* component properties.

### Questions
- [ ] Module 4, services importing services. . . This reminds me of challenges facing Bad-Guy, what's the best practice here? As a potential lead, an aside refers to this as a "service-in-service" scenario.

### Tasks
- [ ] How about getting this basic tutorial app deployed by the jenkins-pi?