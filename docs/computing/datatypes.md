##Type
The type represents the overall idea of the data we are trying to represent or use.
This can be practical or for usability.

Integer - a whole number. This is the most important datatype that we spent the time building up intuition for in chapter 1. It is simply a bianry representation of any number up to the maximum values allowed. If you have exactly 8 bits and only want to represent from 0 and positive numbers, you can represent up to 2^N - 1 different integer numbers.


Floating point - A floating point number is a way of representing decimal points. I say a way because it is not the only way, and is certainly not the most obvious way.
If you think to yourself for a moment you would realise that the simplest way to represent decimal points is the way we humans do that... with decimal points! 
We simply define a point at which we want to have our decimal point and then put it there. Decimal points work for binary the same way they work in binary (except they're not really decimal points anymore). In an eight bit number everything before the decimal point is as with a normal integer, and everything after will simply be a fraction (in binary but it is the exact same principal as decimal decimals). I.e. 1100.1010 is 1100 which is 4 + 8. .1100 is 1/2 + 1/4. So in total we get 12.75. 
To represent 1/3 using only powers of 2 is impossible just like in decimal, so let's get pretty close with 0.333333.
Lets use all 8 bits fractional bits. We can simply take the maximum value of these 8 bits ie 2^8 and multiply this by 1/3. 2^8 / 3 = 85.333. We can't represent the fraction inside our fraction so we will just take 85. 85 in binary is 64 + 16 + 4 + 1 = 0b01010101
So 1/3 with 8 bits of fractional accuracy is 0.01010101
If we convert this to decimal we get 0.25 + 0.0625 + 0.015625 + 0.00390625 = 0.33203123

Not too bad right.




Greedy Algorithm for finding binary number is biggest power of 2 added to sum that doesnt exceed number.



![floating point](https://engineering.fb.com/wp-content/uploads/2018/11/floating_point_4_darkcolor.006.png)


Boolean - a bool is a binary flag. It is the "IS" state of something. This could be represented by a single bit but as we discussed it is not practical to - and thus we have not designed computers to be able to address single bits. For this reason a boolean is often just an 8-bit unsigned integer. Why not just use an 8-bit unsigned integer? Again this is for our feeble human minds. It is convenient to have a number that can only be 0 or 1 since otherwise some programmer will try to set a boolean to 2 at some point which will break things. 




##Size 
This is how many bits are used for representation.
For floats we can have the normal 32 bits of precision (float precision), or we can double that 64 bits of precision (the double data type.) or we can have half precision (16 bits).
For integers we can have byte sized (8) "normal" sized (32) or we can have "long" 64 or long long (128).



##Signedness
Sometimes we don't need the negative part of the numberline, sometimes we do.
When we do, we should denote if a number is positive or negative. Using the first bit of our data type makes this simple. 0 For positive, 1 for negative.
Note that if we are using this bit to store positive and negatives we actually cut our number of possible values in half since we lose a bit of size.






# Examples:

##Float
We said earlier that precision in floating point datatypes wasn't really a huge concern because as a fraction of the whole number you would have a large amount of accuracy.
I.e.

Here are two caveats to that
0.29999999
Coordinate positions