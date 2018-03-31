
ENV:
1. modify configuration.xml to config the servers

RUN:
1. run mserver.jar on MServer
   java -jar mserver.jar
   
2. run server.jar on Servers. You can run a subset of servers from 0 to n;
   java -jar server.jar

3. Run client.jar on clients. You can run as many as you want.
   java -jar client.jar

4. Enter any commands, 0~8;
   
VERTIFY the correstness of the distributed system
1. if no server is running, prompt that "NO SERVERS AVAILABLE";
2. if the operated server is not running, prompt that "Server is not available.";
3. otherwise, the commands work well.
   newCreateFile: means create a new file. You can create one with initial value;
   read: read given length from give offset from a given file.
   append: append at the last chunk of the given file.
4. The number of servers can be from 1 to n.
5. The number of servers can be from 1 to n.
6. the metadata is stored in the metadata.csv. Flush every 5s and when mserver exits.

