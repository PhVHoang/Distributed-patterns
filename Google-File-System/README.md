<img width="811" alt="Screen Shot 2021-06-22 at 23 06 07" src="https://user-images.githubusercontent.com/12546802/122939265-74a9fe00-d3ae-11eb-8691-20868ad0cf8a.png">

<img width="785" alt="Screen Shot 2021-06-22 at 23 05 56" src="https://user-images.githubusercontent.com/12546802/122939272-7673c180-d3ae-11eb-9a4e-a7d3fd55eae6.png">

* Regular heartbeats to ensure chunkservers are alive
* Ensure chunk replica count: if chunkserver is down, master ensures all chunks the were on it are copied on other servers and ensures replica count remains same
* Single master for multi-TB cluster
  * Large chunk size
    * 64MB chunk
    * Reduced meta-data
    * Reduces client interactions
    * Client caches location data
* Operations Log
  * Record of all ops
    * Checkpointed regularly
    * Happens in background thread 
    * Used if master crashes
    * Rebooted master replays log
* Shadow Master
  * Single Point of Failure
    * Ops log is replicated remotely
    * Shadow master uses the logs
    * DNS change can change master
    * Shadow master may lag slightly
* Chunk servers store and re-check checksums for all chunks (in 64kb blocks)
* Master on reboot asks chunkservers for the chunks they have
* Checksum failures are reported to master
* Master can rebalance replicas to distribute load more evenly
* File locks for read/write
* Record appends
* Snapshots
* Write leases provided to clients
* File deletions
* Chunk Garbage Collection  
      
