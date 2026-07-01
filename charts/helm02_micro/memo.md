```bash
# 에러발생시 업그레이드
helm upgrade micro-release ./helm02_micro -n he
lm02
# ns 확인
helm ls -n helm02
# pod,svc 확인
k get pod,svc -n helm02

helm install micro-release ./helm02_micro -n helm02 --create-namespace 


```