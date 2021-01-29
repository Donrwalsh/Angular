Targeting Angular 7

> npm uninstall -g @angular/cli
> npm cache clean
> npm i -g npm
> npm cache verify
> npm install -g @angular/cli@7
> ng new seven 
(yes to angular routing, selected SASS)

ng serve works just fine, though there are some warnings about vulnerabilities. 

Starting with the above and then initing the repo via GitKraken hit an error where it was treating the seven directory as a file. Creating the repo on github and then repeating the ng new worked just fine.