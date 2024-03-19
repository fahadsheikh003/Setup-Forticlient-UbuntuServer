# To Map a specific resource to Localhost using SSH

SSH Script
```
start \b ssh <username>@<Server> -p <Port> <Command>
ssh -L <LocalPort>:<RemoteServer>:<RemotePort> -N <username>@<Server> -p <Port> 
```