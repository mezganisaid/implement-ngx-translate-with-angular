# I _ Download Project

<pre>
git clone https://github.com/mezganisaid/implement-ngx-translate-with-angular.git
cd appTranslate
npm install
ng serve --open
</pre>

# II _ Create Project 

## Install ANGULAR CLI in your PC

<pre>npm install -g @angular/cli</pre>

## Create new project

<pre>ng new appTranslate</pre>

Enter the following if you don't want to share usage data with the creators of Angular:

<pre>ng analytics off</pre>

## Finally start the new project:

<pre>
cd appTranslate
ng serve --open
</pre>

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

# implement-ngx-translate-with-angular

1- Enter the following line in the terminal:

<pre>npm install @ngx-translate/core @ngx-translate/http-loader rxjs --save</pre>

The @ngx-translate/core contains the core routines for the translation: The TranslateService and some pipes.

The @ngx-translate/http-loader loads the translation files from your webserver.

2- Now you have to init the translation TranslateModule in your app.module.ts:

<pre>
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';

import { AppComponent } from './app.component';

// import ngx-translate and the http loader
import {TranslateLoader, TranslateModule} from '@ngx-translate/core';
import {TranslateHttpLoader} from '@ngx-translate/http-loader';
import {HttpClient, HttpClientModule} from '@angular/common/http';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
        BrowserModule,
        // ngx-translate and the loader module
        HttpClientModule,
        TranslateModule.forRoot({
            loader: {
                provide: TranslateLoader,
                useFactory: (HttpLoaderFactory),
                deps: [HttpClient]
            }
        })
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }

// required for AOT compilation
export function HttpLoaderFactory(http: HttpClient) {
    return new TranslateHttpLoader(http, './assets/i18n/', '.json');
}
</pre>

3- in app.components.ts add this line thoe code :

<pre>
import { Component } from '@angular/core';
import {TranslateService} from '@ngx-translate/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
    
    title = 'appTranslate';

    constructor(private translate: TranslateService) {
         // this language will be used as a fallback when a translation isn't found in the current language
        translate.setDefaultLang('fr');
         // the lang to use, if the lang isn't available, it will use the current loader to get them
        translate.use('fr');
    }

	changeLanguage(language: string) {
	    this.translate.use(language);
	}

}
</pre>

4- Create new folder (i18n) in assets, and in this folder create to file json (fr.json, en.json), and create your data.

5- Create yout app.components.html, and get DATA.

6- Abort the server with CTR-C and start the server with 'ng serve'
