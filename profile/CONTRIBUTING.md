# Contributing to the CFIA AI Lab

## What this is

This guide provides an overview of the GitHub workflow using GitHub issues,
GitHub projects, GitHub pull requests, reviews, and closing issues from pull
requests.

## Examples

This documentation uses product codename Louis as the example.

## Using GitHub Issues

1. Go to the organization's GitHub repository.
2. Click on **Projects** and select **Louis** to see all issues within the Louis
   project.
3. Create a new issue and assign it to a specific developer. Make sure to:
   - give the issue meaningful title and description
   - assign it the appropriate labels
   - not create new labels at repository level

## Working with GitHub Projects

1. Open the organization's GitHub repository.
2. Click on **Projects** and select a project. For instance **Louis** to view
   the Louis project board.
3. **Issue Prioritization**: The tasks can be reordered in the table by dragging
   their priority number up or down. The higher up a task is, the more urgent it
   is.
4. **Assignment**: In the `Assignees` column, chose an assignee.
5. **Status**: In the `status` column, update the progress on the issue to keep
   track of it.

**Notes**:
- If the particular repository on which you are working doesn't have a GitHub
  Project, create one with the permission of your supervisor. Follow this
  [guide](https://docs.github.com/en/issues/planning-and-tracking-with-projects/learning-about-projects/quickstart-for-projects).
- Don't assign issues before they are prioritized (by your supervisor or the
  whole team)

## Creating a new repository in the Organization

1. In the Organization's page, select `New` in the `Repositories` section.
2. Give it a meaningful name, making sure to follow the existent repositories
   naming patterns (i.e., lowercase, dash instead of underscore, …)
3. Give it a meaningful description.
4. Make it Public.
5. Include README and .gitignore files.
6. Once created, protect the main branch: check options `Require a pull request
   before merging` and `Require approvals`.

## filing an issue/ticket

A good issue:

* good, descriptive title (preferably something understandable from management)
* full summary with context
* step-by-step details of the work to be done
* acceptance criteria
* a task list and are correctly associated to a project

A great issues will also

* provide links and (sequence) diagrams to further explain the work to be done
* provide version, environment tested against and reproduction steps for issues
  filed
* for webapps, pull up the Developer tools panel of your browser and use it
* text, screenshots, application logs, console logs
* describe root causes of the problem

Issues should also be the right-size.

Stay away from refactoring or small fixes that can be additional tasks to
existing issues.

When the issue is created to follow up on a comment in another issue or pull
request, don't forget to use the "Reference in new issue" Github feature (found
in the ... menu) to provide better context.

## Creating a Pull Request

1. Reference which issue this PR closes in the description
1. Plan the work required to complete the change as a checklist
  1. Make it work first!
  1. Refactoring
  1. documentation of usage and architecture
  1. manual testing (updatest to TESTING.md)
  1. automated testing
  1. versioning bump (_versions.ts in frontend projects)
1. Mark your pull request as a draft.
![Screenshot_59.png](/.attachments/Screenshot_59-8fb3dd7c-dc99-4c2f-8dc1-02dfef9f503b.png)
 2. Make all the necessary changes you want.
3. Once you addressed all the requests, you can ask for a re-review.
![Screenshot_61.png](/.attachments/Screenshot_61-7794e4a4-30af-421c-a70a-306ef0b58b99.png)

## Working on a pull request

Push and share your code early and often. When you share early code still under
development, prefix your PR with WIP (meaning Work-in-Progress) so that
reviewers know this is not your final version.

## Submit for review

Select list of reviewers that are relevant to the PR, including team lead.

You should also include relevant reviewers even if they are absent or on
vacation so they can catch up when they come back. Their approval is not
required in the meantime to complete the PR.

## Reviewing and Approving a Pull Request (PR)

1. Team members review the pull request, leave comments, and suggest changes if
   necessary.
2. Developer addresses the feedback and makes the necessary updates. Developer
   replies to all review comments with "done", comments, new issues (to postpone
   work to future PR) or clarifying questions
3. Once the pull request meets the required criteria, a team member approves the
   pull request.


## Closing Pull Requests

1. Once the pull request is approved, navigate to the pull request's
   description.
1. Update the description by adding the text `Closes #<issue number>` to
   indicate that the issue has been addressed and completed.
1. Consider rebasing and squashing the commit history
1. Merge the pull request into the main branch.
1. Don't delete the branch when done (leave them for future reference).

Following this workflow will help in managing tasks, tracking progress, and
closing issues effectively using GitHub's features.

For more detailed information and specific steps, please refer to the GitHub
documentation or reach out to your team for any additional guidelines or
conventions.

## Editor settings

Ensure that your editor (preferably in project workspaces) has the following
turned on:

* Automatically wrap lines to 80 characters in Markdown files
  * use Rewrap extension
* Trim Final Newlines: Ensures your files end neatly with a single newline.
* Trim Trailing Whitespace: Eliminates any superfluous spaces at the end of
  lines upon file save.
* Insert Final Newline: Add EOF new line when saving

[see this repository .vscode/settings.json as example](/.vscode/settings.json)

## Development processes

* check your [Github organization](https://github.com/ai-cfia)
  [notifications](https://github.com/notifications) twice daily.
  * Customize email routing to route ai-cfia repo notifications to your
    inspection.gc.ca
  * Prioritize pull requests reviews above all else
  * Do not just rubber stamp; provide value as a reviewer
* every work item should have a matching issue describing the work to be done
* pull requests
  * branch -> pull request -> peer review -> fixes -> approval -> rebase and
    merge
  * name branch prefix with issue identifier (```59-some-issue-summary```)
  * reference the issue within the description of the pull request
  * do as many request reviews -> get comments from reviewer -> fix and answer
    comments -> request reviews as necessary (until you get the reviewer(s)
    approval
* update your [Github notification settings with Custom
  Routing](https://github.com/settings/notifications/custom_routing) from the
  ai-cfia org to your inspection.gc.ca email
* single line commits preferably prefixed with issues being worked on or fixed
  * example: `Fixes #19: Introduction Jolan Thomassin`
* don't delete branches when done (leave them for future reference)
* when feedback, suggestions or feature request that come up in one of your PR
  by a reviewer that would require a lot more work outside the scope of the
  current issue, it is encouraged to create a new issue capturing that
  non-trivial piece of work and document it as "postponed work" in the PR.
