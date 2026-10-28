<!-- Header -->
<div align="center">

![header](https://capsule-render.vercel.app/api?type=waving&color=0:0f2027,50:1f4257,100:2c5364&height=220&section=header&text=Daeseok%20Bae&fontSize=56&fontColor=ffffff&fontAlignY=38&desc=Cloud%20%2F%20DevOps%20Engineer&descAlignY=58&descSize=20&animation=fadeIn)

<a href="https://git.io/typing-svg">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=20&duration=3000&pause=800&color=4FA3D1&center=true&vCenter=true&width=600&lines=High+Availability+Infrastructure+%E2%98%81%EF%B8%8F;Config+out+of+the+image%2C+into+SSM+%F0%9F%94%90;Troubleshoot+%E2%86%92+Measure+%E2%86%92+Document+%F0%9F%93%9D" alt="Typing SVG" />
</a>

<br/>

<a href="https://velog.io/@tkdxm0208/"><img src="https://img.shields.io/badge/Velog-20C997?style=flat-square&logo=velog&logoColor=white"/></a>
<a href="mailto:tkdxm0208@gmail.com"><img src="https://img.shields.io/badge/Gmail-EA4335?style=flat-square&logo=gmail&logoColor=white"/></a>
<a href="https://www.linkedin.com/in/%EB%8C%80%EC%84%9D-%EB%B0%B0-253085369/"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white"/></a>

</div>

<br/>

## 🧑‍💻 About Me

```yaml
name: 배대석 (Daeseok Bae)
role: Cloud / DevOps Engineer (Junior)
focus:
  - 고가용성 클라우드 아키텍처 설계·구축
  - 설정과 이미지를 분리한 재현 가능한 인프라
  - 장애 원인을 지표로 좁히고, 해결 과정을 기록하는 운영
goal: AWS Solutions Architect
```

<br/>

## 🛠️ Tech Stack

<div align="center">

**☁️ Cloud**

<img src="https://skillicons.dev/icons?i=aws,azure,gcp&theme=dark" />

<br/><br/>

**⚙️ Infra & Container**

<img src="https://skillicons.dev/icons?i=linux,docker,kubernetes,terraform&theme=dark" />

<br/><br/>

**🚀 CI/CD**

<img src="https://skillicons.dev/icons?i=githubactions,git,github&theme=dark" />

<br/><br/>

**📊 Observability**

<img src="https://skillicons.dev/icons?i=prometheus,grafana&theme=dark" />

</div>

<br/>

## 🚀 Featured Projects

### 🎯 NextPlan — 취업 준비 플랫폼 AWS 인프라 & CI/CD

`2026.04 – 2026.06` · `대학교 캡스톤디자인 팀 프로젝트` · `Cloud / DevOps 담당`

이력서 업로드 → AI 직무 분석 서비스의 **AWS 인프라 구축과 GitHub Actions 배포 자동화**

```
CloudFront + WAF ─┬─ /*     → S3 (React SPA)
                  └─ /api/* → EC2 (Nginx → Spring Boot) → RDS PostgreSQL
                                  └──→ S3 Private (Presigned URL) · Colab AI
```

- **Architecture** — CloudFront 경로 기반 라우팅으로 정적/API 트래픽 분리, 이력서는 Private S3 + Presigned URL
- **CI/CD** — Front: S3 sync + CloudFront 무효화 / Back: Gradle → SCP → systemd, `nohup` 수동 관리 → **systemd 자동 복구**
- **Troubleshooting** — 운영 환경 업로드 실패를 **CloudFront 라우팅 → WAF 차단 → 경로 중복 → multipart 설정** 4단계로 추적·해결
- **Config** — 시크릿을 GitHub Secrets · systemd 환경변수로 분리, `ddl-auto: validate`로 운영 스키마 보호

<img src="https://img.shields.io/badge/CloudFront-8C4FFF?style=flat-square&logo=amazonwebservices&logoColor=white"/> <img src="https://img.shields.io/badge/AWS_WAF-DD344C?style=flat-square&logo=amazonwebservices&logoColor=white"/> <img src="https://img.shields.io/badge/EC2-FF9900?style=flat-square&logo=amazonec2&logoColor=white"/> <img src="https://img.shields.io/badge/S3-569A31?style=flat-square&logo=amazons3&logoColor=white"/> <img src="https://img.shields.io/badge/RDS_PostgreSQL-527FFF?style=flat-square&logo=amazonrds&logoColor=white"/> <img src="https://img.shields.io/badge/Nginx-009639?style=flat-square&logo=nginx&logoColor=white"/> <img src="https://img.shields.io/badge/systemd-30D475?style=flat-square&logo=linux&logoColor=black"/> <img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white"/>

[📂 Repository](https://github.com/ZZGG2/nextplan-infra) · [🔥 트러블슈팅 기록](https://github.com/ZZGG2/nextplan-infra/tree/main/docs/troubleshooting)

<br/>

---

### ☁️ AWS 3-Tier PetClinic Infrastructure

`2026.09 – 2026.10` · `4인 팀` · `Bespin Global 클라우드 엔지니어 과정 최종 프로젝트`

동물병원 예약 서비스를 가정한 **고가용성 AWS 3-Tier 인프라**

```
Route 53 → ALB(HTTPS) → Apache → Internal NLB → Tomcat → RDS Multi-AZ
                                                   └──→ ElastiCache Redis (Session)
```

- **Architecture** — 2 AZ × 4 Tier, Bastion 대신 SSM Session Manager, NAT 대신 VPC Endpoint
- **Config** — 골든 AMI + SSM Parameter Store로 엔드포인트와 비밀번호를 이미지에서 분리
- **Troubleshooting** — 부하 테스트 중 반복된 ALB 502를 Apache 튜닝으로 해결 → **약 8만 건 요청 중 0~1건**
- **Observability** — Apache·Tomcat·ALB·CloudTrail 로그 → CloudWatch → S3, RTO 3h / RPO 10m

<img src="https://img.shields.io/badge/EC2-FF9900?style=flat-square&logo=amazonec2&logoColor=white"/> <img src="https://img.shields.io/badge/ALB%2FNLB-8C4FFF?style=flat-square&logo=awselasticloadbalancing&logoColor=white"/> <img src="https://img.shields.io/badge/RDS-527FFF?style=flat-square&logo=amazonrds&logoColor=white"/> <img src="https://img.shields.io/badge/ElastiCache-C925D1?style=flat-square&logo=redis&logoColor=white"/> <img src="https://img.shields.io/badge/Route_53-8C4FFF?style=flat-square&logo=amazonroute53&logoColor=white"/> <img src="https://img.shields.io/badge/S3-569A31?style=flat-square&logo=amazons3&logoColor=white"/> <img src="https://img.shields.io/badge/Apache-D22128?style=flat-square&logo=apache&logoColor=white"/> <img src="https://img.shields.io/badge/Tomcat-F8DC75?style=flat-square&logo=apachetomcat&logoColor=black"/> <img src="https://img.shields.io/badge/CloudWatch-FF4F8B?style=flat-square&logo=amazoncloudwatch&logoColor=white"/> <img src="https://img.shields.io/badge/k6-7D64FF?style=flat-square&logo=k6&logoColor=white"/> <img src="https://img.shields.io/badge/Systems_Manager-E7157B?style=flat-square&logo=amazonwebservices&logoColor=white"/>

[📂 Repository](https://github.com/ZZGG2/aws-3tier-petclinic) · [📝 Velog 시리즈](https://velog.io/@tkdxm0208/series/AWS-3-Tier-Architecture)

<br/>

---

### ☸️ PetClinic on Amazon EKS

`2026.10` · `개인 프로젝트` · `Bespin Global 클라우드 엔지니어 과정 Docker & Kubernetes 프로젝트`

Spring PetClinic을 컨테이너화해 단계적으로 확장한 **Amazon EKS 기반 3-Tier 인프라**

```
Route 53 → ALB(HTTPS) → Nginx → Tomcat → MySQL StatefulSet (dev) / RDS (prod)
                                └──→ Secrets Manager → External Secrets (DB 자격 증명)
```

- **Architecture** — 2 AZ, Ingress 대신 Gateway API, 시스템 노드그룹과 Karpenter Spot 노드 분리
- **Config & Security** — Kustomize로 dev/prod 분리(WAS 설정은 수정 없이 DB만 전환), Git 평문 비밀번호를 Secrets Manager로 이전, DB 계정 DML 전용
- **Scaling** — WAS는 HPA(CPU), WEB은 KEDA(ALB 요청 수 + cron), 노드는 Karpenter(Spot · Consolidation)
- **Troubleshooting** — Running인데 404이던 WAS를 구간별로 추적 → **Maven 필터링이 XML의 DB 주소를 빌드 시점 값으로 고정**한 원인을 찾아 빌드 후 복원 + 설정 파일 주입으로 해결

<img src="https://img.shields.io/badge/Amazon_EKS-FF9900?style=flat-square&logo=amazoneks&logoColor=white"/> <img src="https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white"/> <img src="https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white"/> <img src="https://img.shields.io/badge/Helm-0F1689?style=flat-square&logo=helm&logoColor=white"/> <img src="https://img.shields.io/badge/Karpenter-232F3E?style=flat-square&logo=amazonwebservices&logoColor=white"/> <img src="https://img.shields.io/badge/KEDA-3B5BDB?style=flat-square"/> <img src="https://img.shields.io/badge/Nginx-009639?style=flat-square&logo=nginx&logoColor=white"/> <img src="https://img.shields.io/badge/Tomcat-F8DC75?style=flat-square&logo=apachetomcat&logoColor=black"/> <img src="https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white"/> <img src="https://img.shields.io/badge/RDS-527FFF?style=flat-square&logo=amazonrds&logoColor=white"/> <img src="https://img.shields.io/badge/Route_53-8C4FFF?style=flat-square&logo=amazonroute53&logoColor=white"/> <img src="https://img.shields.io/badge/Secrets_Manager-DD344C?style=flat-square&logo=amazonwebservices&logoColor=white"/> <img src="https://img.shields.io/badge/CloudWatch-FF4F8B?style=flat-square&logo=amazoncloudwatch&logoColor=white"/>

[📂 Repository](https://github.com/ZZGG2/petclinic-k8s-project) · [📝 Velog 시리즈](https://velog.io/@tkdxm0208/series/AWS-EKS)

<br/>

## 📊 GitHub Stats

<div align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=ZZGG2&show_icons=true&hide_border=true&bg_color=0d1117&title_color=4FA3D1&icon_color=4FA3D1&text_color=c9d1d9&include_all_commits=true" height="165"/>
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=ZZGG2&layout=compact&hide_border=true&bg_color=0d1117&title_color=4FA3D1&text_color=c9d1d9" height="165"/>
</div>

<!-- Footer -->
![footer](https://capsule-render.vercel.app/api?type=waving&color=0:2c5364,50:1f4257,100:0f2027&height=120&section=footer)
