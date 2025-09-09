# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
Name: S Rajath
Reg no: 212224240127
## AIM
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program


```
NAME: S Rajath
REG NO: 212224240127

```

## PROGRAM

CLIENT:


```python
import socket
s = socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c, addr = s.accept()
size = int(input("Enter number of frames to send : "))
l = list(range(size))
s = int(input("Enter Window Size : "))
st = 0
i = 0
while True:
    while (i < len(l)):
        st += s
        c.send(str(l[i:st]).encode())
        ack = c.recv(1024).decode()
        if ack:
            print(ack)
            i += s
```

SERVER:

```python
import socket
s = socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement received from the server".encode())
```


## OUPUT

<img width="513" height="314" alt="Screenshot 2025-09-03 115737" src="https://github.com/user-attachments/assets/6031cff4-f81b-4b9b-b561-4ae4fb842925" />

<img width="910" height="257" alt="Screenshot 2025-09-03 115802" src="https://github.com/user-attachments/assets/3b235dbd-b9a8-41f1-80b2-829230687d2c" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed


