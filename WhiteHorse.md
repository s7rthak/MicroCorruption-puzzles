As usual we start with **b main**. Here we have a *login* function. Now we inspect the *login* function. The *login* function
has an *conditional_unlock_door* function which catches the eye. We also see that *r15* is compared to 0 in the *login* 
function through the *tst* command. If it is zero then password incorrect is displayed but if it is not then access is granted.
Thus we have to check transitions on *r15* on application of *conditional_unlock_door* function.
