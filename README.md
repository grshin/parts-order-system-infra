# Parts Order System - Infra

이 저장소는 **Parts Order System** 마이크로서비스 프로젝트의 인프라 구성을 제공합니다.  
각 서비스는 Git submodule로 관리되며, 본 저장소는 이를 통합하는 루트 저장소입니다.

## 🧱 디렉토리 구조

```
/projects-root/
├── pos-api-gateway/         ← API Gateway (submodule)
├── pos-order-service/       ← 주문 서비스 (submodule)
├── pos-inventory-service/   ← 재고 서비스 (submodule)
├── pos-config-server/       ← Spring Cloud Config Server (옵션)
├── docker-compose.yml       ← MSA 시스템 통합 실행 구성
└── README.md
```

모든 서비스 디렉토리는 Git submodule로 관리됩니다.

## 📦 필요 사항

- Docker & Docker Compose
- Java 17 이상
- Gradle 8 이상
- Git 2.40 이상
- 다음 GitHub 저장소에 접근 권한 필요:
  - `grshin/pos-api-gateway`
  - `grshin/pos-order-service`
  - `grshin/pos-inventory-service`
  - 등등

## 🔁 서브모듈 포함하여 클론하기

```bash
git clone --recurse-submodules https://github.com/grshin/parts-order-system-infra.git
```

이미 클론한 경우:

```bash
git submodule update --init --recursive
```

## 🚀 Docker Compose로 전체 서비스 실행

```bash
docker-compose up --build -d
```

접속 주소:

- API Gateway: http://localhost:8080
- 주문 서비스: http://localhost:8081
- 재고 서비스: http://localhost:8082

## 🛠 서브모듈 명령어

서브모듈 추가:

```bash
git submodule add https://github.com/grshin/pos-order-service.git
```

서브모듈 업데이트:

```bash
git submodule update --remote --merge
```

서브모듈 제거:

```bash
git submodule deinit -f pos-order-service
rm -rf .git/modules/pos-order-service
git rm -f pos-order-service
```

## 📌 Git 관리 팁

- 커밋은 각 모듈별 로컬 저장소에서 관리하세요.
- `parts-order-system-infra`는 전체 인프라 관리 전용입니다.
- `.gitmodules`, `docker-compose.yml` 변경 시 커밋 필요

## 📄 라이선스

MIT 라이선스 (또는 조직 표준 라이선스)
