# WebdriverIO Code Snippet

1. **Browser Related commands**

```js
	await browser.url("https://www.google.com");
	
	await String pageTitle = browser.getTitle();
	
	await browser.pause(3000);
	
	await browser.newWindow('https://webdriver.io')
	await browser.newWindow('https://webdriver.io', {
       		windowName: 'WebdriverIO window',
        	windowFeature: 'width=420,height=230,resizable,scrollbars=yes,status=1',
	});
	
	await browser.switchWindow('http://selenium143.blogspot.com/');	// for tab switch
	await browser.switchToWindow(ID[i]);  // To switch to child window	
	await browser.switchToWindow(parentWindow); // To switch to Parent window
	var parentWindow = await browser.getWindowHandle(); // To get Parent window
	var childWindows = await browser.getWindowHandles(); // To get all child windows
	
	await browser.saveScreenshot('./test/Screenshot/pageview.png');
	
	await browser.maximizeWindow();
	await browser.minimizeWindow();
	
	await browser.getWindowSize();	
	await browser.setWindowSize(400,800);
	
	await browser.keys('Enter')
	
	await browser.acceptAlert();
	await browser.dismissAlert();
	await let AlertText = browser.getAlertText();
	await browser.sendAlertText("How is your WebDriveIO journey is going on ? ");
	
	const activeElement = await browser.getActiveElement();

	browser.action('pointer')
		.move({ duration: 0, origin, x: 0, y: 0 })
		.down({ button: 0 }) // left button
		.pause(10)
		.move({ duration: 0, origin: targetOrigin })
		.up({ button: 0 })
		.perform();

	await browser.action('key)
		.down('f')
		.down('o')
		.down('o')
		.up('f')
		.up('o')
		.up('o')
		.perform();

	await browser.action('key')
		.down(Key.Ctrl).down('c')
		.pause(10)
		.up(Key.Ctrl).up('c')
		.perform();


	await browser.action('wheel').scroll({
		deltaX: 0,
		deltaY: 500,
		duration: 200
	    }).perform();

	await browser.execute(() => window.scrollY);	
	
	await browser.actions([
        browser.action('pointer')
            .move(500, 500)
            .down()
            .move(250, 250)
            .up(),
        browser.action('pointer')
            .move(500, 500)
            .down()
            .move(750, 750)
            .up()
        ]);
	
	await browser.setCookies([
		{name: 'test', value: '123'},
		{name: 'test2', value: '456'},
		{name: 'test3', value: '789'}
	    ]);

	let cookies = await browser.getCookies();

	await browser.deleteCookies(['test3']);

	await browser.deleteCookies();
	
	const result = await browser.execute((a, b, c, d) => { return a + b + c + d }, 1, 2, 3, 4) 

	const result = await browser.executeAsync(function(a, b, c, d, done) {        
		setTimeout(() => {
			done(a + b + c + d)
		}, 3000);
	}, 1, 2, 3, 4);
	
	const windowSize = await browser.getWindowSize();
	
	await browser.keys([Key.Ctrl, 'a', 'c])
	await browser.keys([Key.Ctrl, 'v'])
	
	await browser.closeWindow();

	console.log(browser.sessionId);
	await browser.reloadSession();
	
	await browser.savePDF('./some/path/screenshot.pdf');


	await browser.startRecordingScreen();
	await browser.saveRecordingScreen('./some/path/video.mp4');

	await browser.scroll(0, 200)

	await browser.setTimeout({
		'pageLoad': 10000,
		'script': 60000
	});
	

	const filePath = '/path/to/some/file.png'
	const remoteFilePath = await browser.uploadFile(filePath)


	await browser.waitUntil(
		async () => (await $('#someText').getText()) === 'I am now different',{
			timeout: 5000,
			timeoutMsg: 'expected text to be different after 5s'
		}
	);

```


2. **Element Related commands**

```js
	const text = await $('#menu');
	const text = await $('#menu').scrollIntoView();
	
	const menuList = await $$('#menuList');
	await menuList[1].click();
	
	await const iframe = $("#iframe2")
	await browser.switchToFrame(iframe)
	
	await $("#userName").setValue("abhijit1985");
	
	const selectBox = await $('#selectbox');
	await selectBox.selectByVisibleText('cuatro');
	await selectBox.selectByIndex(4);
	await selectBox.selectByAttribute('value', 'someValue3');	
	 
	
	await $('#q').click()
	await $('#q').doubleClick()
	await $('#q').keys("Text has been Entered in iframe2 text box")
	
	const element = $('#draggable')
	element.dragAndDrop(drop, 5000)
	
	const size = $('#HTML29 > div.widget-content > img').getSize();
	console.log(size.width); 
	console.log(size.height);	
	
	$("li.has-sub > a").moveTo(30,60)

```

3. **expect Related commands**

```js

	await expect(browser).toHaveTitleContaining("Abhijit Biradar");
	await expect(browser).toHaveTextContaining("Abhijit");
	await expect(browser).toHaveUrlContaining("shop");
	await expect(browser).toHaveTitle("Google");
	await expect(element).toBeDisplayed();
	await expect(element).not.toBeDisplayed();

```

4. **wait Related commands**

```js

	$('#finish').waitForDisplayed();
	
	$('#input-example input').waitForEnabled();
	
	$('#finish').waitForExist(); 
	
	browser.waitUntil(() => {                         
		return !($('#checkbox').isExisting());       
	});

```

5. **is Related commands**

```js

	var elementPresent = $('#hbutton').isExisting();
   	var disabledElement = $('//button[@id="but1"]').isClickable();
   	var isSelected = $("input[value='Bicycle']").isSelected(); // for dropdown option
   	var isDisplayed = $("input[value='Bicycle']").isDisplayed()  
	var isEnabled = $("input[value='Bicycle']").isEnabled();

```

5. **Locator Related commands**
	https://dzone.com/articles/how-webdriverio-uses-selenium-locators-in-a-unique
	
	
7. **Mocha Related commands**


5. **Chai Related commands**

```js
	const menu = await $('#menu');
	expect(menu.getValue()).to.equal('foo');
	
```	

# Sample WebdriverIO Login Test

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

const assert = require('assert'); 

describe(‘waitCommands’, () => { 
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

const assert = require('assert'); 
describe('Handle TextBox', () => { 
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


# WebDriverIO – CSS Query Selector

```js

const assert = require('assert');
describe('find Title Using CSS Query Selector', () => {
	it('should be able to find Title using CSS Selector',() => {
		browser.url('http://omayo.blogspot.com');
		var title = $('h1.title').getText();
		console.log(title);
		browser.pause(3000);
	});
});

```

# Link Text Locator in WebDriverIO

```js

const assert = require('assert'); 
describe('print visible text using link text locator ',() => {
	it('should print visible text and attributes using link text locator',() => { 
		browser.url('http://omayo.blogspot.com');       
		var link = $('=Selenium143');       
		console.log(link.getText()); // outputs: "Selenium143"     
		console.log(link.getAttribute('href')); //outputs : "http://www.Selenium143.blogspot.com"    
		link.click(); //Outputs : Redirection to "http://www.Selenium143.blogspot.com"         
		browser.pause(3000);  
	}); 
});

```

# Partial Link Text Locator in WebDriverIO

```js

const assert = require('assert');
describe('print visible text using Partial link text locator ',() => {
	it('should print visible text and attributes and click on link using partial link text locator',() => {
		browser.url('http://omayo.blogspot.com');
		var link = $('*=diumdev');
		console.log(link.getText()); //output :- compendiumdev
		console.log(link.getAttribute('href')); output :-  //http://compendiumdev.co.uk/selenium/basic_web_page.html
		link.click(); //open web page :- http://compendiumdev.co.uk/selenium/basic_web_page.html
		browser.pause(3000);
	});
});

```

# Element with Certain Text Locator in WebDriverIO

```js

const assert = require('assert')
describe('print visible text using Tag Name locator',() => {
	it('should print visible text using Tag Name locator',() => {
		browser.url('http://omayo.blogspot.com')
		console.log($('p=PracticeAutomationHere').getText())
		browser.pause(3000);
	}); 
});

```

# Tag Name Locator in WebDriverIO

```js

const assert = require('assert');
describe('print visible text using Tag Name locator ',() => {
	it('should print visible text using Tag Name locator',() => {
		browser.url('http://omayo.blogspot.com');
		console.log($('<button>').getText());
		browser.pause(3000);
	});
});
  
```

# ID Locators in WebDriverIO  

```js

describe('Navigate to Selenium143 Blogspot using ID Locator/Selector', () => {   
	it('should be able to find ID of URL Link using ID Locator/Selector',() => {        
		browser.url('www.omayo.blogspot.com');        
		$('#selenium143').click();  //using Id Locator and clicking on link Simultaneously   
		browser.pause(3000);      
	});     
});
  
```

# WebDriverIO – Using Xpath Locators

```js

describe('Click on ClickToGetAlert Button Using Xpath Locators in WebDriverIO',() => {        
	it('should find Absolute Xpath for ClickToGetAlert Button and Then click on it',() => {
		browser.url('http://omayo.blogspot.com')
		$('/html/body/div[4]/div[2]/div[2]/div[2]/div[2]/div[2]/div[2]/div/div[4]/div[3]/div/aside/div[1]/div[4]/div[1]/input').click()
		browser.pause(3000); 
	});

	it('should find Relative Xpath for ClickToGetAlert Button and Then click on it',() => {
		browser.url('http://omayo.blogspot.com')
		$('//*[@id="alert1"]').click()
		browser.pause(3000); 
	});   
});
  
 ```
 
# Switching To Frames in WebDriverIO

```js

describe('Locate Iframe Using SwitchToFrame Command in WebDriverIO',() => {
	it('should Locate Iframe and Enter Text in Text Field Present in Iframe',() => {
		browser.url('http://omayo.blogspot.com')
		browser.pause(3000);
		$('#iframe2').isDisplayed()  
		const iframe = $("#iframe2") /* const variable named as iframe is created and iframe id is assigned to iframe */
		iframe.scrollIntoView(); 
		browser.switchToFrame(iframe)
		$('#q').isDisplayed()  
		$('#q').click()
		$('#q').keys("Text has been Entered in iframe2 text box")
		browser.pause(3000);  
	});
});
  
```

# WebDriverIO – Switching To Tabs in WebDriverIO

```js

describe('Switching to tabs in WebDriverIO',() => {
	it('should Switch tabs using switchWindow Command ',() => {        
		browser.url('https://omayo.blogspot.com')
		$("//*[@id='selenium143']").click()  //xpath of the hyperlink on webpage 
		browser.pause(3000);
		browser.switchWindow('http://selenium143.blogspot.com/')
	});
});  

```

# WebDriverIO – Scroll Into View Command in WebDriverIO

```js

describe('ScrollIntoView Command in WebDriverIO',() => {
	it('should scroll to footer of the webpage',() => {        
		browser.url('http://omayo.blogspot.com/')
		const Footer = $('.footer-cap-top');
		// scroll to specific element
		Footer.scrollIntoView();
		browser.pause(3000)
	});
});

```

# WebDriverIO – Save Screenshot in WebDriverIO

```js

describe('save screenshot command takes screenshot in WebDriverIO',() => {
	it('should take screenshot of page view of webpage',() => {        
		browser.url('http://omayo.blogspot.com/')
		$('.footer-cap-top').scrollIntoView()
		browser.pause(3000)
		browser.saveScreenshot('./test/Screenshot/pageview.png')
	});
});

```

# WebDriverIO – Drag and Drop in WebDriverIO

```js

describe('Drag and Drop command moves Drag Box from its position to Destination i.e., Drop Box',()=> {
	it('should make Drag Box to reach out to Drop Box', () => {
		browser.url('https://jqueryui.com/droppable/')
		const frame1 = $('/html/body/div[1]/div[2]/div/div[1]/iframe')
		browser.switchToFrame(frame1)
		const drag = $('#draggable')
		drag.waitForExist(5000)
		console.log(drag)
		const drop =$('#droppable')
		console.log(drop)
		drag.dragAndDrop(drop, 5000)
		browser.pause(8000);
	});
});

```

# WebDriverIO – Skip Test Cases

```js

describe('Explaining how to skip test cases in WebDriverIO',() => {
	it.skip('should skip this test case',() => {
		browser.url ('http://omayo.blogspot.com')
		$('/html/body/div[4]/div[2]/div[2]/div[2]/div[2]/div[2]/div[2]/div/div[4]/div[3]/div/asid   e/div[1]/div[4]/div[1]/input').click()
		browser.pause(3000); 
	});

	It ('should find Relative Xpath for ClickToGetAlert Button and Then click on it',() => {
		browser.url('http://omayo.blogspot.com')
		$('//*[@id="alert1"]').click()
		browser.pause(3000); 
	});  
});

```

# WebDriverIO – Handling Multiple Windows in WebDriverIO

```js

describe('Handling Multiple Windows switching to child window and then switching to parent window back',()=> {
        it('should make switching from parent to child and child to parent window', () => {    
		browser.url('http://omayo.blogspot.com/')
		var parentWindow = browser.getWindowHandle()
		$('#HTML37 > div:nth-child(2) > p:nth-child(2) > a:nth-child(1)').click()
		browser.pause(3000)
		var ID = browser.getWindowHandles()
		for(var i = 0; i< ID.length; i++){
		    if( ID[i]!= parentWindow){
			browser.switchToWindow(ID[i])
			browser.maximizeWindow()
			break;
		    }
		}
		browser.pause(3000)
		browser.switchToWindow(parentWindow)
		browser.pause(3000)
    	});
});

```

# WebDriverIO – Dot Reporter

WebDriverIO Supports many number of Reporters out of which we will discuss few which are mentioned below :-

1) Dot Reporter (https://www.qafox.com/webdriverio-dot-reporter-in-webdriverio/)

2) Spec Reporter (https://www.qafox.com/webdriverio-spec-reporter/)

3) Junit Reporter (https://www.qafox.com/webdriverio-junit-reporter/)

4) Json Reporter (https://www.qafox.com/webdriverio-json-reporter/)

5) Allure Reporter (https://www.qafox.com/webdriverio-allure-reporter/)


# WebDriverIO – Dot Reporter

```js

describe('Demonstrating dot reporter in WebdriverIO',() => {
	it('should find absolute path for clickToGetAlert Button and then click on it',() => {
		browser.url ('http://omayo.blogspot.com')
		$('/html/body/div[4]/div[2]/div[2]/div[2]/div[2]/div[2]/div[2]/div/div[4]/div[3]/div/aside/div[1]/div[4]/div[1]/input').click()
		browser.pause(3000); 
	});

	it('should find Relative Xpath for ClickToGetAlert Button and Then click on it',() => {
		browser.url('http://omayo.blogspot.com')
		$('//*[@id="alert1"]').click()
		browser.pause(3000); 
	});

	it('should print visible text and attributes using link text locator',() => {
		browser.url('http://omayo.blogspot.com');
		var link = $('=Selenium143');
		console.log(link.getText()); // outputs: "Selenium143"
		console.log(link.getAttribute('href')); //outputs : "http://www.Selenium143.blogspot.com"  
		link.click(); //Outputs : Redirection to "http://www.Selenium143.blogspot.com"  
		browser.pause(3000);
	});
});

```

# WebDriverIO – Spec Reporter

```js

describe('Demonstrating spec reporter in WebdriverIO',() => {
	it('should find absolute path for clickToGetAlert Button and then click on it',() => {
		browser.url ('http://omayo.blogspot.com')
		$('/html/body/div[4]/div[2]/div[2]/div[2]/div[2]/div[2]/div[2]/div/div[4]/div[3]/div/aside/div[1]/div[4]/div[1]/input').click()
		browser.pause(3000); 
	});

	it('should print visible text and attributes using link text locator',() => {
		browser.url('http://omayo.blogspot.com');
		var link = $('=Selenium143');
		console.log(link.getText()); // outputs: "Selenium143"
		console.log(link.getAttribute('href')); //outputs : "http://www.Selenium143.blogspot.com"  
		link.click(); //Outputs : Redirection to "http://www.Selenium143.blogspot.com"  
		browser.pause(3000);
	});

	it('should find Relative Xpath for ClickToGetAlert Button and Then click on it',() => {
		browser.url('http://omayo.blogspot.com')
		$('#selenium143').click()
		browser.pause(3000); 
	});
});

```

# WebDriverIO – Junit Reporter

```js

describe('Demonstrating Junit reporter in WebdriverIO',() => {
	it('should find absolute path for clickToGetAlert Button and then click on it',() => {
		browser.url ('http://omayo.blogspot.com')
		$('/html/body/div[4]/div[2]/div[2]/div[2]/div[2]/div[2]/div[2]/div/div[4]/div[3]/div/aside/div[1]/div[4]/div[1]/input').click()
		browser.pause(3000);
	});

	it('should print visible text and attributes using link text locator',() => {
		browser.url('http://omayo.blogspot.com');
		var link = $('=Selenium143');
		console.log(link.getText()); // outputs: "Selenium143"
		console.log(link.getAttribute('href')); //outputs : "http://www.Selenium143.blogspot.com"
		link.click(); //Outputs : Redirection to "http://www.Selenium143.blogspot.com"
		browser.pause(3000);
	});

	it('should find Relative Xpath for ClickToGetAlert Button and Then click on it',() => {
		browser.url('http://omayo.blogspot.com')
		$('#selenium143').click()
		browser.pause(3000);
	});
});

```

# WebDriverIO – Json Reporter

```js

describe('Demonstrating JSON reporter in WebdriverIO',() => {
	it('should find absolute path for clickToGetAlert Button and then click on it',() => {
		browser.url ('http://omayo.blogspot.com')
		$('/html/body/div[4]/div[2]/div[2]/div[2]/div[2]/div[2]/div[2]/div/div[4]/div[3]/div/aside/div[1]/div[4]/div[1]/input').click()
		browser.pause(3000); 
	});

	it('should print visible text and attributes using link text locator',() => {
		browser.url('http://omayo.blogspot.com');
		var link = $('=Selenium143');
		console.log(link.getText()); // outputs: "Selenium143"
		console.log(link.getAttribute('href')); //outputs : "http://www.Selenium143.blogspot.com"  
		link.click(); //Outputs : Redirection to "http://www.Selenium143.blogspot.com"
		browser.pause(3000);
	});

	it('should find Relative Xpath for ClickToGetAlert Button and Then click on it',() => {
		browser.url('http://omayo.blogspot.com')
		$('#selenium143').click()
		browser.pause(3000); 
		});
	});
});

```

# WebDriverIO – Allure Reporter

```js

describe('Demonstrating JSON reporter in WebdriverIO',() => {
	it('should find absolute path for clickToGetAlert Button and then click on it',() => {
		browser.url ('http://omayo.blogspot.com')
		$('/html/body/div[4]/div[2]/div[2]/div[2]/div[2]/div[2]/div[2]/div/div[4]/div[3]/div/aside/div[1]/div[4]/div[1]/input').click()
		browser.pause(3000); 
	});

	it('should print visible text and attributes using link text locator',() => {
		browser.url('http://omayo.blogspot.com');
		var link = $('=Selenium143');
		console.log(link.getText()); // outputs: "Selenium143"
		console.log(link.getAttribute('href')); //outputs : "http://www.Selenium143.blogspot.com"  
		link.click(); //Outputs : Redirection to "http://www.Selenium143.blogspot.com" 
		browser.pause(3000);
	});

	it('should find Relative Xpath for ClickToGetAlert Button and Then click on it',() => {
		browser.url('http://omayo.blogspot.com')
		$('#selenium143').click()
		browser.pause(3000); 
	});
});

```

# WebDriverIO – Timeline Reporter

```js

describe('Demonstrating Timeline reporter in WebdriverIO',() => {
	it('should find absolute path for clickToGetAlert Button and then click on it',() => {
		browser.url ('http://omayo.blogspot.com')
		$('/html/body/div[4]/div[2]/div[2]/div[2]/div[2]/div[2]/div[2]/div/div[4]/div[3]/div/aside/div[1]/div[4]/div[1]/input').click()
		browser.pause(3000); 
	});
	
	it('should print visible text and attributes using link text locator',() => {
		browser.url('http://omayo.blogspot.com');
		var link = $('=Selenium143');
		console.log(link.getText()); // outputs: "Selenium143"
		console.log(link.getAttribute('href')); //outputs : "http://www.Selenium143.blogspot.com"  
		link.click(); //Outputs : Redirection to "http://www.Selenium143.blogspot.com"  
		browser.pause(3000);
	});
	
	it('should find Relative Xpath for ClickToGetAlert Button and Then click on it',() => {
		browser.url('http://omayo.blogspot.com')
		$('#selenium143').click()
		browser.pause(3000); 
	});
});

```

# WebDriverIO – $ Command

```js

describe('This Example show usage of $$ command in webdriverio', () => {
	it('should fetch multiple element based on the locator passed and perform actions accordingly   ', ()=> {
		browser.url('http://omayo.blogspot.com');
		const text = $('//*[@id="HTML25"]/div[1]/ol/li');
		console.log(text[2].getText());
	});
});
    
 ```
   
# WebDriverIO – $$ Command

```js

describe('This Example show usage of $$ command in webdriverio', () => {
	it('should fetch multiple element based on the locator passed and perform actions accordingly', ()=> {
		browser.url('http://omayo.blogspot.com');
		const text = $$('//*[@id="HTML25"]/div[1]/ol/li');
		console.log(text[2].getText());
	});
});

```

# WebDriverIO – getSize Command

```js

describe('This Example show usage of $ command in webdriverio', () => {
	it('should fetch element based on the locator passed and perform actions accordingly', ()=> {
		browser.url('http://omayo.blogspot.com');
		const size = $('#HTML29 > div.widget-content > img').getSize();
		console.log(size); // display result in width and height , output should be { width: 150, height: 200 }
		console.log(size.width) //display only width of Image , output should be 150
		console.log(size.height) //display only height of Image output should be 200
	});
});

```

# WebDriverIO – getWindowSize

```js

describe('This Example show usage of getWindowSize command in webdriverio', () => {
	it('should fetch the size of browserWindow in which mentioned url has been opened', ()=> {
		browser.url('http://omayo.blogspot.com');
	console.log(browser.getWindowSize());
	});
});

```

# WebDriverIO – setWindowSize

```js

describe('This Example show usage of setWindowSize command in webdriverio', () => {
	it('should fetch the size of browser Window in which mentioned url has been opened', ()=> {
		browser.url('http://omayo.blogspot.com');
		console.log(browser.setWindowSize(400,800));
		browser.pause(3000);
	});
});

```

# WebDriverIO – Pause Command

```js

describe('This Example show usage of pause command in webdriverio', () => {
	it('should click on button and pause browser for 25 seconds before exiting', ()=> {
		browser.url('http://omayo.blogspot.com');
		const UL = $('#HTML25 > h2'); 
		UL.scrollIntoView(); // scroll till UnOrderedlist so that Button to click comes under browser view 
		$('#alert2').click();// clicking on button
		browser.acceptAlert() //Accepts the alert which gets open
		browser.pause(25000); //make browser to pause for 25 seconds till text got disappeared.
	});
});

```

# WebDriverIO – Keys Command

```js

describe('This Example show usage of Keys command in webdriverio', () => {
	it('should use Enter Key of Keyboard rather than clicking on search button', ()=> {
		browser.url('http://omayo.blogspot.com');
		$('td.gsc-input > input').setValue('Random'); //Writing in Search Bar 
		browser.keys('Enter')//Hitting Enter Key from Keyboard for Searching Random Word on web Application
		browser.pause(3000);
	});
});

```

# WebDriverIO – Handling Alerts

```js

describe('This Example show usage of acceptAlert() command in webdriverio', () => {
	it('should accept Alert Box', ()=> {
		browser.url('http://omayo.blogspot.com');
		$('#alert1').click(); //Click on Alert Button 
		browser.acceptAlert(); //Accept the Alert/Dialogue Box
		browser.pause(3000);
	});
});

```

# WebDriverIO – Dismiss Alerts

```js

describe('This Example show usage of dismissAlert() command in webdriverio', () => {
	it('should dismiss confirmation Alert Box', ()=> {
		browser.url('http://omayo.blogspot.com');
		$('#confirm').click(); //Click on confirmation Alert Button 
		browser.dismissAlert(); //dimiss the Alert/Dialogue Box
		browser.pause(3000);
	});
});

```

# WebDriverIO – Get Alert Text

```js

describe('This Example show usage of getAlertText() command in webdriverio', () => {
	it('should display Text of Alert Box', ()=> {
		browser.url('http://omayo.blogspot.com');
		$('#alert1').click(); //Click on ClickToGetAlert Button 
		let AlertText = browser.getAlertText(); //Storing the text present on Alert/Dialogue Box
		console.log(AlertText);
		browser.pause(3000);
	});
});

```

# WebDriverIO – sendAlertText

```js

describe('This Example show usage of sendAlertText() command in webdriverio', () => {
	it('should send Text to user prompt Box', ()=> {
		browser.url('http://omayo.blogspot.com');
		$('#prompt').click(); //Click on Get Prompt Button 
		browser.sendAlertText("How is your WebDriveIO journey is going on ? ");
		browser.pause(3000);
	});
});

```

# WebDriverIO – Double click

```js

describe('This Example show usage of doubleCLick() command in webdriverio', () => {
	it('should click on Double Click Here Button on Omayo.blogspot.com Web Application', ()=> {
		browser.url('http://omayo.blogspot.com');
		$("#myBtn").scrollIntoView();
		const myButton = $("//button[contains(text(),'Double click Here')]");
		myButton.doubleClick() //Double Click on Double Click Here Button 
		browser.pause(3000);
	});
});

```

# WebDriverIO – MoveTo

```js

describe('This Example show usage of MoveTo() command in webdriverio', () => {
	it(' should demonstrate mouse hover over blog menu list on omayo.blogspot.com web application’ , () => {
		browser.url('http://omayo.blogspot.com/')
		$("li.has-sub > a").moveTo(30,60) //hovering over blogs menu list
		browser.pause(3000);
	});
});

```

# WebDriverIO – isExisting

```js

describe('This Example show usage of isExisting() command in webdriverio',() => { 
	it('should give us true if element is present on the page else returns false',()=> { 
		browser.url('http://omayo.blogspot.com');  
		var elementPresent = $('#hbutton').isExisting(); 
		console.log(elementPresent); 
	});
});

```

# WebDriverIO – isClickable

```js

describe('This Example show usage of isClickable() command in webdriverio', () => {
	it('should give us false if isClickable() has been applied on disable element', ()=> {
		browser.url('http://omayo.blogspot.com');
		var disabledElement = $('//button[@id="but1"]').isClickable();
		console.log(disabledElement);
	});
});

```

# WebDriverIO – isSelected

```js

beforeEach(function(){
	browser.url('http://omayo.blogspot.com');
});

describe('This Example show usage of isSelected() command in webdriverio', () => {
	it('should give us true if isSelected() has been applied on selected Radio button element',()=> {
		var isSelected = $("input[value='Bicycle']").isSelected(); //RadioButton is in Selected State
		console.log(isSelected);
	});

	it('should give us false if isSelected() has been applied on not selected Radio button element', ()=> {
		var isSelected = $("input[value='Bike']").isSelected();//RadioButton is not in Selected State
		console.log(isSelected);
	});

	it('should give us false if isSelected() has been applied on not selected Radio button element', ()=> {
		var isSelected = $("input[value='Laptop']").isSelected();//CheckBox is not in Selected State
		console.log(isSelected);
	});

	it('should give us true if isSelected() has been applied on selected Radio button element', ()=> {
		var isSelected = $("input[value='Book']").isSelected();//CheckBox is in Selected State
		console.log(isSelected);
	});
});

```

	
# Configure Browser in WebdriverIO
	1. Include "@wdio/selenium-standalone-service" dependency in package.json
	
	2. Update browser details in wdio.conf.js file as below
	   services: ['selenium-standalone']
	   
	3. Update browser details as below 
		browserName: "chrome"		
		or		
		browserName: 'firefox'		
		or
		browserName: 'MicrosoftEdge
		
	Reference: https://webdriver.io/docs/selenium-standalone-service
	

# Execute script in parallel mode
	1. Navigate to wdio.conf.js file  
	
	2. Update maxInstances value more than 1 as below
		maxInstances:3
		
	3. Add more spec file in specs section as below
		specs:['./test/specs/**/*.js']
		
	4. Update acceptInsecureCerts: true


# Execute script in headless mode
	1. Refer capabilities section in this url https://webdriver.io/docs/configurationfile/
	
	
# Execute specific Test cases in webdriverio
		1. Add specific word in it block of test as below
			it('should login with valid credentials-smoke', async () => {});
			
		2. Navigate to wdio.conf.js file
		
		3. Navigate to command prompt and type command as below
			npx wdio run wdio.conf.js --mochaOpts.greep smoke
			
			
# Execute specific test suite	
		1. Navigate to wdio.conf.js file
		
		2. Add below section in that file
			suites:{
				debitCard:['filepath/file1.js','filepath/file2.js'],
				creditCard:['filepath/file3.js','filepath/file4.js']
			}

		3. Navigate to command prompt and execute as below
			npx wdio run wdio.conf.js --suite debitCard
			
			


# Execute specific spec file at runtime
	1. Navigate to command prompt and execute as below
			npx wdio run wdio.conf.js --spec filepath/file4.js

	2. if you want to execute multiple spec file, use as below
		npx wdio run wdio.conf.js --spec filepath/file3.js, filepath/file4.js
		


# Exclude test cases in execution		
	1. Navigate to wdio.conf.js file
	
	2. Update exclude section as below
		exclude: [
			'filepath/file1.js',
			'filepath/file2.js'
		]
		


			
# Stop execution based on total failed test cases
	1. Navigate to wdio.conf.js file
	
	2. Update value for bail section as below
		bail: 6


# Configure Base URL
	1. Navigate to wdio.conf.js file
	
	2. Update baseurl section as below
		baseurl:'https://www.google.com'
		
	3. Update url in script as below
		browser.url(`/login.html`)
		
	
# Custom wdio.conf.js file

	1. Create custom config file

		file name : wdio.uat.conf.js
		const merge= require("deepmerge")
		const wdioConf= require("./wdio.conf.js")

		exports.config = merge(wdioConf.config, {
			baseurl:"https:// www.yahoo.com";
			waitForTimeout: 5000

		});

	2. execute command from command prompt
		npx wdio run wdio.uat.conf.js
	

# Retry Failed Test Cases

	describe('retries', function () {
    // Retry all tests in this suite up to 4 times
    this.retries(4)  // Retry complete test suite

    beforeEach(async () => {
        await browser.url('http://www.yahoo.com')
    })

    it('should succeed on the 3rd try', async function () {
        // Specify this test to only retry up to 2 times
        this.retries(2)   // // Retry specific test case
        console.log('run')
        await expect($('.foo')).toBeDisplayed()
    })
})


# Trigger  Execution through Scripts

	1. Navigate to package.json file
	
	2. update commdna in script section as below
		"scripts":{
			"debitCardTest" : "npx wdio run wdio.conf.js --suite debitCard"
		}
		
	3. execute below command as below 
		npm run debitCardTest


# Configure Reports

https://webdriver.io/docs/allure-reporter/
https://webdriver.io/docs/junit-reporter/




# Configure jenkins










# Additional Resource for more knowladge

1. **WebDriverIO**
		
	https://www.youtube.com/playlist?list=PLFGoYjJG_fqqswF8qDdWNG3b-BtZfiqQn

	https://www.youtube.com/playlist?list=PL6AdzyjjD5HBbt9amjf3wIVMaobb28ZYN

	https://www.youtube.com/playlist?list=PL6flErFppaj3Cjikm_8wHU-I-3V1UhYq-

	https://www.youtube.com/playlist?list=PLBNb67lT6eELvpDN20XpJJ89XFn-j-gcA

	https://www.youtube.com/playlist?list=PLGk7ftfMz7jbZcArQU894rAfo6B1PbXbG

	https://webdriver.io/

	https://webdriver.io/docs/api/

	https://www.lambdatest.com/blog/how-webdriverio-uses-selenium-locators/

	https://webdriver.io/docs/selectors/

	https://webdriver.io/versions/

	https://webdriver.io/docs/api/expect-webdriverio/

	https://webdriver.io/docs/api/element/waitUntil/

	https://webdriver.io/docs/selenium-standalone-service/

	https://webdriver.io/docs/configurationfile/

	https://webdriver.io/docs/allure-reporter/

	https://www.udemy.com/join/login-popup/?next=/course/webdriverio-tutorial-nodejs-javascript/learn/lecture/25707132#overview

	https://www.youtube.com/watch?v=du2Jnm-TzJc		


2. **CucumberJS**

	https://www.testim.io/blog/cucumber-js-for-bdd-an-introductory-tutorial-with-examples/

	https://www.testim.io/blog/detailed-introduction-javascript-bdd/

	https://www.lambdatest.com/blog/cucumberjs-tutorial-selenium/

	https://github.com/cucumber/cucumber-js

	https://modernweb.com/bdd-in-javascript-with-cucumberjs/

	https://www.thinkcode.se/blog/2018/02/07/getting-started-with-cucumber-for-javascript

	https://docs.getxray.app/display/XRAY/Testing+Node.js+apps+using+Cucumber.js+in+JavaScript



# Notes from WebdriverIO Official Documentation

For expect object related commands
https://webdriver.io/docs/api/expect-webdriverio

For browser object related commands
https://webdriver.io/docs/api/browser/$$

For element object related commands
https://webdriver.io/docs/api/element/$$

















