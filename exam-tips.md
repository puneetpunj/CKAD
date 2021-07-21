# Tips

## Autocompletion

- `source <(kubectl completion bash)`
- `echo "source <(kubectl completion bash)" >> ~/.bashrc`

## vim setup

```sh
vim ~/.vimrc
set nu
set expandtab
set shiftwidth=2
set tabstop=2
```

## Set Alias

```sh
alias k=kubectl
alias kccc=kubectl config current-context
alias kcuc=kubectl config use-context
alias kcgc=kubectl config get-context
```

- `complete -F __start_kubectl k`

## Set Namespace

` k config set-context --current --namespace=abc

## Useful Commands

- kubectl run nginx --image=nginx (deployment)
- kubectl run nginx --image=nginx --restart=Never (pod)
- kubectl run nginx --image=nginx --restart=OnFailure (job)
- kubectl run nginx --image=nginx --restart=OnFailure --schedule="\* \* \* \* \*" (cronJob)

- kubectl run nginx -image=nginx --restart=Never --port=80 --namespace=myname --command --serviceaccount=mysa1 --env=HOSTNAME=local --labels=bu=finance,env=dev --requests='cpu=100m,memory=256Mi' --limits='cpu=200m,memory=512Mi' --dry-run -o yaml - /bin/sh -c 'echo hello world'

- kubectl run frontend --replicas=2 --labels=run=load-balancer-example --image=busybox --port=8080
- kubectl expose deployment frontend --type=NodePort --name=frontend-service --port=6262 --target-port=8080
- kubectl set serviceaccount deployment frontend myuser
  = kubectl create service clusterip my-cs --tcp=5678:8080 --dry-run -o yaml
