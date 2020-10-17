# NgxTranslateIn

This lib will allow you to translate in other languages than the current one using a pipe `translateIn`, you can translate a part of your html content in English while the current and default language is French.

## Install

Run `npm i ngx-translate-in --save`

## Usage

    import { BrowserModule } from '@angular/platform-browser';
    import { NgModule } from '@angular/core';
    import { HttpClientModule, HttpClient } from '@angular/common/http';
    import { TranslateModule, TranslateLoader } from '@ngx-translate/core';
    import { TranslateHttpLoader } from '@ngx-translate/http-loader';
    import { AppComponent } from './app.component';
    import { NgxTranslateInModule } from 'ngx-translate-in';

    export function translateHttpLoaderFactory(http: HttpClient) {
    return new TranslateHttpLoader(http);
    }
    @NgModule({
        declarations: [AppComponent],
        imports: [
            BrowserModule,
            HttpClientModule,
            TranslateModule.forRoot({
            loader: {
                provide: TranslateLoader,
                useFactory: translateHttpLoaderFactory,
                deps: [HttpClient],
                    },
             }),
            NgxTranslateInModule, // import the module
        ],
        providers: [],
        bootstrap: [AppComponent],
    })
    export class AppModule {}

If you need a text to be in french while the current language is english, you can use the pipe like this:

        </div> <!-- translated in english -->
        <div> {{"text1" | translate}}
        <!-- translated in french -->
        <div>{{'translationKey' | translateIn: "fr" | async}}</div>
        <!-- translated in english -->
        <div> {{"text2" | translate}} </div>
