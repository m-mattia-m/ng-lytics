# NgLytics [![Build Status](https://travis-ci.org/Raiffeisen-Schweiz/ng-lytics.svg?branch=master)](https://travis-ci.org/Raiffeisen-Schweiz/ng-lytics)

An Angular wrapper for Analytics by using the DataLink concept.

## Installation

First you need to install the npm module:

`npm i ng-lytics --save`

## Usage

#### Import the `NgLytics` module

```typescript
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { NgLytics } from 'nglytics';

@NgModule({
  imports: [
    BrowserModule,
    NgLyticsModule.forRoot({
      appName: 'defaultAppName',
      environmentName: 'dev',
      dataLayerName: 'dataLayer',
      isDevMode: true
    })
  ],
  bootstrap: [AppComponent]
})
export class AppModule {}
```

#### Configuration

- **appName?**
  - Type: `string`
  - Determines the name of the app.
  - Default: **defaultAppName**
- **environmentName?**
  - Type: `string`
  - Determines the environment.
  - Default: **dev**
- **dataLayerName?**
  - Type: `string`
  - Determines the key on the window object, where the events are located.
  - Default: **dataLayer**
- **isDevMode?**
  - Type: `boolean?`
  - If set to _true_, additional logging will be enabled
  - Default: **false**

## API

### NgLyticsService

#### Methods

- `trackPageRequested(data: NgLyticsPageRequested): void`: Tracks a page as initialized and adds an event to the dataLayer array.
- `trackPageLoaded(): void`: Tracks a page as rendered and adds an event the dataLayer array. Needs to be called after _trackPageRequested(data)_.
- `trackAction(data: NgLyticsAction): void`: Tracks an interaction and adds an event to the dataLayer array.
- `trackAsyncAction(data: NgLyticsAction): void`: Tracks an interaction with asynchronous payload and adds an event to the dataLayer array.
- `registerAsyncAction(numberOfActions = 1): void`: Registers upcoming asynchronous action calls.

#### Sample App
Sample app is available [here](https://github.com/Raiffeisen-Schweiz/ng-lytics/tree/master/projects/example/src/app).

## License
MIT
