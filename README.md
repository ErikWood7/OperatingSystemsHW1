# Producer-Consumer Example

## About
This project shows how two programs, called `producer` and `consumer`, can work together to share data. They use a buffer (a small shared space) to pass information, and they make sure not to interfere with each other using some basic controls, called semaphores.

## Files
- **producer.c**: Creates random numbers and adds them to the buffer.
- **consumer.c**: Reads numbers from the buffer and displays them.
- **shared.h**: Contains shared settings and structures that both programs use.

## How It Works

### `producer.c`
1. **Sets Up Memory**: Opens some shared memory for storing numbers.
2. **Prepares Semaphores**: Uses semaphores to coordinate the buffer’s use with the consumer.
3. **Generates Numbers**: Loops to create numbers and place them into the buffer.
4. **Clean-Up**: Closes and unlinks shared memory and semaphores after finishing.

### `consumer.c`
1. **Accesses Shared Memory**: Opens the same shared memory to read numbers.
2. **Uses Semaphores**: Coordinates access with the producer to avoid conflicts.
3. **Consumes Numbers**: Loops to read numbers from the buffer and prints each one.
4. **Clean-Up**: Frees up shared memory and semaphores after all numbers are read.

## How to Run It
1. **Compile**:
   ```bash
   gcc -o producer producer.c -lpthread
   gcc -o consumer consumer.c -lpthread
