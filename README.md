# 4.Execution_of_NetworkCommands
# NAME : Kavinesh M
# REG NO : 212222230064
## AIM :
Use of Network commands in Real Time environment
## Software :
Command Prompt And Network Protocol Analyzer
## Procedure:To do this EXPERIMENT- follows these steps:
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
### PING COMMAND:

# CLIENT:
```
import socket
from pythonping import ping
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
while True:
    c,addr=s.accept()
    print("Connecting from ",addr)
    try:
        hostname=c.recv(1024).decode().strip()
        if hostname:
            try:
                response=str(ping(hostname,verbose=True))
                c.send(response.encode())
            except Exception as e:
                c.send("ping failed  {}".format(e).encode())
        else:
            c.send("Hostname not provided".encode())
    except Exception as e:
        print("Error: ",e)
    finally:
        c.close()
```
# SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
try:
    while True:
        ip= input("Enter Website u want to ping :")
        s.send(ip.encode())
        response=s.recv(1024).decode()
        if response:
            print ("Ping result :",response)
        else:
            print ("No response from server")
except Exception as e:
    print ("Error:", e)
finally:
    s.close()

```

### TRACEROUTE COMMAND:
```
from scapy.all import* 
target = ["www.google.com"] 
result, unans = traceroute(target,maxttl=32) 
print(result,unans)
```
## Output:

# CLIENT:

![image](https://github.com/kavinesh8476/4.Execution_of_NetworkCommends/assets/118466561/11cc90db-5951-4350-a6a8-cf3a7dcf7963)

# SERVER:

![image](https://github.com/kavinesh8476/4.Execution_of_NetworkCommends/assets/118466561/3d799879-e18f-47b2-9df4-f7e293714d9b)

# TRACEROUTE COMMAND:

![image](https://github.com/kavinesh8476/4.Execution_of_NetworkCommends/assets/118466561/cd918923-9f8a-481c-af5a-2db81c5c0b5d)

## Result:
Thus Execution of Network commands Performed 
