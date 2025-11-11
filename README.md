##2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM:
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
@@ -8,6 +8,38 @@
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
CLIENT:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
  while(i<len(l)):
    st+=s
    c.send(str(l[i:st]).encode())
    ack=c.recv(1024).decode()
    if ack:
      print(ack)
      i+=s
```
SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True: 
   print(s.recv(1024).decode())
   s.send("acknowledgement recived from the server".encode())
```
## OUPUT




<img width="1337" height="456" alt="image" src="https://github.com/user-attachments/assets/7a9e3d2c-d976-401f-93f5-0ad119652302" />



## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
