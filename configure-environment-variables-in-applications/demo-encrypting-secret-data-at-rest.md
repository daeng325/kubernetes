# Demo: Encrypting Secret Data at Rest

{% embed url="https://kubernetes.io/docs/tasks/administer-cluster/encrypt-data/" %}

1. Enable Encryption

```bash
vi /etc/Kubernetes/manifests/kube-apiserver.yaml
```

2. Configuration File 생성
3. generate random key

```bash
head -c 32 /dev/urandom | base64 # generate 32byte random key and base64 encode it
```

4. kube-apiserver yaml에 랜덤 키를 적용한 EncryptionConfiguration 파일 주입
   1. \--encryption-provider-config=/etc/kubernetes/enc/enc.yaml  _<mark style="color:blue;"># add this line #</mark>_<mark style="color:blue;">Containers.command에 추가</mark>
5. secret 파일 생성 후 ETCD에서 암호화되는 것 확인





이미 저장된 모든 secret 암호화 하는 방법

각 Secret에 대해 replace 작업을 수행하면 객체가 변경되지 않은 content at rest가 암호화된다. 클러스터의 모든 Secret에 대해 다음과 같이 변경 가능하다.

```
kubectl get secrets --all-namespaces -o json | kubectl replace -f -
```
