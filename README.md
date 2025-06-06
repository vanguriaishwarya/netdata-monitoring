✅ Task: Monitor System Resources Using Netdata.

📝 Objective:Install Netdata using Docker and visualize real-time system and application performance metrics through a web-based dashboard.

🛠️ Tools Used
Netdata (open-source monitoring tool)

Docker

Windows PowerShell

GitHub Container Registry (GHCR) – to pull the image

⚙️ Steps Followed🚀

✅ 1. Pulled the Netdata Image from GHCR:
Due to Docker Hub authorization issues, the official image was pulled from GitHub Container Registry instead:
docker pull ghcr.io/netdata/netdata:latest

✅ 2. Started the Netdata Container:
The following Docker command was used to run Netdata and mount system directories for monitoring:
docker run -d --name=netdata -p 19999:19999 \
  -v netdataconfig:/etc/netdata \
  -v netdatalib:/var/lib/netdata \
  -v netdatacache:/var/cache/netdata \
  -v /etc/passwd:/host/etc/passwd:ro \
  -v /etc/group:/host/etc/group:ro \
  -v /proc:/host/proc:ro \
  -v /sys:/host/sys:ro \
  -v /etc/os-release:/host/etc/os-release:ro \
  --cap-add SYS_PTRACE \
  --security-opt apparmor=unconfined \
  ghcr.io/netdata/netdata:latest
(Note: On Windows PowerShell, the multiline version was converted to a single line for compatibility.)

✅ 3. Verified the Running Container:
docker ps
Output confirms Netdata is up and running on port 19999.

✅ 4. Accessed Netdata Dashboard:
Opened browser and visited:http://localhost:19999
Successfully visualized real-time monitoring metrics including:
CPU usage

RAM and Disk usage

System load

Docker containers

Network activity

🏁 Conclusion
Netdata was successfully installed and configured using Docker. The system resource metrics are now available in real-time through a web interface on localhost:19999.
