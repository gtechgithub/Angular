Angular installation 

1. download the latest version og angular and place it as follows

C:\Softwares\node-v8.9.1-win-x64

2.  edit the user variables as follows

C:\Softwares\node-v8.9.1-win-x64\ in the PATH


PATH
----
C:\Softwares\node-v8.9.1-win-x64\;C:\Softwares\apache-maven-3.1.1\bin\;C:\Users\gopalakrishnanc\AppData\Roaming\npm;C:\Users\gopalakrishnanc\AppData\Roaming\npm\node_modules\@angular\cli\bin;

3. now place the .npmrc in the C:\Users\gopalakrishnanc

registry=https://registry.npmjs.org/
proxy=http://gopalakrishnanc:Qiyenpe0ple%23@10.5.1.26:8080/
https-proxy=http://gopalakrishnanc:Qiyenpe0ple%23@10.5.1.26:8080/
registry=https://registry.npmjs.org/
strict-ssl=false

 
4. now install the CLI

CLI
-----

The Angular CLI is a command-line interface tool that you use to initialize, develop, scaffold, and maintain Angular applications. You can use the tool directly in a command shell, 


npm install -g @angular/cli

5. finally add the path in user environment variables

C:\Users\gopalakrishnanc\AppData\Roaming\npm;C:\Users\gopalakrishnanc\AppData\Roaming\npm\node_modules\@angular\cli\bin;

PATH
----
C:\Softwares\node-v8.9.1-win-x64\;C:\Softwares\apache-maven-3.1.1\bin\;C:\Users\gopalakrishnanc\AppData\Roaming\npm;C:\Users\gopalakrishnanc\AppData\Roaming\npm\node_modules\@angular\cli\bin;

6) now run ng to display the version

C:\Users\gopalakrishnanc>ng version 

7) to create a project 

C:\Users\gopalakrishnanc>ng new Angular

8) compile the project
   
   
C:\Users\gopalakrishnanc\Angular>ng serve

 ?wdm?: Compiled successfully.
 
9) access the url

    http://localhost:4200/  

10) to create a component 

Let us now run the command to create the component.

ng g component new-cmp

or 

npm run ng g component verification-level1 --dry-run

or 


PS C:\Users\gopalakrishnanc\git\iniserve4.0\web> npm run ng g component others\para-admin\verification-related\verification-level

C:\projectA4\Angular 4-app>ng g component new-cmp

11) configured proxy.conf.json
    as follows     "start": "ng serve --proxy-config proxy.conf.json",
	the run with npm start
	
12) install new modules

npm install --save ng2-opd-popup


13) to check the installed packages in angular 

refer to package.json


14) create new component 
also solution for below error

C:\Users\gopalakrishnanc\demo-app-client>ng generate component tmac-simulator
More than one module matches. Use skip-import option to skip importing the component into the closest module.


ng generate service pokemon --module=app


14) install typescript version

npm install -E typescript@3.2.0


15) to install hammerjs

npm install --save hammerjs


15.1) generate the npm dist for building it
 
npm run build


16) 
npm install commands

npm install --save @angular/material
npm install --save-dev @angular/material
 
package.json
------------

  "dependencies": {                            ---> when --save is given it will be stored below
    "@angular/animations": "^7.2.2",
    "@angular/cdk": "^7.3.0",
	
	 "devDependencies": {                       ---> when --save-dev is given it will be stored below
    "@angular-devkit/build-angular": "~0.12.0",
    "@angular/cli": "~7.2.0",
    "@angular/compiler-cli": 
	
------------------------------------------------------------------------------------------------------------------------------------------------	
17)

how to install and  material module

refer to the file 

------------------------------------------------------------------------------------------------------------------------------------------------
18)
problem:
 Can't bind to 'formGroup' since it isn't a known property of 'mat-dialog-content'.

 solution:
 
 
RC5 FIX

You need to import { REACTIVE_FORM_DIRECTIVES } from '@angular/forms' in your controller and add it to directives in @Component. That will fix the problem.

After you fix that, you will probably get another error because you didn't add formControlName="name" to your input in form.

 RC6/RC7/Final release FIX

To fix this error, you just need to import ReactiveFormsModule from @angular/forms in your module. Here's the example of a basic module with ReactiveFormsModule import:


 https://stackoverflow.com/questions/39152071/cant-bind-to-formgroup-since-it-isnt-a-known-property-of-form

------------------------------------------------------------------------------------------------------------------------------------------------


20 ) 
problem:

'mat-form-field' is not a known element in the html used

Solution:

		MatFormFieldModule need to be added to the module file 

		import {MatDialogModule , MatFormFieldModule} from "@angular/material";

		 @NgModule({
			imports:
			[MatButtonModule,
				MatCardModule,
				MatDialogModule,
				MatFormFieldModule
			],
			exports:[MatButtonModule,
				MatCardModule,
				MatDialogModule,
				MatFormFieldModule
			]
		  })

		  export class MaterialModule {}
		  
------------------------------------------------------------------------------------------------------------------------------------------------		  
21.

Problem:

Uncaught Error: Unexpected directive 'MatFormField' imported by the module 'MaterialModule'. Please add a @NgModule annotation.


Solution:

	https://stackoverflow.com/questions/43603515/uncaught-error-unexpected-directive-mycombobox-imported-by-the-module-appmod

	This error frequently comes up when we are not importing, providing, or declaring the angular modules, services, components properly.

	Make sure that we should only

	import modules and not the components or services
	declare components and not the modules or services.
	provide services and not components or modules.
	
	Original Answer :
	
	import {MatInputModule} from '@angular/material';

	
	You don't have to really import MatFormField in your App Module. Since you have already exported it in MatInputModule. So I would suggest you to remove MatFormField from your imports array in AppModule. Importing CoreModule will give you MatInputModule component within AppModule.

------------------------------------------------------------------------------------------------------------------------------------------------	
22:
problem:

NullInjectorError: No provider for MatDialogRef!

Solution:

Solved the problem by importing MatDialogModule, MatDialog and MatDialogRef from @angular/material/dialog instead of @angular/material
then


import {MatDialogModule ,MatDialogRef} from "@angular/material/dialog";

 @NgModule({
    imports:
    [MatButtonModule,
        MatCardModule,
        MatDialogModule,
        MatFormFieldModule,
        MatInputModule,
        BrowserAnimationsModule
    ],
    exports:[MatButtonModule,
        MatCardModule,
        MatDialogModule,
        MatFormFieldModule,
        MatInputModule,
        BrowserAnimationsModule
    ],
    providers: [{provide: MatDialogRef, useValue: {}}, {
        provide: MAT_DIALOG_DATA,
        useValue: {} // Add any data you wish to test if it is passed/used correctly
      } ],

  })
 
 in the component
 ----------------
 
 import  { MatDialogRef } from "@angular/material/dialog";

   constructor(

   constructor(
    private fb: FormBuilder,
    private dialogRef: MatDialogRef<NewCmpComponent>,

    @Inject(MAT_DIALOG_DATA) data) {

      this.description = data.description;
     }

     ngOnInit() {
    }
  
    save() {
      this.dialogRef.close(this.form.value);
  }

  close() {
      this.dialogRef.close();
  }
------------------------------------------------------------------------------------------------------------------------------------------------

23:
problem:
mat-form-field must contain a MatFormFieldControl


solution:

https://github.com/angular/material2/issues/7898

You have to add to app.module.ts:

import {MatInputModule} from '@angular/material';
@NgModule({
  imports: [
  ...
    MatInputModule
  ...
]

------------------------------------------------------------------------------------------------------------------------------------------------
24:

problem:

ERROR Error: Found the synthetic property @transitionMessages. Please include either "BrowserAnimationsModule" or "NoopAnimationsModule" in your application.

solution:

https://stackoverflow.com/questions/45730753/found-the-synthetic-property-enteranimation-please-include-either-browseranim

// animation module
        import { BrowserAnimationsModule } from '@angular/platform-browser/animations'; 
    ...
@NgModule({
    imports: [...
        BrowserAnimationsModule,
        ...
      ],
	  
------------------------------------------------------------------------------------------------------------------------------------------------

25:

using material dialog refer the document.



26:

What is the difference between parentheses, brackets and asterisks in Angular


Solution:

All details can be found here: https://angular.io/docs/ts/latest/guide/template-syntax.html

directiveName - is the short hand form for structural directives where the long form can only be applied to <template> tags. The short form implicitely wraps the element where it's applied in a <template>.

[prop]="value" is for object binding to properties (@Input() of an Angular component or directive or a property of a DOM element).
There are special forms:

[class.className] binds to a css class to enable/disable it
[style.stylePropertyName] binds to a style property
[style.stylePropertyName.px] binds to a style property with a preset unit
[attr.attrName] binds a value to an attribute (visible in the DOM, while properties are not visible)
[role.roleName] binds to the ARIA role attribute (not yet available)
prop="{{value}}" binds a value to a property. The value is stringified (aka interpolation)

(event)="expr" binds an event handler to an @Output() or DOM event

#var or #var has different functions depending on the context

In an *ngFor="#x in y;#i=index" scope variables for the iteration are created
(In beta.17 this is changed to *ngFor="let x in y; let i=index"`)
On a DOM element <div #mydiv> a reference to the element
On an Angular component a reference to the component
On an element that is an Angular component or has an Angular directive where exportAs:"ngForm" is defined, #myVar="ngForm" creates a reference to this component or directive.


------------------------------------------------------------------------------------------------------------------------------------------------

27.
how to install boot strap so that some tab and fonts will be working..


Solution:

npm install --save bootstrap@4.0.0-beta.2 font-awesome

place this entries in src/styles.css

@import "~bootstrap/dist/css/bootstrap.min.css";
@import "~font-awesome/css/font-awesome.css";



------------------------------------------------------------------------------------------------------------------------------------------------

28. if you get this error , try again 


C:\Users\gopalakrishnanc\Angular>npm install --save bootstrap@3.3.1 font-awesome

ode_modules\'',
npm ERR!   errno: -4048,
npm ERR!   code: 'EPERM',
npm ERR!   syscall: 'lstat',
npm ERR!   path: 'C:\\Users\\gopalakrishnanc\\Angular\\node_modules\\fsevents\\node_modules' }
npm ERR!
npm ERR! Please try running this command again as root/Administrator.

npm ERR! A complete log of this run can be found in:
npm ERR!     C:\Users\gopalakrishnanc\AppData\Roaming\npm-cache\_logs\2019-02-03T14_57_12_070Z-debug.log

------------------------------------------------------------------------------------------------------------------------------------------------


29

Clone an Array :

const myClonedArray  = Object.assign([], myArray);
Clone an object :

const myClonedObject = Object.assign({}, myObject);


------------------------------------------------------------------------------------------------------------------------------------------------
30

problem:
how to print object in angular

     console.log("currentrow:" + JSON.stringify(currentRow));



------------------------------------------------------------------------------------------------------------------------------------------------

31
problem:
ERROR TypeError: Cannot read property 'invalid' of undefined angular 4



solution:

Your control reference in the view is bk_name. Replace bankname with bk_name.

<div *ngIf="bk_name.invalid && (bk_name.dirty || bk_name.touched)" class="alert alert-danger">
<div *ngIf="bk_name.errors.required">Name is required.</div>


https://stackoverflow.com/questions/46510180/error-typeerror-cannot-read-property-invalid-of-undefined-angular-4	

------------------------------------------------------------------------------------------------------------------------------------------------


32

searching in visual studio code

search

replace

files to include

files to exclude
.js, .map, .css, .xlf, .spec.ts

------------------------------------------------------------------------------------------------------------------------------------------------

33.

What's alternative to angular.copy in Angular
With AngularJS, I can use angular.copy(object)

For Angular, you can do it like this:

Install lodash with yarn add lodash or npm install lodash.

In your component, import cloneDeep and use it:

import * as cloneDeep from 'lodash/cloneDeep';
...
clonedObject = cloneDeep(originalObject);


or 

this.cloneOrders= [...this.orders];


https://stackoverflow.com/questions/34688517/whats-alternative-to-angular-copy-in-angular

------------------------------------------------------------------------------------------------------------------------------------------------

34.


lets say Angular does not support the version of Node installed in local machine and follow the below instruction.


I think the last version compatible with node 6.9.x is @angular/cli@6.0.8 Check this for all versions

npm uninstall -g @angular/cli
npm cache clean --force
npm install -g @angular/cli@6.0.8

https://stackoverflow.com/questions/51628408/how-to-install-angular-cli-for-node\

------------------------------------------------------------------------------------------------------------------------------------------------




Learning:
---------

https://github.com/hamedbaatour/minimus/tree/master/src/app

https://github.com/duluca/lemon-mart/tree/master/src/app/user

https://github.com/avatsaev/angular-contacts-app-example

https://github.com/DanWahlin/angular-architecture

