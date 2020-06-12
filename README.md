# ng9-card [![npm version](https://badge.fury.io/js/ng9-card.svg)](https://www.npmjs.com/package/ng9-card) [![License: MIT](https://img.shields.io/badge/License-MIT-brightgreen.svg)](https://opensource.org/licenses/MIT)

Angular 9 wrapper for [card.js](https://github.com/jessepollak/card) 

Based on [ngx-card](https://ihym.github.io/ngx-card/) package.

## Installation

Install through `npm`:

```bash
npm install --save ng9-card
```

#### Dependencies
This library depends on [https://github.com/jessepollak/card](https://github.com/jessepollak/card) (tested with 2.3.0).
We don't ship with the library, but you have to take care of including it in your page. There are various ways to achieve this, for example by adding this at the end of your `<body>`:

```html
<script src="https://unpkg.com/card@2.3.0/dist/card.js"></script>
```

## API
### [card]
#### Input

* container: any: A selector or DOM element for the form where users will be entering their information

* card-width: number: default 350px

* messages: any = {validDate: 'valid\ndate', monthYear: 'mm/yyyy'}: Strings for translation

* placeholders: any = {number: '•••• •••• •••• ••••', name: 'Full Name', expiry: '••/••', cvc: '•••'}: Placeholders for rendered fields

* masks: any;

* formatting: boolean = true;

* debug: boolean = false: If true, will log helpful messages for setting up Card

###  [card-number]
###  [card-name]
###  [card-expiry]
###  [card-cvc]


## Usage
Once installed you need to import our main module into yours. You should end up with code similar to this:

```javascript
import {MyComponent} from '...';
import {CardModule} from 'ng9-card';

@NgModule({
  imports: [..., CardModule],
  declarations: [MyComponent, ...],
})
export class MyModule {}
```

Modify slightly your form by adding the correct directives in your form elements.

You can have multiple form elements that render to a single field (i.e. you have a first and last name input).

To use ngx-card with this functionality, just rearrange your form elements in the correct order and add the proper directives. For example,
```javascript
<div class="card-container"></div>
<form card
  container=".card-container"
  card-width="500"
  [messages]="messages"
  [placeholders]="placeholders"
  [masks]="masks"
  formatting="false"
  debug="true">

  <input type="text" name="number" card-number/>
  <input type="text" name="first-name" card-name/>
  <input type="text" name="last-name" card-name/>
  <input type="text" name="expiry" card-expiry/>
  <input type="text" name="cvc" card-cvc/>
</form>
```

***
MIT © [Carlos Possa](https://github.com/carloscpossa)
