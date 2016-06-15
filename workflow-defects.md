## Defects

A **bug report is like a cake**, if you **don't take the time** to bake it well enough, your guests will have a **long and hard time digesting it**. If you **bake it for too long**, then the whole kitchen is going to **smell like burnt caramel**.

A defect is fixed as fast as it is well–communicated (sufficient information, well written).
If the context and the way to reproduce a defect are made clear (not too much information, not too less), it will be easier for everyone to implement it, test it, refer to it…

:warning: **Please [link the defect to its related *User Story*](https://confluence.atlassian.com/jira/linking-issues-185729497.html#LinkingIssues-creatinglinktoanotherissueCreatingalinktoanotherissueonthesameJIRAsite).**

---

Quick links: [Summary](#summary) | [Template](#template) | [Deadline](#deadline)

---

### Summary

The summary of a defect should briefly describe the problem.
Ideally, it would mention the type of user, the topic and the location of the problem. These are all valid summaries:

- “I can’t upload a picture on the add property page”
- “Edit individual profile is not loading”
- “As a consumer, I can’t add a product to cart on the recommendation page”
- “I can’t add a promotion code on checkout page”

### Template

We’re using the following template to create defects. It’s using [markdown][2].
You should get familiar with it if you’re not already, **it’s awesome!**

**The beginning part of the description explains how to reproduce the defect.**

```markdown
1. [If I do A.]
1. [B doesn’t happen.]

### Expected Workflow

1. [If I do A.]
1. [B should happen.]

### Resources:

* URL: [URL to the page the problem appears on]
* User: [User that allows to reproduce the bug]
* Environment:
    * Browser.
    * OS.
    * Connexion used (proxy in Hong Kong, Juwai-guest wifi, Juwai-SH wifi…).
    * Any relevant information…

### Notes

[Some complementary notes if necessary:]

* > Here goes a quote from an email
* Here goes whatever useful information can exist…
```

### Deadline

Defects must be resolved in a timely manner based on the [issue priority guidelines][3].

### No Feedback Actions

There may be times that we might not get feedback from those that raise the defects, we may then follow the [issue priority guidelines][3] as to when we can close the issue. 

As a summary, we may close a defect if a question does not have feedback after:

- Critical: 1 day
- High:     2 days
- Normal:   14 days
- Low:      14 days

Conversely, it is also recommended to provide feedback before the said limits.


[2]: http://daringfireball.net/projects/markdown/basics
[3]: https://github.com/juwai/style-guide/blob/master/workflow-issue-priority.md