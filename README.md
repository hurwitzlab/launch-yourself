# launch-yourself
Template script and instructions for using the TACC Launcher on Stampede.

## Installation
Install the HurwitzLab fork of the TACC Launcher in your Stampede home directory.
```
login2.stampede(4)$ git clone git@github.com:hurwitzlab/launcher.git
```

To get an idea of how to use the launcher clone this repository to some directory on Stampede. For example:
```
login2.stampede(103)$ git clone https://github.com/hurwitzlab/launch-yourself.git
Initialized empty Git repository in /work/04658/jklynch/launch-yourself/.git/
remote: Counting objects: 27, done.
remote: Compressing objects: 100% (23/23), done.
remote: Total 27 (delta 11), reused 13 (delta 4), pack-reused 0
Unpacking objects: 100% (27/27), done.
login2.stampede(105)$ cd launch-yourself/
login2.stampede(106)$ ls -l
total 2
-rw------- 1 jklynch G-814141  240 Oct  4 17:45 joblist
-rw------- 1 jklynch G-814141 1059 Oct  4 17:45 launcher.job
-rw------- 1 jklynch G-814141 1068 Oct  4 17:45 LICENSE
-rw------- 1 jklynch G-814141 4179 Oct  4 17:45 README.md
```

Replace `<developer>` with your email address on the following line of `launcher.job`:
```
#SBATCH --mail-user <developer>@email.arizona.edu
```

### Submit launcher.job to a single node
Submit `launcher.job` to SLURM with `-N 1` to get 1 node. When the job completes you will have a file named something like `launch-yourself.job.o8688690` which shows what happened.

```
login2.stampede(107)$ sbatch -N 1 launcher.job
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
Submitted batch job 8688703
login2.stampede(108)$ ls -l
total 24
-rw------- 1 jklynch G-814141  240 Oct  4 17:45 joblist
-rw------- 1 jklynch G-814141 1059 Oct  4 17:45 launcher.job
-rw------- 1 jklynch G-814141 1717 Oct  4 17:47 launch-yourself.job.o8688703
-rw------- 1 jklynch G-814141 1068 Oct  4 17:45 LICENSE
-rw------- 1 jklynch G-814141 4179 Oct  4 17:45 README.md
login2.stampede(109)$ cat launch-yourself.job.o8688703
LAUNCHER_WORKDIR: /work/04658/jklynch/launch-yourself
Launcher: Setup complete.

------------- SUMMARY ---------------
   Number of hosts:    1
   Working directory:  /work/04658/jklynch/launch-yourself
   Processes per host: 4
   Total processes:    4
   Total jobs:         8
   Scheduling method:  dynamic

-------------------------------------
Launcher: Starting parallel tasks...
Launcher: Task 2 running job 3 on c517-101.stampede.tacc.utexas.edu (sleep 1 && echo $LAUNCHER_JID)
Launcher: Task 0 running job 1 on c517-101.stampede.tacc.utexas.edu (sleep 1 && echo $LAUNCHER_JID)
Launcher: Task 1 running job 4 on c517-101.stampede.tacc.utexas.edu (sleep 1 && echo $LAUNCHER_JID)
Launcher: Task 3 running job 2 on c517-101.stampede.tacc.utexas.edu (sleep 1 && echo $LAUNCHER_JID)
4
1
3
2
Launcher: Job 4 completed in 1 seconds.
Launcher: Job 1 completed in 1 seconds.
Launcher: Job 2 completed in 1 seconds.
Launcher: Job 3 completed in 1 seconds.
Launcher: Task 1 running job 5 on c517-101.stampede.tacc.utexas.edu (sleep 1 && echo $LAUNCHER_JID)
Launcher: Task 0 running job 6 on c517-101.stampede.tacc.utexas.edu (sleep 1 && echo $LAUNCHER_JID)
Launcher: Task 3 running job 7 on c517-101.stampede.tacc.utexas.edu (sleep 1 && echo $LAUNCHER_JID)
Launcher: Task 2 running job 8 on c517-101.stampede.tacc.utexas.edu (sleep 1 && echo $LAUNCHER_JID)
5
6
7
8
Launcher: Job 5 completed in 1 seconds.
Launcher: Job 6 completed in 1 seconds.
Launcher: Job 7 completed in 1 seconds.
Launcher: Job 8 completed in 1 seconds.
Launcher: Task 1 done. Exiting.
Launcher: Task 0 done. Exiting.
Launcher: Task 3 done. Exiting.
Launcher: Task 2 done. Exiting.
Launcher: Done. Job exited without errors

Launcher Job Complete

```

### Submit launcher.job to two nodes

Submit `launcher.job` to SLURN with `-N 2` to get 2 nodes.

```
login2.stampede(110)$ sbatch -N 2 launcher.job
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
Submitted batch job 8688706
login2.stampede(111)$ ls -l
total 25
-rw------- 1 jklynch G-814141  240 Oct  4 17:45 joblist
-rw------- 1 jklynch G-814141 1059 Oct  4 17:45 launcher.job
-rw------- 1 jklynch G-814141 1717 Oct  4 17:47 launch-yourself.job.o8688703
-rw------- 1 jklynch G-814141 1845 Oct  4 17:50 launch-yourself.job.o8688706
-rw------- 1 jklynch G-814141 1068 Oct  4 17:45 LICENSE
-rw------- 1 jklynch G-814141 4179 Oct  4 17:45 README.md
login2.stampede(112)$ cat launch-yourself.job.o8688706
LAUNCHER_WORKDIR: /work/04658/jklynch/launch-yourself
Launcher: Setup complete.

------------- SUMMARY ---------------
   Number of hosts:    2
   Working directory:  /work/04658/jklynch/launch-yourself
   Processes per host: 4
   Total processes:    8
   Total jobs:         8
   Scheduling method:  dynamic

-------------------------------------
Launcher: Starting parallel tasks...
Launcher: Task 3 running job 2 on c517-101.stampede.tacc.utexas.edu (sleep 1 && echo $LAUNCHER_JID)
Launcher: Task 0 running job 4 on c517-101.stampede.tacc.utexas.edu (sleep 1 && echo $LAUNCHER_JID)
Launcher: Task 1 running job 1 on c517-101.stampede.tacc.utexas.edu (sleep 1 && echo $LAUNCHER_JID)
Launcher: Task 2 running job 3 on c517-101.stampede.tacc.utexas.edu (sleep 1 && echo $LAUNCHER_JID)
Launcher: Task 5 running job 7 on c517-102.stampede.tacc.utexas.edu (sleep 1 && echo $LAUNCHER_JID)
Launcher: Task 7 running job 6 on c517-102.stampede.tacc.utexas.edu (sleep 1 && echo $LAUNCHER_JID)
Launcher: Task 4 running job 5 on c517-102.stampede.tacc.utexas.edu (sleep 1 && echo $LAUNCHER_JID)
Launcher: Task 6 running job 8 on c517-102.stampede.tacc.utexas.edu (sleep 1 && echo $LAUNCHER_JID)
4
1
2
3
Launcher: Job 4 completed in 1 seconds.
Launcher: Job 1 completed in 1 seconds.
Launcher: Job 3 completed in 1 seconds.
Launcher: Job 2 completed in 1 seconds.
Launcher: Task 0 done. Exiting.
Launcher: Task 2 done. Exiting.
Launcher: Task 1 done. Exiting.
Launcher: Task 3 done. Exiting.
5
7
6
8
Launcher: Job 8 completed in 1 seconds.
Launcher: Job 6 completed in 1 seconds.
Launcher: Job 5 completed in 1 seconds.
Launcher: Job 7 completed in 1 seconds.
Launcher: Task 6 done. Exiting.
Launcher: Task 5 done. Exiting.
Launcher: Task 7 done. Exiting.
Launcher: Task 4 done. Exiting.
Launcher: Done. Job exited without errors

Launcher Job Complete
```


