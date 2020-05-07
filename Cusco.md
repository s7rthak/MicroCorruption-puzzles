As usual we start with **b main**. The *main* function leads to the *login* function. We directly go to the fork of right or wrong password.
We somehow have to go through the 'Access Granted' route and we see that there is a *jz* statement before it. The *jz* is leading to the 
wrong password statement so the zero flag should not be set. We also see a *tst* (test?) statement before it. I could guess that the *tst* statement
was comparing the argument to something. That something has to be 0. If we somehow manage to
make it non-zero then we are done. Now is the time to investigate the *test_password_valid* function. Maybe we can rewrite the whole program
through injection... But that was not to be as my hexadecimal input was not being injected and the program remained the same. So maybe we
can't change r15 but do something else. And as the previous puzzle was a overflow, this puzzle should be on the same lines. We see that 
the stack has reserved 16 characters for password after putting 0x443c(*stop_progExec*) as the next execution. But due to overflow, we can
change it to our liking. I first tried to go to address 0x452c but that didn't work and then I realized that we just have to unlock the door 
and we would be done. So we can go to the address 0x4446 after completion of *login* function. Therefore simply type any 16 characters after
which **FD** to denote 4644 which denotes the address 0x4446 and in this way the the **main** function after completion goes on to the 
**unlock_door** function and the lock is cracked!
