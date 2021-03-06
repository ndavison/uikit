FAQs
====

> This page contains frequently asked questions from our community.

If you can’t find the answer to your question, you can email guides@digital.gov.au or join our conversation on
[Slack](http://guides.service.gov.au/join-slack/).


## Contents

* [General](#general)
* [Design](#design)
* [Development](#development)


----------------------------------------------------------------------------------------------------------------------------------------------------------------


## General

### Is there any documentation or list of components?
You can find the Design System documentation at [designsystem.gov.au](http://designsystem.gov.au/). For further examples of our tests you can also see the [UI-kit unit tests](https://uikit.service.gov.au/).


### What are you working on?
You can view our [project backlog](https://github.com/orgs/govau/projects/7) to see an up to date list of tasks. We generally try to balance 50% community
engagement (capability uplift and understanding user needs) and 50% product (maintenance and building).


### What are the differences between version one and version two?
Version one was implemented following strict semantic HTML. This caused issues with implementation as users who didn’t have easy control over their HTML
struggled to implement the UI-Kit. Due to this version one is now deprecated and is no longer supported. Version two uses classes that need to be added.
This allows users to be more flexible with the HTML they are provided with.


### Who can use the UI-Kit?
The UI-Kit is built for everyone. We want government and private sector to embrace the UI-Kit. It aims to solve common usability and accessibility
problems in a simple and robust way.


### I found an issue/bug/problem. What do I do?
That’s awesome!
Please take a look at the Github [issue queue](https://github.com/govau/uikit/issues), if you find a relevant issue please join the conversation and note down
any steps you took to find it. If it’s a new issue please [create a new issue](https://github.com/govau/uikit/issues/new) and provide detailed instructions.
We’ve provided an [issue template](./ISSUE_TEMPLATE.md) to make this process easier.


**[⬆ back to top](#contents)**


----------------------------------------------------------------------------------------------------------------------------------------------------------------


## Design

### Why is there a `max-width` on elements inside the body?
To optimise readability we have set a `max-width` on certain elements inside the body. This creates a consistent and easy to use user interface. You can
override the code as necessary, but please understand your users needs.


### Are there `.psd` or `.sketch` files of the UI-Kit?
We currently don’t provide any design files. In the future we’d love to provide users with variations of files to allow them to access the latest
components in the UI-Kit.


### Why no carousels, tabs, and dropdowns?
Complicated functions and interactions need careful accessibility consideration during development and design; usually on a per-project basis. We plan on
looking at some of these things in the future and provide guidance around them.

- **Carousels:** hides content, are difficult to navigate, and often add more accessibility issues than they solve.  
	[http://bradfrost.com/blog/post/carousels/](http://bradfrost.com/blog/post/carousels/)  
	[http://shouldiuseacarousel.com/](http://shouldiuseacarousel.com/)
- **Tabs / Collapsible panels:** Need work to be done correctly. They can hide content, often spoil `find in page` functions, require understanding of how they
	work, add more accessibility issues.  
	[https://baymard.com/blog/accordion-and-tab-design](https://baymard.com/blog/accordion-and-tab-design)


**[⬆ back to top](#contents)**


----------------------------------------------------------------------------------------------------------------------------------------------------------------


## Development

### Is the UI-Kit available with my content management system or JavaScript framework?
The UI-Kit is built to be system agnostic. This means that it can work with any system, development environment, build tools or stack.
Currently we support three different entry-points:

- [vanilla JavaScript](https://www.w3.org/standards/techs/js)
- [jQuery](https://jquery.com/)
- [ReactJS](https://reactjs.org/)

There are also many communities which are connecting content management systems and other JavaScript frameworks to the UI-Kit. If you would like to do
the same we recommend having a look at the question
[How do I add the UI-Kit to my build process? How do I add custom code/variables/overrides?](#how-do-i-add-the-ui-kit-to-my-build-process-how-do-i-add-custom-codevariablesoverrides).


### Why are my HTML elements NOT automatically styled (`h1`, `input`, `blockquote`, etc.)?
The `body` and `headings` components are likely what you're looking for.

HTML elements no longer get styling from the UI-Kit by default. From our learnings in version 1, we decided it was best to provide our users with css classes which they can then invoke onto the HTML output their system provides.


### Why should I use the UI-Kit if I still have to write custom code?
The purpose of the UI-Kit is to help you get started and give you a foundation to work from, which will in turn provide a consistency and efficiency across
government projects. As with any framework, there is still an expectation that custom code will be needed to meet your specific needs.

However, we do plan to provide whole page templates in the future which will greatly minimise the need to write custom code.

Our recommendation is to write your custom code in a reusable and robust pattern. If you’re making a new component, follow the same patterns as the UI-Kit
components. That will allow you to contribute back, or replace those components in the future if your team want to implement another solution.


### What is pancake? Do I need to know pancake?
You don’t need to know or fully understand pancake. It’s a tool used to distribute the UI-Kit. We would recommend reading the
[repository documentation](https://github.com/govau/pancake) and having an understanding of the pancake object in the `package.json` file. Pancake allows users
to `npm install @gov.au/breadcrumbs` and get a the assets file copied into a folder of your choosing. It’s a powerful tool that we have built to enable us to
use npm as our distribution manager. This means that one user can have breadcrumbs version 1.2 and another can have version 2.1 and nothing will break.
Users can then choose to upgrade their components when necessary. A great
[article around pancake](https://medium.com/dailyjs/npm-and-the-front-end-950c79fc22ce) can be found on medium.


### How do I request a new component to be added to the system?

The best place to start is by looking for existing conversation in [the community forums](community.service.gov.au), followed by reviewing the [Contribution Guidelines.](https://github.com/govau/uikit/blob/master/CONTRIBUTING.md)



### How do I add the UI-Kit to my build process? How do I add custom code/variables/overrides?
Build processes can be complicated, we recommend first looking at our [UI-Kit starter pack](https://github.com/govau/uikit-starter). This is a simple
implementation of the UI-Kit showing how to include the UI-Kit into your project. After you `npm install` and run `npm run watch` you should have some generated
files. Looking at the `src/sass/main.scss` file you can see the order:

```
// OVERWRITES


// UI-Kit
@import 'uikit';

// CUSTOM SASS
```

This pattern is how we recommend to apply the UI-Kit. You are able to overwrite variables as we use the SASS
[`default`](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#Variable_Defaults___default) flag on our variables. Then when creating or overriding
existing components we recommend adding your code in the custom SASS section.


### How do I make a pull request? What branch should I pull request into?
[Pull requests](https://help.github.com/articles/fork-a-repo/) are awesome so thank you for reading this! The general procedure we follow when making a pull
request is:

1. Create a new branch off the development branch for what you’re working on
1. Do the necessary changes
1. If possible please test the work, we understand this is not always possible :)
1. Please submit your PR against the `develop` branch of the govau/uikit repo.


### What code standards do I need to follow for a pull request?
While we want to be open to the community and allow collaboration to happen without barriers, we do follow a strict set of
[rules](https://github.com/govau/uikit#checklist-and-browser-support) for code that ends up into the UI-Kit. It would be a great help if you could test
or specify what you have tested against that list. Please also work with the code style, not against it.


### Where can I get help implementing the UI-Kit with my project?
We currently have a community on [Slack](http://guides.service.gov.au/join-slack/) and [Github](https://github.com/govau/uikit). If you’re working on a
specific implementation with a JavaScript framework or content management system there may also be communities external to the UI-Kit.


**[⬆ back to top](#contents)**
