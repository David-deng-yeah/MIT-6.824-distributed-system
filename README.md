# MIT-6.824-distributed-system
![image](https://user-images.githubusercontent.com/65102150/183294228-fd829199-e2cf-4471-a137-9a746d912332.png)


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

## Lab 4
