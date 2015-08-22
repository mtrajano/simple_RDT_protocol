Reliable Data Transfer Protocol
==============================

Realible data transfer on top of the sodium encryption library. 

Usage
-----
```bash
# compiles all test files and links to the main sock352lib library 
make

# binds server test to given udp-port (use -l and -r if on same machine) and outputs to file to given name once transferred
./server -o <output-file> -u <udp-port> -l <local-port> -r <remote-port>

# sends given filename to specified destination and port, must have server listening on the other side
./client -f <filename> -d <destination> -u <udp-port> -l <local-port> -r <remote-port>

# binds server test to given udp-port (use -l and -r if on same machine)
./server2 -o <output-file> -u <udp-port> -l <local-port> -r <remote-port>

# specify remote file to download and its output name, also specify destination and port
./client2 -f <remote filename>  -o <output file> -d <destination> -u <udp-port> -l <local-port> -r <remote-port>

# use ./server_crypto -p to print a set of keys, write these keys to a file with the format given below
# binds server_crypto to the given port using the given set of keys
./server_crypto -u <udp-port> -l <local-port> -r <remote-port> -k <key_file> -p <print_keypair>

# use server_crypto to generate another set of keys for the client (must be different than server's) 
# specify the file from the server and its output file locally, must also specify the destination, port and the key file that is exchanged with the server
./client_crypto -f <remote filename>  -o <output file> -d <destination> -u <udp-port> -l <local-port> -r <remote-port> -k <key-file>
```
**Keys must be in the following form:**
```
public: <your public key>
secrete: <your secrete key>
remote: <remote's public key>
```

Test Files
----------
0. **client.c/server.c** - client sends server a file in plaintext
0. **client2.c/server.c** - client asks for file and server sends client a file in plaintext
0. **client_crypto.c/server_crypto.c** - client retrieves file from server through a secure connection
