This comtains complete random notes I have made or taken from the internet particularly useful for phrasing ideas




for chapt 0/1/2 introduce the concept of computing generally - just perform a culation and store/move it somehow (ie print to screen).

somehow haver to introduce binary before hardware consideration - just explain that thats how it works



ternary logic 
The numerical base (or radix) defines how many digits will be necessary to represent a certain number, this is the radix economy and is written as E(b,N)E(b,N) for base bb and number NN and calculated with the following formula. 
E(b,N)=b⌊1+logb​N⌋
it can be shown that the lowest average radix economy is reached with base natural log e = 2.72. Note that 3 is actually closer tto e than 2.

https://www.reddit.com/r/askscience/comments/1z3f3s/why_did_the_russian_computer_setun_a_ternary/

"The advantage of binary logic over other radix is that the number of interconnections is significantly reduced. Also, in modern semiconductor computers (i.e. vs. tube) noise margin is important and binary systems have greater noise margin than ternary ones."

"You didn't mention one of the biggest advantages of binary logic...power efficiency. Combining binary and CMOS transistors makes it possible to minimize current paths from Vdd to ground with a minimum of transistors/bit. "

"Any radix other than two, the complexity explodes. For example, if you have a binary adder, you have 2 bits (result + carry) as a result. A ternary adder has 7 (0, 1, 2, 3, 4, 5, 6, plus carry). So, for 1.5x the bits you get 3+ times the complexity. "

"There are some forms of division where it is very handy to have ternary bits where the values signify-1 0 and +1. You use the negative value when you over estimated and subtracted too much.
One big problem with ternary signal voltages is that you lose twice as much noise margin for just 50% more info."

"    Unfortunately, Setun did not realize the potential of base 3 to reduce component counts. Each trit was stored in a pair of magnetic cores, wired in tandem so that they had three stable states. A pair of cores could have held two binary bits, which amounts to more information than a single trit, and so the ternary advantage was squandered."






There are 3 very important numbers in computing: the radix which is the base of the numeral system you are using, the byte which is the smallest addressable unit of memory, and the word size which is the number of bits a cpu processes as a single unit in its registers/ALU/data bus.

I have the unfortunate job of trying to explain the motivation for these numbers being chosen when they are in-fact, fairly arbitrary

Note there is a technique referred to as Single Instruction Multiple Data or SIMD, which corresponds to specially large ALU's which do allow for larger than 64 bit processing in a single cycle for multiple small integers eg 4 32 bit or 8 16bits

When we talk about data types this will make more sense