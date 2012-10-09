pointy-haired-boss
==================

Looking over your shoulder just to point out things that are wrong.  Not a very encouraging.

This should do a few things...

Deployed on heroku.

Web method to check for pull requests and new commits against a branch.

(System will have a cron job which hits that periodically).  So watching another branch or something == an entry in cron.

Shows the status of the SQS work queue.

BuildTarget (github URL to a branch w/ a build )
  Build (the status of a build, has build tasks and an overall status)

  BuildTask (each parallel task, one is for setup, and then the rest are run in parallel, one is for shutdown)
    Accepts POSTs to append log information.
    Accepts POSTs to give exit status.
    If passes then you can tag / comment that it passes.


Reqts:
  When you hit the index page, you should see the last 50 builds
  You can filter them by the repo/branch (target for a pull request or a commit link or something)

  You can click on any build task and see the results of the build and console output.
  You can't cancel a running build.

  CRON API:
    /build/check?repo=...&branch=...
    Looks for any pull requests (which haven't been tested) and new commits on the branch which haven't been tested.

    /build/heartbeat
    Checks the SQS queues for old-ish pending builds and spins up an EC2 instance if necessary

Shows the status of the last 50 builds per branch target.
