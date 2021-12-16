# Git Cheatsheet

## Workflow metodologies

### Centralized

Used in small teams with tiny projects or when you dont have enough time to organize more organized workflow.

All commits are being made in main (master) branch.

Example:

<pre>
   O                O
  /                /
O - O - O - O - O - O
      \
       O
</pre>

### Feature Branch Flow

Commits are are being made in defferent feature-branch with no restrictions in amount of developers on each feature-branch. When the feature is done, feature-brunch is being pushed to main (master) branch.

Example:

<pre>
feature/#1    O - O - O - O
             /             \
main        O --------- O --- O
             \         /
feature/#2    O - O - O
               \ /
feature/#2.1    O
</pre>

### Git Flow

There are some dedicated branches:

- **main (master)** - the most stable, could be used as released product, tested branch
- **develop (dev)** - the branch for testing features to work correctly together (being merged from and to **main (master)**)
- *optional* **hotfixes** - used for fixing issues that are already in **main (master)** (being merged from and to **develop (dev)** and **main (master)**
- *optional* **release-\<number\>** - could be used for release *(what a twist)* instead of **main (master)** (being merged from **main (master)**)

Example:

<pre>
main        O ----- O ------------- O
             \     /               /
develop       O - O -------- O -- O
               \ / \        /    /
feature/#1      O --\- O - O    /
                     \         /
feature/#2            O - O - O
</pre>

### Integration Manager Flow

Fits for ditributed team and/or open-sourse projects.

There's one person, **integration manager**, who allowed to push changes to **Blessed Repository**. Developers only may pull from this **Blessed Repository**. They push changes to their's public repositories. Then, **integration manager** pulls changes from developers' repositories and pushes them into the **Blessed Repository**.

Example:

<pre>
╔══════════════╗          ┌──────────────┐            ┌──────────────┐
║              ║          │              |            │              |
║ Blessed Repo ║          | Public Repo  |            | Public Repo  |
║              ║          │              |            │              |
╚══════════════╝          └──────────────┘            └──────────────┘
     ^      |                |       ^                    |       ^
     |   ┌──|────────────────|───────|────────────────────┘       |
     |   |  └────────────────|───────|────────────────────┐       |
     |   V                   V       |                    V       |
╔══════════════╗          ┌──────────────┐            ┌──────────────┐
║ Integration  ║          │              |            │              |
║ manager      ║          |  Developer   |            |  Developer   |
║              ║          │              |            │              |
╚══════════════╝          └──────────────┘            └──────────────┘
</pre>

### Dictator-Leutenants Flow

Use this workflow only if your project is *REALLY* huge.

Almost the same as previous one: **Dictator** is the only one who allowed to push changes to **Blessed Repository**. He accepts changes suggested by **Leutenants**, well-skilled trusted persons who pull changes from developers' public repositories.

### Fork Flow

Provided by GitHub, great for open-sourse projects.

Developers *make a copy (**fork**)* of a repository, developing new features and commiting them to their **fork**. When the feature is finished, developers create **pull request** to original repository. The author of original repository may accept their **pull requests** to apply contibuted changes.
