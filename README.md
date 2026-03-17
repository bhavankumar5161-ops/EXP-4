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
## PROGRAM:
# SERVER:

``` 

import socket
from pythonping import ping

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("Server listening on port 8000...")
c, addr = s.accept()
print(f"Connection from {addr}")

while True:
    try:
        hostname = c.recv(1024).decode('utf-8')
        if not hostname or hostname.lower() == 'exit':
            print("Client disconnected.")
            break
        response = ping(hostname, verbose=False, count=4)
        c.send(str(response).encode('utf-8'))
    except Exception as e:
        c.send(f"Ping failed: {e}".encode('utf-8'))

c.close()

```
## CLIENT:
```

import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    ip = input("Enter the website you want to ping (or type 'exit' to quit): ")
    s.send(ip.encode('utf-8'))
    if ip.lower() == 'exit':
        break
    print(s.recv(4096).decode('utf-8'))

s.close()

``` 

## Output: 

<img width="1112" height="784" alt="Screenshot 2026-03-17 092737" src="https://github.com/user-attachments/assets/ba502bdd-5ad4-4817-adb8-783930a2fcf5" />

<img width="1104" height="844" alt="Screenshot 2026-03-17 092754" src="https://github.com/user-attachments/assets/9e73e4ac-a06a-46b4-a820-8c2f8a365124" />

<img width="991" height="830" alt="Screenshot 2026-03-17 092834" src="https://github.com/user-attachments/assets/fe14b574-f9ae-4ce4-9e2b-eb4754dc5586" />

<img width="968" height="323" alt="Screenshot 2026-03-17 092857" src="https://github.com/user-attachments/assets/6b776d06-55fb-4133-a727-fc7cac5913d4" />





## Result
Thus Execution of Network commands Performed 
