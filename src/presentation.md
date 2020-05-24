
# Presentation **Vue.js**
***

#### slide №1
## About **Vue.js**
Today I want to tell about js framework **Vue**

***

#### slide №2
## History
**Vue** was created by Evan You after working for Google using AngularJS in a number of projects.

He later summed up his thought process:
>I figured, what if I could just extract the part that I really liked about Angular and build something really lightweight.

***

#### slide №3
## History
The first source code commit to the project was dated July 2013, and **Vue** was first released the following February, in 2014.

At the end of September 2016 was released **Vue** 2.0.

The latest version of the program to date 2.6.11.

What's in the future? There's no official release date, but the roadmap shows the release **Vue** 3.0 is planned in Q2 2020.

***

#### slide №4
## Advantages
It is very easy to start working with it, even if you have never worked with JavaScript frameworks.

**Vue** took the best features of other libraries such as **templating syntax**, **two-way data binding** and **directives** from Angular, **virtual DOM implementation** from React.

All that makes using **Vue** very comfortable.
Seems like it has the purpose to become a JavaScript framework of choice.

***

#### slide №5
## Ecosystem
**Vue** can easily be a library and a framework depending on our goals. It consists of a core library that focuses on the view layer and an ecosystem of supporting libraries.

Some of the core libraries maintained by **Vue** team:
+ **Vue** Router - it makes building Single Page Applications with **Vue** more simple.
+ Vuex is a state management pattern and a library for **Vue** applications.
+ Vue-CLI is a full system for rapid **Vue** development.
+ Vue-loader is loader that allows us to make **Vue** components in a format called Single-File Components (SFCs).
+ Vue-Server-Renderer runs both on server and client side where the majority of the application code is shared.
+ **Vue** Test Utils is the official unit testing utility library for **Vue**.
+ **Vue** Dev-Tools is a Browser devtools extension for debugging **Vue** applications.
And others...

***

#### slide №6
## How it works?
+ MVVM:

Technically, **Vue** is focused on the ViewModel layer of the MVVM pattern. It connects the View and the Model via two way data bindings. Actual DOM manipulations and output formatting are abstracted away into Directives and Filters.

ViewModel - an object that syncs the Model and the View. In **Vue**, every **Vue** instance is a ViewModel. They are instantiated with the **Vue** constructor or its sub-classes.

View - The actual DOM that is managed by **Vue** instances. **Vue** uses DOM-based templating. Each **Vue** instance is associated with a corresponding DOM element. When a **Vue** instance is created, it recursively walks all child nodes of its root element while setting up the necessary data bindings. After the View is compiled, it becomes reactive to data changes.

Model - A slightly modified plain JavaScript object. In **Vue**, models are simply plain JavaScript objects, or data objects. Once an object is used as data inside a **Vue** instance, it becomes reactive. You can manipulate their properties and **Vue** instances that are observing them will be notified of the changes.

+ Components:

In **Vue**, every component is simply a **Vue** instance. Components form a nested tree-like hierarchy that represents our application interface. They can be instantiated by a custom constructor returned from `Vue.extend`, but a more declarative approach is registering them with `Vue.component(id, constructor)`. Once registered, they can be declaratively nested in other **Vue** instance’s templates in the form of custom elements.

+ Lifecycle:

Each **Vue** instance goes through a series of initialization steps when it’s created - for example, it needs to set up data observation, compile the template, mount the instance to the DOM, and update the DOM when data changes. Along the way, it also runs functions called lifecycle hooks, giving users the opportunity to add their own code at specific stages.

+ Reactivity:

One of Vue’s most distinct features is the unobtrusive reactivity system. Models are just plain JavaScript objects. When we modify them, the view updates. It makes state management simple and intuitive.

When we pass a plain JavaScript object to a **Vue** instance as its data option, **Vue** will walk through all of its properties and convert them to **getter/setters** using `Object.defineProperty`. Every component instance has a corresponding **watcher** instance, which records any properties “touched” during the component’s render as dependencies. Later on when a dependency’s setter is triggered, it notifies the watcher, which in turn causes the component to re-render.

***

#### slide №7
## Component structure
Anatomy of **Vue** Component give us a brief overview of a typical **Vue** single file component (SFC). At high-level, **Vue** single file component consists of three sections:
+ Template
+ Script
+ Style

Template section is where we put our HTML markup code along with any data variables or computed properties which are defined in script section of the code.

In script section, we can define any local data, props, computed properties, watchers, methods, **Vue** lifecycle hooks along with the registration of any child component as needed.

Finally, the style section allow us to define our component styles to make it presentable using normal CSS or by using Less, SCSS pre-processors etc.

***

#### slide №8
## Interpolations
**Vue** uses an HTML-based template syntax that allows us to declaratively bind the rendered DOM to the underlying **Vue** instance’s data. All **Vue** templates are valid HTML that can be parsed by spec-compliant browsers and HTML parsers.
Under the hood, **Vue** compiles the templates into Virtual DOM render functions. Combined with the reactivity system, **Vue** is able to intelligently figure out the minimal number of components to re-render and apply the minimal amount of DOM manipulations when the app state changes.

+ text:

The most basic form of data binding is text interpolation using the “Mustache” syntax (double curly braces).

+ raw HTML:

The double mustaches interprets the data as plain text, not HTML. In order to output real HTML, we will need to use the `v-html` **directive**.

+ attributes:

Mustaches cannot be used inside HTML attributes. Instead, we need to use a `v-bind` **directive**.

+ using javascript expressions:

**Vue** actually supports the full power of JavaScript expressions inside all data bindings. These expressions will be evaluated as JavaScript in the data scope of the owner **Vue** instance. One restriction is that each binding can only contain **one single expression**.

***

#### slide №9
## Directives
Directives are special attributes with the `v-` prefix. Directive attribute values are expected to be **a single JavaScript expression**. A directive’s job is to reactively apply side effects to the DOM when the value of its expression changes.

+ dynamic arguments:

It is also possible to use a JavaScript expression in a directive argument by wrapping it with square brackets.

+ modifiers:

Modifiers are special postfixes denoted by a dot, which indicate that a directive should be bound in some special way. For example, the `.prevent` modifier tells the `v-on` **directive** to call `event.preventDefault()` on the triggered event.

***

#### slide №10
## Computed Properties and Watchers
+ computed property:

In-template expressions are very convenient, but they are meant for simple operations. Putting too much logic in our templates can make them bloated and hard to maintain. That’s why for any complex logic, we should use a computed property.

+ watched property:

Vue does provide a more generic way to observe and react to data changes on a **Vue** instance: **watch properties**. When we have some data that needs to change based on some other data, it is tempting to overuse `watch`.

+ computed setter:

Computed properties are by default getter-only, but we can also provide a `setter` when we need it.

***

#### slide №11
## Class and Style Bindings

A common need for data binding is manipulating an element’s class list and its inline styles. Since they are both attributes, we can use `v-bind` to handle them. For this reason, **Vue** provides special enhancements when `v-bind` is used with `class` and `style`. In addition to strings, the expressions can also evaluate to objects or arrays.

+ binding Html classes:
+ binding Inline Styles:

The object syntax for `v-bind:style` is pretty straightforward - it looks almost like CSS, except it’s a JavaScript object.

***

#### slide №12
## Conditional rendering
The directive `v-if` is used to conditionally render a block. It is also possible to add an “else block” with `v-else`. The `v-else-if` serves as an “else if block” for `v-if`. It can also be chained multiple times.

Another option for conditionally displaying an element is the `v-show` directive. An element with `v-show` will always be rendered and remain in the DOM; `v-show` only toggles the `display` CSS property of the element.

***

#### slide №13
## List rendering
One of the options for list rendering is mapping an array to elements with `v-for`.

***

#### slide №14
## Method event handlers
We can use the `v-on` directive to listen to DOM events and run some JavaScript when they’re triggered.

***

#### slide №15
## Form input bindings
We can use the `v-model` directive to create two-way data bindings on form input, textarea, and select elements.

`v-model` internally uses different properties and emits different events for different input elements:
- text and textarea elements use `value` property and `input` event;
- checkboxes and radiobuttons use `checked` property and `change` event;
- select fields use `value` as a prop and `change` as an event.

***

#### slide №16
## Event & Key modifiers
- event modifiers:
It is a very common need to call `event.preventDefault()` or `event.stopPropagation()` inside event handlers. To address this problem, **Vue** provides event modifiers for `v-on`. Some of event modifiers are:
+ .stop
+ .prevent
+ .capture
+ .self
+ .once
+ .passive

- key modifiers:
Vue allows adding key and mouse modifiers for `v-on` when listening for key and mouse events, such as:
+ .enter
+ .tab
+ .delete (captures both “Delete” and “Backspace” keys)
+ .esc
+ .space
+ .up
+ .down
+ .left
+ .right
+ .middle

***

#### slide №18
## Dev tools
For debugging in the browser there is a Vue-devtools, which allows us to see what components are in our application and their current status.

It also works great with Vuex and allows us to perform so-called time-travel debugging: in the browser, we can see the status history and switch between them.

***

#### slide №19
## Vue 3
As Evan You summarized it, **Vue** 3 will be **faster**, **smaller**, **more maintainable** and it will be **easier to target native**.

One of the most significant changes is that a new API that will allow for a function-based way of writing our component, inspired by React Hooks. It lets us encapsulate logic into "composition functions" and reuse that logic across components.

Other pretty exciting changes in **Vue** 3:
+ Virtual DOM rewrite for better performance and improved TypeScript support
+ Native portals – now called Teleport
+ Fragments (virtual elements that won't be rendered in the DOM tree)
+ Global mounting
+ Conditional suspending of component rendering
+ ... and more.

***

## END
