WordPress plugin projects normally have only one update server, which holds the current release of the plugins. This is fed from the main branch of the repositories, so there is never a need to have multiple different bug-fix versions available. 
Contrast with systems where you would have version 1,2 and 3 in the field, and customers would have multiple different bugfixes applied to their versions – all would need to be reproducible in the build systems.
Our requirements are much simpler. We need a single main branch into which features and bug fixes are fed - we really have no need to distinguish between a feature and a bugfix – except to say that in general bug-fixes are shorter development time, so features may require merging back after many bug-fixes have been merged.

## In summary:

Main is the branch from which the update server is populated.
We have a single main into which nothing is ever pushed – and all features and bug-fixes are created as a branch. There is no need to distinguish between the two types, they are both just development branches.

Every time the update server is modified, a release file is created to correspond to the version which is shipped. This release takes the form of a zip, but it’s a zip of the entire main branch, not just the shipped files – the purpose being that we can pull that release and get a working project which corresponds to the released code.
At a release, a new branch is created for that release.
 
Features branches are created from main and pulled back into main when complete.
Bug fix branches may be started from main if they are fixes which are not going to be part of a bugfix update to the update server.
Bug fix branches may be started from the current release branch if they are required for an emergency update. These are pulled back into the current release branch, and subsequently pulled back from that branch into main.
When a new feature release happens, the update server is updated from main, and a new release branch is started. The old release branch is deleted as it should be parallel with main in terms of bug fixes.

Branches are created for each bug or feature – named with initials plus some reference, e.g es-bug777 or es-new-page-layout etc. When ready the developer will issue a pull request for it to be pulled into main.
Pull requests must be reviewed and approved by a senior member of the team.
 
There are two ways of merging, which are 'merge' and 'rebase'. They serve different purposes. Merge is generally ‘upwards’ – I.E you merge from other branches into main, never backwards.
Rebasing is the reverse, but you do it locally as its almost certain to require user interaction. In this case you have a branch with a long-running feature in it and want to have all the bug-fixes which have passed you by since you cloned main. You gather a new version of main onto your local machine, and use ‘git rebase’ on your local branch to update it before delivery, so it looks like it came from the current main.  This avoids complex merges – which are at best slightly risky.





When a feature needs to be merged, the developer can take the decision to either merge and let GitHub try to fix any conflicts or pull the head of the main branch and rebase on it. Rebase is quite hard to get right but complex merges where main is ahead by many fixes are liable to fail because the conflict is not resolvable without a human decision.
Hopefully we will have mostly short running features and small fixes – so the merges will be easy. Also, we have quite a few plugins, so the chances of needing a merge are smaller, as the bugs may not be in the same plugin as the feature.


