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