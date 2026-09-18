Git Team Sync Workflow

1\. What did the rejected push error message tell you, and why did it happen?



The rejected push told me that the remote branch contained changes that were not in my local branch. Git rejected the push because my local branch was behind the remote branch.



The first rejection happened in Clone B because Clone A had already pushed its changes to the shared feature/loyalty-points branch. Clone B had not fetched those changes before trying to push.



The second rejection happened in Clone A because Clone B had already pushed the merge commit to the remote branch. Clone A had not fetched the latest remote changes before making and pushing its new commit.



2\. What is the actual difference between how you resolved Task 3 (merge) vs Task 4 (rebase)?



In Task 3, I used a merge. I fetched the latest remote changes and merged them into Clone B's branch. Git created a merge conflict in orders.js, so I manually resolved it and kept both the VIP bonus and rounding behavior. The result included a merge commit.



In Task 4, I used a rebase. I fetched the latest remote changes and rebased my local commit on top of the updated remote branch. Git found another conflict in orders.js, which I resolved manually. The rebase replayed my commit on top of the remote history and produced a more linear history.



3\. What one habit would have avoided both rejected pushes in this lab?



One useful habit is to fetch the latest remote changes before starting work on a shared branch and before pushing. Running git fetch origin helps me check whether another developer has already pushed changes.



However, fetching does not guarantee that there will be no conflicts. If two developers modify the same part of a file, the changes may still need to be resolved manually.



4\. Which approach merge or rebase would you default to on a shared team branch, and why?



I would generally use merge on a shared team branch because it preserves the history of how different developers' changes were combined and does not rewrite commits that other developers may already have.



I would use rebase mainly for my own local commits before sharing them, or when the team has agreed to use rebase. For commits that are already shared, I would avoid rewriting the branch history unless the team specifically agrees to it.

