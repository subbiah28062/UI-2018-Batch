06-04-2018
        
    -JS is a single thread programming language.
    -JS is a dynamic, prototypical and functional language.
    
    -object:
        literal
        constructor
        create(.create study by yourself)
    -function:
        named:
            function name(param){}
            var name = new function(){}
    -operators:
        ==(coeration i.e. conversion and comparison, which decreases performance)
        ===(use === for increased performance)
    -prototype:
        Inheritance(prototypical chain)
            Multi level inheritance
                function College(name,location){
                    this.name = name;
                    this.location = location;
                }
                function Year(period){
                    this.period = period;
                }
                Year.prototype=new College("TAMUK","Kingsville");
                var college1 = new Year();
                console.log(college1);
            one level multiple parents
        Extending a class			
            //Create a empty function and use prototype to add parameters, because evry instance creates a reference for every properties which wastes memory.
    
    -We get server ip from dns using the domain name.
    -single thread programming??
    -DOM lookup- quering a DOM using query selectors(by id, class, tag etc,)
    
    //undefined: var z; console.log(z);
    //error:console.log(z);
    //Without new constructor this statement wont work. This will point windows.
        
06-05-2018
        
    -virtual DOM
    -shadow DOM
    
    //DOM is expensive(perfomance), so save the DOM when u access once. 
    ex: var a = document.GetElementById("name");
    a.style.color="red";
    b= a.value;
    
    //Create a empty function and use prototype to add parameters, because every instance creates a reference for every properties which wastes memory.
    
    -Event:
        Event type
        Element(HTML elements)
        Event Handler(on Event occurrence it will trigger Event Handler)
        Binding(binding event and html elemt)//-This gives current target element
    
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
        THIRD WAY:
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
        apply -array ex:
        bind- creates a function copy which can be called later
    Call back
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
        End point url- url where payload is going to be sent.
        pay load-json data sent from client side is called as pay load.
        CRUD-creating,reading,updating and deleting a data
        Method type:(To interact with server)
            GET-get data from server
            POST-to send data to server
            PUT-to update the posted data. To access the server we should have the id(id specified to each user) 
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
    Attributes:
        Button not to submit use attribute type="button" orelse it will submit the form.
        Method attribute:
    -restful services made by backend 
    -API-
        REQUEST HEADER
        RESPONSE HEADER
    
    gvar getDisplayId = document.getElementById("displayId");
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
        setInterval:(fn,1000) // should clear the interval orelse would be running and would kill the memory.
            
        
 