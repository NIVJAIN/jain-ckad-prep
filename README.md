## Nilesh Gule
```
https://www.handsonarchitect.com/2022/01/how-to-prepare-and-clear-ckad.html
▬▬▬▬▬▬ 🔗 Additional Info 🔗 ▬▬▬▬▬▬ 
- 🔗 Linux Foundation CKAD exam information - https://training.linuxfoundation.org/certification/certified-kubernetes-application-developer-ckad/

- 🔗 Kubernetes docs - https://kubernetes.io/docs/home/
- 🔗 Kubernetes.io tasks - https://kubernetes.io/docs/tasks/
- 🔗 kubectl cheatsheet - https://kubernetes.io/docs/reference/...
- 🔗 Kubernetes imperative commands -  https://www.youtube.com/watch?v=QOv26a-yaq8

- 🔗 Linux Foundation CKAD + Kubernetes for developers bundle - https://training.linuxfoundation.org/certification/certified-kubernetes-application-developer-ckad/
- 🔗 Udemy Kubernetes Certified Application Developer (CKAD) with Tests - https://www.udemy.com/course/certified-kubernetes-application-developer/

Github repositories
- 🔗 CKAD Exercises - https://github.com/dgkanatsios/CKAD-exercises
- 🔗 CKAD resources - https://github.com/lucassha/CKAD-resources
- 🔗 Nilesh Gule CKAD exam prep - https://github.com/NileshGule/ckad-exam-prep
- 🔗 Denny Zhang kubectl cheatsheet - https://github.com/dennyzhang/cheatsheet-kubernetes-A4
- 🔗 Ahmet Alp Balkan Kubernetes network policy recipes - https://github.com/ahmetb/kubernetes-network-policy-recipes

Blogs
- 🔗 Be fast with kubectl - https://faun.pub/be-fast-with-kubectl-1-18-ckad-cka-31be00acc443
- 🔗 How to nail Kubernetes certification exams - https://www.infoworld.com/article/3631108/how-to-nail-the-kubernetes-certification-exams.html
- 🔗 Codefresh Kubernetes cheatsheet - https://codefresh.io/blog/kubernetes-cheat-sheet/
- 🔗 CKAD practical challenge series -  https://codeburst.io/kubernetes-ckad-weekly-challenges-overview-and-tips-7282b36a2681
- 🔗 killer.sh CKAD exam simulator - https://killer.sh/ckad
- 🔗 vi cheat sheet - https://www.cs.cmu.edu/~15131/f17/topics/vim/vim-cheatsheet.pdf

```

## CKAD
```
https://kubernetes.io/docs/home/
https://kubernetes.io/docs/tasks/
https://kubernetes.io/docs/reference/kubectl/cheatsheet/    

https://killer.sh/course/preview/052229bd-1062-44a4-8aae-f50d0770165a
https://github.com/dennyzhang/cheatsheet-kubernetes-A4
https://github.com/cncf/curriculum/blob/master/CKAD_Curriculum_v1.27.pdf
```

## setup
```
alias k=kubectl
export do="--dry-run=client -o yaml"
```

## How to switch kubectl clusters between awseks and minikube
```
kubectl config get-contexts
kubectl config use-context <CONTEXT_NAME>
kubectl config use-context sripal_jain@imda.gov.sg@fleetman.ap-southeast-1.eksctl.io
kubectl config use-context minikube
```

## How to change default namespace to <somename>
```
kubectl config set-context --current --namespace=<insert-namespace-name-here>
# Validate it
kubectl config view --minify | grep namespace:
```

## Run a container in a specific namespace
```
kubectl run nginxpodams --image=nginx --namespace=<insert-namespace-name-here>
kubectl get pods --namespace=<insert-namespace-name-here>
```

