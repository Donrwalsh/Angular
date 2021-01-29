Targeting Angular 7

Following v7.angular.io/guide/quickstart#prerequisites with a little help from https://stackoverflow.com/questions/43344600/installing-a-specific-version-of-angular-with-angular-cli.

> npm uninstall -g @angular/cli
> npm cache clean
> npm i -g npm
> npm cache verify
> npm install -g @angular/cli@7
> ng new seven 
(yes to angular routing, selected SASS)

ng serve works just fine, though there are some warnings about vulnerabilities. 

Starting with the above and then initing the repo via GitKraken hit an error where it was treating the seven directory as a file. Creating the repo on github and then repeating the ng new worked just fine.

Making changes while ng serve is running doesn't seem to auto update. Ghost in the machine, needed to restart a few times.

Working to convert seven into the tour of heroes via the tutorial. 

1. The Hero Editor

>ng generate component heroes

I actually made a typo here and needed to delete the component. There seems to be no cli command to destroy a component, so what I did was delete the folder under src/app and then modify app.modules.ts to remove references to the destroyed component (two places but highlighted due to missing directory).