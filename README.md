### helm chart 깃허브 push
git init
git add .
git commit -m "helm01_member 추가함"
git push -u origin master

## 나만의 helm chart를 만들고 github pages 배포해보자
### docs 폴더를 구성한다
```bash

# docs 폴더 준비하기
mkdir -p docs
# chart를 압축해서 docs/ 폴더 안에 저장
helm package charts/helm01_member -d docs/
# index.yaml 파일을 docs/ 폴더에 생성하기
helm repo index docs/ --url https://<나의github아이디>.github.io/저장소이름/
helm repo index docs/ --url https://yimjongwon.github.io/my-helm-chart/


git add ./docs
git commit -m "release: member-app chart v1.0.0 package"
git push
```

### push 후에 github에 pages에 관련된 설정


### 우리가 만든 helm chart 저장소를 사용해보기

```bash
helm repo add my-repo https://yimjongwon.github.io/my-helm-chart/
helm repo ls
helm repo update
helm search repo my-repo

# github pages에서 내려받은 helm chart를 배포하기
# 이미 존재하는 namespace가 있으면 삭제후
kubectl delete ns helm01
# 배포하기
helm install member-release my-repo/member-app -n helm01 --create-namespace
# 확인하기
kubectl get pod,svc -n helm01

# helm01 네임스페이스에 배포된 목록확인
helm ls -n helm01

# 배포취소
helm uninstall member-release -n helm01
kubectl delete ns 


### 버전 v1.0.1
helm package charts/helm01_member -d docs/
helm repo index docs/ --url https://yimjongwon.github.io/my-helm-chart/
git add ./docs
git commit -m "release: member-app chart v1.0.1 package"
git push

# push 후 1~2분 뒤 업데이트
helm repo update
# 저장소에 어떤 chart 있는지 검색
helm search repo my-repo
# version이 올라간걸 확인가능
NAME                    CHART VERSION   APP VERSION     DESCRIPTION               
my-repo/member-app      0.1.1           1.0.1           fastapi member application

```