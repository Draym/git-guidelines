# GIT guidelines


## Base branches: Dev . Staging . Main
Base branches are codebase which are deployed to live environments. These branches should reject any commits or direct merge events.

Only a PullRequest from a Release or HotFix branch should be authorized to be merged to a base branch (exceptions can be made for the Dev branch).

- Dev : represents the development branch where developers can push their code and features freely. This branch should have its own live environment to help developers with their own test procedures.
- Staging : host Release branches that need to be tested by QA. Once a developer is confident with his work within a Release branch, he should create a PR to Staging. He then needs to plan a testing session with QA . Once QA is ready to test, the PR can be merged.
- Main: host the latest stable code. After QA fully tested and approved a Release branch, it is then merged to Main. The developer then creates a TAG release. The Main branch can be the source of a pre-release environment to test again before deploying the Tag to production.

## Release branches
A Release branch represents a planned release and can be composed of different features and work that needs to be released at a given time. It can be associated as an Epic on Jira. It is advised to isolate business scope within different Release in order to minimise the risk of conflicts with other simultaneous releases.

It should be composed of the Jira Epic/MainTask number and a name.

The name should be explicit and short. Avoid using verbs, because it is redundant for a branch name. $\textcolor{pink}{\text{The goal here is to specify the scope, not the task.}}$

todo

### SubRelease branches
todo
## HotFix branches
todo
## Commits
Commits are used to save work progress under a Release branch or SubRelease branch. It is advised to commit your progress regularly (at least one per day) with a relevant name which describes your changes. If possible, split your work into different commits to explicitly show your progress and facilitate commit reverse. $\textcolor{pink}{\text{One commit per completed step should be your goal.}}$

Commits messages will be composed of an action keyword, an explanation message and need to contain the Jira task or subtask to which it belongs.

The required format will be as follows : 
```
{action_keywork}: {message} #{jira_number}
```

**Commit Keyword**:
  - **$\textcolor{green}{\text{task}}$** : a development task which represents a code update to improve the product. It includes add/update/delete of code as features
  - $\textcolor{orange}{\text{fix}}$ : represent the correction of a bug. Use it either to fix a previous task keyword during development or during the QA phase.
  - $\textcolor{red}{\text{hotfix}}$ : represent the correction of a bug from Main branch, it should only be used for commits within a HotFix branch
  - $\textcolor{red}{\text{break}}$: use this keyword to highlight a breaking change, such as removing an API endpoint. You have to mention in the message, after a line breaks every feature that is now deleted/deprecated.
  - $\textcolor{magenta}{\text{clean}}$ : represent the deletion of non-relevant or unused codebase, the rename or restructuration of code. Overall, it should not have any impact on the inner logic and does not require testing.
  - $\textcolor{lightblue}{\text{doc}}$ : include readme file, codebase (function & class docs ...) documentation or any other kind of documentation related to your project
  - $\textcolor{grey}{\text{extra}}$ : any changes which are not related to your codebase (so it doesn't affect the code or its dependencies) and that are not documentations but are still part of your repository. For example, if you maintain an external SDK as package.
  

## PullRequest

**Naming:**
- The title should include the target branch nickname and the current branch
- The description should be composed of:
  -  a short detailed message
  -  a summary of all the main changes made within your branch. Each change should be composed of an action keyword and a message : {keyword}: {message}
     - add : some new api / features etc..
     - break : deleted some used features
     - update : if some logic has been updated
  - If the Feature branch has a parent Jira task (an Epic for example), you should add it at the end
- Keep it concise
  - Example :
```
TITLE: [DEV] DX-50/login_flow
 
DESCRIPTION:
 Implement login APIs and set new password rules
 
 add: /auth/login
 add: /auth/metamask/login
 update: password rules

 Parent: DX-10
```

## Merge PullRequest Commit
**Naming:**
- The title should include the target branch nickname and the current branch
- The description should be composed of:
  -  copy & paste of the PullRequest body
- Example :
```
TITLE: (DEV) merge (DX-50/login_flow)
 
DESCRIPTION:
 Implement login APIs and set new password rules
 
 add: /auth/login
 add: /auth/metamask/login
 update: password rules
```




## Appendix
