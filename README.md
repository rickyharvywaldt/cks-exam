# CKS Exam Tips
The tips below are based on the <ins>kind of questions</ins> I had on my CKS Exam.  

## Cluster Setup (15%)

### Network Policies

### CIS benchmark
A very useful tip I can give here is to run the command: 
<br>```kube-bench run --check 1.2.20```<br> 
Replace 1.2.20 with the check number that's provided in the question. Then follow the instructions under remediations. After you've made the change, run the same command again, and check if the status has changed from FAIL to PASS. Note: some checks may already have a pass by default. In that case you can just skip to the next check. 

### Ingress with TLS
You may need to refer to this documentation during the exam: https://kubernetes.github.io/ingress-nginx/user-guide/tls/

After you have created the TLS secret, add the following in the nginx-controller deployment:
<br>```--default-ssl-certificate=namespace/tls-secret-name```<br>
Replace namespace with the namespace the secret is in and tls-secret-name with the name of the TLS secret. 

## Monitoring, Logging and Runtime Security (20%)

### Falco
If Falco is not installed as a service, then you could run the command:
<br>```falco -U | grep httpd```<br>
Alternatively, you can run the command:
<br>```cat /var/log/syslog | grep httpd```<br>
Copy the container ID and run:
<br>```crictl inspect <container ID> | grep pod.name```<br>

## Minimize Microservice Vulnerabilities (20%)

### Cilium
Create a layer 4 network policy. Allow ingress from another namespace.
