ローカルにあるdocker imageを出力し、　VMのkubernetesにデプロイする
```
docker build --platform amd64 -t python_web_amd:minikube --target python_web .
```
```
docker save python_web_amd:minikube > python_web_amd.tar 
```
workerへ移動
```
sudo ctr -n k8s.io images import --all-platforms python_web_amd.tar
```
```
sudo crictl image import --all-platforms python_web_amd.tar
```
