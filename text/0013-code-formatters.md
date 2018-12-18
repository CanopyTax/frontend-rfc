# Code formatters
- Start Date: Mid 2016
- RFC PR: https://github.com/CanopyTax/frontend-rfc/pull/13

## Squad vs Chapter vs Frontend-wide
Each squad may choose whether to use a code formatter and, if so, which one to use.

## Definition
A code formatter is a tool that changes source code to have consistent indentation, styling, and formatting.

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
- Consider turning off your IDE's code formatting when authoring code for projects that do not enforce a code formatter. This avoids code reviews where the reviewers
  are sifting through stylistic changes to find actual changes.
- If submitting a merge request to another squad that does not use Prettier, do not run prettier on all of the files you touch, since that makes it hard to review
  and will make the git blame less useful.
