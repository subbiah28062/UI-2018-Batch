06-17-2018

    Interface
        problem:cohesion
    class is similar like object:
        class contist of properties and methods.
        we can create instance of a class

        constructor:
            constructor(x?:number,y?:number){
            this.x=x;
            this.y=y;
            }

            arguments of constructor should be passed on creating an instance.
            to make the arguments optional add ? after the argument.

    Access modifiers:
        public,private and
    method vs function:
        function getX(abc){};
            to call a function class.getX(10);
        method get X(abc){};
            to call a method class.X = 10;
06-18-2018

    modules:
        used to export class, so that all program can access it
        to export just write export in the file you want to export
        import { className } from 'fileName'
    component:
        create a component//create component  in src folder
        register it in a module//register in app module
        add an element in html markup
    
    creating a module using cli:
        ng g c name//cmd command
        //module consist of html css and ts files and it get automatically updated in app.module 
    directives:
        we use directives to manipulate DOM elements and remove or change a dom element
        //` is used if dom is changing according to data.
        `
        <h2>{{"Title:" + getTitle()}}</h2>
        <ul>
            <li *ngFor="let course of courses">
                {{course}}
            </li>
        </ul>
        `

    services:

    //logic for calling an http service
        //http endpoints make testing hard.
    We define a seperate class called service and there we add this code to call http service and we reuse them.
    //using EX:let service = new coursesService; //couples the service to compenent which makes unit testing hard. sowe we pass them on constructor parameter EX: constructor(service: coursesService);

    //This is called dependancy injection; providing dependancy of a class into constructor.
    //In second ex component is dependant upon service, so you must add class in courses.service as provider in app.module.ts

    //We might have 100 components in a app so instead of creating 100 instance of service, we create one instance and angular provide it to all. this is called singleton pattern. 
    
    <!-- single instance of given pattern in the memory  -->

    //Ctrl+l to clear cmd
    //ctrl+p for search bar
    //ctrl+tab to navigate recent

    DOM vs HTML:
        dom is a model of object that represents the structutre of a document.tree of objects in memeory
        html is a markup language we use to represent dom in text 

         two ways to give input to html thorugh angular 1)<img [src]="image" /> 2)<h2>{{"Title:" + getTitle()}}</h2>
    
    class binding:
        binding a class to a tag with a condition that is writen in Type script angular. if this happens add the class, else dont add the class.
            [class.active]="isActive"//write this in attr of html tag.//instead of active change your class
            isActive=true or false;// write this into angular class.
    style binding:
        [style.backgroundColor]="isActive ? blue : green";

    Event binding:
        (click)="onsave($event)"
        //$event same as event in js
        onsave($event){
            console.log("button was clicked",$event);
        }
        (keyup.enter)="onKeyUp($event)" 

        to get value from input field
            1)  (keyup.enter)="onKeyUp($event)"

                onKeyUp($events){
                    console.log($event.target.value)
                }
            2)  //use template variable to reduce your code.
                <input #email class="btn btn-primary" (keyup.enter)="onSave(email.value)">
                onSave(email1){
                    console.log("button clicked ", email1);
                }
            3)  //using one way binding://property binding
                <input [value]="email" class="btn btn-primary" (keyup.enter)="onSave()" />
                email="me@gmail.com";
                onSave(){
                    console.log("button clicked ", this.email);
                }
            4)  //twoway binding. component to view and view to component.//property binding
                <input [value]="email" (keyup.enter)="email = $event.target.value; onSave()" />
                email="me@gmail.com";
                onSave(){
                    console.log("button clicked ", this.email);
                }
            5)  //simple 2way binding.bannana in a box.
                    <input [(ngModel)]="email" class="btn btn-primary" (keyup.enter)="onSave()" />
                    email="me@gmail.com";
                    onSave(){
                        console.log("button clicked ", this.email);
                    }
                    //To use this binding you must add FormsModule to imports in app.module.ts

    Pipes:
        To create custom pipe.
            ng generate pipe name //name with no . or pipe ex ng generate pipe summary. creates summary.pipe.ts
                EX:
                    <h1>{{ text | summary}}</h1>
                    define text in component class. generate summary pipe in app folder using cmd and then write below logic in pipe.
                        transform(value: string, args?: any): any {
                            if (!value)
                                return null;
                            return value.substr(0,50) + '...';
                        }
                EX://sending arg value:
                    <h1>{{ text | summary:'20'}}</h1>
                    define text in component class. generate summary pipe in app folder using cmd and then write below logic in pipe.
                        transform(value: string, args?: any): any {
                            if (!value)
                                return null;
                            let actValue = (args) ? args : 50;
                            return value.substr(0,actValue) + '...';
                        }

                    //on multiple value of args use : and '':''

    Assignment:
        simple replacement of codes:
            old code:
                class = "glyphicon" 
                [class.glyphicon-star]="isActive"
                [class.glyphicon-star-empty]="!isActive"
            Simple code repalcement:
                class="glyphicon glyphicon-star{{(isActive) ? null : '-empty'}}"
    
    Simple problems to note:

        inputText : String;
        isActive : Boolean = false; //varialbe: datatype = "value";/syntax
    property binding:[],Event binding:()

    custom component:
        properties binding:[] //this passes data from app.component to your component
        event binding:() //this passes data from your component to app.component i.e parent folder
        for both input and output:[()] this is used to receive and send value through same varibl

06-21-2018

    HTML:
        template: can be written in template in Typescript or
        html: can be written in seperate html tag
    
    main.bundle.js: all the files will be compiled into this file and this file one file only will be used by browser to run the page.

    styles:
        css file
        style:[``] in TypeScript file
        or in html file
    Shadow DOM:
        styles only apply to the element
            var el = document.queryselector("ul");
            var root = el.createShodowRoot();
            root.inerHTML = `<styles>
                                h1{
                                    color:red;
                                }
                            </styles>
                            <h1>
                                hello   
                            </h1>`
            The h1 style will only be applied to this h1 and not to any other h1 in the file.

    encapsulation: 
        viewEncapsulation: 
            emulated-creates unique tag to styles and to html element to link them
            native- places styles in inline
            none- styles set to whole html
            //emulated and native or type of shadow DOM.
    
    div.panel.panel-default-> on enter creates below
    <div class="panel panel-default"></div>

    div.panel-default>div.panel-heading+div.panel-body-> on enter creates
    <div>
        <div></div>
        <div></div>
    </div>//creates this with class names

    ng-content:
    //used to read the innertest of a div
    //using ng-container we can hide the div and just pass the innertext
        component:
        <div class="panel panel-default">
            <div class="panel-heading">
                <ng-content select=".heading"></ng-content>
            </div>
            <div class="panel-body">
                <ng-content select=".body"></ng-content>
            </div>
        </div>

        on App:
        <bootstrap-panel>
            <ng-container class="heading">heading</ng-container>
            <ng-container class="body">
               <h1>body topic</h1>
                 <p>some ransdom text</p>
            </ng-container>
        </bootstrap-panel>

    Directives:
        structural: modifies stucture of the DOM //not sure 
        attribute: modifies the attr of the DOM //not sure

        *ngIF,*ngFor,etc are inbuilt directives.//we can even create our own directives.

    Go through all those below from internet or from your hand notes:
        *ngIf://use <ng-tempelate> if select if or else
        
        [Hidden]="": on true hides content ofthe element // use ngIf because it hides the element makes more effecient.
        
        ngSwitchCase:
        <div [ngSwitch]="variable"
            <div *ngSwitchCase = "'variable"
            <div *ngSwitchCase = "'variable"
            <div *ngSwitchDefault>otherwise</div>
        </div>

        ngFor:
        <div *ngFor ="let course of courses: index as i">{{i}}-{{course.name}}</div>
            it has index,first,last,even and odd attributes.
        
        ngFor and trackby:
            Html:
                <button (click)="onClickEvent()">click me</button>
                <button (click)="onClickEventNew()">click me new</button>
                <ul>
                <li *ngFor="let course of courses; trackBy: trackId">
                    {{course.name}}
                </li>  
                </ul>
            Ts:
                courses;
                onClickEvent(){
                    this.courses = [
                    { id : 1 , name : 'course1' },
                    { id : 2 , name : 'course2' },
                    { id : 3 , name : 'course3' }]
                }
                onClickEventNew(){
                    this.courses = [
                    { id : 1 , name : 'course1' },
                    { id : 2 , name : 'course2' },
                    { id : 3 , name : 'course3' },
                    { id : 4 , name : 'course4' }
                    ]
                }
                trackId(index , course){
                    console.log('course ' + course);
                    console.log('course.id ' + course.id);
                    console.log('index ' + index);
                    return course ? index : undefined;
                }

        [ngClass]="{}" and [ngStyle]="{}"

    Template driven form:
        
        ngForm//for name form tag it captures submit event
        //ngForm contist of (ngSubmit)=anyfunction(att1,attr2,...). it send the output of attributes to the TS

        ngModelGroup//used to club two or more ngModel. like we might need 4fields for address like street city state zipcode . In such situations ngModelGroup is used to group two or more ngModel

        ngModel// used to get the values and various attributes of the form inputs
        //method to bing ng tags.//ex: ngModel ang #name = "ngModel"//instead of name replace whatever you want

        //For all above ex: ngModel #defineAName="ngModel" name="defineAName" //on input tag
        //on any other tag ngModel="defineAName" #defineAName="ngModel"

        //these ng attributes are used to get the events and values of form inputs, like input, textarea, checkbox, dropdown box, etc.

        styling form:
            USE form-group for parent of input and form-control to the input for responsive styling.
            <div class="form-group">
                <input class="form-control" />
            </div>

        Input field attr:
            minlength,maxlength,pattern(what you should write in input to make it valid). if pattern="subbiah", input will be valid only on typing subbiah required gives error if field is empty.
            pattern="^[a-z0-9@.A-Z]{8,30}"//pattern ex. this accepts a to z, A to Z, 0 to 9, @ and . 

        disabling submit button on invalid:
            <button class="btn btn-primary" [disabled]="f.invalid">submit</button>
            //f is ngForm's name..

        //all ng output will be in json so to print it in html should pharse it. for that we simply use   <p>{{f.value | json}}</p> //p optional

        check-box code:
            <div *ngFor="let course of contactMethod" class="radio">
                <label for="radioButton">
                <input ngModel name="radioButton" type="radio" [value]="course.id">{{course.name}}
                </label>
            </div>
        
        dropdown box:
            <div class="form-group">
                <label for="contactMethod"></label>
                <select ngModel name="contactMethod" id="contactMethod" class="form-control">
                <option value=""></option>
                <option *ngFor="let course of contactMethod" [value]="course.id">{{course.name}}</option>
                </select>
            </div>

        checkbox:
            <div class="checkbox ">
                <label for="isSubscribed">
                <input type="checkbox" ngModel #isSubscribed="ngModel" name="isSubscribed"> do you want to subscribe
                </label>
            </div>

        teaxtarea tag is used to craete comment box

    Reactive form:  
        In reactive form we add validations dynamically in ts not in html.
        on HTML:
            [formGroup]="form" on top form div.
            formGroupName="name" on child formGroups.
            formControlName="name" on child formControls

            to get value from formgroup or any this.form.get('account.username')

        ON TS :
            normal code:
                form = new FormGroup({
                    account: new FormGroup({
                    username: new FormControl('' , [
                        Validators.required,
                        Validators.minLength(8),
                        usernameValidator.cannotContainSpace,
                    ],
                    usernameValidator.shouldBeUnique
                    ),
                    password: new FormControl('' , Validators.required)
                    }),
                    topics: new FormArray([])
                });

            same code with form builder:
                 form; 
                    constructor(formComponent: FormBuilder){
                        this.form = formComponent.group({
                        account: formComponent.group({
                            username: ['',[Validators.required, Validators.minLength(8), usernameValidator.cannotContainSpace],
                            usernameValidator.shouldBeUnique],
                            password: ['' , Validators.required]
                        }),
                        topics: formComponent.array([])
                        })
                    }

            Adding form control to form array onclick:
                ts:
                    topicsOnClick(topic: HTMLInputElement){
                        this.topics.push(new FormControl(topic.value));
                        console.log(this.topics);
                    }
                    removeTopic(topic: FormControl){
                        let index = this.topics.controls.indexOf(topic);
                        this.topics.removeAt(index);
                    }

                    get topics(){
                        return this.form.get('topics') as FormArray;
                    }
                html:
                    <div class="form-group">
                        <label for="password">course list</label>
                        <input type="text" name="password" 
                        class="form-control" (keyup.enter)="topicsOnClick(topic)" #topic>
                        <ul class="list-group">
                            <li class="list-group-item" *ngFor="let topic of topics.value"
                            (click)="removeTopic(topic)">{{ topic }}</li>
                        </ul>
                    </div>
    //interpolation {{}}

    //dont forget to give all validators in array. async in seperate array and sync in seperate array 

    common mistakes made:
        first div should form div with [formGroup]="name"
        to access errors dont miss errors after the name of formcontrol or formgroup
        write validators and directives in seperate folder so it can be accessed later

    Json:
        import { Http } from '@angular/http';
        posts: any[];

        Initializing:
            constructor(private http: Http) { 
                http.get(this.url)
                .subscribe(response =>{
                    this.posts = response.json();
                });
            }

        creating a json object:
            createpost(input: HTMLInputElement){
                let post = {title : input.value};
                input.value="";
                this.http.post(this.url, JSON.stringify(post))
                .subscribe(response =>{
                    post['id'] = response.json().id;
                    this.posts.splice(0,0,post);
                })
            }
        
        Updating a post
            updatePost(post){
                this.http.patch(this.url + '/' + post.id, JSON.stringify({isRead: true}))
                .subscribe(response =>{
                    console.log(response.json());
                })
            }
        deleting a post:
            deletePost(post){
                this.http.delete(this.url + '/' + post.id)
                .subscribe(response=>{
                let index = this.posts.indexOf(post);
                this.posts.splice(index,1);
                })
            }

    Life cycle hook:
        onInit
        onChange
        doCheck
        afterContentInit
        

                