# Welcome to the OGHPC Devito-GPU hackathon


That's enough of the pleasantries. Let us get started.

## Step 1: Get account and GPU enabled VM for development
You need to click on this link:
https://labs.azure.com/register/jltt9mv2

You will be redirected to your Azure Labs VM.
There you can set your password for logging in to your VM.
You have to wait for a minute or so.
When your password is updated, click on the screen emoji at your VM and select
`Connect via SSH`. Copy the ssh command to your terminal
and start hacking!

## Step 2: Enroll in the hackathon
Simply fork this repo. All forks will be checked periodically.

## Step 3: Start hacking!
In the repository that you have just cloned, you will find two Python files.
One of these is `run-preset.py`, which allows you to execute a set of Devito
benchmarks that we have pre-selected for this hackathon. Aspects like
discretization and duration of the benchmark are fixed, so you won't care about
them. The only argument that `run-preset.py` accepts is the name of the
benchmark -- there are two alternatives:

* `python run-preset.py acoustic`: to generate and run an isotropic acoustic
  forward propagator.
* `python run-preset.py tti`: to generate and run an anisotropic (TTI) acoustic
  forward propagator.

We suggest to start with the simplest one, `acoustic`.  The first time you run
the command, the code gets generated. Instructions will be provided on screen
explaining how to hack the generated code. Then, to test your hacking, just
re-run the same command. The execution time will be displayed at the end of
each run -- look for something along the lines of
```
Operator `Forward` run in 1.22 s
```
Where "Forward" is the name of the Operator. If interested in more performance
metrics, such as the GFlops/s and GPoints/s performance, just run with the
environment variable ``DEVITO_LOGGING=PERF``.

Note: we have configured the VM such that Devito, by default, generates and
compiles code with OpenMP GPU-offloading pragmas. This is achieved through the
following environment variables:

```
DEVITO_ARCH=clang
DEVITO_PLATFORM=nvidiaX
```

If one wants to:

* Use a different backend compiler, for example `pgcc`; then set `DEVITO_ARCH=pgcc`.
* Generate sequential code, then unset `DEVITO_PLATFORM`


## Step 4: Push your work
To submit your work at the end of the hackathon, just run `python
push-files.py`.  And that's it!

## Step 5:
TODO @navjot - look at league table. @navjot to write benchmarking script.
