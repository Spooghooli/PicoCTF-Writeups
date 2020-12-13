# flag_shop challenge

We are given the source code of a program and the host and port for a netcat connection

Looking over the source code let's us know that it's a program about buying flags and we can probably guess that our flag is the "1337" flag that costs way too much

Once we connect to the host we quickly understand that the program running is the one we were given

There is one place that looks more interesting than the rest

```c
printf("These knockoff Flags cost 900 each, enter desired quantity\n");
                
                int number_flags = 0;
                fflush(stdin);
                scanf("%d", &number_flags);
                if(number_flags > 0){
                    int total_cost = 0;
                    total_cost = 900*number_flags;
                    printf("\nThe final cost is: %d\n", total_cost);
                    if(total_cost <= account_balance){
                        account_balance = account_balance - total_cost;
                        printf("\nYour current balance after transaction: %d\n\n", account_balance);
                    }
                    else{
                        printf("Not enough funds to complete purchase\n");
                    }
```
Due to the way that the account balance is computed we get the idea that we should somehow get the "total_cost" variable to be negative, so as to add money to our account every time we buy flags we can do this by giving a pretty large number when we are asked for the number of flags to buy
