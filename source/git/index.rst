===
Git
===

Deleting all previous commits in Git [001]_
===========================================
Deleting the .git folder may cause problems in your git repository. If you want to delete all your commit history but keep the code in its current state, it is very safe to do it as in the following:

.. code:: batch

	git checkout --orphan latest_branch
	# Add all the files
	git add -A
	Commit the changes
	git commit -am "commit message"
	Delete the branch
	git branch -D master
	Rename the current branch to master
	git branch -m master
	Finally, force update your repository
	git push -f origin master
	PS: this will not keep your old commit history around


Rename local and remote branch [002]_
=====================================

.. code:: batch

  # Rename the branch locally
  git branch -m old-name new-name

  # Delete the old-name remote branch and push the new-name local branch
  git push origin :old-name new-name

  # Reset the upstream branch for the new-name local branch
  git checkout new-name
  git push origin -u new-name

Set proxy in Git [003]_
=======================

``git config --global http.proxy http://proxyuser:proxypwd@proxy.server.com:8080``


- change proxyuser to your proxy user
- change proxypwd to your proxy password
- change proxy.server.com to the URL of your proxy server
- change 8080 to the proxy port configured on your proxy server

If you decide at any time to reset this proxy and work without proxy:

Command to use:
``git config --global --unset http.proxy``

Finally, to check the currently set proxy:
``git config --global --get http.proxy``


Git log filter by branch [004]_
===============================

Assuming that your branch was created off of master:

.. code:: shell
  
   git cherry -v master

   # or

   git log master..

If your branch was made off of origin/master, then say origin/master instead of master.

Merge branch as a single commit [005]_
======================================

.. code:: shell
   
   git merge --squash <branch-you-want-to-merge>

   # all changes from the branch will be added
   # do a commit

   git commit -m "<What is the branch about?>"


References
==========

.. [001] https://stackoverflow.com/questions/13716658/how-to-delete-all-commit-history-in-github
.. [002] https://multiplestates.wordpress.com/2015/02/05/rename-a-local-and-remote-branch-in-git
.. [003] https://stackoverflow.com/questions/783811/getting-git-to-work-with-a-proxy-server
.. [004] https://stackoverflow.com/questions/4649356/how-do-i-run-git-log-to-see-changes-only-for-a-specific-branch
.. [005] https://stackoverflow.com/a/3697263/836472
