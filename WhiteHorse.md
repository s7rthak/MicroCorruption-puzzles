As usual we start with **b main**. Here we have a *login* function. Now we inspect the *login* function. The *login* function
has an *conditional_unlock_door* function which catches the eye. We also see that *r15* is compared to 0 in the *login* 
function through the *tst* command. If it is zero then password incorrect is displayed but if it is not then access is granted.
This is very similar to the **Cusco** challenge so maybe the same idea can be used. There we had used stack overflow to directly
go to the *unlock_door* function. But this challenge doesn't have an unlock door function. Unlocking the door, as we go back to 
see what was occurring in the **Cusco** challenge, was simply passing 0x7f as argument to the <*INT*> function and calling the
function. We notice that this challenge also has an <*INT*> function similar to the **Cusco** challenge. Calling it is what remains.
This can be directly done as all those instructions can be passed on as the password and the return address can be modified
to point to the start of the instructions that we inputted as password. The idea is sort of similar to XSS as we are executing 
the code that we pass on as input. We go back to the **Cusco** challenge and copy the instructions of the *unlock_door* function.
Care should be taken to note the address of the <*INT*> function in the present challenge. Now we pad the instructions with
required number of 0 (to take care of 16 character allowed passsword), add 3c40 to its end and a further 3c44 to the end to
safely stop program execution. Thus we input 30127f00b012324521533041000000003c403c44 into the prompt and the lock is cracked!
