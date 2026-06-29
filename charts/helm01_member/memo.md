```bash
helm install member-release ./helm01_member -n helm01 --create-namespace
helm ls
helm ls -n helm01
helm uninstall member-release -n helm01

```