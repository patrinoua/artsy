## Proposal:

Create a uniform way of referring to things.

## Goal

The motivation for this is having less ambiguity and not spending time 
on how to describe different things under different context. 
It is hoping to allow for easy collaboration between the different developers and designers.

In a big team, that's also growing fast it is important to have clarity between what is what.

#### Current Implementation

Example ticket https://github.com/artsy/eigen/pull/5700 

Feat: CX-773 enables enableClearButton on input field

#### Jira has some information. 
Currently some of the information is also stored on Notion and other locations. 

For example, here the title is

Feat: CX-773 enables enableClearButton on input field

but the description is provided as a link to a notion page. 
Ideally, we'd want to include all the information on the ticket, add screenshots and instructions on how to navigate to each issue.


## Suggestion

### Jira is the single source of truth. 

Ideally, we'd want to include all the information on the ticket, add screenshots and instructions on how to navigate to each issue.
Questions it would solve are:
* Which team is working on it? (CX, FX, ...)
* If known by the person creating the ticket, which repo is relevant
* Is it a feature, a fix, or something else? We could have **feat** as the default and only indicate if it's something else. 

So a Jira ticket could look something like this:

(CX-773) 

CX/eigen/feat: enables enableClearButton on input field

Even though we have different Jira boards, adding CX here would help in gaining clarity on the changelogs. 
Alternatively we could alternate the automation, unless if there is a way to directly mention the ticket name on the [changelogs](https://github.com/artsy/eigen/pull/5331/files) 

## Exceptions:

Of course developers should use their best judgment about how to spend their time. Some are successful at creating time for these sorts of efforts within the regular course of their work and don't need this [somewhat artificial] prompt.

## Additional Context:

Some developers have really run with the Future Friday idea; others not so much. However I've received strong, consistent feedback from product and business folks who feel resistant to engineers doing off-roadmap work for any length of time, especially with little oversight or expectations about deliverables. If there's appetite for Future Fridays beyond the Platform practice, I'd like to make a strong case for it to Product. If not, I'd like to know so we can stop debating and evaluate other ways to accomplish the same goals.

In case it's illustrative, I tried to collect [some examples of Future Friday topics](https://gist.github.com/joeyAghion/e180a4ba7e707ab217f9f9aabd5bdba4).
