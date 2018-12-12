# Master Based Development (MBD)
- Start Date: Sometime in late 2015 / early 2016
- RFC PR: https://github.com/CanopyTax/frontend-rfc/pull/1

## Squad vs Chapter vs Frontend-wide
All squads should use master based development as their branching scheme for deployed services.

## Definition
Only the master branch may be deployed to integration, staging, and production.
Other branches only exist for code reviews, not for other devs to write code for. The master branch must
be production ready at all times, even when a feature is still being worked on.

## Reason for decision
- This is a Canopy-wide stance for both backend and frontend development.
- See [google doc from 2016](https://docs.google.com/document/d/1_mgzp0gSO-LZV5UlFCEWtyCILyBEDorijuyqZhwXXr4).
- See [google slides from 2016 and 2018](https://docs.google.com/presentation/d/1Ya-NKCShuJuWcb6hbHA6TooXnR3nob_BhWUTWK2QORA).

## Alternatives
Git Flow is a popular alternative to master based development, along with a variety of other branching schemes.

See [this medium article](https://medium.com/@patrickporto/4-branching-workflows-for-git-30d0aaee7bf) for a decent assessment of
branching schemes (we are similar to the "Gitlab Flow" in that article).

## Common practices (not enforced)
- Use feature toggles so that the master branch is production-ready while still keeping code reviews small.
- Automatically deploy new commits on master to integ, so that if the commit breaks anything it is surfaced
  as soon as possible (i.e. early integration).
- Own the deployment of your merges to master by shepherding the commit all the way to production. This
  helps future devs not have to worry about whether your commit really was production ready.
