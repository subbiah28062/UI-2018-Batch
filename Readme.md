06-04-2018
        
    -JS is a single thread programming language.
    -JS is a dynamic 
        no int no float. just variable with var
    prototypical 
        In javascript, every object has a secret link to the object which created it, forming a chain.
        When an object is asked for a property that it does not have, its parent object will be asked...
         continually up the chain until the property is found or until the root object is reached.
    functional language.
    
    -object:
        literal {}
            var car = {type:"Fiat", model:"500", color:"white"};
        constructor 
            To create new instance of object of a object
            function person(a,b){
                this.a=a;//this point to person on using new constructor
                this.b=b;
            }
            var name = new person(attr1,attr2);
            new is the constructor and it is a function by itself;
        create(.create study by yourself)
    -function:
        named:
            function name(a){this.a=a}
            var name1 = new function(a){this.a=a}
        anonyms function:
            IIFE
                (function(i){
                })(i);
                
        //method and function should be called with();
        // you can call a function and a method but you can call a object; name.a=error;
        //method is diffrent;object is diffrent and object is diffrent;
    -operators:
        ==(coeration i.e. conversion and comparison, which decreases performance)
        ===(use === for increased performance)
    -prototype:
        Prototype is used to inherit method and properties of object.
        
        Sometimes you want to add new properties to all existing objects of a given type.
        
        Sometimes you want to add new properties to an object constructor.
                
        Inheritance(prototypical chain)
            Multi level inheritance
                //inheriting properties of college object into year.
                function College(name,location){
                    this.name = name;
                    this.location = location;
                }
                function Year(period){
                    this.period = period;
                }
                Year.prototype=new College("TAMUK","Kingsville");
                var college1 = new Year(1989);
                console.log(college1);
                
                //inheriting new property to an object
                function a(b){
                    this.b=b;
                }
                var c = new a(123);
                a.prototype.d = function(){
                    return this.b
                }
                console.log(c.d());
                
            one level multiple parents
        Extending a class			
            //Create a empty function and use prototype to add parameters, because evry instance creates
            a reference for every properties which wastes memory.
    
    -We get server ip from dns using the domain name.
    -single thread programming??
    -DOM lookup- quering a DOM using query selectors(by id, class, tag etc,)
    
    //undefined: var z; console.log(z);
    //error:console.log(z);
    //Without new constructor this statement wont work. This will point windows.
        
06-05-2018
        
    -virtual DOM
        There’s no big difference between the “regular” DOM and the virtual DOM. This is why the JSX 
        parts of the React code can look almost like pure HTML
    -shadow DOM
    http://reactkungfu.com/2015/10/the-difference-between-virtual-dom-and-dom/
    //dom link
    
    //DOM is expensive(perfomance), so save the DOM when u access once. 
    ex: var a = document.GetElementById("name");
    a.style.color="red";
    b= a.value;
    
    //Create a empty function and use prototype to add parameters, because every instance creates a 
    reference for every properties which wastes memory.
    
    -Event:
        Event type
        Element(HTML elements)
        Event Handler(on Event occurrence it will trigger Event Handler)
            getelementbyid
            get elementbytagname
        Binding(binding event and html elemt)//-This gives current target element
            onclick;
            onchange;etc
    
        Binding inline: 
            using events(link onclick) on html. Ex: <button onclick=”start()”/>
            //We don’t use inline for both styles and JS.
        Traditional way:
            Var btnEleObj = document.GetElementById(“btn”)
            btnEleObj.OnClick = showname;//Don’t add () #IMP
            //on using 
            //showname =event handler
            function showname(){
            console.log(“test console”)
            }
        TEvent Listeners:
            .addEventListener("click",function name,false)
            
        Event bubbling:
            e.stoppropagation()
                var googleBtn = document.getElementById("googleId");
                        googleBtn.addEventListener("click",showname,false);
                        function showname(e){
                            e.preventDefault();
                            console.log("event prevented");
                        }
                        var total1 = document.getElementById("total");
                        total1.onclick= showname2;
                        function showname2(){
                            total1.style.display= "none";
                        }
                        var un_list = document.getElementById("unordered_list");
                        un_list.addEventListener("click",showname1,false);
                        function showname1(e) {
                            e.stopPropagation();
                            console.log(e.target.innerText);
                        }
                        //this does not work with inline events;
            **e.stop.immediatePropagation()**
        
        //Onclick has an drawback. On calling it twice it overwrites the first onclick.
         To overcome that we use btnEleObj.addEventListener(“click”,”showname”,false)
        
        e.target to acces events html paramenters.
    
    -Script:
        //Having script in body is lazy loading.
        //script is preferred to write in body.
        //quirks mode-
        
        
    -PreventDefault:
        <script>
                var googleBtn = document.getElementById("googleId");
                googleBtn.addEventListener("click",showname,false);
                function showname(e){
                    e.preventDefault();
                    console.log("event prevented");
                }
        </script>
            
    -querySelectorAll:
        var btn = document.querySelectorAll("li");
        
    **Current Event vs Target Event**
    **bubbling,delegation,capturing**
    //script in body: lazy loading is good
    
06-06-2018

    CALL, APPLY and Bind:
        call -coma seperated arg ex: .call(this, age,location)
            The call method is used to call a method or functoin on behalf of another object. 
            It allows you to change the THIS object of a function from the original context to the
            new object specified by thisObj.
            1)Using call to chain constructors for an object.
                function Product(name, price) {
                  this.name = name;
                  this.price = price;
                }
                
                function Food(name, price) {
                  Product.call(this, name, price);
                  this.category = 'food';
                }
                
                function Toy(name, price) {
                  Product.call(this, name, price);
                  this.category = 'toy';
                }
                
                var cheese = new Food('feta', 5);
                var fun = new Toy('robot', 40);
            2)Using call to invoke an anonymous function//using iife
                var animals = [
                  { species: 'Lion', name: 'King' },
                  { species: 'Whale', name: 'Fail' }
                ];
                
                for (var i = 0; i < animals.length; i++) {
                  (function(i) {
                    this.print = function() {
                      console.log('#' + i + ' ' + this.species
                                  + ': ' + this.name);
                    }
                    this.print();
                  }).call(animals[i], i);
                }
            3)Using call to invoke a function and specifying the context for 'this'
                function greet() {
                  var reply = [this.animal, 'typically sleep between', this.sleepDuration].join(' ');
                  console.log(reply);
                }
                
                var obj = {
                  animal: 'cats', sleepDuration: '12 and 16 hours'
                };
                
                greet.call(obj);
            4)Using call to invoke a function and without specifying the first argument
        apply -array ex:
            1)Using apply to append an array to another
                var array = ['a', 'b'];
                var elements = [0, 1, 2];
                var array = array.concat(elements);//both gives same result
                array.push.apply(array, elements);
                console.info(array);
            2)using apply to chain constructors
            //same as call but arrguments sent in array
            
        bind- creates a function copy which can be called later
            
            var module = {
                x:10,
                xyz : function(){
                    return this.x;
                }
            }
            var unbond = module.xyz;
            var bond = unbond.bind(module);
    Call back
        function, sending a function as an parameter to another function
        
        function greeting(name) {
          alert('Hello ' + name);
        }
        
        function processUserInput(callback) {
          var name = prompt('Please enter your name.');
          callback(name);
        }
        
        processUserInput(greeting);
        
    json-javascript object notation;
    //sync, await-read by userself;Object properties-study;


06-07-2018

    Form element has an action attribute
        <form action = "users/add">
            <input>
            <button></button>
        </form>
    Ajax(Asynchronous JavaScript and XML)
        used for client server communication; its not a technology its a way of js to 
        -use object XMLHttpRequest
        **End point url**- url where **payload** is going to be sent.
        pay load-json data sent from client side is called as pay load.
        CRUD-creating,reading,updating and deleting a data
        Method type:(To interact with server)
            GET-get data from server
            POST-to send data to server
            PUT-to update the posted data. To access the server we should have the id(id specified 
            to each user) 
            DELETE- delete data from server.
    Ajax steps:  
        1)create an instance of XMLHttpRequest
        2)open connection between client and server
        3)send request 
        4)RECEIVE response
            readstate
                0-no
                1
                2
                3
                4
            status(HTTP Status codes)**study it**
                -100's
                -200's
                -300's
                -400's
    Ajax jquery:
         $.get("https://jsonplaceholder.typicode.com/posts", function(data, status){
                            data.map( items =>{
                                $('#content').append("<li>" + items.body + "</li>");
              })
          });
    Attributes:
        Button not to submit use attribute type="button" orelse it will submit the form.
        Method attribute:
    -restful services made by backend 
    -API-
        REQUEST HEADER
        RESPONSE HEADER
    
    var getDisplayId = document.getElementById("displayId");
    //creating select element
    var dropDown = document.createElement("select");
    dropDown.id = "selectList";
    //appending slect to main div
    getDisplayId.append(dropDown);
    
06-08-2018

    **Big O notation**
        https://medium.com/cesars-tech-insights/big-o-notation-javascript-25c79f50b19b
        for(i=0;i<n;i++){
        }
            The code is O(n);
            
        for(i=0;i<n;i++){
            for(j=0;j<n;j++){
            }
        }
            The code is O(n*n);
            
        for(i=0;i<n;i++){
                for(j=0;j<n;j++){
            }
        }
        for(k=0;k<n;k++){
        }
            The code is O(n*n)+n;
            
    Design pattern:
        nicholos (books) read them
        creational pattern
        structural pattern
        behavioural pattern
        Constructor pattern-already practiced
        
    ECMA:
        javascript derived from ECMA script; so far we have used ES 5.
        ES6 is latest
        In ES6 defined let and conct. it can be used to define variables.
            but when using Let or conct, variable becomes block scope.i.e u cant access varaible outside
            their block.
        Let: allows to update variable.
        const: doesnt allows to change variable. on trying to change throughs error.
        
    //javascript has functional scope. i.e variable can be accessed within the function.
    //when the function is declared it looks for all the variable inside it before executing.
    
    Arrow function:
        Lexical scope:
        let s = (a,b) => a+b;  
        
        equal to
        
        function s(a,b){
            return a+b;
        }
        
    
    Closures
            inner function keeps track of outer functions variable
                function pow(a){
                            return function(b){
                                return a+b;
                            }
                        }
                        var a =pow(2);
                        a(2);//ans:4
                        a(4);//ans:6
                        
    Timer:
        setTimer(fn,1000) //it takes ms. it execeutes function after 1000ms;
        setInterval:(fn,1000) // should cler the interval orelse would be running and would kill the 
        memory.
            
        
06-09-2018

    Promises:
        var promise = new promise(function(resolve,reject))
    ES6:
        MAP-array
            var b = a.map(obj, index)=>{
                return index            
            }
            
            
            creates a array of index from object a
            
            Next function.
            
            //for each and map are same. but for each just iterates but map can be saved in new array.
        Filter-array
            
        Reduce-
            const array1 = [1, 2, 3, 4];
            const reducer = (accumulator, currentValue) => accumulator + currentValue;
            
            // 1 + 2 + 3 + 4
            console.log(array1.reduce(reducer));
            // expected output: 10
            
            // 5 + 1 + 2 + 3 + 4
            console.log(array1.reduce(reducer, 5));
            // expected output: 15
        
        ES6 new syntax:
        
        value swap: 
        a={1,2,3,4,5}
        [a,b]=[b,a];
        [c,d]=a
        //c=a[0];d=a[1];
        [c,,d]=a
        //c=a[0];d=a[2];
        [c,d,...e]=a;//... means spread operators it takes rest all array
        //c=1;d=2;e=[3,4,5];
        //map,filter,reduce,promise
        //... spread operator takes all array
        name = "subbiah";
        console.log("this is ${name}");//prints: this is subbiah;
        
        
        Object destruction:
            
06-11-2018
    
    jquery:
        library 
        angular 1 use jquery
        can write in angular or react based application, but now we have better oprions   
        2ways to use jquery. can download the full jquery file, keep in local and use them.
            another method use content delivery network, website hosts these codes online we can just
            call these links and use the jquery in our program.
            
         
    CDN:content delivery network
        
    mvc:
    
    Javascript minifiers removes the empty space,
    
    Taskrunners:
        GruntJS:used to do tasks. ex:less compiling ect
        Gulp
    
    WebPack
    
    //There can be only one windows.onload for a html
    //event handler
    //dom lookup by selector
    //jquery chaining
    
    
    jquery dom lookup 
        $(".container")
        $("#name")
        $(".container").val()
        $("label[for=name]")
        $("label[for=name]").text()/get text from html
        $("label[for=name]").text("new text")//changes text
        $("input:text:visible")//: means and. find input which is a text and visible.
        $("label[for]")[0].attr("").style({"color":"red","background-color":"blue"})



        //toggleclass jquery used to add remove class based on toggle state.**interesting****read it**            
        // cant add anything after hasclass().// hasclass used to find whether element has the class 
        or not.
        // in jquery in every method u can set the value and get the value. .val()-getting the value
            .vale("show this")-setting the value 
        
        
        jquery method:
            live
            delegate
            on- on is used to add event handler to dynamically added element
            
            
    //absolute (url)and relative path (local path).
    //ajax get post pull is possible with one address. it is possible with restful web service.
    
    
    
closure
hoisting
bubbling
less
grunt


About project
About yourself.
Html,Css-new
es6 
    arrow function
block scope
    
css flex
call and apply

promise- resolve,reject. call backs are used in promises. async

callback-promise,ajax call,event handler. 