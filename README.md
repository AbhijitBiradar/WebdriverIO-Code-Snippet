# WebdriverIO Code Snippet

# Sample WebdriverIO Script

1. **Run your first automation script**

```js

const { remote } = require('webdriverio'); (async () => { 
const browser = await remote({ logLevel: 'error', path: '/', 
capabilities: {browserName: 'firefox'} });
await browser.url('http://tutorialsninja.com/demo/'); 
const title = await browser.getTitle(); 
console.log('Title was:' + title); 
await browser.deleteSession(); 
}) ().catch((e) => console.error(e));

```

# Sample WebdriverIO Login Test

1. **Run Authentication Login Test**

```js

const assert = require('assert');

describe('Tutorials Ninja Login Form', () => {
  it('should not allow login with invalid username', () => {
    browser.url('http://tutorialsninja.com/demo');
    browser.pause('2000');
    $('/html[1]/body[1]/nav[1]/div[1]/div[2]/ul[1]/li[2]/a[1]').click();
    browser.pause('2000');
    $('=Login').click();
                browser.pause('2000');
    $('#input-email').addValue('asdaad');
    $('#input-password').addValue('asd@123$');
    $('[type="submit"]').click(); 
    browser.pause('2000');
    const error = $('/HTML[1]/BODY[1]/DIV[2]/DIV[1]').getText();
    console.log(error);
    assert.equal(error, 'Warning: No match for E-Mail Address and/or Password.');
    browser.pause('2000');
  });
});

```


# WebDriverIO – Wait Commands

1. **waitForDisplayed**

```js

const assert = require('assert');
   describe('waitForCommands', () => {
     it('waitForDisplayed', ()=> {
         browser.url('https://the-internet.herokuapp.com/dynamic_loading/1');
         $('#start button').click();
         $('#finish').waitForDisplayed();  //will wait for text present under ID finish to display.
         assert.equal( ($('#finish h4').getText()),'Hello World! ');
     });
});

```

2. **waitForEnabled**

```js

const assert = require('assert');
describe('waitForCommands', () => {
it('waitForEnabled',()=> {
                         browser.url('https://the-internet.herokuapp.com/dynamic_controls');
                         $('#input-example button').click();
                         $('#input-example input').waitForEnabled();
                         $('#input-example input').addValue('test');
                         browser.pause(5000);
   });
});

```

3. **waitForExist**

```js

const assert = require('assert');
describe('waitForCommands', () => {
it('waitForExist', ()=> {
                         browser.url('https://the-internet.herokuapp.com/dynamic_loading/1');
                         $('#start button').click();
                         $('#finish').waitForExist();  //will wait for text present under ID finish to display.                                
   });
});

```

4. **waitUntil**

```js

const assert = require('assert'); describe(‘waitCommands’, () => { 
   it('waitUntil',() => {
   browser.url('https://the-internet.herokuapp.com/dynamic_controls');
   $('#checkbox-example button').click();                      
   browser.waitUntil(() => {                         
   return !($('#checkbox').isExisting());       
  });      
 }); 
});

```

# WebDriverIO – Handling Checkboxes

```js

const assert = require('assert');
 describe('Handle Checkboxes', () => {
 it('should be checked', ()=> { 
 browser.url('http://omayo.blogspot.com'); 
 const checkbox_two = $('[type="checkbox"]:nth-child(2)'); 
 checkbox_two.scrollIntoView(); browser.pause(3000); 
 checkbox_two.click(); 
 browser.pause(3000); 
 }); 
});

```

# WebDriverIO-Handling Dropdowns

```js

const assert = require('assert');
describe('Handle Dropdowns', () => {
    it('should select value from dropdown menu', ()=> {
      browser.url('http://omayo.blogspot.com');
      $('#drop1').selectByVisibleText('doc 3');
      browser.pause(3000);
    });  
});


```

# WebDriverIO – Handling Radio Button

```js

const assert = require('assert');
describe ('Handle Radio Button', ()=> {
it('should handle radio button on webpage', ()=> {
    browser.url('http://omayo.blogspot.com/');
    const  radio_button = $('input[id="radio2"]');  //storing Xpath for the required Radio Button
                radio_button.click(); // clicking on radio button
                browser.pause(3000);
   });
});

```

# WebDriverIO – Handling Text Area and Text Box fields

```js

const assert = require('assert'); describe('Handle TextBox', () => { 
it('should handle text area/text box on webpages', ()=> {
    browser.url('http://omayo.blogspot.com/'); 
    $('#ta1').addValue('Test') //Writing Test to Text Area on WebPage
    $('#ta1').addValue('_Data') //Appending _Data to already written text in Text Area
    $('#textbox1').setValue('Test WebDriver')//Writing Test WebDriver to text box with predefined text 
    browser.pause(5000);
   }); 
});

```

WebDriverIO – Locators/Selectors

Commonly used different Locators/Selectors in WebDriverIO are listed as below: –

1) CSS Query Selector

2) Link Text

3) Partial Link Text

4) Element with certain text

5) Tag Name

6) id

7) Xpath

8) Chain Selectors

















