# The memory hierarchy 

While we're talking about space and memory, it's worth mentioning that not all memory in computers is equal! In fact, there is a *memory hierarchy*.

Computers have different types of memory available for use, each with different physical properties. Together, they compose a __memory hierarchy__. This image illustrates their relative speeds, costs, and capacities:

<center>
<img
  src="/images/week-01/memory-hierarchy.png"
  alt="A pyramid diagram showing a hierarchy from top to bottom: registers and caches, main memory, secondary storage, and network-based storage."
  style="width:500px;" />
</center>

<figcaption align="center">Figure: The memory hierarchy.</figcaption>

## Registers and Caches

At the top of the diagram we have types of memory that reside on the CPU itself, such as registers and caches. The CPU can retrieve data from registers and caches very quickly, but space on the CPU is limited, so together they represent only a small fraction of the available memory on a computer. Because of this, the data held in registers and caches is generally limited to only the data that was very recently used or will soon be used by the programs being executed by the CPU.

## Main Memory

The next level down in the hierarchy is primary storage, or *main memory*. Physically, it typically consists of what's known as random access memory (RAM) devices. Compared to registers and caches, RAM is much less expensive and can therefore be much larger in size, but it takes the CPU longer to fetch data from main memory. However, the data held in main memory generally represents *all* of the data of programs that are currently being executed.

## Secondary storage

After RAM, the next level in the memory hierarchy is secondary storage, often implemented using magnetic hard disk drives (HDDs) or solid state drives (SSDs). Secondary storage is *persistent*, meaning that the data in secondary storage remains there even when the computer is turned off. This is in contrast to caches and main memory, whose contents are cleared when the computer is powered off. Secondary storage is much larger than main memory, but it also takes much longer for the CPU to fetch data from secondary storage. This is because in order to use it, the data stored on disk must first be moved into main memory through a process known as *paging*.

## Network-based storage

The last level of the memory hierarchy that we will consider is network-based storage. This represents all data that is not stored locally on a computer, and that must be requested and fetched over a network. For example, downloading a file from cloud storage over the Internet is a form of network-based storage. The time to senda request for data over the Internet and then download that file is considerably larger than secondary storage, but you can store much more, since you are accessing files that could potentially be stored on many different computers, or servers.

There are other levels and details within this hierarchy that we have not touched on, but this view of memory is sufficient for our purposes.

<aside>
<b>Check your understanding</b>

Order the following types of memories from least capacity (i.e., can hold only a small amount of data) to greatest capacity (i.e., can hold a large amount of data).

- Network-based storage
- Main memory
- Registers and caches
- Secondary storage

<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>

<b>Answer.</b> In order from smallest to largest capacity: registers and caches, main memory, secondary storage, network-based storage. This is also the ordering of the fastest to slowest types of memory.

</details>
</aside>
