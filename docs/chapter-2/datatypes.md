##Type
The type represents the overall idea of the data we are trying to represent or use.
This can be practical or for usability.

Integer - a whole number. This is the most important datatype that we spent the time building up intuition for in chapter 1. It is simply a bianry representation of any number up to the maximum values allowed. If you have exactly 8 bits and only want to represent from 0 and positive numbers, you can represent up to 2^N - 1 different integer numbers.


##Fixed point
If you think to yourself for a moment you would realise that the simplest way to represent decimal points is the way we humans do that... with decimal points! 
We simply define a point at which we want to have our decimal point and then put it there. Decimal points work for binary the same way they work in binary (except they're not really decimal points anymore). In an eight bit number everything before the decimal point is as with a normal integer, and everything after will simply be a fraction (in binary but it is the exact same principal as decimal decimals). I.e. 1100.1010 is 1100 which is 4 + 8. .1100 is 1/2 + 1/4. So in total we get 12.75. 
To represent 1/3 using only powers of 2 is impossible just like in decimal, so let's get pretty close with 0.333333.
Lets use all 8 bits fractional bits. We can simply take the maximum value of these 8 bits ie 2^8 and multiply this by 1/3. 2^8 / 3 = 85.333. We can't represent the fraction inside our fraction so we will just take 85. 85 in binary is 64 + 16 + 4 + 1 = 0b01010101
So 1/3 with 8 bits of fractional accuracy is 0.01010101
If we convert this to decimal we get 0.25 + 0.0625 + 0.015625 + 0.00390625 = 0.33203123

Not too bad right.

Of course if I simply hand you 0b01010101 I haven't told you where the decimal place is, it actually just looks like the number 85 in decimal. I could define the datatype as having the decimal place at a fixed position. This is completely fine. I might say that in this datatype half or a third or even all of the digits are after the point symbol. This is the ideal case where we know ahead of time the exact precision we want on our datatype, but this is often not the case. Remember that if we want to do addition with out new datatype with n places of "decimal" place, we would have to ensure the number we are adding it to also has the same number of decimal places for this addition to work. 
We might also want to be able to change the number of bits dedicated to the decimal place. We can define the first 4 bits in a 32 bit datatype to encode the place of the decimal place. This would let us allow a maximum place of 15 binary places of precision (4-5 places of decimal precision), or if we chose 0 placea of binary precision we could allow up to 32-4 = 28 bits of integer size i.e. 268 million in unsigned or 134 million in signed integerness. See that we have allowed ourselves to control the precision so that we can preserve accuracy even for relatively high numnbers, ie choosing the maximum of 15 binary places gives 8192. We can then add a fraction on top of this i.e. down to a precision of 1/2^15.

Notice that we balance between decimal precision and maximum integer size here.
In my opinion a good balance would be to ditch the leading 4 zeros and instead have 16 binary places of each i.e. 16 binary places (5 decimal places) and a max size of 2^16. The problem with this is that you might disagree with me completely. If you work with small numbers you might want a full 32 bits of precision, and would have to agree with that beforehand. A person working with large numbers would just want a full 32 bit integer.

What if we could satisfy both exclusively. We already achieved a simple version of this with our controllable digit places, but we can do even better at the cost of ditching integer arithmetic.

##Floating point
What if I told you that I can multiply numbers on the scales of thousand of zeroes, and so can you! 10 with 100 zeroes following it multiplied by 10 with 50 zeroes following it is 10 with 150 zeroes following it. 10 with 100 zeroes following it divided by 10 with 20 zeroes following it is 10 with 80 zeroes following it. 10 with 10 zeroes following it plus 10 with 10 zeroes following it is 20 with 10 zeroes folloing it. 30 with 100 zeroes following it minus 5 with 100 zeroes following it is 25 with 100 zeroes following it!  
Cherry-picked? Yes, but I have demonstrated something pretty cool with scientific notation. If you have never seen scientific notation, instead of writing 5 with 100 zeroes following it, I can say 5 x 10^100 or even simpler, 5E100. 
Even writing out 100 digits would take a long time and yet I can do some basic arithmetic on these huge numbers just by representing it a certain way. The same works for fractions. I can represent one one-thousandth with 1E-3, a millionth with 1E-6, 1 googolth with 1E-100. 
Imagine doing these equations with the normal written multiplication on explicit numbers like we are taught in grade school. It would take forever. 

###Scientific Notation Addition

3.1415E10 plus 9.2653E5
We need both numbers to have the same exponent to perform simple addition, so we shift the smaller number to the right by the difference in exponents (10-5 = 5). This gives 3.1415E10 plus 0.000092653E10.  
3.1415E10  
0.000092653E10  

Now we can see that the numbers line up very simply to give us 3.141592653E10!


I conveniently ignored overflow here, lets do numbers that will create an additional decimal place.  
1.81828E5 plus
9E6

Again we want the same exponent so shift 1.81828E5 by 1 to get 18.1828E6.   

Add them
27.1828E6

So far we have been sticking to one decimal place for consistency, so IF we want to stick to that we will have to normalise them. Shift the digit back to give 2.71826E5.

Another consideration is that here I am working in decimal and doing this manually, but what happens if we only want a certain level of precision, i.e. a significand (the number of non-zero leading numbers) of a maximum value.
If our significand is too small we would have to drop a digit after adding.

###Scientific Notation Subtraction

Subtraction is no different, we simply shift the smaller number to match the larger's. Then we subtract these scaled nubmers. Finally we normalise if necessary.



###Scientific Notation Multiplication 

Multiplication in scientific notation is a similarly simple process. We simply multiply our coefficients and add our exponents.

I.e. 1.5E3 * 2.3E5 
(2.3*1.5) = 2.45
(E3 + E5) = E8

= 2.45E8


###Scientific Notation Division 

Scientific notation is the reverse process. If we want AEB / CED we simply
Divide A by C.   
Subtract D from B.   


##Float
Now we need to convert our findings into binary.

We will want our first bit to correspond to the sign.
Then we will have our exponent. 

I note on the exponent:
All zeros exponent and mantissa = positive and negative sign bit.




What if instead of treating each number as a power of two, we could treat the accumulation of these numbers as the exponent of two itself. That is, we dedicate a few bit to creating a number that controls our scale. If we used 8 bits, we could get a exponent of up to (a maximum of b11111111) 2^255. This would allow us to represent seriously huge numbers. However if we make this exponent only unsigned then we can't get negative exponents and thus can't get fractions. Instead we again use 1 bit for signedness and the other 7 for the actual magnitude of the exponent, that is, -128 to +127. 

Now we also want to decide if this datatype should be signed.
With basic integers this is not actually a problem because you can add signed and unsigned integers together using the exact same hardware - negative signed integers are stored as two's complement. The only thing that changes is whether the extra bit is treated as carry or overflow - but the arithmetic is the same.

With our current float design this is not the case. Remember this is a completely different representation of numbers we have decided on, thus the hardware will have to be physically different to accomodate this. Another feature of being baked into hardware is that we cannot just "decide" when programming if we want our float to be signed or unsigned. The two's complement trick does not work here because our numbers are not linear powers of two anymore. Instead we have an exponent that is is instead used to scale two by.  
Remember, a single bit can usually only double the level of information stored. That might mean having both the positive and negative end of the number line or doubling the amount of precision. Scaling the exponent actually doubles the precision of the exponent in scientific notation - that is, we are getting more bang for our book in terms of size but not decimal place accuracy.  
We could hypothetically have two different floating point datatypes - signed and unsigned - but why fret about doubling our accuracy for the occassional case we want only positive floats when at that point we could just use a 64 bit float.  
That's right, we dedicate a whole 11 bits to the exponent for a maximum scale of 2^1023 and minimum scale 2^-1024, and then a maximum precision of 52 bits in the mantissa!



Greedy Algorithm for finding binary number is biggest power of 2 added to sum that doesnt exceed number.



![floating point](https://engineering.fb.com/wp-content/uploads/2018/11/floating_point_4_darkcolor.006.png)


Boolean - a bool is a binary flag. It is the "IS" state of something. This could be represented by a single bit but as we discussed it is not practical to - and thus we have not designed computers to be able to address single bits. For this reason a boolean is often just an 8-gbit unsigned integer. Why not just use an 8-bit unsigned integer? Again this is for our feeble human minds. It is convenient to have a number that can only be 0 or 1 since otherwise some programmer will try to set a boolean to 2 at some point which will break things. 




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

