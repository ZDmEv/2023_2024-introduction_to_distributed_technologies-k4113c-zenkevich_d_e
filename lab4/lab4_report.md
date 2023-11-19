University: [ITMO University](https://itmo.ru/ru/) \
Faculty: [FICT](https://fict.itmo.ru) \
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies) \
Year: 2023/2024 \
Group: K4113с \
Author: Zenkevich Dmitrii Evgenyevich \
Lab: Lab4 \
Date of create: <none> \
Date of finished: <none>

```bash
minikube start --network-plugin=cni --cni=calico --nodes 2 --driver=docker --no-vtx-check
minikube kubectl -- get pods -l k8s-app=calco-node -A
kubectl exec -i -n kube-system calicoctl -- /calicoctl get ippool --allow-version-mismatch
kubectl exec -i -n kube-system calicoctl -- /calicoctl delete ippools default-ipv4-ippool --allow-version-mismatch
kubectl label nodes minikube name=spb
kubectl label nodes minikube-m02 name=msk
kubectl exec -i -n kube-system calicoctl -- /calicoctl apply -f - < calico.yaml --allow-version-mismatch

```