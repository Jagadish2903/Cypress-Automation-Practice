                                          Cypress Basic Documentation
                                          
 What is Cypress?
· Cypress is a next generation front end Automation testing tool built for the modern web applications
How Cypress is Unique from other Automation tools?
•	Cypress automatically waits for commands and assertions before moving on. No more async hell.
•	Ability to test Edge Testcases by Mocking the server response
•	Cypress takes snapshots as your tests run. We can hover over each command in the Command Log to see exactly what happened at each step.
•	Because of its Architectural design, Cypress delivers fast, consistent and reliable test execution compared to other Automation tools
•	View videos of your entire tests execution when run from the Cypress Dashboard.
•	Cypress is Asynchronous in nature 
*******************************************************************************************
	Cypress built on Node.js and comes packaged as a npm module,
	As it is built on Node.js, It uses JavaScript for writing tests. But 90% of coding can be done using Cypress inbuilt commands which are easy to understand.
	Cypress also bundles with jQuery and inherits many of jQuery methods for UI components Identification
Cypress Architecture
•	Most testing tools (like Selenium) operate by running outside of the browser and executing remote commands across the network. But Cypress engine directly operates inside the browser. In other words, It is the browser that is executing your test code
•	This enables Cypress to listen and modify the browser behavior at run time by manipulating DOM and altering Network requests and responses on the fly
•	Cypress open doors to New Kind of testing with Having ultimate control over your application (front and back)

Cypress Browser Support:
•	Chrome
•	Electron
•	Firefox
•	IE

Cypress Components:
•	Test Runner
•	Dashboard Service

Node.js:
 Node.js is the run time environment for javaScript and it’s a open source, cross platform that runs on VB engine and executes javaScript outside the browser.

Cypress Test:
•	To write a Cypress Test, we need to follow a standard javaScript framework like Mocha or Jasmine.
•	Cypress recommends Mocha and its auto bundled in cypress 
•	describe is something like a Test Suite 
•	it is something like a Testcase 
•	describe('My First Test Suite', function(){
•	
•	it('My First Test case', function(){
•	//Testcase1
•	
•	})
•	
•	it('My second test case', function(){
•	 //Testcase2   
•	})
•	
•	})

•	Cy is the object and we can use different methods from the cy (Eg. cy.visit(“url”)

•	To open the Cypress we need to use Cypress open and to run the TestRunner we need to use cypress run 
•	When Testcases is executed from the Command line Cypress will always run in headless and run in electron browser which is a default one 
•	To execute the testcases in headed mode in terminal we need to pass path/cypress run - -headed .
•	To execute the testcases in particular browser we need to use the command path/cypress run - -browser chrome
•	To execute the particular spec file thorough the terminal we need to use path of the spec file …path.js/cypress run –headed 

Cypress Structure:
•	Fixtures – This is used to achieve the data driven concept we can place our data in excel and put it here and easily invoke using fixture command 
•	Integration- This is where we used to write our testcases 
•	Plugins- This is where we can use listeners like what to do when event is happening and after the event is happened.
•	Support – All Re-usable methods should be declared here so that we can use those in for testcases…N:b we can use different folder to store our re-usable functions as well but we need to import and do some stuffs whereas when we use support folder cypress directly looks into it 
•	Node Modules- This is automatically done when we use npm install without these we cannot use any cypress things 
•	Cypress.config.js- This is where we need to define all the properties for our cypress project (something like a config file in selenium)
•	Cypress Test Runner has the option to get the locators as well 
N:B
•	Cypress only supports CSS selectors for locating an element 
We can get the Auto completion by adding the reference type in config.json

Cypress Promise Handling:
•	Cypress is Asynchronous in nature and there is no guarantee that it  will run in sequence but cypress takes care of it. Promise comes under Rejection,Resolved,Pending 
•	To get the promise get resolved we need to use . then() (Eg. cy.visit(‘’).then() cy.get(‘’).type(‘’)
•	But Cypress is packed internally with that so no need to worry about that 
N:B text() is not a method in cypress it’s a j query method which is supported by Cypress
•	Since Cypress works directly on the browser console.log will print directly on the browser console (in inspect)
•	If methods are not related to cypress it will work in non-sequential order to clear that promise manually we need to use .then (eg.printing normal console.log(‘s’) where as when we handle the promise we will get it as cy.get(‘’).click().then(function(){  console.log(‘s’) })
•	cy.log will print in the test runner where as console.log will print it in the console of the browser
•	Cypress autohandles Pop-ups and Alerts 

How to handles JavaScript Pop-ups/Alerts ?
•	By default Cypress accepts the Pop-ups/Alerts 
•	Cypress have the capability of firing browser event
•	window:alert is the event fired when alert is opened and cypress get access to the alert
How to handle Authentication Pop-ups/Alerts?
•	By default Cypress accepts the Pop-ups/Alerts 
•	Cypress have the capability of firing browser event
•	window:confirm is the event fired when alert is opened and cypress get access to the alert
Install Cypress xpath plugin to support Xpath 
•	In CMD type    npm install -D @cypress/xpath
•	Then add require('@cypress/xpath'); to the support file 

How to perform Mouse hover ?
•	Cypress doesn’t support directly for mouse hover but we can use jquery method for this 
•	show() method in jquery will show all the hidden elements in any button 
•	To invoke this function in cypress we need to use invoke(show) 
N:b show method will display only the immediate child 
However we can forcibly click the hidden element without opening the menu 
Eg. cy.get(‘’).click({force:true})

How to handle Child window?
•	Cypress doesn’t support child window handle we can use .invoke method from jquery is the first method 
•	Eg. cy.get(‘’).invoke(‘remove Attr’,’target’).click()
•	Second method is using another jquery prop() which will get the property value of the attribute and from that we can use cy.visit and the url but not recommended if incase of different domain 
How to handle frames?
•	Install the plugin cypress iframe using command cypress npm install -D cypress-iframe                  in CMD
Add  
•	Add above line in the Cypress frames file 
•	Cy.frameloaded(‘’) should be given first to load the frames in the page if any 
•	Cy.iframe().find(‘’) to let know the cypress to switch to frame page
•	Always use cy.iframe() to switch to iframes.

Test Hooks : 
	before(function(){
// Executed first like opening of the URL i.e executes before all it blocks
})
	after(function(){
//executes last after the test execution like disconnect from database i.e executes after all it blocks
})
	beforeEach(function(){
//executes before each test in the block i.e executes before each it blocks
})
	afterEach(function(){
//executes after each test in the block i.e executes after each it blocks
})
FrameWork Basics:
3 things to be maintained.
1.	Create a class and declare all the page objects and export it (To make a page object available to all the class we need to mention as below 
Eg.   Class LoginPage{
getUserName{
return cy.get()
}
}
export default LoginPage;


2.	In Test import the Page objects using below command   

Use import LoginPage from "../TestHenryPageObjects/LoginPage";
 
3.	Create a Object for that Page as like below and use it
const LoginPage=new Loginpage()


Environmental Variables:
We need to define the environmental variables in cypress.config.json and call it in the page class.
We can run from the terminal as well using cypress run –spec ….—headed ..—browser chrome –
Cypress gives priority to the terminal 

CYPRESS Dashboard CLOUD:
•	We need to login to the cloud and then copy the project id and paste it in the cypress.config.json 
•	And then we need to pass the record key from the terminal after the run command to record and display in dashboard
•	N:B Execution will happen in the local but results will be fetched in the dashboard
•	We can see the logs of everything and have screenshot for failed one and recorded video of test run as well 
•	It even records the performance like how much time it takes to run the test and even which test is flaky(often failure ) 
 
•	We can also pass the file path in package.json in test and pass the command in the terminal like npm test run  (This will look into the config file and run the same 

Retry Logic in Cypress:
•	We can rerun the cypress failed cases just by having the below command in Cypress.config.json and will capture screenshot as well 
 
CI/CD integration : > Can be done with Jenkins or Azure devops 


BDD: Behaviour Data Driven Framework :
•	We need to install Cucumber Preprocess for supporting Cucumber framework using below command 
•	npm install @badeball/cypress-cucumber-preprocessor

	once it is installed we can see the dependencies in package.json
"dependencies": {
    "@badeball/cypress-cucumber-preprocessor": "^15.1.1"
  }

•	Then add the broserify-preprocessor dependency to the dependency which support framework as well 
  "dependencies": {
  "@badeball/cypress-cucumber-preprocessor": "^15.1.1",
    "@cypress/browserify-preprocessor": "latest"
  }

•	we have to add below code to the cypress.config to load the cypress events and call this function inside e2e
async function setupNodeEvents(on, config) {
 // This is required for the preprocessor to be able to generate JSON reports after each run, and more,
  await preprocessor.addCucumberPreprocessorPlugin(on, config);

  on("file:preprocessor", browserify.default(config));

  // Make sure to return the config object as it might have been modified by the plugin.
 return config;
}

•	Install the plugin Cucumber for Visual Studio code from chrome for getting the gherkin keywords automatically














                                         
                                          
