# Frameworks at Canopy
- RFC PR: https://github.com/CanopyTax/frontend-rfc/pull/12

## Definition
There are a lot of front-end frameworks out there and we use several at Canopy. By design we've sought to avoid locking ourselves
into a specific framework and becoming an `${frameworkX} shop`. This has come with a lot of pros and cons. Our goal is for the 
best tools to "bubble up", rather than be selected and pushed "top down".

## Why can we be so flexible with frameworks
- [single-spa](https://github.com/CanopyTax/single-spa)
- [SystemJS](https://github.com/systemjs/systemjs)
- [SOFE](https://github.com/CanopyTax/sofe)

### pros
- Easy to build, experiment, and change our tech stack.
- We aren't locked into Angular or React.
- We can, theorectially, choose the best framework for the job.

### cons
- It could become the wild west of frameworks, where each squad uses frameworks/tools that no one else has any familiarity with.
- Bundle size if multiple frameworks need to be downloaded
- Could affect hiring (Squad X has an opening but they use Framework Y so we have to hire a Y specialist)
- Standardized and sharable components / styles

## Squad vs Chapter vs Frontend-wide
All chapters should standardize on our supported frameworks.

When a new customer facing feature is being built it's important to recognize that introducing a new framework comes with a 
lot of costs and we have to manage those costs across the entire front-end. New frameworks should be added with care as a 
result it isn't a squad level decision.

Introducing a new framework requires your colleagues to understand the framework paradigm in order to make changes, fix bugs, or properly 
respond to an alert.


## Supported Frameworks
- React
- AngularJS (legacy)

We're currently moving away from AngularJS and have bubble-up standardized on React. We have a few experiments in Vue and 
Svelte but they aren't something we're fully committed to introducing into our application yet.


## Introducing a new framework

This is somethine that isn't well defined yet. Previous discussions have lead to a loose process resembling this:

  - Evaluate options (squad)
  - Build Squad concensious
  - Discuss it with Chapter lead
  - Build some concensious frontend-wide
  - Get approval from chapter leads
  - Schedule a frontend training on the new framework.
