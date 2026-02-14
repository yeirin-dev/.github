<div align="center">
  <img src="./assets/yeirin-yello-logo.png" alt="Yeirin Logo" width="400"/>
  <h1>예이린 사회적협동조합</h1>
  <p><b>기술로 돌봄을 새롭게, 아이들의 내일을 따뜻하게</b></p>
  <p>대한민국을 넘어 글로벌 돌봄 혁신을 선도하는 Tech Non-Profit</p>

  <br/>

  <a href="https://yeirin.com">
    <img src="https://img.shields.io/badge/Website-yeirin.com-FFCA28?style=for-the-badge&logo=google-chrome&logoColor=white"/>
  </a>
  <a href="mailto:yeirin.dev@gmail.com">
    <img src="https://img.shields.io/badge/Contact-yeirin.dev@gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white"/>
  </a>
</div>

<br/>

## About

**예이린**은 아동·청소년 돌봄 분야의 사회 문제를 기술로 해결하는 **사회적협동조합**입니다.
AI 기반 상담 매칭, 심리상담 챗봇, B2B SaaS 플랫폼 등을 직접 설계·개발하며, 돌봄이 필요한 모든 아이에게 적절한 지원이 닿을 수 있도록 기술 인프라를 구축하고 있습니다.

<br/>

## Architecture

```mermaid
graph TB
    subgraph Clients["Clients"]
        Landing["yeirin-landing<br/><i>공식 웹사이트</i>"]
        Guardian["yeirin-guardian<br/><i>보호자 앱</i>"]
        Admin["yeirin-admin<br/><i>관리자 대시보드</i>"]
        SoulEFE["soul-e-frontend<br/><i>AI 챗봇 UI</i>"]
        MFConsole["myfriend-console<br/><i>테넌트 대시보드</i>"]
        MFLanding["myfriend-landing<br/><i>SaaS 소개</i>"]
    end

    subgraph Shared["Shared"]
        DS["yeirin-design-system<br/><i>공용 UI 컴포넌트</i>"]
    end

    subgraph Services["Backend Services"]
        YBackend["yeirin-backend<br/><i>매칭 플랫폼 API</i><br/>NestJS · TypeScript"]
        YAI["yeirin-ai<br/><i>상담기관 추천 AI</i><br/>Python · RAG"]
        SoulEBE["soul-e-backend<br/><i>심리상담 챗봇 API</i><br/>Python"]
        MFBackend["myfriend-backend<br/><i>멀티테넌트 SaaS API</i><br/>Python"]
    end

    subgraph Infra["Infrastructure · yeirin-infra"]
        AWS["AWS (EC2 · S3 · RDS)"]
        Docker["Docker Compose"]
        CICD["GitHub Actions CI/CD"]
        Terraform["Terraform IaC"]
    end

    DS -.->|컴포넌트 제공| Landing & Guardian & Admin & SoulEFE & MFConsole & MFLanding

    Guardian & Admin & Landing --> YBackend
    YBackend <-->|추천 요청| YAI
    SoulEFE --> SoulEBE
    MFConsole & MFLanding --> MFBackend
    MFBackend <-->|AI 엔진 공유| SoulEBE

    YBackend & YAI & SoulEBE & MFBackend --> AWS
    Terraform -->|프로비저닝| AWS
    Docker -->|컨테이너 배포| AWS
    CICD -->|자동 배포| Docker

    style Clients fill:#E3F2FD,stroke:#1565C0
    style Services fill:#FFF3E0,stroke:#E65100
    style Infra fill:#E8F5E9,stroke:#2E7D32
    style Shared fill:#F3E5F5,stroke:#6A1B9A
```

<br/>

## Projects

### Yeirin Platform &mdash; 상담기관 매칭 플랫폼

아동·청소년과 보호자가 적합한 상담 기관을 찾고 연결될 수 있도록 돕는 AI 기반 매칭 플랫폼입니다.

| Repository | Description | Stack |
|:--|:--|:--|
| [yeirin-backend](https://github.com/yeirin-dev/yeirin-backend) | 매칭 플랫폼 API 서버 (DDD + TDD) | NestJS · TypeScript |
| [yeirin-ai](https://github.com/yeirin-dev/yeirin-ai) | RAG 기반 상담기관 추천 AI 서비스 | Python · RAG |
| [yeirin-landing](https://github.com/yeirin-dev/yeirin-landing) | 공식 랜딩 페이지 | Next.js · TypeScript |
| yeirin-admin | 관리자 대시보드 | Next.js 16 · TypeScript |
| yeirin-guardian | 보호자용 클라이언트 | Next.js · TypeScript |

<br/>

### Soul-E &mdash; 아동 심리상담 AI 챗봇

9~15세 아동·청소년을 위한 AI 심리상담 챗봇입니다. 전문 상담 전 초기 탐색과 정서적 지원을 제공합니다.

| Repository | Description | Stack |
|:--|:--|:--|
| [soul-e-frontend](https://github.com/yeirin-dev/soul-e-frontend) | 챗봇 프론트엔드 | Next.js · TypeScript |
| soul-e-backend | AI 상담 챗봇 백엔드 | Python |

<br/>

### MyFriend (내친구) &mdash; AI 챗봇 B2B SaaS

기관·기업이 자체 AI 상담 챗봇을 손쉽게 구축할 수 있는 멀티테넌트 B2B SaaS 플랫폼입니다.

| Repository | Description | Stack |
|:--|:--|:--|
| myfriend-backend | 멀티테넌트 SaaS API 서버 | Python |
| myfriend-console | 테넌트 관리 대시보드 | Next.js 16 · React 19 |
| myfriend-landing | 서비스 소개 랜딩 페이지 | Next.js 16 · React 19 |

<br/>

### Shared Infrastructure

| Repository | Description | Stack |
|:--|:--|:--|
| [yeirin-infra](https://github.com/yeirin-dev/yeirin-infra) | AWS 인프라 IaC 및 CI/CD 파이프라인 | Terraform · Docker · GitHub Actions |
| [yeirin-design-system](https://github.com/yeirin-dev/yeirin-design-system) | 공용 UI 컴포넌트 라이브러리 | React · TypeScript |

<br/>

## Tech Stack

<table>
  <tr>
    <td><b>Frontend</b></td>
    <td>
      <img src="https://img.shields.io/badge/Next.js-000000?style=flat&logo=next.js&logoColor=white"/>
      <img src="https://img.shields.io/badge/React-61DAFB?style=flat&logo=react&logoColor=black"/>
      <img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white"/>
      <img src="https://img.shields.io/badge/TailwindCSS-06B6D4?style=flat&logo=tailwindcss&logoColor=white"/>
    </td>
  </tr>
  <tr>
    <td><b>Backend</b></td>
    <td>
      <img src="https://img.shields.io/badge/NestJS-E0234E?style=flat&logo=nestjs&logoColor=white"/>
      <img src="https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white"/>
      <img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white"/>
    </td>
  </tr>
  <tr>
    <td><b>AI / ML</b></td>
    <td>
      <img src="https://img.shields.io/badge/LangChain-1C3C3C?style=flat&logo=langchain&logoColor=white"/>
      <img src="https://img.shields.io/badge/RAG-412991?style=flat&logo=openai&logoColor=white"/>
    </td>
  </tr>
  <tr>
    <td><b>Database</b></td>
    <td>
      <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white"/>
      <img src="https://img.shields.io/badge/MongoDB-47A248?style=flat&logo=mongodb&logoColor=white"/>
      <img src="https://img.shields.io/badge/Redis-DC382D?style=flat&logo=redis&logoColor=white"/>
    </td>
  </tr>
  <tr>
    <td><b>Infra / DevOps</b></td>
    <td>
      <img src="https://img.shields.io/badge/AWS-232F3E?style=flat&logo=amazon-web-services&logoColor=white"/>
      <img src="https://img.shields.io/badge/Terraform-844FBA?style=flat&logo=terraform&logoColor=white"/>
      <img src="https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white"/>
      <img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat&logo=github-actions&logoColor=white"/>
      <img src="https://img.shields.io/badge/Vercel-000000?style=flat&logo=vercel&logoColor=white"/>
    </td>
  </tr>
</table>

<br/>

## Team

| Name | Role | GitHub |
|:--:|:--:|:--:|
| 윤상현 | CTO · Backend / DevOps | [@sxngt](https://github.com/sxngt) |
| 김훈정 | Frontend Engineer | [@hxont](https://github.com/hxont) |

<br/>

<div align="center">
  <sub>Since 2025.11 · 예이린 사회적협동조합 기술팀</sub>
</div>
