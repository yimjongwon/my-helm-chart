```bash
# 에러발생시 업그레이드
helm upgrade micro-release ./helm02_micro -n he
lm02
# ns 확인
helm ls -n helm02
# pod,svc 확인
k get pod,svc -n helm02

helm install micro-release ./helm02_micro -n helm02 --create-namespace 

# my-helm-chart에서 실행
[user1@master my-helm-chart]$ 
# chart를 압축해서 docs/ 폴더 안에 저장
helm package charts/helm02_micro -d docs/
# index.yaml 파일을 업데이트
helm repo index docs/ --url https://<나의github아이디>.github.io/저장소이름/
helm repo index docs/ --url https://yimjongwon.github.io/my-helm-chart/


# 깃허브에 push한다.
git add .
git commit
git push

```