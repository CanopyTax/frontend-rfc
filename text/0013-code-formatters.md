# Project title
- Start Date: Mid 2016
- RFC PR: https://github.com/CanopyTax/frontend-rfc/pull/13

## Squad vs Chapter vs Frontend-wide
Each squad may choose whether to use a code formatter and, if so, which one to use.

## Definition
A code formatter is a tool that changes all source code in a project in a consistent way.

## Reason for decision
- There has traditionally been a difference in opinion about code formatters, so making it autonomous to squads is a decent compromise.
  For example, there were some feisty conversations where it was compared to a school uniform by some, and an industry standard by others :).
- The formatting and styling of code wasn't deemed important enough to enforce at a company wide level.

## Alternatives
- We could enforce the use of [Prettier](https://github.com/prettier/prettier) or another code formatter.

## Common practices (not enforced)
- If your squad is using a code formatter, consider adding a [pre-commit hook](https://prettier.io/docs/en/precommit.html) that automatically runs the code formatter.
  This makes it so people don't have to remember to run it everytime they push code.
- If your squad is using a code formatter, consider having the build fail if the source code does not match the formatted code.
  See [Prettier's Integration with eslint](https://prettier.io/docs/en/eslint.html) for more details.
