# Code Style, Linters, and Code Formatters
- Start Date: First discussion in mid 2016, revived in 2017.
- RFC PR: https://github.com/CanopyTax/frontend-rfc/pull/14

## Squad vs Chapter vs Frontend-wide
All squads must use the rules defined in [eslint-config-canopy](https://github.com/CanopyTax/eslint-config-canopy) to lint the javascript code for deployed services.
Any code styling and linting beyond what is in eslint-config-canopy is not enforced and is autonomous to the squads. Each squad may choose whether to use a code
formatter and, if so, which one to use.

## Definition
[Code style](https://en.wikipedia.org/wiki/Programming_style) is the way that source code is indented and formatted. For example, code style includes whether code is indented
with tabs or spaces, whether it has semicolons after each line, whether an opening curly brace should be followed with a new line, etc.

A code formatter is a software tool that modifies source code to follow a set of coding style guidelines. The most popular javascript code formatter (at the time of this writing)
is [Prettier](https://prettier.io/).

A [linter](https://en.wikipedia.org/wiki/Lint_(software)) is a software tool that analyzes source code to find problems in it. Linters may raise warnings or errors about the following:
- Code style
- Bugs or potential errors in the code
- Best practices, including which parts of Javascript to allow or disallow

## Reason for decision
Linting and enforcing code style has historically been a controversial subject at Canopy. There have been strong feelings for and against it. Those for it argue that consistency increases the
readability and maintainability of code while also removing the need to discuss code style. Those who argue against it argue that enforcing code style and javascript best practices can be
oppressive for developers or lead to a culture where arbitrary best practices are constantly debated. Sometime in 2017, the two sides compromised on making a set of
linting rules that is not very opinionated about code style or javascript best practices, but instead focuses on finding bugs and enforcing a very small number of stylistic rules,
such as tabs vs spaces.

## Alternatives
Canopy could enforce the use of a more opinionated set of linter rules and/or enforce the use of a code formatter such as [Prettier](https://prettier.io/).

## Process for changing eslint-config-canopy
Anybody can submit a pull request to [eslint-config-canopy](https://github.com/CanopyTax/eslint-config-canopy) to start the process of changing the linter.
The process for deciding whether to merge the pull request is not well defined right now. If the pull request is not controversial, it can be merged without much
ceremony. But if the change is controversial, we should discuss as a group whether we want to merge it.

## Common practices (not enforced)
- Use [eslint](https://github.com/eslint/eslint) and [babel-eslint](https://github.com/babel/babel-eslint).
- Run eslint as part of the `test` step in the gitlab pipeline for projects.
- Use [husky](https://github.com/typicode/husky) to run eslint during the pre-commit or pre-push git hooks, so that developers don't have to wait for the gitlab build to fail
  to know that their code fails linting.
- Within each squad, discuss whether you'd like to enforce more strict linting rules or a code formatter.
- If your squad is using a code formatter, consider adding a [pre-commit hook](https://prettier.io/docs/en/precommit.html) that automatically runs the code formatter.
  This makes it so people don't have to remember to run it everytime they push code.
- If your squad is using a code formatter, consider having the build fail if the source code does not match the formatted code.
  See [Prettier's Integration with eslint](https://prettier.io/docs/en/eslint.html) for more details.
- Consider turning off your IDE's code formatting and Prettier when authoring code for projects that do not enforce a code formatter. This avoids code reviews where the reviewers
  are sifting through stylistic changes to find actual changes.
