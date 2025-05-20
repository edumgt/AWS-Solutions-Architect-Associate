
# Block Storage
In block storage, data is stored in fixed-size blocks that have their own addresses.
Because each block is addressable, blocks can be retrieved efficiently and directly.
When data is requested, the addresses are used by the storage system to organize the blocks in the correct order to form a complete file to present back to the requestor.
If you want to change one character in a file, you just change the block, or the piece of the file, that contains the character.

### Use case
block storage is optimized for low-latency operations, high-performance enterprise workloads and transactional, mission-critical, and I/O-intensive applications.
- Transactional workloads: transactional and fault-tolerant database
- Containers: store containerized applications on the cloud
- Virtual machines: supports popular virtual machine (VM) hypervisors
