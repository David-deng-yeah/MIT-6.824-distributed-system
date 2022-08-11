# MIT-6.824-distributed-system
![image](https://user-images.githubusercontent.com/65102150/183294228-fd829199-e2cf-4471-a137-9a746d912332.png)

# 实验源码
[实验源码](https://github.com/David-deng-yeah/distributed-system-sourceCode)

# 课程大纲：

[https://pdos.csail.mit.edu/6.824/schedule.html](https://pdos.csail.mit.edu/6.824/schedule.html)

# 课程时间线

- lec 1 inroduction
    - preparation: read paper mapreduce
    - assigned: **Lab-1-MapReduce**
- lec 2 RPC and Threads
    - code: crawler.go, kv.go
    - preparation: do online go tutorial
- lec 3 GFS
    - preparation: read GFS
    - assigned: **lab-2-raft**
- lec 4 primary-backup replication
    - preparation: read fault-tolerant virtual machines
- lec 5-8 fault tolerance: raft
    - preparation: read raft
- lec 9 zookeeper
    - preparation: read zookeeper
    - assigned: **lab-3-KV raft**
- lec 10 chain replication
    - preparation: read CR
- lec 11 distributed transaction
- lec 12 cache consistency: frangipani
    - preparation: read frangipani
    - assigned: **lab-4-shared KV**
- lec 13 spanner
    - preparation: read spanner
- lec 14 optimistic concurrency control
    - preparation: read FaRM
- lec 15 big data: spark
    - read paper Spark
- lec 16 cache consistency: memcached at facebook
    - preparation: read memcached at facebook
- lec 17 causal consistency, COPS
    - preparation: read COPS
- lec 18 fork consistency, SUNDR
    - preparation: read SUNDR
- lec 19 peer-to-peer: Bitcoin
    - preparation: read Bitcoin
- lec 20 blockstack
    - preparation: read blockstack
- lec 21 smart contracts, Billboard.sol, Casino.sol
    - preparation: read Ethereum White Paper

# Lab

- [ ]  lab1
- [ ]  lab2
    - [ ]  a
    - [ ]  b
    - [ ]  c
    - [ ]  d
- [ ]  lab3
    - [ ]  a
    - [ ]  b
- [ ]  lab4
    - [ ]  a
    - [ ]  b

## Lab 1

lab: mapreduce

introduction:

build a MapReduce system

- implement a worker process
    - calls application Map and Reduce functions
    - handles reading and writing files
- implement a coordinator(master) process
    - hands out tasks to workers
    - copes with failed workers

## Lab2

lab: raft

introduction:

this is the first in a series a labs that we will build a **fault-tolerant key/value storage system**

- in lab2 we will implement raft( a replicated state machine protocol)
- in lab3 we will build a key/value service on top of raft
- then we can “shard” sour service over multiple replicated state machines for higher performance

and in this lab we will implement raft(a replicated state machine protocol)

Raft organizes client requests into a sequence, called the log, and ensures that all the replica servers see the same log.

this lab is splited into four parts: 

- A: leader election
- B: log
- C: persistence
- D: log compaction

## Lab 3

lab: Fault-tolerant Key/Value Service

introduction: 

in this lab we need to build a fault-tolerant key/value storage service using our Raft library from lab2.

our key/value service will be a replicated machine, consisting of several key/value servers that use Raft for replication.

after lab3, we have implemented all part(clerk, service and raft) shown in the diagram of Raft interactions.

![image](https://user-images.githubusercontent.com/65102150/183304044-1ba16da1-4029-4af3-b407-ecfd3bed8dc5.png)


this lab have two part:

- in part A, we will implement key/value service using your Raft implmentation, but without using snapshots.
- in part B, we will use our snapshot implementation from lab 2-d, which will allow Raft to discard old log entries

## Lab 4

lab: Sharded key/value service

introduction:

in this lab, we will implement a key/value system that “shards”, or partitions, the keys over a set of replica groups. A shards is a subset of the key/value pairs, for examples, all the keys started with “a” might be one shard, and all the keys started with “b” will be another, etc.

the reason for shards is performance, cause every replica group can handles puts and gets for just a few of the shards, and groups operate in parallel.

our sharded key/value store will have two main componets:

- a set of replica groups
    - each replica consists of a handful of servers that use Raft to replicate the group’s shards
- the shard controller
    - the shards controller decides which replica group should serve each shard
    - there is a single shard controller for the whole system, implemented as a fault-tolerant service using Raft.
