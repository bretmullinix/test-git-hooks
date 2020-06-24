






[![Build Status](https://jenkins.com/job/test-git-hooks/job/test-merge/badge/icon)](https://jenkins.com/job/test-git-hooks/job/test-merge/)









# Testing Branch
test again and again
# Procedure to work with git hooks

1.  cp -r .git/hooks git-hooks
2.  git config core.hooksPath git-hooks
3.  git config --global merge.ours.driver true
4.  make .gitattributes file with the following:

    git-hooks/ merge=ours

5.  commit the following to the master branch:
     a.  git-hooks and contents
     b.  .gitattributes

6.  commit the following to the current branch:
     a.  git-hooks and contents
     b.  .gitattributes

7.  In GitHub during a pull request, the git-hooks folder should be ignored for the hooks that exist in the master branch.  
    GitHub sees the .gitattributes file and will merge according to the file. 
    The .gitattributes has "git-hooks/ merge=ours" in it and so GitHub will ignore anything in the folder.

Take a look at the .gitattributes file:
  a. Go to the "test-jenkinsfile" repo
  b. Go to the branch "new_test_branch"
  c. Click on the .gitattributes file

     In this case, we are not allowing the "README.md" file
     or the "git-hooks" folder to be merged into master if they already
     exist in master

Take a look at the pre-commit hook:
  a.  Go to the "test-jenkinsfile" repo
  b.  Go to the branch "new_test_branch"
  c.  Click on the "git-hooks" folder
  d.  Click on the "pre-commit" file.

      The python file is used to generate the build status button according to
      the current repo and branch after every commit.

