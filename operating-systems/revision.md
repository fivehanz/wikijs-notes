<!-- TITLE: Revision -->
<!-- SUBTITLE: A quick summary of Revision -->

# Revision
Process Management
		* Process
		* a process is a program under execeution
		* active entity (program is passive entity)
		* can be assigned/executed on a cpu core
		* enables concurrent programming
			* cpu switch depending on scheduling
		* processes are secure (files, i/o, p-p, can't choose which cpu core)
		* don't share resources like threads
	- Two main characteristics
		* Resource ownership
			> own an address space (Vmem)
			> access to set of resources (mem, files, io)
			> OS blocks interference p-p
		* Scheduling
			> running - actually using cpu
			> ready	- runnable, temp stopped
			> waiting/blocked - unable to run, waiting for a signal/event

	- Implementation
		* Ready queue (fifo)
		* Blocked queue (fifo)
		* weakness - looking through all processes that need to be WOKE
	
	- Context switch - enables cpu to switch between processes (running->blocked, pick blocked->ready->running)

Multithreading
	- A process has at least one thread
	- Can support multiple threads in one process
	- Threads share memory
		* Thread creation only creates a new thread control structure, not a whole process
	
Threads
	- Thread -> unit of dispatching in modern OSs
		* has own register context & stack space
		* "lightweight" processes
	- Process -> unit of resource ownership
		* has at least one thread created with process
		* threads share process resources (code, data, file, i/o)

	- Threads have no protection between t-t
		* might overwrite eachothers data

	
Thread Implementation
	- User-level
		* use thread library (not real threads)
		* cannot run on multi cores
		* if one thread blocks, the whole process blocks
		* no context switch
		* mode switch slow as fuck (one thread accesses kernel at a time)
		* create your own inferior scheduling
		* not used by mainstream OSs
	- Kernel-level
		* generally better
		* can run on multiple cores
		* independent threads
		* used by mainstream OSs
		* multiple threads can access Process at the same time
		* actually good scheduling
	- Combined
		* for compatibility
		
Comparison Threads & Processes
	- Speed: Threads > Processes
		* creation, termination, switch
	- Communication: Threads > Processes
		* no need for kernel routines
	- Flexiblity: Threads < Processes
		* threads cannot run on multiple cores
	- Protection: Threads < Processes
		* threads share memory, may intefere t-t
	- If one user thread blocks, all block (¬for kernel)

Scheduling
	- Non-preemptive
		* bad boi
		* hogs resources until finished
		* cannot be interrupted
	- Preemptive
		* gud boi
		* interrupts after time slot expires -> ReadyQ
		* used by most OSs

	- Performance
		* CPU - needs to be busy
		* Throughput - how many processes completed for a time unit
		* Response time - time it takes for the OS to respond for 1 process
		* Turnaround time - time to execute a process (including wait time)
		* Waiting time - time a process has been in the ReadyQ
	
First come first serve scheduling (FCFS)
	- Non-preemptive (bad boi)
	- Serve processes that are first on the readyQ first
	- Favours long processes (long burst times)
	- Leads to poor utilisation of CPU/IO
	- Average waiting time fluctuates
	
Round Robin (RR)
	- Preemptive (gud boi)
	- Fixed time units (usually 10-100ms)
	- Each process gets 1/n time
	- Longest time to wait is (n-1)q (q is time, n is p count)

Lottery Scheduling
	- Gives all processes a "lottery ticket" (resources)
	- Each winner gets 20msec of CPU

Scheduling in real-time systems
	- Have to meet some deadline
	
	- Hard real time
		* Absolute deadlines
		* Danger/damage if deadline missed
		
	- Soft real time
		* Not mandatory, but preferred 
		* No danger, system continues to operate

	- Periodic scheduling algorithm
		* Effective if you meet all deadlines

Synchronisation
	- Resource competition
	- Solution
		* Enforce mutual exclusion between processes
			> Put processes in an orderly queue for some resource they all need
	
	- Race condition
		* Multiple processes read/write shared data
		* Race to perform the action first
		* Result depends on order of execution

The Critical Section Problem
	- Causation
		* Race conditions
		* Deadlocks
		* Starvation
	- Solution
		* mutual exclusion (may result in deadlocks/starvation)
		* serialisation
			> one process is allowed at critical section for a resource
		* semaphores/locks

	- Lock
		* shared data item
		* acquire on entering CS
		* release on exiting CS
	- Semaphore 
		* locks, but better
		* allow multiple processes in the CS
		* easier to implement
		* increment/decrement mechanism
	NOTE: Can change decrement/if order on semaphore
		* negative number - processes blocked count
		* finished process needs to wake up next in Q

Producer - Consumer Ring buffer
	- Producer & Consumer are mutually excluded
		* Only one Producer OR one Consumer can interact with the buffer at any given time
		* Semaphores track 'emptiness' and 'fullness' of the buffer
	
Dining Philosophers problem
	if you have 5 forks and 5 seats, needs 2 forks to eat.
	How to prevent deadlocks and starvation?
	- Restrict 'sitting' on table to n-1 where n is number min(seats,forks)
	- Done via semaphore to track seats & forks

Monitor
	- enforces mutual exclusion
	- semaphore, lock etc.
	- have wait/signal mechanisms

Memory Management
	- Memory Abstraction
		* programs operate with abstraction of physical memory
			> program is a set of processes
			> programs logical adress is translated to physical in the kernel whenever its accessed from a process

	- Size of address space depends on processor architecture (e.g. 2^32 - 4 billion logical adresses for 32bit)
	
Internal fragmentation
	- Programs utilise complete partition, even if they don't need it
	- The block of data is smaller than the partition

External fragmentation
	- When data blocks are not contiguous 
	- Memory utilisation declines

Virtual Memory Management
	- Modern approach
	- Not bothered by external fragmentation
	- Processes are only partially loaded into logical memory

Paging
	- Allows non-contiguous allocation of memory
	- Frames are in physical memory
	- Pages are in logical memory
	NOTE: They're the same size, frames go into pages

	- avoids external fragmentation
		* it uses it as an advantage (kind-of)
	- Supported by modern hardware

Adressing Virtual Memory
	- If you have a 32 bit architecture
		* 4kB per page (2^12 bytes)
		* 12 bits to reference location in a page
		* 32-12 = 20 bits to reference a page
		* 2^20 = 1,048,576 pages

Translation Lookaside Buffer (TLB)
 	- Cache the most used pages
	- TLB hit 
		* A requested page is in the cache
		* Fast as heck
	- TLB miss 
		* A request page is NOT in the cache
		* Page added to cache alongside with Frame, potentially replacing other less used pages
		* Slow as heck

	- No external fragmentation
	- Internal fragmentation
		* Last allocated process frame might not be needed e.g. Process may need N frames + 1 byte, but there will be N+1 allocated frames
		* Expected is one half page per process
	- May not be able to allocate a contiguous area of mem
	- Page table may be subject to paging

Resident set
	- Reference list of pages in RAM (stored as frames)
	- Limited to number of frames a process may use
	- Periodically clean up pages from the resident set if not in the working set

Working set
	- Pages that a process needs to complete itself
	- An approximation of the program's locality
	- Gives estimate of how many frames are to be allocated to a process
	- Creates a working set window
		* Approximates the Working set
		* Drops a page from the working set window after a period of time

Principle of Locality 
	- References to memory locations cluster
	- Can "predict" which memory locations to call in the future, without a prompted request
	- Indicates that virtual memory can be managed efficiently

Replacement Policy
	- Which page to replace with a new page (when needed)
	- Try to remove least needed page (in the future)
	- Use patterns to 'predict' future
	- Minimising page faults is key

Page replacement algorithms
	- Optimal policy (OPT) is benchmark
	- Least Recently Used (LRU)
	- First-in-first-out (FIFO)
	- Clock algorithm

Optimal Policy (OPT)
	- Optimal in theory
		* Cannot implement
		* Looks in the future
	- Benchmark for replacement algorithms
		* Gives minimum page faults
	- Replaces the block that is referenced the furthest in the future
	- There's always at least N page faults (Initialisation), where N is number of the frames.
	
Least Recently Used (LRU)
	- Replace page that has been referenced the furthest away in the past.
	- Good behaviour in terms of page faults
	- Hard to implement as it's costly and has a lot of overhead
	- Keep track of Tick number/Time when a page was last referenced

First-In-First-Out (FIFO)
	- Round-robin style
	- "Oldest" initiated page gets removed
	- Doesn't account for usage, only initialisation

Clock Algorithm
	- Circular buffer, all frames are empty
	- Expansion on FIFO
	- Implementation of Second Chance algorithm
	- Replaces pages that are unused recently 
	- Arrow pointer does not move per tick (moves when new page is to be added or a replacement is to occur)
	- Initialise page as used recently
	- Once clock hand goes over a used page, sets it to unused

Thrashing
	- When a process is repeatedly page faulting
		* Not enough frames to support set of pages
		* Replace a page you'd have to add later
	- A process is thrashing if it's spending more time on paging than execution

	-Prevention
		* Use sufficient number of frames
		* Principle of Locality

Frame Allocation to Process
	- Each process is allocated empty frames
	- Demand-paging
		* Allocates more frames to a process in case it Thrashes
	- How many frames to allocate to a process

Minimum number of Frames
	- Increase/Decrease the size of the resident set
		* Too low - it thrash
		* Too high - it waste
		* Get just enough frames so it works perfectly

File Management
	- Files
		* Provide a way to store information on disk
		* Abstraction concept
			> A user does not care how the file is saved, only by its paths & contents
	- File System
		* Organised
			> Directories
			> Files
			> Data
		* Efficient
			> Files are blocks of bytes
		* Secure
			> Permissions
			> Back-ups
			> Error recovery
	- File Allocation
		* Disks are organised as blocks
			> Blocks have a set size
		* A file is at least 1 block
		* Block allocation strategies
			> Contiguous
			> Non-contiguous
				! chained
				! indexed
				! FAT
				! i-Nodes
File Allocation Table (FAT)
	- Linked-list allocation form
	- FAT stored in memory
		* Blocks don't waste space for pointers
		* All pointers in main memory
		* FAT entry points to data block and next FAT entry

Indexed Allocation
	- Fast load of complete file
	- Random access to a particular block
	- Indexes are hierarchical
		* Contain small list of addresses

Inodes (index node)
	- Inodes have references to N blocks
	 	* If file cannot be stored in N blocks (InodeParent)
		* InodeParent reference other Inodes
		* Inodes will resemble a tree with N branches
	- Wizardry
		
Journaling File System
	- Idea
		* Keep a small circular log
		* Record actions prior to doing them (easy traceback)
		* Operations needs to be idempotent
	- System can "roll forward" in case of a crash
		* Proceeds from last known completed step
	- Robust in case of a system crash
		* Logs checked after recovery
	- Changes to file system are atomic
	- Logged operations must be idempotent

Deadlock Conditions
	- Mutual Exclusion
		* 1 thing at a time pls
	- Hold & Wait
		* wait until the 1 thing is done
	- No Preemption
		* No fixed time slots (long boi takes up cpu boi)
	- Circular Wait
		* x waits y and y waits x

Handling Deadlocks
	- Prevention
		* Avoid one of the pre conditions
	- Avoidance 
		* The system is aware when a deadlock will happen and refuses to pass resources to the process
	- Detection
		* Resources are not limited
		* Periodic check
			> Abort all deadlocked processes
			> Rollback deadlocked processes
			> Successively abort until no more deadlock
			> Abort all deadlock processes and pass resources to other processes








		