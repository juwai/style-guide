## Defects

A **bug report is like a cake**, if you **don't take the time** to bake it well enough, your guests will have a **long and hard time digesting it**. If you **bake it for too long**, then the whole kitchen is going to **smell like burnt caramel**. 

A defect is fixed as fast as it is well–communicated (sufficient information, well written).
If the context and the way to reproduce a defect are made clear (not too much information, not too less), it will be easier for everyone to implement it, test it, refer to it…

---

Quick links: [Summary](#summary) | [Description](#description) | [Template](#template) | [Resources](#resources)

---

### Summary

The summary of a defect should briefly describe the problem.
Ideally, it would mention the type of user, the topic and the location of the problem. These are all valid summaries:

- “I can’t upload a picture on the add property page”
- “Edit individual profile is not loading”
- “As a consumer, I can’t add a product to cart on the recommendation page”
- “I can’t add a promotion code on checkout page”

### Description

We’re using the following template to create defects. 

Since we have mentioned the type of user, the user story can refer to it with “I”.
This is useful for **consistency** and to **avoid repetition** in the Acceptance criteria.
It’s also good to practice a little **empathy**.

For example:

```markdown
1. I click on the “submit” button.
1. No modal window appears if I don’t have enough credits.
```

The template uses [markdown][2].
You should get familiar with it if you’re not already, **it’s awesome!**

### Template

1. The beginning part of the description explains how to reproduce the defect.
2. “Acceptance Criteria” explains the expected workflow.

```markdown
1. [If I do A.]
1. [B doesn’t happen.]

### Acceptance Criteria

1. [If I do A.]
1. [B should happen.]

### Resources:

* URL: [URL to the page the problem appears on]
* User: [User that allows to reproduce the bug]
* Environment:
    * Browser.
    * OS.
    * Connexion used (proxy in Hong Kong, Juwai-guest wifi, Juwai-SH wifi…).
    * 

### Notes

[Some complementary notes if necessary:]

* > Here goes a quote from an email
* Here goes whatever useful information can exist…
```


### Resources:

* [“Advantages of the “As a user, I want” user story template.”][1]


[1]: http://www.mountaingoatsoftware.com/blog/advantages-of-the-as-a-user-i-want-user-story-template
[2]: http://daringfireball.net/projects/markdown/basics
