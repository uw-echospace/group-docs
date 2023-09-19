# High-Performance Computing (HPC) and SLURM

## HPC and SLURM
High-performance computing (HPC) is a broad term used to describe the use of high-capacity computing power, such as supercomputers and cluster computing, to solve computationally advanced/challenging tasks. Here, we introduce an approach to using HPC through the Slurm workload manager. 

The Slurm workload manager, formerly Simple Linux Utility for Resources Management (SLURM), is an open-source job scheduler for Linux and Unix kernels used by various supercomputers and computer clusters worldwide. It is highly scalable management for job scheduling for large and small Linux clusters. A general overview of the Slurm workload manager can be found [here](https://slurm.schedmd.com/overview.html).


## Using SLURM (on Windows)

Here, we will introduce an approach to using Slurm on Windows by installing `Windows Subsystems for Linx (WSL)`. In light of this, we will start with installing `Ubuntu` to install Linux on Windows. For those not using Windows, you can skip the `Installing Ubuntu` below.

### Installing Ubuntu

To install Ubuntu, open up the Windows `command prompt` and type
```bash
wsl --list --online
```
This will demonstrate available WSLs, which include `Ubuntu`. Then, install `Ubuntu` by typing: 
```bash
--install -d Ubuntu
```
Once `Ubuntu` is installed, you will be asked to create a new username and password. After doing so, you will be in the Linux command prompt. To open up a new Linux command line, you can open up a Windows command prompt and type `wsl` to do so.

### SSH to a Server
To SSH into a server computer that you want to submit Slurm jobs, first open the Linux command line. Next, you can ssh into the server using typing `ssh`.
For example, for a server computer with the address of `server.computer.edu` with your user name `username`, type the following.
```bash
ssh username@server.computer.edu
```
Now, you are on the server computer, and you can access files and explore the server computer.

### Transferring files from and to the Server Computer
Before submitting jobs to Slurm and after the jobs are done, you will have to transfer data from your PC to the server computer and from the server computer to your PC. For example, we will transfer a file `my_file.mph` from the PC to the server computer using the following command.
```bash
rsync my_directory/my_file.mph username@server.computer.edu/server_directory/my_file.mph
```
Now, your server computer will have the file `my_file.mph` under the directory `server_directory`.
Transferring a file (for example, an output file `my_output_file.mph` generated as a result of computation from the job submitted to Slurm) from a server computer to the PC can be similarly done using the following command.
```bash
rsync username@server.computer.edu/server_directory/my_output_file.mph my_directory/my_output_file.mph
```
Various options using `rsync` command to transfer files can be found [here](https://www.computerhope.com/unix/rsync.htm).

### Creating shell scripts and running batch jobs
In Slurm, a batch script can be submitted using `sbatch` command, with shell scripts (`.sh` files) that contain information about the jobs.

Consider the following simple example of a shell script `run_comsol.sh` that runs `my_file.mph`.
```bash
#!/bin/bash

#SBATCH --nodes=2
#SBATCH --nodelist=node-1,node-2
#SBATCH --cpus-per-task=12
#SBATCH --time=2-23:59:59
#SBATCH --mem=50GB
#SBATCH --mail-type=ALL
#SBATCH --mail-user=myemail@myschool.edu

INPUT_PATH="/server_directory"
SAVE_PATH="/server_directory"

comsol batch -nn 2 -inputfile $INPUT_PATH/my_file.mph -outputfile $SAVE_PATH/my_output_file.mph -study std1;
```
Note that `#SBATCH --nodes=2` means that I am requesting 2 nodes for the job using cluster computers, and `#SBATCH --nodelist=node-1,node-2` is assigning the two nodes. Other `comment lines` are to used to assign the cpus per task (`#SBATCH --cpus-per-task=12`), specify a wall clock time (`#SBATCH --time=2-23:59:59`) , assign memory of each node (`#SBATCH --mem=50GB`), and receive emails about the job's status (`#SBATCH --mail-type=ALL`, `#SBATCH --mail-user=myemail@myschool.edu`). 

Now, using the following command line, you can submit the job to Slurm using the following command.
```bash
sbatch run_comsol.sh
```
After submitting the batch job using `sbatch`, when the requested computational resources are available after the queue, the batch job will run. Note that this particular example is to run comsol in batch using `comsol` command and `batch` argument. The commands for running applications are application-specific. 

### Viewing and Canceling jobs
After submitting the batch jobs, you can view the submitted jobs using `squeue` command. For example, the following command allows you to see all the jobs submitted by the user with the user name=`username`

```bash
squeue -u username
```

Also, you can cancel a submitted job using `scancel` command. For example, if your submitted job has a job ID of `12345`, you can cancel that job using the following command

```bash
scancel 12345
```
