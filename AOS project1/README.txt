
ENV:
1. Create three folders: server1, server2, and server3 in the share directory;
   Put DreamX.jar in each folders
2. Create one folder:clients in the share directory;
   Put BinX.jar in clients

RUN:
1. run DreamX.jar on three servers, like dc01, dc02, dc03
   cd server1
   java -jar DreamX.jar
   
   cd server2
   java -jar DreamX.jar

   cd server3
   java -jar DreamX.jar
   
2. Configure 'servers' in configuration.xml
   You can get the servers' address from the console/terminal after run DreamX.jar

3. Run BinX.jar on five clients, like dc11, dc12, dc13, dc14, dc15
   java -jar BinX.jar
   get the clients addresses from the console/terminal
4. Configure 'clients' in configuration.xml

5. Run BinX.jar on five clients again

6. Enter any commands, like ENQUIRY/READ/WRITE/TEST/RET
   
7. Random test
   "TEST" will triger a test,  periodically and randomly read/write a file
   You can enter a number after "TEST", like "TEST 50", to modify the number of R/W.

    periodically: 
        The interval between two operations is between 30 and 2000(2s), which is randomly generated.
        Every clients will operate 5 times.(the number of R/W is 5.)
    randomly:
        The operation may be eighter READ or WRITE
        The file will be one of files in the filelist.

    You are able to configure the parameters in com.ghw.utils.Utils.java
   

VERTIFY the correstness of the distributed system
1. from print, there is no cmds left unexecuted;

For example, the below log is right:
[FileServer] ===========print all request===========
[FileServer] client 0
[FileServer] --file1.txt
[FileServer] --file3.txt
[FileServer] --file2.txt
[FileServer] client 1
[FileServer] --file1.txt
[FileServer] client 2
[FileServer] --file1.txt
[FileServer] --file3.txt
[FileServer] --file2.txt
[FileServer] client 3
[FileServer] --file1.txt
[FileServer] client 4
[FileServer] --file1.txt
[FileServer] --file3.txt
[FileServer] ======================================
The following log is wrong: one command left unexecuted
[FileServer] ===========print all request===========
[FileServer] client 0
[FileServer] --file1.txt
[FileServer] --file3.txt
[FileServer] --file2.txt
[FileServer]     42:0:W:file2.txt
[FileServer] client 1
[FileServer] --file1.txt
[FileServer] client 2
[FileServer] --file1.txt
[FileServer] --file3.txt
[FileServer] --file2.txt
[FileServer] client 3
[FileServer] --file1.txt
[FileServer] client 4
[FileServer] --file1.txt
[FileServer] --file3.txt
[FileServer] ======================================

2. Enter 'RET', you will get the number of R/W successfully executed, which should correspond with the "TEST #".

3. All files on every Server should be same;

4. The order in every file should be totally ordering according to Lamport's algorith.






