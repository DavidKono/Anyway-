##Bytes
Question: how big is a byte? 
Answer: two nybbles!

A byte doesn't have to be 8 bits (an octet), but as we discussed with the binary system itself, there is such thing as being both small-and-big enough to be useful.  

Here is a very true modern definition of a byte: it is the smallest addressable unit of memory and it is 8 bits long.

Now, the truth is that what we think of as a byte nowadays does not NEED to be how it is. Bytes were once 5 or 6 (or 9!) bits long. They were also once not addressable by memory.  
Why did they even have a distinct unit called "byte" if they couldnt' address it?  
The most fundamental reason is because of what we want to represent. If we only want numbers, sure, you can use 1 bit or 128 bits, just chain them together and create an instruction that knows how many bits you are using. What if we want a specific type of data of which there are a set number of values. Apart from just numbers, we will at some point want to use our computer for things other than than just mathematics. We haven't even printed "Hello World!". That's right we need characters, and how many chars do we need to represent all the "useful" ASCII characters? 2^7! Wait what? Well yeah, we definitely can't have a 7-bit byte. We have arrived at a pretty useful thing to be able to address, so if we made it a power of 2 we could address it super easily. This is also where hexadecimals usefulness comes from. This extra bit we add to make it 8 bits allows us to perform a parity check on our 7 ASCII bits, or define another 128 characters (in the UTF-8 standard).

Now, upon learning this you may feel enraged at the implication that having text characters had any influence on the effiency of my use of memory space, what about the speed of my numerical calculations! Fortunately, you need not fret. The most aggregious case is with boolean where we use 8 bits to represent what could be done with one bit. The question you might have to ask yourself is in what application do we need 8 booleans let alone 64 in one cycle? When we eventually get to 64-bit processing you will see that there might be little practical difference in using 8, 32, or 64 bits for a boolean in terms of processing speed, and the 7 bits of memory we waste we should not cry about for all the complexity we have saved by not addressing individual bits. Of course if you really still want bit addressability you can always just bit shift your integers. 

## Memory
Finally, our last number to explain in basic computer architecture, the word-size, 64!
This is the 64 in 64-bit computer. It refers to how many register addresses our architecture can address.

This again is "arbitrary" in that we not too long ago had (and sometimes still have) 32-bit CPUs. The central reason to move to a 64-bit architecture is that 32-bit supports up to 2^32 addresses which is 2^2 (32 - 30) gigabytes, or 4 gigabytes. This was once a futureproof amount of memory but is currently this is less than the amount of memory in a cheap android smartphone. Doubling our exponent of addressable range of bits now gives us 2^4 exabytes (2^60) = 16 exabytes.








## Instructions



# Binary code


Single-core single-thread 
Nope

Superscalar and out-of-order execution
Multiple execution units per core. Can performn multiple instructions in same cycle for a thread.

Simultaneous multithreading  
Single core can interleave instructions from multiple thread in same cycle
Depends on workload - obviously can't use same execution unit at once.

Multi-core - each core execute instruction each cycle for assigned thread(s)






