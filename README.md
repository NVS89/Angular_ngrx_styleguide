
* [*HTML*](#HTML)
    * [Props Naming](#props-naming)
    * [Alignment](#Alignment)
    * [Quotes](#Quotes)
    * [Spacing](#Spacing)
    * [Props](#Props)
    * [Tags](#Tags)

<hr/>

* [**TypeScript**](#TypeScript)
    * [Variable](#variable-and-function)
    * [Class](#class)
    * [Interface](#interface)
    * [Type](#type)
    * [Namespace](#namespace)
    * [Enum](#enum)
    * [`null` vs. `undefined`](#null-vs-undefined)
    * [Formatting](#formatting)
    * [Single vs. Double Quotes](#quotes)
    * [Tabs vs. Spaces](#spaces)
    * [Use semicolons](#semicolons)
    * [Annotate Arrays as `Type[]`](#array)
    * [File Names](#filename)
    * [`type` vs `interface`](#type-vs-interface)
<hr/>

* [**Angular**](#Angular)
    * [*__File structure conventions__*](#File-structure-conventions)
        * [Ordering](#Ordering
)
    * [*__Single responsibility__*](#Single-responsibility)
        * [Rule of One](#Rule-of-One)
        * [Small functions](#Small-functions)
    * [*__Naming__*](#Naming)
        * [General Naming Guidelines](#General-Naming-Guidelines)
        * [Separate file names with dots and dashes](#Separate-file-names-with-dots-and-dashes)
        * [Symbols and file names](#symbols-and-file-names)
        * [Service names](#service-names)
        * [Component selectors](#component-selectors)
        * [Component custom prefix](#component-custom-prefix)
        * [Directive selectors](#directive-selectors)
        * [Pipe names](#pipe-names)
        * [Angular NgModule names](#angular-ng-module-names)
        * [Application structure and NgModules](#application-structure-and-ng-modules)
    * [*__Application structure and NgModules__*](#application-structure-and-ng-modules)
        * [LIFT principle](#lift-principle)
        * [Locate](#Locate)
        * [Identify](#Identify)
        * [DRY](#DRY-principle)
        * [Overall structural guidelines](#overall-structural-guidelines)
        * [Folders-by-feature structure](#folders-by-feature-structure)
        * [App root module](#app-root-module)
        * [Feature modules](#feature-modules)
        * [Shared feature module](#shared-feature-module)
        * [Lazy Loaded folders](#lazy-loaded-folders)
        * [Never directly import lazy loaded folders](#never-directly-import-lazy-loaded-folders)
    * [*__Components__*](#Components)
        * [Components as elements](#Components-as-elements)
        * [Decorate input and output properties](#Decorate-input-and-output-properties)
        * [Avoid aliasing inputs and outputs](#Avoid-aliasing-inputs-and-outputs)
        * [Member sequence](#Member-sequence)
        * [Delegate complex component logic to services](#Delegate-complex-component-logic-to-services)
        * [Don't prefix output properties](#do-not-prefix-output-properties)
        * [Put presentation logic in the component class](#put-presentation-logic-in-the-component-class)
    * [**__Directives__**](#use-directives-to-enhance-an-element)
        * [Use directives to enhance an element](#Use-directives-to-enhance-an-element)
        * [HostListener and HostBinding decorators versus host metadata](#HostListener-and-host-binding-decorators-versus-host-metadata)
    * [*__Services__*](#Services)
        * [Services are singletons](#Services-are-singletons)
        * [Single responsibility](#Single-responsibility)
        * [Providing a service](#Providing-a-service)
        * [Use the class decorator](#Use-the-class-decorator)
    * [*__Data Services__*](#Data-services)
        * [Talk to the server through a service](#Talk-to-the-server-through-a-service)
    * [*__Lifecycle hooks__*](#Lifecycle-hooks)
        * [Implement lifecycle hook interfaces](#Implement-lifecycle-hook-interfaces)
<hr/>

* [**Redux NgRx**](#Redux-State-management)
    * [Do Not Mutate State](#Do-not-mutate-state)
    * [Reducers Must Not Have Side Effects](#Reducers-must-not-have-side-effects)
    * [Do Not Put Non-Serializable Values in State or Actions](#Do-not-put-non-serializable-values-in-state-or-actions)
    * [Structure Files as Feature Folders or Ducks](#Structure-files-as-feature-folders-or-ducks)
    * [Reducers Should Own the State Shape](#Reducers-should-own-the-state-shape)
    * [Treat Reducers as State Machines](#Treat-reducers-as-state-machines)
    * [Normalize Complex Nested/Relational State](#Normalize-complex-nested-relational-state)
    * [Model Actions as Events, Not Setters](#model-actions-as-events-not-setters)
    * [Write Meaningful Action Names](#write-meaningful-action-names)
    * [Allow Many Reducers to Respond to the Same Action](#allow-many-reducers-to-respond-to-the-same-action)
    * [Avoid Dispatching Many Actions Sequentially](#Avoid-dispatching-many-actions-sequentially)
    * [Evaluate Where Each Piece of State Should Live](#evaluate-where-each-piece-of-state-should-live)
    * [Use Plain JavaScript Objects for State](#use-plain-java-script-objects-for-state)
    * [Write Action Types as domain/eventName](#write-action-types-as-domain-event-name)
    * [Use Action Creators](#use-action-creators)
    * [Use Selector Functions to Read from Store State](#use-selector-functions-to-read-from-store-state)

# HTML


* [Props Naming](#props-naming)
* [Alignment](#Alignment)
* [Quotes](#Quotes)
* [Spacing](#Spacing)
* [Props](#Props)
* [Tags](#Tags)

## Props Naming

* Avoid using DOM component prop names for different purposes.

> People expect props like style and className to mean one specific thing. Varying this API for a subset of your app makes the code less readable and less maintainable, and may cause bugs.

## Alignment
``` html
    // bad
    <app-component superLongParam="bar"
        anotherSuperLongParam="baz" />

    // good
    <app-component
        superLongParam="bar"
        anotherSuperLongParam="baz"
    ></app-component>

    // if props fit in one line then keep it on the same line (with 140 characters)
    <app-component bar="bar" ></app-component>

    // children get indented normally
    <app-component
        superLongParam="bar"
        anotherSuperLongParam="baz"
    >
        <children-component> </children-component>
    </app-component>
```
## Quotes
Always use double quotes (") for HTML attributes, but single quotes (') for all other JS

```html
// bad
<app-component bar='bar' />

// good
<app-component bar="bar" />

// bad
<app-component style='{{ left: "20px" }}' />

// good
<app-component style="{{ left: '20px' }}" />

```

## Spacing
* Always include a single space in your self-closing tag
``` html
// bad
<app-component/>

// very bad
<app-component                 />

// bad
<app-component
 />

// good
<app-component />
```

* Do not pad interpolation curly braces with spaces
``` html
// bad
<app-component bar=" { baz } " />

// good
<app-component bar="{{ baz }}" />
```

## Props

* Always use camelCase for prop names if the prop value is a Angular component.

``` html
// bad
<app-component
  UserName="hello"
  phone_number="{{12345678}}"
></app-component>

// good
<app-component
  userName="hello"
  phoneNumber="{{12345678}}"
  component="{{SomeComponent}}"
></app-component>
```

* Always include an alt prop on <img> tags. If the image is presentational, alt can be an empty string or the <img> must have role="presentation"

``` html
// bad
<img src="hello.jpg" />

// good
<img src="hello.jpg" alt="Me waving hello" />

// good
<img src="hello.jpg" alt="" />

// good
<img src="hello.jpg" role="presentation" />
```
* Do not use words like "image", "photo", or "picture" in ```<img>``` alt props.
> Screenreaders already announce img elements as images, so there is no need to include this information in the alt text.

```html
// bad
<img src="hello.jpg" alt="Picture of me waving hello" />

// good
<img src="hello.jpg" alt="Me waving hello" />
```
* Use only valid, non-abstract [ARIA roles](https://www.w3.org/TR/wai-aria/#usage_intro)

```html
// bad - not an ARIA role
<div role="datepicker" > </div>

// bad - abstract ARIA role
<div role="range" > </div>

// good
<div role="button" > </div>
```

* Do not use accessKey on elements
> Inconsistencies between keyboard shortcuts and keyboard commands used by people using screenreaders and keyboards complicate accessibility.

```html
// bad
<div accessKey="h" > </div>

// good
<div> </div>
```

## Tags

* If your component has multiline properties, close its tag on a new line
``` html
// bad
<app-component
  bar="bar"
  baz="baz" ></app-component>

// good
<app-component
  bar="bar"
  baz="baz"
></app-component>
```

# TypeScript

* [Variable](#variable-and-function)
* [Class](#class)
* [Interface](#interface)
* [Type](#type)
* [Namespace](#namespace)
* [Enum](#enum)
* [`null` vs. `undefined`](#null-vs-undefined)
* [Formatting](#formatting)
* [Single vs. Double Quotes](#quotes)
* [Tabs vs. Spaces](#spaces)
* [Use semicolons](#semicolons)
* [Annotate Arrays as `Type[]`](#array)
* [File Names](#filename)
* [`type` vs `interface`](#type-vs-interface)

## Variable and Function
* Use `camelCase` for variable and function names

> Reason: Conventional JavaScript

**Bad**
```ts
var FooVar;
function BarFunc() { }
```
**Good**
```ts
var fooVar;
function barFunc() { }
```

## Class
* Use `PascalCase` for class names.

> Reason: This is actually fairly conventional in standard JavaScript.

**Bad**
```ts
class foo { }
```
**Good**
```ts
class Foo { }
```
* Use `camelCase` of class members and methods

> Reason: Naturally follows from variable and function naming convention.

**Bad**
```ts
class Foo {
    Bar: number;
    Baz() { }
}
```
**Good**
```ts
class Foo {
    bar: number;
    baz() { }
}
```
## Interface

* Use `PascalCase` for name.

> Reason: Similar to class

* Use `camelCase` for members.

> Reason: Similar to class


**Bad**
```ts
interface Foo {
}
```
**Good**
```ts
interface IFoo {
}
```

## Type

* Use `PascalCase` for name.

> Reason: Similar to class

* Use `camelCase` for members.

> Reason: Similar to class


## Namespace

* Use `PascalCase` for names

> Reason: Convention followed by the TypeScript team. Namespaces are effectively just a class with static members. Class names are `PascalCase` => Namespace names are `PascalCase`

**Bad**
```ts
namespace foo {
}
```
**Good**
```ts
namespace Foo {
}
```

## Enum

* Use `PascalCase` for enum names

> Reason: Similar to Class. Is a Type.

**Bad**
```ts
enum color {
}
```
**Good**
```ts
enum Color {
}
```

* Use `PascalCase` for enum member

> Reason: Convention followed by TypeScript team i.e. the language creators e.g `SyntaxKind.StringLiteral`. Also helps with translation (code generation) of other languages into TypeScript.

**Bad**
```ts
enum Color {
    red
}
```
**Good**
```ts
enum Color {
    Red
}
```

## Null vs. Undefined

* Prefer not to use either for explicit unavailability

> Reason: these values are commonly used to keep a consistent structure between values. In TypeScript you use *types* to denote the structure

**Bad**
```ts
let foo = {x:123,y:undefined};
```
**Good**
```ts
let foo:{x:number,y?:number} = {x:123};
```

* Use `undefined` in general (do consider returning an object like `{valid:boolean, value?:Foo}` instead)

***Bad***
```ts
return null;
```
***Good***
```ts
return undefined;
```

* Use `null` where it's a part of the API or conventional

> Reason: It is conventional in Node.js e.g. `error` is `null` for NodeBack style callbacks.

**Bad**
```ts
cb(undefined)
```
**Good**
```ts
cb(null)
```

* Use *truthy* check for **objects** being `null` or `undefined`

**Bad**
```ts
if (error === null)
```
**Good**
```ts
if (error)
```

* Use `== null` / `!= null` (not `===` / `!==`) to check for `null` / `undefined` on primitives as it works for both `null`/`undefined` but not other falsy values (like `''`, `0`, `false`) e.g.

**Bad**
```ts
if (error !== null) // does not rule out undefined
```
**Good**
```ts
if (error != null) // rules out both null and undefined
```

## Formatting
The TypeScript compiler ships with a very nice formatting language service. Whatever output it gives by default is good enough to reduce the cognitive overload on the team.

Use [`tsfmt`](https://github.com/vvakame/typescript-formatter) to automatically format your code on the command line. Also, your IDE (atom/vscode/vs/sublime) already has formatting support built-in.

Examples:
```ts
// Space before type i.e. foo:<space>string
const foo: string = "hello";
```

## Quotes

* Prefer single quotes (`'`) unless escaping.

> Reason: More JavaScript teams do this (e.g. [airbnb](https://github.com/airbnb/javascript), [standard](https://github.com/feross/standard), [npm](https://github.com/npm/npm), [node](https://github.com/nodejs/node), [google/angular](https://github.com/angular/angular/), [facebook/react](https://github.com/facebook/react)). It's easier to type (no shift needed on most keyboards). [Prettier team recommends single quotes as well](https://github.com/prettier/prettier/issues/1105)

> Double quotes are not without merit: Allows easier copy paste of objects into JSON. Allows people to use other languages to work without changing their quote character. Allows you to use apostrophes e.g. `He's not going.`. But I'd rather not deviate from where the JS Community is fairly decided.

* When you can't use double quotes, try using back ticks (\`).

> Reason: These generally represent the intent of complex enough strings.

## Spaces

* Use `4` spaces. Not tabs.

> Reason: More JavaScript teams do this (e.g. [airbnb](https://github.com/airbnb/javascript), [idiomatic](https://github.com/rwaldron/idiomatic.js), [standard](https://github.com/feross/standard), [npm](https://github.com/npm/npm), [node](https://github.com/nodejs/node), [google/angular](https://github.com/angular/angular/), [facebook/react](https://github.com/facebook/react)). The TypeScript/VSCode teams use 4 spaces but are definitely the exception in the ecosystem.

## Semicolons

* Use semicolons.

> Reasons: Explicit semicolons helps language formatting tools give consistent results. Missing ASI (automatic semicolon insertion) can trip new devs e.g. `foo() \n (function(){})` will be a single statement (not two). TC39 [warning on this as well](https://github.com/tc39/ecma262/pull/1062). Example teams: [airbnb](https://github.com/airbnb/javascript), [idiomatic](https://github.com/rwaldron/idiomatic.js), [google/angular](https://github.com/angular/angular/), [facebook/react](https://github.com/facebook/react), [Microsoft/TypeScript](https://github.com/Microsoft/TypeScript/).

## Array

* Annotate arrays as `foos:Foo[]` instead of `foos:Array<Foo>`.

> Reasons: It's easier to read. It's used by the TypeScript team. Makes easier to know something is an array as the mind is trained to detect `[]`.

## type vs. interface

* Use `type` when you *might* need a union or intersection:

```
type Foo = number | { someProperty: number }
```
* Use `interface` when you want `extends` or `implements` e.g.

```
interface Foo {
  foo: string;
}
interface FooBar extends Foo {
  bar: string;
}
class X implements FooBar {
  foo: string;
  bar: string;
}
```

# Angular

* [File structure conventions](#File-structure-conventions)
    * [Ordering](#Ordering)
* [Single responsibility](#Single-responsibility)
    * [Rule of One](#Rule-of-One)
    * [Small functions](#Small-functions)
* [Naming](#Naming)
    * [General Naming Guidelines](#General-Naming-Guidelines)
    * [Separate file names with dots and dashes](#Separate-file-names-with-dots-and-dashes)
    * [Symbols and file names](#symbols-and-file-names)
    * [Service names](#service-names)
    * [Component selectors](#component-selectors)
    * [Component custom prefix](#component-custom-prefix)
    * [Directive selectors](#directive-selectors)
    * [Pipe names](#pipe-names)
    * [Angular NgModule names](#angular-ng-module-names)
    * [Application structure and NgModules](#application-structure-and-ng-modules)
* [Application structure and NgModules](#application-structure-and-ng-modules)
    * [LIFT principle](#lift-principle)
    * [Locate](#Locate)
    * [Identify](#Identify)
    * [DRY](#DRY-principle)
    * [Overall structural guidelines](#overall-structural-guidelines)
    * [Folders-by-feature structure](#folders-by-feature-structure)
    * [App root module](#app-root-module)
    * [Feature modules](#feature-modules)
    * [Shared feature module](#shared-feature-module)
    * [Lazy Loaded folders](#lazy-loaded-folders)
    * [Never directly import lazy loaded folders](#never-directly-import-lazy-loaded-folders)
* [Components](#Components)
    * [Components as elements](#Components-as-elements)
    * [Decorate input and output properties](#Decorate-input-and-output-properties)
    * [Avoid aliasing inputs and outputs](#Avoid-aliasing-inputs-and-outputs)
    * [Member sequence](#Member-sequence)
    * [Delegate complex component logic to services](#Delegate-complex-component-logic-to-services)
    * [Don't prefix output properties](#do-not-prefix-output-properties)
    * [Put presentation logic in the component class](#put-presentation-logic-in-the-component-class)
* [Directives](#Use-directives-to-enhance-an-element)
    * [Use directives to enhance an element](#Use-directives-to-enhance-an-element)
    * [HostListener and HostBinding decorators versus host metadata](#HostListener-and-host-binding-decorators-versus-host-metadata)
* [Services](#Services)
    * [Services are singletons](#Services-are-singletons)
    * [Single responsibility](#Single-responsibility)
    * [Providing a service](#Providing-a-service)
    * [Use the class decorator](#Use-the-class-decorator)
* [Data Services](#Data-services)
    * [Talk to the server through a service](#Talk-to-the-server-through-a-service)
* [Lifecycle hooks](#Lifecycle-hooks)
    * [Implement lifecycle hook interfaces](#Implement-lifecycle-hook-interfaces)

## File structure conventions
Some code examples display a file that has one or more similarly named companion files. For example, hero.component.ts and hero.component.html.

The guideline uses the shortcut hero.component.ts|html|scss|spec to represent those various files. Using this shortcut makes this guide's file structures easier to read and more terse.

## Ordering

> Ordering for class

    1. @Input() / @Output () 
    2. variables
    3. optional static methods
    4. constructor
    5. ngOnChanges()
    6. ngOnInit()
    7. ngDoCheck()
    8. ngAfterContentInit()
    9. ngAfterContentChecked()
    10.ngAfterViewInit() 
    11. ngAfterViewChecked()
    12. business logic processing methods
    13. clickHandlers or eventHandlers like clickSubmit() or changeDescription() 
    14. ngOnDestroy()

## **Single responsibility**

## Rule of One

Apply the [single responsibility principle (SRP)](https://wikipedia.org/wiki/Single_responsibility_principle) to all components, services, and other symbols. This helps make the app cleaner, easier to read and maintain, and more testable.

It is a better practice to redistribute the component and its supporting classes into their own, dedicated files.

>Define one thing, such as a service or component, per file.
__Consider__ limiting files to 400 lines of code.

 * One component per file makes it far easier to read, maintain, and avoid collisions with teams in source control.
 * One component per file avoids hidden bugs that often arise when combining components in a file where they may share variables, create unwanted closures, or unwanted coupling with dependencies.
 * A single component can be the default export for its file which facilitates lazy loading with the router.

The key is to make the code more reusable, easier to read, and less mistake prone.

## Small functions

>Define small functions.
__Consider__ limiting to no more than 75 lines.
* Small functions are easier to test, especially when they do one thing and serve one purpose.
* Small functions promote reuse.
* Small functions are easier to read.
* Small functions are easier to maintain.
* Small functions help avoid hidden bugs that come with large functions that share variables with external scope, create unwanted closures, or unwanted coupling with dependencies.

## **Naming**

## General Naming Guidelines

>Use consistent names for all symbols. Follow a pattern that describes the symbol's feature then its type. The recommended pattern is feature.type.ts.

* Naming conventions help provide a consistent way to find content at a glance. Consistency within the project is vital. Consistency with a team is important. Consistency across a company provides tremendous efficiency.

* The naming conventions should simply help find desired code faster and make it easier to understand.

* Names of folders and files should clearly convey their intent. For example, app/heroes/hero-list.component.ts may contain a component that manages a list of heroes.

## Separate file names with dots and dashes

>Use dashes to separate words in the descriptive name. Use dots to separate the descriptive name from the type.

>Use conventional type names including .service, .component, .pipe, .module, .enum, .validator, .action, .reducer, .effect, .guard, .resolver, .interface, .model, and .directive. Invent additional type names if you must but take care not to create too many.

* Type names provide a consistent way to quickly identify what is in the file.

* Type names make it easy to find a specific file type using an editor or IDE's fuzzy search techniques.

* Unabbreviated type names such as .service are descriptive and unambiguous. Abbreviations such as .srv, .svc, and .serv can be confusing.

* Type names provide pattern matching for any automated tasks

## Symbols and file names

>Use consistent names for all assets named after what they represent. 

>Use Pascal case for class names. Match the name of the symbol to the name of the file. 

>Append the symbol name with the conventional suffix (such as Component, Directive, Module, Pipe, or Service) for a thing of that type. 

>Give the filename the conventional suffix (such as .component.ts, .directive.ts, .module.ts, .pipe.ts, or .service.ts) for a file of that type.

* Consistent conventions make it easy to quickly identify and reference assets of different types.

```ts
@Component({ ... })
export class AppComponent { }  //app.component.ts

@Component({ ... })
export class HeroesComponent { }  //heroes.component.ts

@Component({ ... })
export class HeroListComponent { }  //hero-list.component.ts

@Component({ ... })
export class HeroDetailComponent { }  //hero-detail.component.ts

@Directive({ ... })
export class ValidationDirective { }  //validation.directive.ts

@NgModule({ ... })
export class AppModule  //app.module.ts

@Pipe({ name: 'initCaps' })
export class InitCapsPipe implements PipeTransform { } //init-caps.pipe.ts

@Injectable()
export class UserProfileService { } // user-profile.service.ts
```

## Service names

> Use consistent names for all services named after their feature.

> Suffix a service class name with Service. For example, something that gets data or heroes should be called a DataService or a HeroService.

A few terms are unambiguously services. They typically indicate agency by ending in "-er". You may prefer to name a service that logs messages Logger rather than LoggerService. Decide if this exception is agreeable in your project. As always, strive for consistency.

* Provides a consistent way to quickly identify and reference services.

* Clear service names such as Logger do not require a suffix.

* Service names such as Credit are nouns and require a suffix and should be named with a suffix when it is not obvious if it is a service or something else.

```ts
@Injectable()
export class HeroDataService { }
hero-data.service.ts

@Injectable()
export class CreditService { }
credit.service.ts

@Injectable()
export class Logger { }
logger.service.ts
```

## Component selectors

> Use dashed-case or kebab-case for naming the element selectors of components.

* Keeps the element names consistent with the specification for [Custom Elements](https://www.w3.org/TR/custom-elements/).

```ts
/* avoid */

@Component({
  selector: 'tohHeroButton',
  templateUrl: './hero-button.component.html'
})
export class HeroButtonComponent {}
```

## Component custom prefix

> Use a hyphenated, lowercase element selector value; for example, admin-users.

> Use a custom prefix for a component selector. For example, the prefix toh represents Tour of Heroes and the prefix admin represents an admin feature area.

> Use a prefix that identifies the feature area or the app itself.

* Prevents element name collisions with components in other apps and with native HTML elements.

* Makes it easier to promote and share the component in other apps.

* Components are easy to identify in the DOM.

## Directive selectors

> Use camel case for naming the selectors of directives.

* Keeps the names of the properties defined in the directives that are bound to the view consistent with the attribute names.

* The Angular HTML parser is case sensitive and recognizes lower camel case.

**Bad**
``` ts
/* avoid */

@Directive({
  selector: '[validate]'
})
export class ValidateDirective {}
```

**Good**
```ts
@Directive({
  selector: '[tohValidate]'
})
export class ValidateDirective {}
```

## Pipe names

> Use consistent names for all pipes, named after their feature. The pipe class name should use UpperCamelCase (the general convention for class names), and the corresponding name string should use lowerCamelCase. The name string cannot use hyphens ("dash-case" or "kebab-case").

* Provides a consistent way to quickly identify and reference pipes.

```ts
@Pipe({ name: 'ellipsis' })
export class EllipsisPipe implements PipeTransform { } //ellipsis.pipe.ts

@Pipe({ name: 'initCaps' })
export class InitCapsPipe implements PipeTransform { } //init-caps.pipe.ts
```

## Angular NgModule names

> Append the symbol name with the suffix Module.

> Give the file name the .module.ts extension.

> Name the module after the feature and folder it resides in.

* Provides a consistent way to quickly identify and reference modules.

* Upper camel case is conventional for identifying objects that can be instantiated using a constructor.

* Easily identifies the module as the root of the same named feature.

> Suffix a RoutingModule class name with RoutingModule.

> End the filename of a RoutingModule with -routing.module.ts.

* A RoutingModule is a module dedicated exclusively to configuring the Angular router. A consistent class and file name convention make these modules easy to spot and verify.

``` ts
@NgModule({ ... })
export class AppModule { }
// app.module.ts

@NgModule({ ... })
export class HeroesModule { }
// heroes.module.ts

@NgModule({ ... })
export class VillainsModule { }
// villains.module.ts

@NgModule({ ... })
export class AppRoutingModule { }
// app-routing.module.ts

@NgModule({ ... })
export class HeroesRoutingModule { }
// heroes-routing.module.ts
```
## Application structure and NgModules
Have a near-term view of implementation and a long-term vision. Start small but keep in mind where the app is heading down the road.

All of the app's code goes in a folder named src. All feature areas are in their own folder, with their own NgModule.

All content is one asset per file. Each component, service, and pipe is in its own file. All third party vendor scripts are stored in another folder and not in the src folder. You didn't write them and you don't want them cluttering src. Use the naming conventions for files in this guide.

## **Application structure and NgModules**

## LIFT principle

> Structure the app such that you can **L**-ocate code quickly, **I**-dentify the code at a glance, keep the **F**-lattest structure you can, and **T**-ry to be DRY.

> Define the structure to follow these four basic guidelines, listed in order of importance.

* LIFT provides a consistent structure that scales well, is modular, and makes it easier to increase developer efficiency by finding code quickly. To confirm your intuition about a particular structure, ask: can I quickly open and start work in all of the related files for this feature?

## Locate

> Make locating code intuitive, simple, and fast.

* To work efficiently you must be able to find files quickly, especially when you do not know (or do not remember) the file names. Keeping related files near each other in an intuitive location saves time. A descriptive folder structure makes a world of difference to you and the people who come after you.

## Identify

> Name the file such that you instantly know what it contains and represents.

> Be descriptive with file names and keep the contents of the file to exactly one component.

>**Avoid** files with multiple components, multiple services, or a mixture.

* Spend less time hunting and pecking for code, and become more efficient. Longer file names are far better than short-but-obscure abbreviated names.

>**Note** : It may be advantageous to deviate from the one-thing-per-file rule when you have a set of small, closely-related features that are better discovered and understood in a single file than as multiple files. Be wary of this loophole.

## Flat

>Keep a flat folder structure as long as possible.

>Consider creating sub-folders when a folder reaches seven or more files.

>Consider configuring the IDE to hide distracting, irrelevant files such as generated .js and .js.map files.

* No one wants to search for a file through seven levels of folders. A flat structure is easy to scan.

On the other hand, psychologists believe that humans start to struggle when the number of adjacent interesting things exceeds nine. So when a folder has ten or more files, it may be time to create subfolders.

Base your decision on your comfort level. Use a flatter structure until there is an obvious value to creating a new folder.

## DRY-principle

>Be DRY (Don't Repeat Yourself).

>**Avoid** being so DRY that you sacrifice readability.

* Being DRY is important, but not crucial if it sacrifices the other elements of LIFT. That's why it's called T-DRY. For example, it's redundant to name a template hero-view.component.html because with the .html extension, it is obviously a view. But if something is not obvious or departs from a convention, then spell it out.

## Overall structural guidelines

> Start small but keep in mind where the app is heading down the road.

> Have a near term view of implementation and a long term vision.

> Put all of the app's code in a folder named src.

**Consider** creating a folder for a component when it has multiple accompanying files (.ts, .html, .css and .spec).

* Helps keep the app structure small and easy to maintain in the early stages, while being easy to evolve as the app grows.

* Components often have four files (e.g. *.html, *.css, *.ts, and *.spec.ts) and can clutter a folder quickly.

>**Note**: While components in dedicated folders are widely preferred, another option for small apps is to keep components flat (not in a dedicated folder). This adds up to four files to the existing folder, but also reduces the folder nesting. Whatever you choose, be consistent.


## Folders-by-feature structure

> Create folders named for the feature area they represent.

* A developer can locate the code and identify what each file represents at a glance. The structure is as flat as it can be and there are no repetitive or redundant names.

* The LIFT guidelines are all covered.

* Helps reduce the app from becoming cluttered through organizing the content and keeping them aligned with the LIFT guidelines.

* When there are a lot of files, for example 10+, locating them is easier with a consistent folder structure and more difficult in a flat structure.

> Create an NgModule for each feature area.

* NgModules make it easy to lazy load routable features.

* NgModules make it easier to isolate, test, and reuse features.

## App root module

> Create an NgModule in the app's root folder, for example, in /src/app.

* Every app requires at least one root NgModule.

**Consider** naming the root module app.module.ts.

* Makes it easier to locate and identify the root module.

## Feature modules

> Create an NgModule for all distinct features in an application; for example, a Heroes feature.

> Place the feature module in the same named folder as the feature area; for example, in app/heroes.

> Name the feature module file reflecting the name of the feature area and folder; for example, app/heroes/heroes.module.ts.

> Name the feature module symbol reflecting the name of the feature area, folder, and file; for example, app/heroes/heroes.module.ts defines HeroesModule.

* A feature module can expose or hide its implementation from other modules.

* A feature module identifies distinct sets of related components that comprise the feature area.

* A feature module can easily be routed to both eagerly and lazily.

* A feature module defines clear boundaries between specific functionality and other application features.

* A feature module helps clarify and make it easier to assign development responsibilities to different teams.

* A feature module can easily be isolated for testing.

## Shared feature module

> Create a feature module named SharedModule in a shared folder; for example, app/shared/shared.module.ts defines SharedModule.

> Declare components, directives, and pipes in a shared module when those items will be re-used and referenced by the components declared in other feature modules.

**Consider** using the name SharedModule when the contents of a shared module are referenced across the entire application.

**Consider** not providing services in shared modules. Services are usually singletons that are provided once for the entire application or in a particular feature module. There are exceptions, however. For example, in the sample code that follows, notice that the SharedModule provides FilterTextService. This is acceptable here because the service is stateless;that is, the consumers of the service aren't impacted by new instances.

> Import all modules required by the assets in the SharedModule; for example, CommonModule and FormsModule.

* SharedModule will contain components, directives and pipes that may need features from another common module; for example, ngFor in CommonModule.

> Declare all components, directives, and pipes in the SharedModule.

> Export all symbols from the SharedModule that other feature modules need to use.

* SharedModule exists to make commonly used components, directives and pipes available for use in the templates of components in many other modules.

>**Avoid** specifying app-wide singleton providers in a SharedModule. Intentional singletons are OK. Take care.

* A lazy loaded feature module that imports that shared module will make its own copy of the service and likely have undesirable results.

* You don't want each module to have its own separate instance of singleton services. Yet there is a real danger of that happening if the SharedModule provides a service.

## Lazy Loaded folders

A distinct application feature or workflow may be lazy loaded or loaded on demand rather than when the application starts.

> Put the contents of lazy loaded features in a lazy loaded folder. A typical lazy loaded folder contains a routing component, its child components, and their related assets and modules.

* The folder makes it easy to identify and isolate the feature content.

## Never directly import lazy loaded folders

>**Avoid** allowing modules in sibling and parent folders to directly import a module in a lazy loaded feature.

* Directly importing and using a module will load it immediately when the intention is to load it on demand.

## **Components**

## Components as elements

**Consider** giving components an element selector, as opposed to attribute or class selectors.

* Components have templates containing HTML and optional Angular template syntax. They display content. Developers place components on the page as they would native HTML elements and web components.

* It is easier to recognize that a symbol is a component by looking at the template's html.

>There are a few cases where you give a component an attribute, such as when you want to augment a built-in element. For example, [Material Design](https://material.angular.io/components/button/overview) uses this technique with ```<button mat-button>```. However, you wouldn't use this technique on a custom element.

*app/heroes/hero-button/hero-button.component.ts*
``` ts
/* avoid */

@Component({
  selector: '[tohHeroButton]',
  templateUrl: './hero-button.component.html'
})
export class HeroButtonComponent {}

```
*app/app.component.html*
```html
<!-- avoid -->

<div tohHeroButton></div>
```

## Extract templates and styles to their own files

>Extract templates and styles into a separate file, when more than 3 lines.

>Name the template file [component-name].component.html, where [component-name] is the component name.

>Name the style file [component-name].component.css, where [component-name] is the component name.

>Specify component-relative URLs, prefixed with ./.

* Large, inline templates and styles obscure the component's purpose and implementation, reducing readability and maintainability.

* In most editors, syntax hints and code snippets aren't available when developing inline templates and styles. The Angular TypeScript Language Service (forthcoming) promises to overcome this deficiency for HTML templates in those editors that support it; it won't help with CSS styles.

* A component relative URL requires no change when you move the component files, as long as the files stay together.

* The ./ prefix is standard syntax for relative URLs; don't depend on Angular's current ability to do without that prefix.

## Decorate input and output properties

>Use the ```@Input()``` and ```@Output()``` class decorators instead of the inputs and outputs properties of the @Directive and @Component metadata:

**Consider** placing ```@Input()``` or`` @Output()`` on the same line as the property it decorates.

* It is easier and more readable to identify which properties in a class are inputs or outputs.

* If you ever need to rename the property or event name associated with ``@Input()`` or ``@Output()``, you can modify it in a single place.

* The metadata declaration attached to the directive is shorter and thus more readable.

* Placing the decorator on the same line usually makes for shorter code and still easily identifies the property as an input or output. Put it on the line above when doing so is clearly more readable.

## Avoid aliasing inputs and outputs

>**Avoid** input and output aliases except when it serves an important purpose.

* Two names for the same property (one private, one public) is inherently confusing.

* You should use an alias when the directive name is also an input property, and the directive name doesn't describe the property.

*app/heroes/shared/hero-button/hero-button.component.ts*
``` ts
/* avoid pointless aliasing */

@Component({
  selector: 'toh-hero-button',
  template: `<button>{{label}}</button>`
})
export class HeroButtonComponent {
  // Pointless aliases
  @Output('heroChangeEvent') heroChange = new EventEmitter<any>();
  @Input('labelAttribute') label: string;
```
*app/app.component.html*
``` html
<!-- avoid -->

<toh-hero-button labelAttribute="OK" (changeEvent)="doSomething()">
</toh-hero-button>
```

## Member sequence

> Place properties up top followed by methods.

> Place private members after public members, alphabetized.

* Placing members in a consistent sequence makes it easy to read and helps instantly identify which members of the component serve which purpose.
**BAD**
```ts
/* avoid */

export class ToastComponent implements OnInit {

  private defaults = {
    title: '',
    message: 'May the Force be with you'
  };
  message: string;
  title: string;
  private toastElement: any;

  ngOnInit() {
    this.toastElement = document.getElementById('toh-toast');
  }

  // private methods
  private hide() {
    this.toastElement.style.opacity = 0;
    window.setTimeout(() => this.toastElement.style.zIndex = 0, 400);
  }

  activate(message = this.defaults.message, title = this.defaults.title) {
    this.title = title;
    this.message = message;
    this.show();
  }

  private show() {
    console.log(this.message);
    this.toastElement.style.opacity = 1;
    this.toastElement.style.zIndex = 9999;

    window.setTimeout(() => this.hide(), 2500);
  }
}
```
**GOOD**
``` ts
export class ToastComponent implements OnInit {
  // public properties
  message: string;
  title: string;

  // private fields
  private defaults = {
    title: '',
    message: 'May the Force be with you'
  };
  private toastElement: any;

  // public methods
  activate(message = this.defaults.message, title = this.defaults.title) {
    this.title = title;
    this.message = message;
    this.show();
  }

  ngOnInit() {
    this.toastElement = document.getElementById('toh-toast');
  }

  // private methods
  private hide() {
    this.toastElement.style.opacity = 0;
    window.setTimeout(() => this.toastElement.style.zIndex = 0, 400);
  }

  private show() {
    console.log(this.message);
    this.toastElement.style.opacity = 1;
    this.toastElement.style.zIndex = 9999;
    window.setTimeout(() => this.hide(), 2500);
  }
}
```

## Delegate complex component logic to services
> Limit logic in a component to only that required for the view. All other logic should be delegated to services.

> Move reusable logic to services and keep components simple and focused on their intended purpose.

* Logic may be reused by multiple components when placed within a service and exposed via a function.

* Logic in a service can more easily be isolated in a unit test, while the calling logic in the component can be easily mocked.

* Removes dependencies and hides implementation details from the component.

* Keeps the component slim, trim, and focused.

## Do not prefix output properties

> Name events without the prefix on.

> Name event handler methods with the prefix on followed by the event name.

* This is consistent with built-in events such as button clicks.

* Angular allows for an alternative syntax on-*. If the event itself was prefixed with on this would result in an on-onEvent binding expression.

## Put presentation logic in the component class

> Put presentation logic in the component class, and not in the template.

* Logic will be contained in one place (the component class) instead of being spread in two places.

* Keeping the component's presentation logic in the class instead of the template improves testability, maintainability, and reusability

## **Directives**

## Use directives to enhance an element

> Use attribute directives when you have presentation logic without a template.

* Attribute directives don't have an associated template.

* An element may have more than one attribute directive applied.

## HostListener and HostBinding decorators versus host metadata

**Consider** preferring the @HostListener and @HostBinding to the host property of the @Directive and @Component decorators.

> be consistent in your choice.

* The property associated with @HostBinding or the method associated with @HostListener can be modified only in a single place—in the directive's class. If you use the host metadata property, you must modify both the property/method declaration in the directive's class and the metadata in the decorator associated with the directive.

*app/shared/validator.directive.ts*
``` ts
import { Directive, HostBinding, HostListener } from '@angular/core';

@Directive({
  selector: '[tohValidator]'
})
export class ValidatorDirective {
  @HostBinding('attr.role') role = 'button';
  @HostListener('mouseenter') onMouseEnter() {
    // do work
  }
}
```

Compare with the less preferred host metadata alternative.

* The host metadata is only one term to remember and doesn't require extra ES imports.

``` ts
import { Directive } from '@angular/core';

@Directive({
  selector: '[tohValidator2]',
  host: {
    '[attr.role]': 'role',
    '(mouseenter)': 'onMouseEnter()'
  }
})
export class Validator2Directive {
  role = 'button';
  onMouseEnter() {
    // do work
  }
}
```
## *Services*

## Services are singletons

> Use services as singletons within the same injector. Use them for sharing data and functionality.

* Services are ideal for sharing methods across a feature area or an app.

* Services are ideal for sharing stateful in-memory data.

*app/heroes/shared/hero.service.ts*

``` ts
export class HeroService {
  constructor(private http: HttpClient) { }

  getHeroes() {
    return this.http.get<Hero[]>('api/heroes');
  }
}
```

## Single responsibility

> Create services with a single responsibility that is encapsulated by its context.

> Create a new service once the service begins to exceed that singular purpose.

* When a service has multiple responsibilities, it becomes difficult to test.

* When a service has multiple responsibilities, every component or service that injects it now carries the weight of them all.

## Providing a service

> Provide a service with the app root injector in the ```@Injectable ```decorator of the service.

* The Angular injector is hierarchical.

* When you provide the service to a root injector, that instance of the service is shared and available in every class that needs the service. This is ideal when a service is sharing methods or state.

* When you register a service in the ```@Injectable``` decorator of the service, optimization tools such as those used by the Angular CLI's production builds can perform tree shaking and remove services that aren't used by your app.

* This is not ideal when two different components need different instances of a service. In this scenario it would be better to provide the service at the component level that needs the new and separate instance.

*src/app/treeshaking/service.ts*
```ts
@Injectable({
  providedIn: 'root',
})
export class Service {
}
```
## Use the class decorator

> Use the @Injectable() class decorator instead of the @Inject parameter decorator when using types as tokens for the dependencies of a service.

* The Angular Dependency Injection (DI) mechanism resolves a service's own dependencies based on the declared types of that service's constructor parameters.

* When a service accepts only dependencies associated with type tokens, the @Injectable() syntax is much less verbose compared to using @Inject() on each individual constructor parameter.

**BAD**
``` ts
/* avoid */

export class HeroArena {
  constructor(
      @Inject(HeroService) private heroService: HeroService,
      @Inject(HttpClient) private http: HttpClient) {}
}
```
**GOOD**

```ts
@Injectable()
export class HeroArena {
  constructor(
    private heroService: HeroService,
    private http: HttpClient) {}
}
```

## *Data Services*

## Talk to the server through a service

> Refactor logic for making data operations and interacting with data to a service.

> Make data services responsible for XHR calls, local storage, stashing in memory, or any other data operations.

* The component's responsibility is for the presentation and gathering of information for the view. It should not care how it gets the data, just that it knows who to ask for it. Separating the data services moves the logic on how to get it to the data service, and lets the component be simpler and more focused on the view.

* This makes it easier to test (mock or real) the data calls when testing a component that uses a data service.

* The details of data management, such as headers, HTTP methods, caching, error handling, and retry logic, are irrelevant to components and other data consumers.

A data service encapsulates these details. It's easier to evolve these details inside the service without affecting its consumers. And it's easier to test the consumers with mock service implementations.

## **Lifecycle hooks**
Use Lifecycle hooks to tap into important events exposed by Angular.

## Implement lifecycle hook interfaces

> implement the lifecycle hook interfaces.

* Lifecycle interfaces prescribe typed method signatures. Use those signatures to flag spelling and syntax mistakes.

**BAD**
``` ts
/* avoid */

@Component({
  selector: 'toh-hero-button',
  template: `<button>OK<button>`
})
export class HeroButtonComponent {
  onInit() { // misspelled
    console.log('The component is initialized');
  }
}
```
**GOOD**
``` ts
@Component({
  selector: 'toh-hero-button',
  template: `<button>OK</button>`
})
export class HeroButtonComponent implements OnInit {
  ngOnInit() {
    console.log('The component is initialized');
  }
}
```

# Redux State management

* [Do Not Mutate State](#Do-not-mutate-state)
* [Reducers Must Not Have Side Effects](#Reducers-must-not-have-side-effects)
* [Do Not Put Non-Serializable Values in State or Actions](#Do-not-put-non-serializable-values-in-state-or-actions)
* [Structure Files as Feature Folders or Ducks](#Structure-files-as-feature-folders-or-ducks)
* [Reducers Should Own the State Shape](#Reducers-should-own-the-state-shape)
* [Treat Reducers as State Machines](#Treat-reducers-as-state-machines)
* [Normalize Complex Nested/Relational State](#Normalize-complex-nested-relational-state)
* [Model Actions as Events, Not Setters](#model-actions-as-events-not-setters)
* [Write Meaningful Action Names](#write-meaningful-action-names)
* [Allow Many Reducers to Respond to the Same Action](#allow-many-reducers-to-respond-to-the-same-action)
* [Avoid Dispatching Many Actions Sequentially](#Avoid-dispatching-many-actions-sequentially)
* [Evaluate Where Each Piece of State Should Live](#evaluate-where-each-piece-of-state-should-live)
* [Use Plain JavaScript Objects for State](#use-plain-java-script-objects-for-state)
* [Write Action Types as domain/eventName](#write-action-types-as-domain-event-name)
* [Use Action Creators](#use-action-creators)
* [Use Selector Functions to Read from Store State](#use-selector-functions-to-read-from-store-state)

## Do Not Mutate State

Mutating state is the most common cause of bugs in Redux applications, including components failing to re-render properly, and will also break time-travel debugging in the Redux DevTools. Actual mutation of state values should always be avoided, both inside reducers and in all other application code.

## Reducers Must Not Have Side Effects

Reducer functions should only depend on their state and action arguments, and should only calculate and return a new state value based on those arguments. They must not execute any kind of asynchronous logic (AJAX calls, timeouts, promises), generate random values (Date.now(), Math.random()), modify variables outside the reducer, or run other code that affects things outside the scope of the reducer function.
Note: It is acceptable to have a reducer call other functions that are defined outside of itself, such as imports from libraries or utility functions, as long as they follow the same rules.

## Do Not Put Non-Serializable Values in State or Actions

Avoid putting non-serializable values such as Promises, Symbols, Maps/Sets, functions, or class instances into the Redux store state or dispatched actions. This ensures that capabilities such as debugging via the Redux DevTools will work as expected. It also ensures that the UI will update as expected.

A standard Redux application should only have a single Redux store instance, which will be used by the whole application. It should typically be defined in a separate file such as store.js or reducers/index.js.

## Structure Files as Feature Folders or Ducks
Redux itself does not care about how your application's folders and files are structured. However, co-locating logic for a given feature in one place typically makes it easier to maintain that code.

Because of this, we recommend that most applications should structure files using a "feature folder" approach (all files for a feature in the same folder) or the "ducks" pattern (all Redux logic for a feature in a single file), rather than splitting logic across separate folders by "type" of code (reducers, actions, etc).
Detailed Explanation
An example folder structure might look something like:

-   /src
    -   /app
        -   app.component.ts
        -   app.module.ts
    -   /store
        -   /actions
            -   todo.action.ts
        -   /reducers
            -   todo.reducer.ts
            -   index.ts
        -   /effects
            -   todos.effect.ts


<span style="background: grey"> /app </span>  contains app-wide setup and layout that depends on all the other folders.

<span style="background: grey">/store</span> has folders that contain all functionality related to a state management. In this 


## Reducers Should Own the State Shape

The Redux root state is owned and calculated by the single root reducer function. For maintainability, that reducer is intended to be split up by key/value "slices", with each "slice reducer" being responsible for providing an initial value and calculating the updates to that slice of the state.

Picture a "current user" reducer that looks like:
``` js
        const initialState = {
            firstName: null,
            lastName: null,
            age: null,
        };

        export default usersReducer = (state = initialState, action) {
            switch(action.type) {
                case "users/userLoggedIn": {
                    return action.payload;
                }
                default: return state;
            }
        }
```
In this example, the reducer completely assumes that <span style="background: grey"> action.payload </span> is going to be a correctly formatted object.

However, imagine if some part of the code were to dispatch a "todo" object inside the action, instead of a "user" object:
``` js
        dispatch({
            type: 'users/userLoggedIn',
            payload: {
                id: 42,
                text: 'Buy milk'
            }
        })
```
The reducer would blindly return the todo, and now the rest of the app would likely break when it tries to read the user from the store.

This could be at least partly fixed if the reducer has some validation checks to ensure that <span style="background: grey">action.payload</span> actually has the right fields, or tries to read the right fields out by name. That does add more code, though, so it's a question of trading off more code for safety.

Use of static typing does make this kind of code safer and somewhat more acceptable. If the reducer knows that action is a PayloadAction<User>, then it should be safe to do <span style="background: grey">return action.payload</span>

In addition, slice reducers should exercise control over what other values are returned as part of the calculated state. Minimize the use of "blind spreads/returns" like return action.payload or return {...state, ...action.payload}, because those rely on the code that dispatched the action to correctly format the contents, and the reducer effectively gives up its ownership of what that state looks like. That can lead to bugs if the action contents are not correct.

>__Note__: A "spread return" reducer may be a reasonable choice for scenarios like editing data in a form, where writing a separate action type for each individual field would be time-consuming and of little benefit.

Name State Slices Based On the Stored Data
As mentioned in Reducers Should Own the State Shape , the standard approach for splitting reducer logic is based on "slices" of state. Correspondingly, rootReducer: ActionReducerMap<IAppState> is the standard object for joining those slice reducers into a larger reducer function.

The key names in the object of rootReducer: ActionReducerMap<IAppState> will define the names of the keys in the resulting state object. Be sure to name these keys after the data that is kept inside, and avoid use of the word "reducer" in the key names. Your object should look like <span style="background: grey">{users: {}, posts: {}}</span>, rather than <span style="background: grey">{usersReducer: {}, postsReducer: {}}</span>.
ES6 object literal shorthand makes it easy to define a key name and a value in an object at the same time:
``` js
        const data = 42
        const obj = { data }
        // same as: {data: data}
```
combineReducers accepts an object full of reducer functions, and uses that to generate state objects that have the same key names. This means that the key names in the functions object define the key names in the state object.

This results in a common mistake, where a reducer is imported using "reducer" in the variable name, and then passed to combineReducers using the object literal shorthand:
``` js
        import usersReducer from 'features/users/usersSlice'

        const rootReducer = combineReducers({
            usersReducer
        })
```
In this case, use of the object literal shorthand created an object like {usersReducer: usersReducer}. So, "reducer" is now in the state key name. This is redundant and useless.

Instead, define key names that only relate to the data inside. We suggest using explicit key: value syntax for clarity:
``` js
        import usersReducer from 'features/users/usersSlice'
        import postsReducer from 'features/posts/postsSlice'

        const rootReducer = combineReducers({
            users: usersReducer,
            posts: postsReducer
        })
```
It's a bit more typing, but it results in the most understandable code and state definition.

## Treat Reducers as State Machines

Many Redux reducers are written "unconditionally". They only look at the dispatched action and calculate a new state value, without basing any of the logic on what the current state might be. This can cause bugs, as some actions may not be "valid" conceptually at certain times depending on the rest of the app logic. For example, a "request succeeded" action should only have a new value calculated if the state says that it's already "loading", or an "update this item" action should only be dispatched if there is an item marked as "being edited".

To fix this, __treat reducers as "state machines", where the combination of both the current state and the dispatched action determines whether a new state value is actually calculated__, not just the action itself unconditionally.

### Detailed Explanation
A [ finite state machine ](https://en.wikipedia.org/wiki/Finite-state_machine) is a useful way of modeling something that should only be in one of a finite number of "finite states" at any time. For example, if you have a fetchUserReducer, the finite states can be:

* "idle" (fetching not started yet)
* "loading" (currently fetching the user)
* "success" (user fetched successfully)
* "failure" (user failed to fetch)

To make these finite states clear and make [impossible states impossible](https://kentcdodds.com/blog/make-impossible-states-impossible), you can specify a property that holds this finite state:
``` js
    const initialUserState = {
    status: 'idle', // explicit finite state
    user: null,
    error: null
    }
```
With TypeScript, this also makes it easy to use discriminated unions to represent each finite state. For instance, if state.status === 'success', then you would expect state.user to be defined and wouldn't expect state.error to be truthy. You can enforce this with types.

Typically, reducer logic is written by taking the action into account first. When modeling logic with state machines, it's important to take the state into account first. Creating "finite state reducers" for each state helps encapsulate behavior per state:
``` js
    import {
    FETCH_USER,
    // ...
    } from './actions'

    const IDLE_STATUS = 'idle';
    const LOADING_STATUS = 'loading';
    const SUCCESS_STATUS = 'success';
    const FAILURE_STATUS = 'failure';

    const fetchIdleUserReducer = (state, action) => {
    // state.status is "idle"
    switch (action.type) {
        case FETCH_USER:
        return {
            ...state,
            status: LOADING_STATUS
        }
        }
        default:
        return state;
    }
    }

    // ... other reducers

    const fetchUserReducer = (state, action) => {
        switch (state.status) {
            case IDLE_STATUS:
            return fetchIdleUserReducer(state, action);
            case LOADING_STATUS:
            return fetchLoadingUserReducer(state, action);
            case SUCCESS_STATUS:
            return fetchSuccessUserReducer(state, action);
            case FAILURE_STATUS:
            return fetchFailureUserReducer(state, action);
            default:
            // this should never be reached
            return state;
        }
    }
```
Now, since you're defining behavior per state instead of per action, you also prevent impossible transitions. For instance, a FETCH_USER action should have no effect when status === LOADING_STATUS, and you can enforce that, instead of accidentally introducing edge-cases.

## Normalize Complex Nested/Relational State
Many applications need to cache complex data in the store. That data is often received in a nested form from an API, or has relations between different entities in the data (such as a blog that contains Users, Posts, and Comments).

__Prefer storing that data in a "normalized" form in the store__. This makes it easier to look up items based on their ID and update a single item in the store, and ultimately leads to better performance patterns.

## Model Actions as Events, Not Setters
Redux does not care what the contents of the action.type field are - it just has to be defined. It is legal to write action types in present tense ("users/update"), past tense ("users/updated"), described as an event ("upload/progress"), or treated as a "setter" ("users/setUserName"). It is up to you to determine what a given action means in your application, and how you model those actions.

Recommend trying to treat actions more as "describing events that occurred", rather than "setters". Treating actions as "events" generally leads to more meaningful action names, fewer total actions being dispatched, and a more meaningful action log history. Writing "setters" often results in too many individual action types, too many dispatches, and an action log that is less meaningful.

### Detailed Explanation
Imagine you've got a restaurant app, and someone orders a pizza and a  bottle of Coke. You could dispatch an action like:
```js
    { type: "food/orderAdded",  payload: {pizza: 1, coke: 1} }
```
Or you could dispatch:
```js
    {
        type: "orders/setPizzasOrdered",
        payload: {
            amount: getState().orders.pizza + 1,
        }
    }

    {
        type: "orders/setCokesOrdered",
        payload: {
            amount: getState().orders.coke + 1,
        }
    }
```
The first example would be an "event". "Hey, someone ordered a pizza and a pop, deal with it somehow".

The second example is a "setter". "I know there are fields for 'pizzas ordered' and 'pops ordered', and I am commanding you to set their current values to these numbers".

The "event" approach only really needed a single action to be dispatched, and it's more flexible. It doesn't matter how many pizzas were already ordered. Maybe there's no cooks available, so the order gets ignored.

With the "setter" approach, the client code needed to know more about what the actual structure of the state is, what the "right" values should be, and ended up actually having to dispatch multiple actions to finish the "transaction".

## Write Meaningful Action Names

The action.type field serves two main purposes:

* Reducer logic checks the action type to see if this action should be handled to calculate a new state
* Action types are shown in the Redux DevTools history log for you to read

Per [Model Actions as "Events"](https://redux.js.org/style-guide/style-guide#model-actions-as-events-not-setters), the actual contents of the type field do not matter to Redux itself. However, the type value does matter to you, the developer. __Actions should be written with meaningful, informative, descriptive type fields__. Ideally, you should be able to read through a list of dispatched action types, and have a good understanding of what happened in the application without even looking at the contents of each action. Avoid using very generic action names like "SET_DATA" or "UPDATE_STORE", as they don't provide meaningful information on what happened

## Allow Many Reducers to Respond to the Same Action
Redux reducer logic is intended to be split into many smaller reducers, each independently updating their own portion of the state tree, and all composed back together to form the root reducer function. When a given action is dispatched, it might be handled by all, some, or none of the reducers.

As part of this, you are encouraged to __have many reducer functions all handle the same action separately__ if possible. In practice, experience has shown that most actions are typically only handled by a single reducer function, which is fine. But, modeling actions as "events" and allowing many reducers to respond to those actions will typically allow your application's codebase to scale better, and minimize the number of times you need to dispatch multiple actions to accomplish one meaningful update.

## Avoid Dispatching Many Actions Sequentially
__Avoid dispatching many actions in a row to accomplish a larger conceptual "transaction"__. This is legal, but will usually result in multiple relatively expensive UI updates, and some of the intermediate states could be potentially invalid by other parts of the application logic. Prefer dispatching a single "event"-type action that results in all of the appropriate state updates at once, or consider use of action batching addons to dispatch multiple actions with only a single UI update at the end.

## Evaluate Where Each Piece of State Should Live

The "Three Principles of Redux" says that "the state of your whole application is stored in a single tree". This phrasing has been over-interpreted. It does not mean that literally every value in the entire app must be kept in the Redux store. Instead, there should be a single place to find all values that you consider to be global and app-wide. Values that are "local" should generally be kept in the nearest UI component instead.

Because of this, it is up to you as a developer to decide what state should actually live in the Redux store, and what should stay in component state. Use these rules of thumb to help evaluate each piece of state and decide where it should live.

## Use Plain JavaScript Objects for State

Prefer using plain JavaScript objects and arrays for your state tree, rather than specialized libraries like Immutable.js. While there are some potential benefits to using Immutable.js, most of the commonly stated goals such as easy reference comparisons are a property of immutable updates in general, and do not require a specific library. This also keeps bundle sizes smaller and reduces complexity from data type conversions.

## Write Action Types as domain/eventName
The original Redux docs and examples generally used a "SCREAMING_SNAKE_CASE" convention for defining action types, such as "ADD_TODO" and "INCREMENT". This matches typical conventions in most programming languages for declaring constant values. The downside is that the uppercase strings can be hard to read.

Other communities have adopted other conventions, usually with some indication of the "feature" or "domain" the action is related to, and the specific action type. The NgRx community typically uses a pattern like "[Domain] Action Type", such as "[Login Page] Login". Other patterns like "domain:action" have been used as well.

Redux Toolkit's createSlice function currently generates action types that look like "domain/action", such as "todos/addTodo". Going forward, we suggest using the "domain/action" convention for readability.

## Use Action Creators

Prefer using action creators for dispatching any actions. 

## Use Selector Functions to Read from Store State
"Selector functions" are a powerful tool for encapsulating reading values from the Redux store state and deriving further data from those values. In addition, libraries like Reselect enable creating memoized selector functions that only recalculate results when the inputs have changed, which is an important aspect of optimizing performance.

We strongly recommend using memoized selector functions for reading store state whenever possible, and recommend creating those selectors with Reselect.

However, don't feel that you must write selector functions for every field in your state. Find a reasonable balance for granularity, based on how often fields are accessed and updated, and how much actual benefit the selectors are providing in your application.
