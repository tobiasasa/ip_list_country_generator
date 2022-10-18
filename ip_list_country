import requests
import json
import socket, struct
 
data = requests.get(url="https://cdn-lite.ip2location.com/datasets/US.json")
#US.json por que es para US, cambiar diminutivo del nombre para cambiar el pais.
 
def ips(start, end):
    start = struct.unpack('>I', socket.inet_aton(start))[0]
    end = struct.unpack('>I', socket.inet_aton(end))[0]
    return [socket.inet_ntoa(struct.pack('>I', i)) for i in range(start, end)]
 
datadict = json.loads(data.text)
print(datadict["data"][0])
 
for ipdata in datadict["data"]:
    print(f"[*]processing: {ipdata[0]} - {ipdata[1]}, total of {ipdata[2]} ip's")
    with open("ip_list.txt", "a") as f:
        for ip in ips(ipdata[0], ipdata[1]):
            f.write(f"{ip}\n")
 
print("[*]operation finnished :D")
