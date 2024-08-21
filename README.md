# Notifying Teams on Pull Requests 

## Overview

This workflow is created to automatically triggered when a Pull Request (PR) is opened or edited. It checks the PR description to determine which teams need to be informed and if there are any breaking changes that need to be communicated(more can be added late).

## Workflow Description
1. **Checkout Code**: Retrieves the latest code from the repository.

2. **Set Up Node.js**: Configures the Node.js environment.

3. **Checkout PR body and notify Teams**: Checks the PR body to determine which teams are selected and sends notifications accordingly. We cna select anything from the PR body but for now I used breaking changes to be added in the notification.

### Detailed Steps

1. **Retrieve PR Details**:
   - The workflow extracts the PR body and URL from the GitHub event context.

2. **Determine Team Notifications**:
   - The PR body is checked for selections using checkboxes (e.g., `- [x] Team A`). Based on these selections, notifications are sent to the respective Slack channels.

3. **Handle Breaking Changes**:
   - For now, I used breaking changes to be added in the slack notification but we can add any other points/steps. 

## How to Set Up
1. **Create Slack Webhooks**:
   - Set up Slack webhooks for each team and store these webhook URLs as secrets in your GitHub repository (e.g., `NOTIFY_TEAM_A`, `NOTIFY_TEAM_B`).

2. **Configure the Workflow**:
   - Ensure that the GitHub Actions workflow file is located in the `.github/workflows` directory of your repository.

3. **Update the PR Template**:
   - Make sure your PR template includes checkboxes for team selections. The template might look something like this(this is just an example):

     ```markdown
     ## Summary
     _A brief summary of the changes and their impact on other teams._

     ## Related Teams
     - [ ] Team A
     - [ ] Team B

     ## Description
     _Detailed description of the changes._

     ## Breaking Changes
     _Describe any breaking changes here._
     ```


We can connect if needed for more detailed discussion.
