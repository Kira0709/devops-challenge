# Task

Provide steps to troubleshoot two production issues.

### Scenario

You are working as a DevOps Engineer on a cloud-based infrastructure where a virtual machine (VM), running Ubuntu 24.04, with 64GB of storage is under your management. Recently, your monitoring tools have reported that the VM is consistently running at 99% memory usage. This VM is responsible for only running one service - a NGINX load balancer as a traffic router for upstream services.

### Challenge

Describe how you would troubleshoot the issue, and what causes/scenario do you expect to encounter, as well as what are the impacts and recovery steps for each possible root cause.

Solution:
First of all i will use tool monitor (if i had) or use command like top/htop to see what process consuming a lot of memory.If the process causing the VM to use 99% Memory comes from nginx, and nginx is only used for routing traffic to upstream services, the usual reason is that too many processes are keeping connections open. The fix would be to set timeouts for those requests, for example:
proxy_connect_timeout 60;
proxy_send_timeout 60;
proxy_read_timeout 60;
send_timeout 60;

And if the process consuming a lot of memory isn't nginx, we can inspect what process is running and continue debugging further.

