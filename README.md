# Spawn_debugserver
Jailed ios 17.4+ tool to create a debugserver for lldb to attach.

# Info 
This is a slightly modified version of https://github.com/fritzlb/iOS17-JIT-WIN by fritzlb. Instead of initialising jit this is about setting up debugserver.
Requirements are the same. Tested on 17.4 iphone 14 pro max.

# Files

DebugApp script opens the app sets up the debugserver and prints the apps pid for easier connecting.

JustDebugserver script only sets up the debugserver without launching any apps.

# usage
>.\DebugApp.py {Bundleid of the app you want to attach}

keep in mind you can only use developer certificates to sign those apps.

run the python script from powershell, this will create the debugserver and tell you the address/port then you can use:

>lldb
>
>gdb-remote [ipv6 adress]:port
>
>attach -p pid

to connect and attach to the process.

Or if you use JustDebugserver script 

>lldb
>
>gdb-remote [ipv6 adress]:port
>
>process attach --name {name of the process} --waitfor.
Then when you open the app it will start getting debugged immediately 
