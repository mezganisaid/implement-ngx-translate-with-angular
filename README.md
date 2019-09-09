## Install ANGULAR CLI in your PC

npm install -g @angular/cli

## Create new project

ng new appTranslate

Enter the following if you don't want to share usage data with the creators of Angular:

ng analytics off

## Finally start the new project:

cd appTranslate
ng serve --open

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

# implement-ngx-translate-with-angular

Enter the following line in the terminal:

<pre>npm install @ngx-translate/core @ngx-translate/http-loader rxjs --save</pre>

The @ngx-translate/core contains the core routines for the translation: The TranslateService and some pipes.

The @ngx-translate/http-loader loads the translation files from your webserver.

Now you have to init the translation TranslateModule in your app.module.ts:
