## Issue priorities

The priority of issues indicates when the issue should be handled and when it should be resolved.
There are examples of issue *severity* to give an idea of how a *priority* can be assigned.

Defects which have un-addressed questions for more time than their priority probably have the wrong priority.
We may **close a defect** if a question does not have a **[timely feedback](https://github.com/juwai/style-guide/blob/master/workflow-defects.md#no-feedback-actions)**.

Although *severity* and *priority* are often related, please keep in mind they are [different topics](http://wiki.openbravo.com/wiki/QA_Processes/Defects_Severity_Priority).

### Triage (default)

This issue has not been prioritized yet.

### Critical

Commit what you are working on and work on fixing the issue right now.

**There should not be any unaddressed critical issue after 24 hours.**

- Production website can not run.
- Development or testing work are blocked.
- All users can’t use one of the features.

### High

Finish the task presently assigned to you, commit, then work on the issue.

**There should not be any unaddressed high priority issue after 48 hours.**

- Functionality or performance are severly impacted.
- A certain type of users can’t use one of the features.

### Normal

You can address these issues once no story is available for you in the sprint backlog.

- Functionality or performance are impacted.
- A certain type of users can’t use one of the features, but with low impact on revenue.

### Low

**These issues will be handled in backlog’s order and don’t need any specific attention.**

- Some colors or texts are not as they should be.
- A problem impacts very specific users without impacting usage of the features.
