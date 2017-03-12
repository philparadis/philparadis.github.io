---
layout: post
title: Intro to using GPUs at MILA
published: true
permalink: /:year/:month/:day/:title/
author: Philippe Paradis
categories: IFT6266-project
---

# Introduction to using GPUs at MILA

We will see how to use SLURM to find available GPUs, submit GPU jobs or request GPU interactive allocations, detach and eattach to GPU interactive sessions and more.

### High-level information about SLURM partition
`> sinfo`

### Aggregate list of available GPUs by model
`> savail`

### More detailed list of available GPU by nodes, but more importantly, displays the total memory per GPU model
`> sinfo -Ogres:27,nodelist,features -tidle,mix,alloc`

### Request an interactive shell *with CPU only*
`> sinter`

### Request an itneractive shell with randomly assigned GPU
`> sinter --gres=gpu`

### Request an interactive shell with a specific GPU, in this case, the model must be a Titan X GPU
`> sinter --gres=gpu:titanx`

### Show all running or queued jobs belonging to myself
`> squeue -u $USER`

### Reattach to a job still running after the terminal or SSH connection was interrupted (find the job ID with squeue)
`> sattach --pty <jobid>.0`
