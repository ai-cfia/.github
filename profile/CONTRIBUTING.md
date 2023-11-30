# Contributing to the CFIA AI Lab

## filing an issue/ticket

A good issue:

* good, descriptive title (preferably something understandable from management)
* full summary with context
* step-by-step details of the work to be done
* acceptance criteria
* a task list and are correctly associated to a project

A great issues will also provide links and (sequence) diagrams to further explain the work to be done.

Issues should also be the right-size. Stay away from refactoring or small fixes that can be additional tasks to existing issues.

When the issue is created to follow up on a comment in another issue or pull request, don't forget to use the "Reference in new issue" Github feature (found in the ... menu) to provide better context.

## Development processes

* check your [Github organization](https://github.com/ai-cfia) [notifications](https://github.com/notifications) twice daily. 
  * Customize email routing to route ai-cfia repo notifications to your inspection.gc.ca
  * Prioritize pull requests reviews above all else
  * Do not just rubber stamp; provide value as a reviewer
* every work item should have a matching issue describing the work to be done
* pull requests
  * branch -> pull request -> peer review -> fixes -> approval -> rebase and merge
  * name branch prefix with issue identifier (```issue59-some-issue-summary```)
  * reference the issue within the description of the pull request
  * do as many request reviews -> get comments from reviewer -> fix and answer comments -> request reviews as necessary (until you get the reviewer(s) approval
* update your [Github notification settings with Custom Routing](https://github.com/settings/notifications/custom_routing) from the ai-cfia org to your inspection.gc.ca email
* single line commits preferably prefixed with issues being worked on or fixed 
  * example: `Fixes #19: Introduction Jolan Thomassin`
* don't delete branches when done (leave them for future reference)
* when feedback, suggestions or feature request that come up in one of your PR by a reviewer that would require a lot more work outside the scope of the current issue, it is encouraged to create a new issue capturing that non-trivial piece of work and document it as "postponed work" in the PR.

## for testing and reporting issues

* provide version, environment tested against and reproduction steps for issues filed
* for webapps, pull up the Developer tools panel of your browser and use it
* text, screenshots, application logs, console logs
* try to identify the general area where the problem is coming from
