pipes:
    we call it after a input variable in html tag to customize it.
    we call pipe with name given in @pipe in the pipe file.
    pipes send the text value as argument so we must recieve them in transform function as a parameter.transform(value:string){}.
    to send a value to pipe from html use :.ex:     <h1>{{ text | summary:'20'}}</h1>

passing parameter:
    use [] when passing paramet from app.component.html to the original component.
    
Trackby:
    We can help Angular to track which items added or removed by providing a trackBy function
     trackBy: trackId Add this is html ngFor. ex:  <li *ngFor="let course of courses; trackBy: trackId">
    Then create a function for trackbyId. ex:  
        trackId(index , course){
            return course ? index : undefined;
        }

To display text content inside a custom component.
    Ex in app.component.html 
        <zippy title="Heading"> <div>content inside the heading</div> </zippy>
    now to display the innner content we use <ng-content></ng-content>
    ex:
        <div class="body panel-body"
            *ngIf = "isActive">
            <ng-content></ng-content>
        </div>

Template form:
    ngForm //has ngSubmit
        ngModelGroup // group of models
            ngModel
            ngModel
    // ngForm #randomname=ngForm // name="randomName" on input tag name is IMP

Reactive form:
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

    on html:
        formGroup
            formGroupName
                formControlName
                formControlName
            formArrayName
    To call a reactive form in a html:
        this.form.get('account.username');

    //no need of #randomname="formGroup" as it has been already binded using reactive forms method in constructor

    To add validator to formgroup:
        this.passwordForm = FormComponent.group({//formcontrol should be written inside this//},
        { validator: ContainSpaceDirective.invalidPassword})

Custom Validation error:
        static cannotContainSpace(control: AbstractControl) : ValidationErrors | null{
            if((control.value as string).indexOf(' ') >= 0){
                return {cannotContainSpace: true}
            }
            else{
                return null;
            }
        }

        //onusing async function proimise must be used instead of return:
            //control is the innertext of the div, we will get it automatically.
            static shouldBeUnique( control: AbstractControl): Promise<ValidationErrors | null > {
                return new Promise((resolve, reject) => {
                    setTimeout(() => {
                        if(usernameValidator.emailCheck(control.value)){
                            resolve (null);
                        }
                        else{
                            resolve ({'shouldBeUnique' : true});
                        }
                    }, 2000);
                });
            }
    
routerMOdule:
    constructor(private router: Router,private route: ActivatedRoute) { }

    //call above code in all ts for router module

    [routerLink]="['/followers', follower.id, follower.login] on html 

    submit()
    {
        this.router.navigate(['/followers'],{queryParams:{ page: 1, order:'newest'}});
    }
    //same as first one but in .ts file

    To get the parameters of the link:
         constructor(private route: ActivatedRoute, private router: Router) { }

            ngOnInit() {
                // let id = this.route.snapshot.paramMap.get('id');
                // console.log(id);
                this.route.paramMap
                .subscribe(params =>{
                    let id = +params.get('id');
                    let username = params.get('username');
                    console.log(username);
                    console.log(id);
                })
            }
        //for queryParameters use queryPramMap

to find token not expired:
      isLoggedIn() { 
            return tokenNotExpired();
        }

Router-navigate
route-get url parameters

to decode token:
    get currentUser(){
        let token = localStorage.getItem('token');
        if (!token) 
        return null;
        let jwtHelper = new JwtHelper();
        return jwtHelper.decodeToken(token);
    }


tslint:
    cnt+shift+p;
        tslint:fix all autofixable errors

spec empty file:
    describe('VoteComponent', () => {
        it('', () => {
        });

        it('', () => {
        });
    });


installing and importing:
    import { Observable } from 'rxjs/Observable';
    import 'rxjs/add/observable/from';

    to create spec for already created components:
        npm install -g angular-spec-generator
        angular-spec-generator 'src/app'

    install bootstrap:
        npm install bootstrap
        //import below code in global styles:
        @import "~bootstrap/dist/css/bootstrap.css";