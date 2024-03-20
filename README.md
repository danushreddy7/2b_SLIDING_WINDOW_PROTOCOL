# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
CLIENT:
```
#CLIENT:
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
#SERVER:
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())
```
## OUPUT
![Screenshot 2024-03-20 113014](https://github.com/danushreddy7/2b_SLIDING_WINDOW_PROTOCOL/assets/149035740/406eeb9c-de9b-4a60-b5b2-d820a387b98a)
![Screenshot 2024-03-20 113025](https://github.com/danushreddy7/2b_SLIDING_WINDOW_PROTOCOL/assets/149035740/67a050d7-82ac-4cd1-aa04-008acc75a344)
## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
