## Liveprobes
```
kubectl apply -f 1-project-23-api.yaml
kubectl run tmp --restart=Never --rm -i --image=nginx:alpine -- curl -m 5  172.17.0.7
# or 
kubectl run mycurlpod --image=curlimages/curl -i --tty -- sh
# we could also wget
kubectl run tmp --restart=Never --rm --image=busybox -i -- wget -O- 172.17.0.7
```

## 
```
use kubectl >= 1.18
alias k=kubectl
k run -h # show help
k run pod1 --image=bash -- bash -c "hostname >> /tmp/hostname && sleep 1d"
k get pod pod1 -o yaml > pod1.yaml
k get pod pod1 -o yaml --export > pod1.yaml # DEPRECATED do not use!
k replace -f pod1.yaml --force
k get pod -l my-label
  NAME   READY   STATUS      RESTARTS   AGE
  pod1   0/1     Completed   0          39s
k exec -it pod1 cat /tmp/hostname
k delete pod pod1 --force --grace-period 0
can also change label manually in command line
k label -h # show help
k label pod pod1 new-label=awesome
kubectl get pods --show-labels
```

## deployment and service
```
Todays Task: Namespaces, Deployments and Services
Create a new namespace k8s-challenge-2-a and assure all following operations (unless different namespace is mentioned) are done in this namespace.
Create a deployment named nginx-deployment of three pods running image nginx with a memory limit of 64MB.
Expose this deployment under the name nginx-service inside our cluster on port 4444, so point the service port 4444 to pod ports 80.
Spin up a temporary pod named pod1 of image cosmintitei/bash-curl, ssh into it and request the default nginx page on port 4444 of our nginx-service using curl.
Spin up a temporary pod named pod2 of image cosmintitei/bash-curl in namespace k8s-challenge-2-b, ssh into it and request the default nginx page on port 4444 of our nginx-service in namespace k8s-challenge-2-a using curl.

k create ns k8n-challenge-2-a
k config current-context # show current context
  docker-for-desktop
# now set default namespace for context
k config set-context docker-for-desktop --namespace=k8n-challenge-2-a
# or simply use the --current flag, thanks to Anton!
k config set-context --current --namespace=k8n-challenge-2-a

k create deploy nginx-deployment --image=nginx -o yaml --replicas 3 --dry-run=client > nginx-deployment.yaml

update resources with limits in yaml file

k create -f nginx-deployment.yaml

expose service
k expose deployment nginx-deployment --name=nginx-service --port=4444 --target-port=80

k run -it pod1 --image=cosmintitei/bash-curl --restart=Never --rm
curl http://nginx-service:4444

k create ns k8n-challenge-2-b
k run -it pod2 --image=cosmintitei/bash-curl --restart=Never --namespace=k8n-challenge-2-b --rm
curl http://nginx-service.k8n-challenge-2-a:4444
```