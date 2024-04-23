aws configure list 

aws configure #secret_key وال access_key لو محتاج تعدل ال 

aws eks update-kubeconfig --name eks-cluster-test

kubectl get nodes

kubectl get pods -A

---
kubectl get ns

cat /home/cloudshell-user/.kube/config 

kubectl cluster-info

--- #Cluster AutoScaler

kubectl apply -f https://raw.githubusercontent.com/kubernetes/autoscaler/master/cluster-autoscaler/cloudprovider/aws/examples/cluster-autoscaler-autodiscover.yaml

kubectl get deployment -n kube-system cluster-autoscaler

kubectl edit deployment -n kube-system cluster-autoscaler

kubectl get pod -n kube-system

kubectl get pod POD_NAME -n kube-system -o wide

kubectl logs -n kube-system POD_NAME

---

kubectl get pod 

kubectl get svc

kubectl edit deployment nginx

kubectl get pod 

