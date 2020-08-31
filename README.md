# GossipSimulator
A simulation for demonstrating process failure detection via gossiping. This program was developed as part of the course 'Verteilte Systeme (SS20)' for the written composition of the lecture notes 'Systemmodelle & Architekturstile'.

## Requirements 
- Java SDK 11.0.2

## About 
This program simulates a cluster of processes by using threads. By clicking on the process-buttons in the graphical user interface, processes can be dis- or enabled. 
When a process has been disabled, the other members of the cluster will recognize its absence by using the gossip-method. The textfield below will show the information each process knows about the rest of the cluster.

## How it works 
Each process has a list of healthy (active) and suspicious (inactive) members that it knows about. By sending out messages periodically to their immediate neighbours, processes let other members know that they are still alive. When such a message reaches a process, a heartbeat counter increases in the healthy-list for that specific member. Once the counter has not increased for a certain amount of time (in this case 3 seconds), that process will be saved in the suspicious-list.
The processes also periodically send out all of the information they know about the other members to a random process from the cluster. That information is used to compare the lists of the receiver with the sent lists. If some heartbeats are greater than what it knows or the healthy list contains a processes which it deemed as suspicious, the receiver updates its information accordingly. 
By using this gossiping method, all processes stay up to date about the state of the cluster.
