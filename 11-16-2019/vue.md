VueJS:
    Single File Components: Essentially it is a file with the suffix .vue containing up to 3 parts (the css, html and javascript) for each component. This coupling of technologies feels right. It makes it easy to understand each component in a single place. Minimal Template Syntax: minimum effort is required to create a component. Vue template by default binds html css and sript in same file, those reducing the effort of binding them.

    In vue all script are object based.

    css: <style tag> 
        1)on adding scoped variable styles will be fully encapsulate the styling to this component. Meaning if we had a .name CSS selector defined in this component, it won’t apply that style in any other component.

    Template Syntax(HTML): 
        in vue html should be written inside template tag. this variable is implicit, any js function or const can be accesed without 'this' variable.

        js expressions can be used inside v-bind and {{}} 
            ex: {{isdisabled ? 'blocked': 'enter site'}},
            v-bind:id="isdisabled ? 'blocked' :'notBlocked'"

        directives: 
            v-bind: [shorthand :]
                {{}} cannot be used inside HTML attributes. 
                Instead, use a v-bind directive,
                js expression can be used inside 
                    ex: v-bind:href="ishome ? '/login' : '/home"
                use {} to   dynamically toggle
                    ex:  v-bind:class="{ active: isActive }" //isActive is js object
                use [] to add list of expressions
                    ex:  v-bind:class="[{ active: isActive }, ishome  'login' : 'home ]" //isActive is js object
            v-html
                 use v-html directive 
                ex: <span v-html="rawHtml"></span>
            v-if
            v-on: [shorthand @]
                Another example is the v-on directive, which listens to DOM events:
        
        Dynamic Attributes:
            v-bind:[attributeName]="url"
            v-on:[eventName]="doSomething"
            //null caan be provided to explicitly remove the binding
            v-bind:['foo' + bar]="value" // foo is string, bar vue scope data
        Modifiers:
            v-on:submit.prevent="onSubmit" // .prevent means event.preventDefault()



    Vuex: 
        Vuex is a state management library. It uses a global, centralized store for all the components.
        It's easier to maintain and synchronize the state between multiple components, even if the component hierarchy changes.
        If a component is destroyed, the state in the Vuex store will remain intact. So on returning, we can retrive data from vuex instead of making service calls.
        Vuex makes direct cross-component communication possible
        Vuex: I find that the integration between vue and vuex is neater and more minimal than that of react and redux. sample vuex store file store.js

    computed:  
        complex logics in html can be moved to computed object. componnet is similar to method but computed properties are cached based on their reactive dependencies. A computed property will only re-evaluate when some of its reactive dependencies have changed. This means as long as message has not changed, multiple access to the reversedMessage computed property will immediately return the previously computed result without having to run the function again.

            computed whould always bbe involved a data ocject(reactive dependencies)

        diffrence between watch and computed: watch should be with only single data object. while computed can involve multiple data object

        computed can also bbe used to set value to multiple data object aat once.

    watch: same as in angularJS



// helpfull npm modules
npm install gsap lodash scrollmagic vue-material