# OpenCSP 문서

**[ [English](README.md) | [한국어](./README.ko.md) ]**

이 저장소는 OpenCSP의 기술 명세 및 아키텍처 가이드를 담고 있습니다.

## OpenCSP란?

OpenCSP(Cloud Service Platform)는 다양한 오픈소스 도구를 활용하여 유휴 컴퓨팅 자원(PC, 서버 등)을 풀링하고, 외부 클라이언트에게 제공할 수 있는 오픈소스 프로젝트입니다.

리소스 프로비저닝은 멱등성과 자동화를 위해 Terraform과 Ansible로 구동되며, SSoT(단일 진실 공급원), 감사 & TAM(Teleport), 빌링(Lago)과 같은 클라우드 핵심 기능들은 오픈소스 솔루션으로 구현됩니다.

현재는 특정 도구 세트로 개발 중이며, 향후 더 광범위한 오픈소스 도구와의 호환성을 위해 아키텍처를 추상화할 계획입니다.

## 주요 기능

- **선언적 인프라**: Terraform(OpenTofu) CR을 통한 Proxmox 리소스 관리
- **GitOps 네이티브**: Flux CD와 Tofu-controller를 활용한 자동 조정(reconciliation)
- **보안 중심 설계**: ZITADEL과의 통합 IAM 및 Ansible을 통한 자동 보안 강화
- **완전한 옵저버빌리티**: 모든 인스턴스에 자동 배포되는 OTel 컬렉터

## 기술 스택

- **컨트롤 플레인**: K3s (경량 Kubernetes)
- **IAM**: ZITADEL (OIDC)
- **프로비저닝**: OpenTofu (Tofu-controller 경유)
- **사후 설정**: Ansible Semaphore
- **프론트엔드**: Next.js & Next-auth

## 문서

- [시스템 아키텍처](./docs/ko/02-architecture/index.md)
- [운영 플로우](./docs/ko/03-flows/user-journey.md)
- [시작하기](./docs/ko/01-getting-started/installation-guide.md)

## 라이선스

OpenCSP는 커뮤니티 성장과 프로젝트 보호의 균형을 위해 멀티 라이선스 모델을 따릅니다:

- **코어 플랫폼 (콘솔, Ops, 문서)**: [GNU Affero General Public License v3 (AGPL-3.0)](./LICENSE) 하에 배포됩니다. 표준 GPL과 달리 AGPL은 네트워크를 통해 소프트웨어와 상호작용하는 모든 사용자에게 수정된 소스 코드를 공개할 것을 요구합니다.
- **인프라 모듈**: 광범위한 도입과 벤더 통합을 장려하기 위해 [Apache License 2.0](https://github.com/h001-lab/OpenCSP-modules?tab=Apache-2.0-1-ov-file) 하에 배포됩니다.
