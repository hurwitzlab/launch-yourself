# launch-yourself
Template script and instructions for using the TACC Launcher on Stampede.

## Installation
Install the HurwitzLab fork of the TACC Launcher in your Stampede home directory.
```
login2.stampede(4)$ git clone git@github.com:hurwitzlab/launcher.git
```

To get an idea of how to use the launcher copy `launcher.job` and `joblist` from this repository to some directory on Stampede. For example:
```
login2.stampede(88)$ mkdir launch-me
login2.stampede(89)$ cd launch-me/
```

Replace `<developer>` with your email address on the following line of `launcher.job`:
```
#SBATCH --mail-user <developer>@email.arizona.edu
```

## Submit launcher.job to a single node
Submit `launcher.job` to SLURM with `-N 1` to get 1 node. When the job completes you will have a file named something like `launch-yourself.job.o8688690` which shows what happened.

```
login2.stampede(93)$ sbatch -N 1 launcher.job
-----------------------------------------------------------------
              Welcome to the Stampede Supercomputer
-----------------------------------------------------------------

No reservation for this job
--> Verifying valid submit host (login2)...OK
--> Verifying valid jobname...OK
--> Enforcing max jobs per user...OK
--> Verifying availability of your home dir (/home1/04658/jklynch)...OK
--> Verifying availability of your work dir (/work/04658/jklynch)...OK
--> Verifying valid ssh keys...OK
--> Verifying access to desired queue (normal)...OK
--> Verifying job request is within current queue limits...OK
--> Checking available allocation (iPlant-Collabs)...OK
Submitted batch job 8688690
login2.stampede(94)$ squeue -u jklynch
             JOBID   PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           8688690      normal launch-y  jklynch  R       0:07      1 c517-101
login2.stampede(95)$ squeue -u jklynch
             JOBID   PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
login2.stampede(96)$ ls -l
total 12
-rw------- 1 jklynch G-814141  240 Oct  4 17:32 joblist
-rw------- 1 jklynch G-814141  994 Oct  4 17:32 launcher.job
-rw------- 1 jklynch G-814141 1841 Oct  4 17:33 launch-yourself.job.o8688690
login2.stampede(97)$ cat launch-yourself.job.o8688690
LAUNCHER_WORKDIR: /work/04658/jklynch/launch-me
Launcher: Setup complete.

------------- SUMMARY ---------------
   Number of hosts:    1
   Working directory:  /work/04658/jklynch/launch-me
   Processes per host: 16
   Total processes:    16
   Total jobs:         8
   Scheduling method:  dynamic

-------------------------------------
Launcher: Starting parallel tasks...
Launcher: Task 13 running job 6 on c517-101.stampede.tacc.utexas.edu (sleep 1 && echo $LAUNCHER_JID)
Launcher: Task 12 running job 2 on c517-101.stampede.tacc.utexas.edu (sleep 1 && echo $LAUNCHER_JID)
Launcher: Task 1 running job 7 on c517-101.stampede.tacc.utexas.edu (sleep 1 && echo $LAUNCHER_JID)
Launcher: Task 14 running job 8 on c517-101.stampede.tacc.utexas.edu (sleep 1 && echo $LAUNCHER_JID)
Launcher: Task 6 running job 3 on c517-101.stampede.tacc.utexas.edu (sleep 1 && echo $LAUNCHER_JID)
Launcher: Task 7 running job 4 on c517-101.stampede.tacc.utexas.edu (sleep 1 && echo $LAUNCHER_JID)
Launcher: Task 8 running job 1 on c517-101.stampede.tacc.utexas.edu (sleep 1 && echo $LAUNCHER_JID)
Launcher: Task 0 running job 5 on c517-101.stampede.tacc.utexas.edu (sleep 1 && echo $LAUNCHER_JID)
6
2
1
8
7
4
5
3
Launcher: Job 2 completed in 1 seconds.
Launcher: Job 8 completed in 1 seconds.
Launcher: Job 5 completed in 1 seconds.
Launcher: Job 1 completed in 1 seconds.
Launcher: Job 4 completed in 1 seconds.
Launcher: Job 6 completed in 1 seconds.
Launcher: Job 7 completed in 1 seconds.
Launcher: Job 3 completed in 1 seconds.
Launcher: Task 12 done. Exiting.
Launcher: Task 13 done. Exiting.
Launcher: Task 0 done. Exiting.
Launcher: Task 8 done. Exiting.
Launcher: Task 14 done. Exiting.
Launcher: Task 7 done. Exiting.
Launcher: Task 1 done. Exiting.
Launcher: Task 6 done. Exiting.
Launcher: Done. Job exited without errors

Launcher Job Complete

```

## Submit launcher.job to more than one node

Submit `launcher.job` to SLURN with `-N 2` to get 2 nodes.
