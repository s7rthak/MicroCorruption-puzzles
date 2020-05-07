As usual we start with **b main**. The main function leads us to the login function which prompts the box asking for password. We type a 
random password and check the memory dump to see where it is stored. Then we proceed further into the login function. We now come to the 
part where we fork into correct password via 'Access Granted' or we run into wrong password. We see a *jne* statement so something is checked
before jumping. That something lies on the line before it i.e. a *cmp.b* satatement. It is comparing the thing at address 2410 with the number
45. If you check what is presently at address 2410, you are likely to find 00(8-bit, as *cmp.b* compares bytes), unless you typed more than
16 cahracters as password. And that basically is the answer to this puzzle. The password checker isn't checking if the the number of characters 
you entered is between 8 to 16 characters. This leads to the topic of overflow which was common in old softwares. Thus what we can do is 
simply type any 16 characters and the character 'E' which corresponds to the ascii value of 0x45(69?) and we have cracked the lock!
