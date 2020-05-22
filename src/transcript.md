
# Presentation Vue.js
***

#### slide №1
## About Vue.js
Today I want to tell about js framework VUE

***

#### slide №2
## History
Vue was created by Evan You after working for Google using AngularJS in a number of projects. He later summed up his thought process: "I figured, what if I could just extract the part that I really liked about Angular and build something really lightweight."

The first source code commit to the project was dated July 2013, and Vue was first released the following February, in 2014.

At the end of September 2016 was released Vue.js 2.0.

The latest version of the program to date 2.6.11.

What's in the future? There's no official release date, but the roadmap shows the release Vue 3.0 is planned in Q2 2020.

***

#### slide №3
## Advantages
It is very easy to start working with it, even if you have never worked with JavaScript frameworks. It's the perfect combination of convenience and power.

It's even smaller now.

He's faster. In Vue.js has always paid great attention to performance.

Vue took the best features of other libraries such as **templating syntax**, **two-way data binding** and **directives** from Angular, **virtual DOM implementation** from React. The setup is quite simple. All that makes using Vue.js very comfortable. Seems like it has the purpose to become a JavaScript framework of choice.

***

#### slide №4
## Ecosystem
Vue is a progressive framework for building user interfaces. It is designed from the ground, and can easily be a library and a framework depending on your goals. It consists of a core library that focuses on the view layer and an ecosystem of supporting libraries.

Some of the core libraries maintained by Vue team are as follows with their definitions:
+ Vue Router the official router for Vue.js. It makes building Single Page Applications with Vue.js more simple.
+ Vuex is a state management pattern and a library for Vue.js applications.
+ Vue-CLI is a full system for rapid Vue.js development. It aims to be the standard tooling baseline for the Vue ecosystem.
+ Vue-loader is loader that allows you to make Vue components in a format called Single-File Components (SFCs).
+ Vue-Server-Renderer runs both on server and client side where the majority of the application code is shared.
+ Vue Test Utils is the official unit testing utility library for Vue.js.
+ Vue Dev-Tools is a Browser devtools extension for debugging Vue.js applications.
And others...

***

#### slide №5
## How it works?
+ MVVM:

Technically, Vue.js is focused on the ViewModel layer of the MVVM pattern. It connects the View and the Model via two way data bindings. Actual DOM manipulations and output formatting are abstracted away into Directives and Filters.

ViewModel - an object that syncs the Model and the View. In Vue.js, every Vue instance is a ViewModel. They are instantiated with the Vue constructor or its sub-classes.

View - The actual DOM that is managed by Vue instances. Vue.js uses DOM-based templating. Each Vue instance is associated with a corresponding DOM element. When a Vue instance is created, it recursively walks all child nodes of its root element while setting up the necessary data bindings. After the View is compiled, it becomes reactive to data changes.

Model - A slightly modified plain JavaScript object. In Vue.js, models are simply plain JavaScript objects, or data objects. Once an object is used as data inside a Vue instance, it becomes reactive. You can manipulate their properties and Vue instances that are observing them will be notified of the changes.

+ Components:

In Vue.js, every component is simply a Vue instance. Components form a nested tree-like hierarchy that represents your application interface. They can be instantiated by a custom constructor returned from `Vue.extend`, but a more declarative approach is registering them with `Vue.component(id, constructor)`. Once registered, they can be declaratively nested in other Vue instance’s templates in the form of custom elements.

This simple mechanism enables declarative reuse and composition of Vue instances in a fashion similar to Web Components, without the need for latest browsers or heavy polyfills. By breaking an application into smaller components, the result is a highly decoupled and maintainable codebase.

+ Lifecycle:

Each Vue instance goes through a series of initialization steps when it’s created - for example, it needs to set up data observation, compile the template, mount the instance to the DOM, and update the DOM when data changes. Along the way, it also runs functions called lifecycle hooks, giving users the opportunity to add their own code at specific stages.

+ Reactivity:

One of Vue’s most distinct features is the unobtrusive reactivity system. Models are just plain JavaScript objects. When you modify them, the view updates. It makes state management simple and intuitive, but it’s also important to understand how it works to avoid some common gotchas.

When we pass a plain JavaScript object to a Vue instance as its data option, Vue will walk through all of its properties and convert them to **getter/setters** using `Object.defineProperty`. Every component instance has a corresponding **watcher** instance, which records any properties “touched” during the component’s render as dependencies. Later on when a dependency’s setter is triggered, it notifies the watcher, which in turn causes the component to re-render.

***

#### slide №6
## Interpolations
Vue.js uses an HTML-based template syntax that allows you to declaratively bind the rendered DOM to the underlying Vue instance’s data. All Vue.js templates are valid HTML that can be parsed by spec-compliant browsers and HTML parsers.
Under the hood, Vue compiles the templates into Virtual DOM render functions. Combined with the reactivity system, Vue is able to intelligently figure out the minimal number of components to re-render and apply the minimal amount of DOM manipulations when the app state changes.

+ text:

The most basic form of data binding is text interpolation using the “Mustache” syntax (double curly braces). The mustache tag will be replaced with the value of the `msg` property on the corresponding data object. It will also be updated whenever the data object’s `msg` property changes.

We can also perform one-time interpolations that do not update on data change by using the `v-once` **directive**, but this will also affect any other bindings on the same node.

+ raw HTML:

The double mustaches interprets the data as plain text, not HTML. In order to output real HTML, we will need to use the `v-html` **directive**.

+ attributes:

Mustaches cannot be used inside HTML attributes. Instead, we need to use a `v-bind` **directive**.

In the case of boolean attributes, where their mere existence implies `true`, `v-bind` works a little differently. In this example, if `isButtonDisabled` has the value of `null`, `undefined`, or `false`, the `disabled` attribute will not even be included in the rendered `<button>` element.

+ using javascript expressions:

So far we’ve only been binding to simple property keys in our templates. But Vue.js actually supports the full power of JavaScript expressions inside all data bindings. These expressions will be evaluated as JavaScript in the data scope of the owner Vue instance. One restriction is that each binding can only contain **one single expression**.

***

#### slide №7
## Directives
Directives are special attributes with the `v-` prefix. Directive attribute values are expected to be **a single JavaScript expression**. A directive’s job is to reactively apply side effects to the DOM when the value of its expression changes.

Consider some built-in directives:
- v-bind — dynamically binds to one or more attributes
- v-if — condition for element rendering
- v-for — loops an array of objects.
- v-model — associates a condition with input element
- v-on — connects the event listener to the element
- v-show — toggles element visibility by changing the CSS display property

+ v-bind:

Some directives can take an “argument”, denoted by a colon after the directive name. For example, the `v-bind` directive is used to reactively update an HTML attribute. Here `href` is the argument, which tells the `v-bind` directive to bind the element’s `href` attribute to the value of the expression `url`.

+ v-on:

Another example is the `v-on` directive, which listens to DOM events.

+ dynamic arguments:

Starting in version 2.6.0, it is also possible to use a JavaScript expression in a directive argument by wrapping it with square brackets. Here `attributeName` will be dynamically evaluated as a JavaScript expression, and its evaluated value will be used as the final value for the argument.

+ modifiers:

Modifiers are special postfixes denoted by a dot, which indicate that a directive should be bound in some special way. For example, the `.prevent` modifier tells the `v-on` **directive** to call `event.preventDefault()` on the triggered event.

***

#### slide №8
## Computed Properties and Watchers
+ computed property:

In-template expressions are very convenient, but they are meant for simple operations. Putting too much logic in our templates can make them bloated and hard to maintain. That’s why for any complex logic, we should use a computed property.

+ watched property:

Vue does provide a more generic way to observe and react to data changes on a Vue instance: **watch properties**. When we have some data that needs to change based on some other data, it is tempting to overuse `watch`. However, it is often a better idea to use a **computed property** rather than an imperative `watch` callback.

While computed properties are more appropriate in most cases, there are times when a custom watcher is necessary. That’s why Vue provides a more generic way to react to data changes through the `watch` option. This is most useful when you want to perform asynchronous or expensive operations in response to changing data.

+ computed setter:

Computed properties are by default getter-only, but we can also provide a `setter` when we need it.

***

#### slide №9
## Class and Style Bindings

A common need for data binding is manipulating an element’s class list and its inline styles. Since they are both attributes, we can use `v-bind` to handle them: we only need to calculate a final string with our expressions. However, meddling with string concatenation is annoying and error-prone. For this reason, Vue provides special enhancements when `v-bind` is used with `class` and `style`. In addition to strings, the expressions can also evaluate to objects or arrays.

+ binding Html classes:

We can pass an object to `v-bind:class` to dynamically toggle classes. This syntax means the presence of the `active` class will be determined by the **truthiness** of the data property `isActive`.

We can also bind to a **computed property** `classObject` that returns an object. This is a common and powerful pattern.

We can pass an array to `v-bind:class` to apply a list of classes.

+ binding Inline Styles:

The object syntax for `v-bind:style` is pretty straightforward - it looks almost like CSS, except it’s a JavaScript object. You can use either camelCase or kebab-case (use quotes with kebab-case) for the CSS property names.

The array syntax for `v-bind:style` allows to apply multiple style objects to the same element. Starting in 2.3.0+ we can provide an array of multiple (prefixed) values to a style property.

***

#### slide №10
## Conditional rendering
The directive `v-if` is used to conditionally render a block. The block will only be rendered if the directive’s expression returns a truthy value. It is also possible to add an “else block” with `v-else`. The `v-else-if` (new in v2.1.0+), as the name suggests, serves as an “else if block” for `v-if`. It can also be chained multiple times.

Another option for conditionally displaying an element is the `v-show` directive. The usage is largely the same.

The difference is that an element with `v-show` will always be rendered and remain in the DOM; `v-show` only toggles the `display` CSS property of the element.

***

#### slide №11
## List rendering
One of the options for list rendering is mapping an array to elements with `v-for`. We can use the `v-for` directive to render a list of items based on an array. The `v-for` directive requires a special syntax in the form of `item in items`, where `items` is the source data array and `item` is an alias for the array element being iterated on.

***

#### slide №12
## Method event handlers
We can use the `v-on` directive to listen to DOM events and run some JavaScript when they’re triggered.

The logic for many event handlers will be more complex though, so keeping our JavaScript in the value of the `v-on` attribute isn’t feasible. That’s why `v-on` can also accept the name of a method we’d like to call.

***

#### slide №13
## Form input bindings
We can use the `v-model` directive to create two-way data bindings on form input, textarea, and select elements. It automatically picks the correct way to update the element based on the input type. Although a bit magical, `v-model` is essentially syntax sugar for updating data on user input events, plus special care for some edge cases.

`v-model` internally uses different properties and emits different events for different input elements:

- text and textarea elements use `value` property and `input` event;
- checkboxes and radiobuttons use `checked` property and `change` event;
- select fields use `value` as a prop and `change` as an event.

***

#### slide №14
## Event & Key modifiers


***
