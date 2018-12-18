# Frameworks at Canopy
- RFC PR: https://github.com/CanopyTax/frontend-rfc/pull/12

## Squad vs Chapter vs Frontend-wide
Before using a framework outside our [supported frameworks](#supported-frameworks), squads should follow the path outlined 
in [Introducing a new framework](#introducing-a-new-framework).

## Definition
A UI framework is a library that creates DOM elements (e.g. React, Angular, Vue). Most of the most popular frameworks have an
implmentation of a "component" building block for creating user interfaces. On the frontend at Canopy we've embraced 
microservices that could be written in any framework (polyglot) instead of a single framework that everything must be built in.

## Reason for decision
Whenever a single framework is chosen it becomes the "core" of the application. It pushes us towards a single ecosystem and 
a single set of solutions. This works very well until that framework changes, either from a big rewrite (AngularJS -> Angular), 
the framework is no longer supported, or a new framework solves our problems better.

To avoid a cycle of framework migrations we've intentionally chosen to avoid locking ourselves into a specific framework and 
becoming an `${frameworkX} shop`. We've done this with a microservices approach. This has come with a lot of pros and cons. 
Our goal is for the best tools to "bubble up", rather than be selected and pushed "top down".

When a new customer facing feature is being built, it's important to recognize that introducing a new framework comes with a 
lot of costs and we have to manage those costs across the entire front-end. New frameworks should be added with care and, as a 
result, doing so isn't a squad level decision.

Introducing a new framework requires your colleagues to understand the framework paradigm in order to make changes, fix bugs, or properly 
respond to an alert.

## Why can we be so flexible with frameworks
- [single-spa](https://github.com/CanopyTax/single-spa)
- [SystemJS](https://github.com/systemjs/systemjs)
- [SOFE](https://github.com/CanopyTax/sofe)

### pros of our Polyglot/micro-services approach
- Easy to build, experiment, and change our tech stack.
- We aren't locked into Angular or React.
- We can, theorectially, choose the best framework for the job.
- Avoid product rewrites until the product needs to change.

### cons of our Polyglot/micro-services approach
- It could become the wild west of frameworks, where each squad uses frameworks/tools that no one else has any familiarity with.
- Bundle size if multiple frameworks need to be downloaded (initial load time performance)
- Could affect hiring (Squad X has an opening but they use Framework Y so we have to hire a Y specialist)
- Standardized and sharable components / styles
- Less ability to transfer between squads

### Managing our cons
- Limit ["fully supported"](supported-frameworks) frameworks
- Code splits and lazy loading
- Use webcomponents for styleguide components so any framework can use them
- Invest in tooling and DX (developer experience)

## Supported Frameworks
### Definition
A supported framework at Canopy is one that is already being used extensively. You can expect an easier path when using these 
frameworks since there is already a lot of infrastructure and tooling in place for them. When choosing a framework to use 
for a project, the supported frameworks can be used without going through the [Introducing a New Framework process](#introducing-a-new-framework)
### Fully Supported Frameworks
- React
- AngularJS (legacy)

We're currently moving away from AngularJS and have bubble-up standardized on React. We have a few experiments in Vue and 
Svelte but they aren't something we're fully committed to introducing into our application yet.

## Introducing a new framework
The core principle here is intentionality. We want to have a base level of familiarity across the entire frontend so anyone 
can commit to another squads project with relative ease.

At the squad level you'll need to do the following:
- Build squad consensus
- Find a small but meaningful area where a framework experiment could fit.
- Experiment freely, keeping in mind the challenges of interop between frameworks

If the experiment is successful and your squad wants to push to make the framework one of Canopy's fully supported frameworks 
do the following at the frontend organization level
- Pitch the framework
- Discuss how it would fit in our organization
- Get approval from Chapter leads (and eventually the technical track)
- Schedule a few trainings with the frontend chapter.
