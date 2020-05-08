As usual we start with **b main**. We break at the *main* function. Now we inspect the *main* function. It has two function calls
after which *stopProgExec* runs ending the program. Thus our password-checking must be occurring in one of the two functions.
We set a breakpoint at second function call i.e., **b 444a** to check what the first function does. But we notice that the
the prompt for password has still not appeared so we can conclude that it is not checking the password but does something else.
So the second function displays the prompt and (maybe?) checks the password. So we continue and get the prompt for password.
We type a random string and check what happens with it. The string is placed in the stack. Now stepping through the instructions,
we come across a cmp we see that 0x7358 is being compared with 0x24(*r4*) which is essentially the memory address of our *sp*
which presently points to our inputed string! 0x7358 is equivalent to sX but we have to swap the value due to sort of FIFO
policy and we have Xs. Let us input this and check if there are any other *cmp* branches. Fortunately there aren't and we have
cracked the lock!
