# ArgoCD

- kubectl apply -f https://github.com/jetstack/cert-manager/releases/download/v1.12.1/cert-manager.yaml

- cert-manager 설치

- issuer yaml로 생성 후 적용

- certificate yaml로 생성 후 적용

- istio gateway, virtualService, LB 포트 설정

- Istio 연결시 계속 에러 발생, TLS off하고 argocd-server LB svc로 배포해서 접속

- Argo 프로젝트의 CRD 중 Rollout이 Deployment를 대체할 수 있지만 StatefulSet, DaemonSet, ReplicaSet 등 모든 네이티브 리소스들에 대응되는 대체제가 있는 것 같지는 않다.

- ArgoCD의 CRD는 대규모 클러스터에서 배포될 어플리케이션을 그룹화하는 용도가 주인 것 같다.

## Argo Rollouts

- Argo 프로젝트 중 하나로 Canary, Blue-Green과 같은 배포 전략을 적용시켜서 Deployment 리소스같이 어플리케이션을 배포하는 Rollout이라는 CRD를 가지고 있다.

- CRD인 Rollout은 Deployment의 대체제로 볼 수 있다.

- https://argoproj.github.io/argo-rollouts/

- 공식문서에서도 비슷한 표현을 한다. Deployment YAML에서 정의하는 rollingUpdate 부분을 Canary, Blue-Green과 같은 배포 전략으로 갈음하고 동일하게 Replica를 가진다.

- rollout도 별도의 CLI 툴을 가지고 있는데 Canary 배포 중 트래픽을 조금씩 나눠서 배포할 때 그 과정을 모니터링할 수 있다고 한다.

- 실제로 rollout의 정의를 변경하고 새로 배포한 경우 기존 Rollout이 있는 상태에서 새로운 Rollout 리소스가 생성되고 정해진 시간동안 조금씩 트래픽을 전달하면서 새로운 버전이 배포되는 것 같다.

# CI/CD

- Github Action이랑 조합해서 간단한 CI/CD를 한번 해볼까
