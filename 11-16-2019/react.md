Why react and not angular:
    For example, AngularJS (1.x) approaches building an application by extending HTML markup and injecting various constructs (e.g. Directives, Controllers, Services) at runtime. As a result, AngularJS is very opinionated about the greater architecture of your application — these abstractions are certainly useful in some cases, but in many situations, they come at the cost of flexibility.

 
    By contrast, React focuses exclusively on the creation of components, and has few (if any) opinions about an application’s architecture. This allows a developer an incredible amount of flexibility in choosing the architecture they deem “best” — though it also places the responsibility of choosing (or building) those parts on the developer.

    JSX: 
        When Facebook first released React to the world, they also introduced a new dialect of JavaScript called JSX that embeds raw HTML templates inside JavaScript code. JSX code by itself cannot be read by the browser; it must be transpiled into traditional JavaScript using tools like Babel and webpack. 

    redux:
        why redux not MVC:
            data in model can be mutaated(changed) from anywhere resulting in delay in debugging if there is any issue.

            Redux restricts direct access to the shared data. data can only bbe accessed through getters

    state vs stateless components:

    The literal difference is that one has state, and the other doesn’t. That means the stateful components are keeping track of changing data, while stateless components print out what is given to them via props, or they always render the same thing.
        Stateless:
            Stateless components (a flavor of “reusable” components) are nothing more than pure functions that render DOM based solely on the properties provided to them
            component has no need for any internal state
        state:
            What state actually is — data we hold that we’re aware is subject to change

            a stateful component keeps track of the data.

            You’ll need state somewhere when information dynamically changes, like a user’s current favorite songs or top scores. Aim to have a parent component keep all the information, and pass it down to its children stateless components. Having a parent component pass data down to its children also assures that if there is any debugging needed regarding state management, we can go to the parent component to see what’s up, instead of checking state in each child component. All the children components have to worry about is receiving the information as props properly 
    
    Pure components
        Based on the concept of purity in functional programming paradigms, a function is said to be pure if:

        its return value is only determined by its input values
        its return value is always the same for the same input values