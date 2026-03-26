# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## Software : Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>
## Program
~~~
SERVER.PY:
import socket
import subprocess
import platform
server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
host = "127.0.0.1"
port = 6000
server.bind((host, port))
server.listen(1)
print("Server started... Waiting for connection...")
conn, addr = server.accept()
print("Connected to:", addr)
while True:
    command = conn.recv(1024).decode()
    if command.lower() == "exit":
        print("Client disconnected.")
        break
    print("Command received:", command)
    try:
        output = subprocess.check_output(command, shell=True)
        conn.send(output)
    except Exception as e:
        conn.send(str(e).encode())
conn.close()
server.close()
~~~
```
CLIENT.PY:
import socket
client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
host = "127.0.0.1"
port = 6000
client.connect((host, port))
print("Connected to Server")
print("You can use commands like: ping google.com, ipconfig, netstat, nslookup google.com")
print("Type 'exit' to quit")
while True:
    command = input("\nEnter Network Command: ")
    client.send(command.encode())
    if command.lower() == "exit":
        break
    output = client.recv(4096).decode()
    print("\n--- Command Output ---")
    print(output)
client.close()
```
## Output

<img width="982" height="202" alt="image" src="https://github.com/user-attachments/assets/4b4df051-466b-49bc-a863-79faad8d6445" />


<img width="1097" height="437" alt="image" src="https://github.com/user-attachments/assets/d3c84edd-a3ae-4448-b6f4-c41301031daa" />

## Result
Thus Execution of Network commands Performed 
