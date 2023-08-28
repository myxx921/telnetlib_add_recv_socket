# telnetlib_external_socket
Just added to the standard python telnetlib module the ability to receive an external socket

I use telnet over SOCKS5 proxy
like this:
```
def create_socket(host_ip, port=22, timeout=60):
    socket = socks.socksocket() 
    socket.set_proxy(socks.SOCKS5, "127.0.0.1")  # SOCKS4 and SOCKS5 use port 1080 by default
    socket.settimeout(timeout)
    socket.connect((host_ip, port))  # socket connect to host use port 22 by default
    print(f'create socket to {host_ip} port {port}')
    return socket
```
and then pass it to telnetlib
```
class Telnet:
    
    def __init__(self, host=None, port=0,
                 timeout=socket._GLOBAL_DEFAULT_TIMEOUT, socket=None):
```
