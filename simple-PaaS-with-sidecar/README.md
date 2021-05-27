<img width="521" alt="Screen Shot 2021-05-27 at 22 43 53" src="https://user-images.githubusercontent.com/12546802/119836932-1b7cb500-bf3d-11eb-82ed-4ed273590101.png">

Imagine building a simple patform as service (PaaS) built around the `git` workflow. Once you deploy this PaaS, simply pushing new code to a Git repository results in that caode being deployed to the running servers. Assume that the main container is a Node.js server that implements a web server. The Node.js server is instrumented so that it automatically reloads the server when new files are updated. The sidecar container shares a filesystem with the main application container and runs a simple loop that synchronizes the filesytem with an existing Git repository

```bash
#!/bin/bash
while true; do
  git pull
  sleep 10
done
```
The Node.js application and Git synchronization sidecar are coscheduled and deployed together to implement this simple PaaS. Once deloyed, every time new code is pushsed to a Git repository, the code is automatically updated by the sidecar and reloaded by the server.
