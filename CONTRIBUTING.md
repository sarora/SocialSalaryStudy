# CONTRIBUTING

### Method of adding changes

Changes will be added via branching:

* Create a new branch with a descriptive name, followed by _ and initials, (for example: contributing_AG).
* Make all changes in this branch, and commit and push your changes.  
* When the branch is ready to merge, open a pull request for the merge, tagging the other two contributors.
* Once this issue is raised STOP working in this branch until the issue is resolved.
* Either of the other contributors has full authority to merge changes.
* When a branch is merged in with the Master, that branch should be immediately deleted.

### Raising Issues

Please raise an issue for any and all things!  As a courtesy, please tag all of the contributors.

### Commit Messages

Remember that commit messages are the way to remember what was done, and keep messages meaningful.

### Directory Structure

Keep all documents in the correct folder, when in doubt, ask the other contributors (perhaps in an issue?).  Remember to cite any sources in the `doc\references\README.md`, which documents any citations.


### Git Commands

1. Create a new branch
    ```
    git branch -b [BRANCH NAME]
    ```
2. After completing some tasks:

    1. Add *all* files that have been worked on
        ```
        git add .
        ```
   2. Add commit message
       ```
       git commit -m '[COMMIT MESSAGE]'
       ```
   3. Push from new branch for the first time
       ```
       git push --set-upstream origin [BRANCH NAME]
       ```
   4. Push anytime after that
       ```
       git push
       ```
   5. Navigate to  [Compare changes](https://github.com/UBC-MDS/ptoolkit/compare) and create pull request for the branch of interest.

   6. Wait for a member of the team to merge [pull request](https://github.com/UBC-MDS/ptoolkit/pulls).

3. If you need to update the branch that you are currently working in with the updated master branch:
    ```
    git pull origin master
    ```


Sourced from [Ptoolkit](https://github.com/UBC-MDS/ptoolkit)
