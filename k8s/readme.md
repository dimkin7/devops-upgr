Как получить доступ к apache
1. узнать адрес ноды
kubectl get nodes -o wide
172.18.0.2
2. Перейти по http://172.18.0.2:30010/

---

Примеры:

    kubectl get services -n Имя_неймспейса - выводит все сервисы в пространстве имён

    kubectl get pods --all-namespaces - выводит все поды во всех пространств имён

    kubectl get pods -o wide - выводит все поды в текущем пространстве имён с подробностями в виде расширенной таблицы

    kubectl get pods -n Имя_неймспейса - выводит все поды в пространстве имён

Kubectl apply -f [имя манифеста yaml] - команда apply применяет манифест к кластеру, управляет созданием объектов в кластере с помощью манифестов yaml. Если в манифесте не указано пространство имен, его можно задать с помощью ключа -n [Имя_пространства_имен].

Примеры:

    kubectl apply -f ./my-manifest.yaml - создать ресурсы

    kubectl apply -f ./my1.yaml -f ./my2.yaml - создать ресурсы из нескольких файлов

    kubectl apply -f ./dir - создать ресурсы из всех файлов манифеста в директории

    kubectl apply -f https://K8S.io/manifest - создать ресурсы из URL-адреса

---
24  [ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.21.0/kind-linux-amd64
25  chmod +x ./kind
26  sudo mv ./kind /usr/local/bin/kind
27  curl -LO https://dl.k8s.io/release/`curl -LS https://dl.k8s.io/release/stable.txt`/bin/linux/amd64/kubectl
28  chmod +x ./kubectl
29  sudo mv ./kubectl /usr/local/bin/kubectl

30  kubectl version --client
31  kind create cluster --name k8s-test-1 
32  kind get clusters
33  kubectl cluster-info --context kind-k8s-test-1
34  kubectl get namespace
35  kubectl apply -f test-namespace.yaml
36  kubectl get namespace
37  kubectl apply -f hello.yaml
38  kubectl get pods
39  docker ps
40  kubectl port-forward nginx-hello-6cd6ccff9f-6pz9v 30080:80 -n test
41  kubectl port-forward nginx-hello-6cd6ccff9f-9bhf6 30080:80