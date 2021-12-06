# GitLab 사용 가이드

본 가이드에서는 GitLab의 주요 기능 및 특징을 소개하고 GitLab을 이용하여 프로젝트에서 업무를 수행하는 방법을 설명합니다.

## GitLab 소개

GitLab은 Git 원격 저장소(Repository) 관리뿐만 아니라, 이슈 트래킹, 코드 리뷰, Wiki, CI/CD, 테스트, 모니터링 등 전체 소프트웨어 개발 라이프사이클(Software Development Life Cycle, SDLC)에 필요한 기능을 제공합니다.

**GitLab은 단일 애플리케이션으로 제공되는 완전한 DevOps 플랫폼입니다.** 간소화된 소프트웨어 워크플로우를 생성하여 서로 짜맞추어진 툴체인(Toolchain)의 제약에서 벗어나게 합니다.

현대적인 소프트웨어 개발 방법인 클라우드 네이티브(Cloud Native) 환경 구축에 필요한 DevOps, Container, Kubernetes, CI/CD를 위한 기능을 제공합니다.

### 주요 기능

GitLab은 초기에 Git 원격 저장소, 코드 탐색, 이슈 트래커 기능 등을 제공하는 소프트웨어의 형태로 시작되어, 이후 더 많은 기능들을 추가하여 전체 소프트웨어 개발 라이프사이클을 커버하는 플랫폼으로 성장했습니다.

* **그룹 및 프로젝트 관리 :** [그룹](https://docs.gitlab.com/ee/user/group/index.html) 및 [프로젝트](https://docs.gitlab.com/ee/user/project/index.html)를 통해 업무를 계획(Milestone)하고 세부화한 업무(Issue)를 구성원에게 배정하여 팀의 수행 프로젝트를 관리할 수 있습니다. 그룹은 동일한 네임스페이스에서 관련 프로젝트를 구성하고 최상위 그룹에 구성원을 추가하여 여러 프로젝트와 여러 팀 구성원에게 더 적은 단계로 액세스 권한을 부여할 수 있습니다. 프로젝트는 코드베이스 단위로 만듭니다. 이를 이슈 트래커로 사용하고, 코드에 대해 공동 작업하고, 내장된 GitLab CI/CD를 사용하여 앱을 지속적으로 빌드, 테스트 및 배포할 수 있습니다.
* **Repository :** 프로젝트를 생성하면 자동으로 Git 원격 저장소가 생성됩니다. 코드베이스를 저장하고 버전 제어를 통해 코드를 변경하는데 사용되며, 파일을 탐색하고 상호 작용하는 다양한 방법을 Web UI로 제공합니다.
* **이슈 트래커(Tracker) :** 공동으로 아이디어를 개발하고 문제를 해결하며 작업을 계획하기 위한 고급 도구입니다. 새로운 아이디어의 구현 논의, 태스크(Task) 및 작업 상태 추적, 기능 제안, 질문, 지원 요청 또는 버그 보고서의 수락, 새로운 코드 구현에 대해 자세히 설명하는데 활용할 수 있습니다.
* **이슈 보드(Board) :** 기능 또는 제품 릴리즈에 대한 워크플로우를 계획, 구성 및 시각화하는데 사용되는 소프트웨어 프로젝트 관리 도구입니다. 칸반(Kanban) 또는 스크럼(Scrum) 보드로 사용할 수 있습니다. 레이블(Label) 기반으로 이슈 추적과 프로젝트 관리를 결합하여 모든 것을 함께 유지하므로 워크플로우를 구성하기 위해 서로 다른 플랫폼 사이를 이동할 필요가 없습니다. 레이블을 추가하여 기존 이슈에 해당하는 목록을 만들고, 카드를 한 단계에서 다른 단계로 끌어다 놓을 수 있습니다.
* **레이블(Labels) :** 이슈, 병합 요청 및 에픽의 수가 증가함에 따라 이러한 항목을 추적하는 것이 점점 더 어려워집니다. 특히 조직이 소수에서 수백 또는 수천으로 성장함에 따라 더욱더 그렇습니다. 레이블은 작업을 구성하고 태그를 지정하여 관심 있는 작업 항목을 추적하고 찾을 수 있도록 도와줍니다. 버그, 기능 요청 또는 문서와 같은 설명 제목과 색상을 사용하여, 에픽, 이슈 및 병합 요청을 분류하여 동적으로 필터링하고 관리하며 이런 항목들을 검색할 수 있습니다.
* **마일스톤(Milestone) :** 특정 기간 동안 더 광범위한 목표를 달성하기 위해 생성된 이슈 및 병합 요청(Merge Request)을 추적하는 방법입니다. 마일스톤을 이용하면 선택적 시작일과 마감일을 사용하여 이슈와 병합 요청을 응집력 있는 그룹으로 구성할 수 있습니다.
* **병합 요청(Merge request) :** 한 브랜치를 다른 브랜치로 병합하기 위한 요청입니다. 병합 요청을 사용하여 소스 코드에 대해 제안된 변경사항을 시각화하고 협업할 수 있습니다.
* **내장 CI/CD :** 무료로 내장된 CI/CD를 가지고 있으며 별도로 설치할 필요가 없습니다. 이를 사용하여 애플리케이션을 빌드, 테스트 및 배포합니다. 작업 결과는 쉽게 액세스할 수 있도록 병합 요청(Merge request)에 표시됩니다.
* **WiKi :** 문서화를 위한 별도 시스템이 각 GitLab 프로젝트에 내장되어 있습니다. Wiki는 문서를 저장소에 보관하고 싶지 않지만 코드가 있는 동일한 프로젝트에 보관하고 싶은 경우 매우 편리합니다. 모든 Wiki는 별도의 Git 저장소이므로 웹 인터페이스에서 또는 Git Clone하여 로컬에서 작업할 수 있습니다.
* **스니펫(Snippets) :** 자주 사용하는 코드 조각과 텍스트를 저장하고 다른 사용자와 공유할 수 있습니다.
* **Web IDE :** Git CLI(명령 줄 인터페이스)에 익숙하지 않은 사용자도 쉽게 사용할 수 있는 기능으로, 코드를 변경하고 Web 브라우저에서 직접 커밋할 수 있는 커밋 스테이징(Commit Staging)을 제공하여 프로젝트에 변경사항을 빠르고 쉽게 적용할 수 있습니다.

### 전체 DevOps 라이프사이클

GitLab은 [동시(Concurrent) DevOps](https://about.gitlab.com/topics/concurrent-devops/)를 가능하게 하는 소프트웨어 개발, 보안 및 운영을 위한 최초의 단일 애플리케이션으로, 소프트웨어 라이프사이클을 더 빠르게 만들고 비즈니스 속도를 획기적으로 향상시킵니다.

이슈 추적 및 소스 코드 관리에서 CI/CD 및 모니터링에 이르기까지 모든 것을 한 곳에 모아두면 툴체인 복잡성이 단순화되고 사이클 타임(Cycle Time)이 단축됩니다.

![DevOps Lifecycle](images/06/devops-lifecycle.png "DevOps Lifecycle")

GitLab은 [DevOps 라이프사이클의 각 단계](https://about.gitlab.com/stages-devops-lifecycle/)에 대한 솔루션을 제공합니다.

![Stages of the DevOps lifecycle](images/06/gitlab_devops_stages.png "Stages of the DevOps lifecycle")

* **[Manage](https://about.gitlab.com/stages-devops-lifecycle/manage/) :** 비즈니스 성과에 대한 가시성과 인사이트 확보를 위한 통계 및 분석 기능을 제공합니다.
* **[Plan](https://about.gitlab.com/stages-devops-lifecycle/plan/) :** 에픽, 이슈, 보드, 레이블, 마일스톤을 통해 포트폴리오 계획 및 관리를 지원하여 진행 상황을 구성하고 추적합니다.
* **[Create](https://about.gitlab.com/stages-devops-lifecycle/create/) :** 강력한 브랜칭(Branching) 도구를 통해 소스 코드 및 프로젝트 데이터를 만들고, 조회하고, 관리합니다.
* **[Verify](https://about.gitlab.com/stages-devops-lifecycle/verify/) :** 내장된 정적 코드 분석, 코드 테스트, 코드 품질, 종속성 확인 및 리뷰 앱을 통해 오류를 더 빨리 발견하고 보안을 향상시키며 피드백 주기를 단축할 수 있습니다.
* **[Package](https://about.gitlab.com/stages-devops-lifecycle/package/) :** 애플리케이션 및 종속성을 패키징하고 컨테이너를 관리하고, 아티팩트를 쉽게 빌드할 수 있습니다.
* **[Secure](https://about.gitlab.com/stages-devops-lifecycle/secure/) :** 정적 애플리케이션 보안 테스트 (SAST), 동적 애플리케이션 보안 테스트 (DAST), 컨테이너 스캔 및 종속성 스캔을 제공하여 라이선스 준수와 함께 안전한 애플리케이션을 제공할 수 있도록 지원합니다.
* **[Release](https://about.gitlab.com/stages-devops-lifecycle/release/) :** 애플리케이션 출시 및 제공을 자동화하여, 제공 라이프사이클을 단축하며, 수동 프로세스를 간소화하며, 팀 속도를 가속화합니다.
* **[Configure](https://about.gitlab.com/stages-devops-lifecycle/configure/) :**  애플리케이션 환경 및 인프라를 구성하고 관리할 수 있도록 지원합니다.
* **[Monitor](https://about.gitlab.com/stages-devops-lifecycle/monitor/) :** 배포된 애플리케이션에 대한 성능 메트릭을 수집하고 표시하므로 코드 변경이 프로덕션 환경에 미치는 영향을 즉시 알 수 있습니다.
* **[Protect](https://about.gitlab.com/stages-devops-lifecycle/protect/) :** 통합 정책 관리, 컨테이너 스캔, 컨테이너 네트워크 및 호스트 보안을 포함한 클라우드 네이티브 보호를 제공합니다.

### 강력한 클라우드 네이티브 지원

기업은 속도, 안정성 및 확장성을 확보하기 위해 기존 배포 모델에서 클라우드 네이티브 애플리케이션으로 전환하고 있습니다.

GitLab은 클라우드 네이티브 애플리케이션을 구축하는 가장 쉬운 방법입니다.
클라우드 네이티브 애플리케이션은 컨테이너, 마이크로 서비스 아키텍처 및 Kubernetes와 같은 컨테이너 오케스트레이션을 사용합니다. GitLab은 긴밀한 Kubernetes 통합을 통해 클라우드 네이티브 애플리케이션을 위해 설계되었습니다.

* Docker 컨테이너 이미지를 저장, 공유, 사용하기 위한 Container Registry가 내장되어 있습니다.
* GitLab UI를 이용하여 Amazon EKS, Google GKE에 그룹, 프로젝트 또는 인스턴스 수준의 새 클러스터(Cluster)를 생성하거나 기존 클러스터에 연결할 수 있습니다. 또한 온프레미스(On-premise) 또는 호스팅된 모든 표준 Kubernetes 프로바이더와 통합할 수 있습니다.
* GitLab 내에서 직접 앱의 주요 지표를 모니터링하기 위해 Prometheus와의 강력한 통합을 제공합니다. 각 환경에 대한 메트릭은 Prometheus에서 검색된 다음, GitLab 인터페이스에 표시됩니다.

## GitLab 워크플로우 기반으로 프로젝트 수행

GitLab은 단일 애플리케이션으로 제공되는 완전한 오픈소스 DevOps 플랫폼으로 개발, 보안 및 운영 팀이 협업하고 소프트웨어를 구축하는 방식을 근본적으로 변화시킵니다. GitLab은 아이디어에서 프로덕션에 이르기까지 팀이 몇 주에서 몇 분으로 사이클 타임(Cycle time)을 개선하고, 개발 프로세스 비용을 줄이고 출시 시간을 단축하는 동시에 개발자 생산성을 높일 수 있도록 지원합니다.

![GitLab Workflow](images/06/gitlab_flow.svg "GitLab Workflow")

GitLab을 사용하면 워크프로우를 단순화할 수 있습니다.

1. [그룹](https://docs.gitlab.com/ee/user/group/index.html) 및 [프로젝트](https://docs.gitlab.com/ee/user/project/index.html)를 이용하여 조직(팀)을 구성합니다. 사용자 역할을 결정하고 모든 사람에게 필요한 그룹 및 프로젝트에 대한 액세스 권한을 부여합니다.
2. [Milestones](https://docs.gitlab.com/ee/user/project/milestones/index.html)을 생성합니다. 마일스톤으로 업무를 스케줄링하고 팀의 [시간을 추적](https://docs.gitlab.com/ee/user/project/time_tracking.html)합니다.
3. [Labels](https://docs.gitlab.com/ee/user/project/labels.html)을 생성합니다. 레이블로 작업을 구성하고 태그를 지정하여 관심있는 작업 항목을 추적하고 검색합니다.
4. [Epics](https://docs.gitlab.com/ee/user/group/epics/index.html)(PREMIUM) 및 [Issues](https://docs.gitlab.com/ee/user/project/issues/index.html)를 생성하여 업무를 계획합니다.
5. [Issue Boards](https://docs.gitlab.com/ee/user/project/issue_board.html)에서 작업할 이슈를 다음 단계(예 : `To Do` -> `Doing`)로 드래그 합니다. 이슈 보드를 사용하면 기능 또는 제품 릴리즈에 대한 워크플로우를 계획, 구성 및 시각화하여 관리할 수 있습니다.
6. 프로젝트를 생성하면 자동으로 생성되는 기본(`master`) 브랜치로부터 이슈에 해당하는 기능 구현 또는 개선을 위한 Feature 브랜치를 생성합니다.
7. 리포지토리를 복제(clone)하여 로컬에 작업 환경을 구성하고, 코드 작성한 다음, 변경사항을 Feature 브랜치에 푸시합니다.
8. 푸시 하면 프로젝트의 CI 파이프라인이 트리거 되어 애플리케이션을 빌드하고 테스트합니다.
9. 병합 요청(Merge request)을 생성하여 코드를 검토하고 승인합니다.
10. Feature 브랜치를 기본 브랜치에 병합(Merge)합니다.
11. 기본 브랜치에 병합이 완료되면 CD 파이프라인이 트리거 됩니다.
12. CD 파이프라인은 변경사항을 프로덕션 환경에 수동 또는 자동으로 배포합니다.

### 그룹 생성

GitLab에서는 그룹을 사용하여 하나 이상의 관련 프로젝트를 동시에 관리합니다.  
그룹을 사용하여 프로젝트에 대한 권한을 관리할 수 ​​있습니다. 누군가 그룹에 액세스 할 수 있는 경우, 그룹의 모든 프로젝트에 액세스 할 수 있습니다.  
또한 그룹의 프로젝트에 대한 모든 이슈 및 머지 리퀘스트(Merge requests)을 보고 그룹의 활동을 보여주는 분석(Analytics)을 볼 수 있습니다.  
그룹을 사용하여 그룹의 모든 구성원과 한 번에 소통할 수 있습니다.  
대규모 조직의 경우 [하위 그룹](https://docs.gitlab.com/ee/user/group/subgroups/index.html)을 만들 수도 있습니다.

그룹을 생성하려면 :

1. 상단 바에서 다음 중 하나를 수행합니다.
    * **Groups**를 클릭하고 **Your Groups**를 선택한 후, 우측 상단에 있는 **New group**을 선택합니다.
    * 검색 박스 왼쪽에서 플러스 기호(**[+]**)를 선택한 다음, **New group**을 선택합니다.
2. **Create group** 탭을 선택합니다.
3. 그룹명에는 다음만 사용할 수 있습니다.
    * 영숫자 (Alphanumeric characters)
    * 이모티콘
    * 밑줄(_)
    * 대시(-), 점, 공백 및 괄호 (그러나 이러한 문자로 시작할 수 없음)

    그룹명으로 사용할 수 없는 단어 목록은 [예약된 이름](https://docs.gitlab.com/ee/user/reserved_names.html)을 참조하십시오.

4. [네임스페이스](https://docs.gitlab.com/ee/user/group/#namespaces)에 사용되는 그룹 URL은 다음만 사용할 수 있습니다.
    * 영숫자
    * 밑줄
    * 대시 및 점 (대시로 시작하거나 점으로 끝날 수 없음)
5. [가시성 수준](https://docs.gitlab.com/ee/public_access/public_access.html)을 선택합니다.
6. GitLab 회원 또는 다른 사용자를 그룹에 초대합니다.

좀 더 상세한 내용은 [그룹](https://docs.gitlab.com/ee/user/group/) 문서를 참고하세요.

### 프로젝트 생성

GitLab에서 코드베이스를 호스팅할 프로젝트를 생성할 수 있습니다. 이를 사용하여 이슈를 추적하고, 작업을 계획하고, 코드에서 공동 작업하며, 내장된 CI/CD를 사용하여 앱을 지속적으로 빌드, 테스트 및 배포할 수 있습니다.  
프로젝트는 원하는 대로 공개, 내부 또는 비공개로 사용할 수 있습니다. GitLab은 생성하는 비공개 프로젝트의 수를 제한하지 않습니다.

GitLab에서 프로젝트를 생성하면 다음과 같은 많은 [기능](https://about.gitlab.com/features/)에 액세스할 수 있습니다.

GitLab에서 프로젝트를 생성하려면 :

1. 대시보드에서 **New project** 버튼을 클릭하거나, 상단 내비게이션 바에서 플러스(+) 아이콘을 사용합니다. 이렇게 하면 **Create new project** 페이지가 열립니다.
2. **Create new project** 페이지에서, 다음 중 원하는 것을 선택합니다.
    * [빈 프로젝트](https://docs.gitlab.com/ee/user/project/working_with_projects.html#blank-projects)를 만듭니다. (Create blank project)
    * 사용 가능한 [프로젝트 템플릿](https://docs.gitlab.com/ee/user/project/working_with_projects.html#project-templates) 중 하나를 사용하여 프로젝트를 만듭니다. (Create from template)
    * GitLab 인스턴스에서 활성화된 경우, 다른 저장소에서 [프로젝트를 가져옵니다](https://docs.gitlab.com/ee/user/project/import/index.html). 사용할 수 없는 경우 GitLab 관리자에게 문의하십시오. (Import project)

**Create new project** 페이지에서 **새 빈 프로젝트**를 만들려면 :

1. **Create blank project**를 클릭합니다.
2. 다음 정보를 제공합니다.
    * **Project name** 필드에 프로젝트의 이름. 특수 문자는 사용할 수 없지만 공백, 하이픈, 밑줄 또는 이모티콘을 사용할 수 있습니다. 이름을 추가하면 **Project slug**가 자동으로 채워집니다. 슬러그는 GitLab 인스턴스가 프로젝트의 URL 경로로 사용하는 것입니다. 다른 슬러그를 원한다면 먼저 프로젝트 이름을 입력한 다음 슬러그를 변경하십시오.
    * **Project slug** 필드에 프로젝트 경로. GitLab 인스턴스가 사용하는 프로젝트의 URL 경로입니다. **프로젝트 이름**이 비어 있으면 **프로젝트 슬러그**를 채울 때 자동으로 채워집니다.
    * **Project description** (선택 사항) 필드를 사용하여 프로젝트의 대시보드에 대한 설명을 입력 할 수 있으며, 이 설명을 통해 다른 사용자가 프로젝트에 관하여 이해하는 데 도움이 됩니다. 필수는 아니지만, 이를 채우는 것이 좋습니다.
    * **Visibility Level**을 변경하면 사용자에 대한 프로젝트의 [보기 및 액세스 권한](https://docs.gitlab.com/ee/public_access/public_access.html)이 수정됩니다.
    * **Initialize repository with a README** 옵션을 선택하면 Git 저장소가 초기화되도록 README 파일이 생성됩니다. Git 저장소는 기본 브랜치가 있으며 Clone할 수 있습니다.
3. **Create project** 버튼을 클릭합니다.

좀 더 상세한 내용은 [프로젝트 관리](https://docs.gitlab.com/ee/user/project/working_with_projects.html) 문서를 참고하세요.

### 멤버 설정

GitLab의 그룹과 프로젝트에 사용자를 초대하고 권한을 부여할 수 있습니다. 사용자는 특정 그룹이나 프로젝트에서 가지고 있는 액세스 수준에 따라 다른 능력을 갖습니다. GitLab에서는 `Guest`, `Reporter`, `Developer`, `Maintainer`, `Owner`로 역할을 구분하여 접근 권한을 부여합니다.

**Owner**  
기본적으로 그룹이나 프로젝트를 생성한 사람이 가지며, 그룹에서는 추가적으로 구성원에게도 부여할 수 있습니다. 그룹 또는 프로젝트에서 모든 권한을 가집니다. 일반적으로 팀장이나 PM 등 프로젝트 및 제품을 관리하는 사람에게 부여합니다.

**Maintainer**  
그룹 또는 프로젝트 수정/삭제, 그룹 회원 관리 등 일부 기능을 제외하고 `Owner`의 대부분 권한을 가집니다. `master` 브랜치에 Push 하고 Production으로 배포할 수 있습니다. 주로 업무를 배정하고 Merge Request를 승인하는 PL이나 시니어 엔지니어에게 부여합니다. 코드 리뷰를 하며 제품 및 코드베이스(codebase)을 알고 있어야 합니다.

**Developer**  
개발 또는 유지보수를 담당하는 개발자에게 부여합니다. 기본적으로 `master` 브랜치, 추가적으로 설정한 `develop` 브랜치와 같은 Protected 브랜치에는 Push 할 수 없습니다. 할당된 업무를 진행하기 위해 Feature 브랜치를 생성하고, 신규 기능 개발 또는 기존 기능 수정이 완료되면 소스를 Feature 브랜치에 Push 후 워크플로우에 따라 Merge Request를 작성하여 승인을 요청합니다.

**Reporter**  
리포지토리(Repository)에 쓸 수는 없지만, 이슈를 할당하거나 이슈 가중치를 설정하는 등의 이슈 관리와 Merge Request를 만들 수 있습니다.

**Guest**  
프로젝트에 적극적인 기여자는 아니지만, 이슈를 만들거나 코멘트(댓글)를 남김으로써 협업에 기여할 수 있습니다.

각 역할에서 사용할 수 있는 프로젝트 및 그룹의 권한은 [프로젝트 구성원 권한](https://docs.gitlab.com/ee/user/permissions.html#project-members-permissions), [그룹 구성원 권한](https://docs.gitlab.com/ee/user/permissions.html#group-members-permissions) 문서를 참고하세요.

#### 멤버 추가

그룹 또는 프로젝트의 Members 메뉴에서 추가할 사용자를 선택하거나 다른 그룹을 선택하여 구성원을 추가할 수 있습니다.

전제 조건 :

* **Maintainer** 또는 **Owner** 역할이 있어야 합니다.

그룹 또는 프로젝트에 사용자를 추가하려면 :

1. 사이드 바에서 **Members**를 선택합니다.
2. **Invite member** 탭에서, **GitLab member or Email address** 필드에 사용자 이름 또는 이메일 주소를 입력합니다.
3. 역할을 선택합니다.
4. (선택사항) 만료일을 선택합니다. 해당 날짜에 사용자는 더 이상 프로젝트에 액세스 할 수 없습니다.
5. **Invite** 버튼을 클릭합니다.

사용자에게 GitLab 계정이 있으면 구성원 목록에 추가됩니다. 이메일 주소를 사용한 경우 사용자는 이메일을 받습니다.  
초대가 수락되지 않으면 GitLab은 2일, 5일, 10일 후에 알림 이메일을 보냅니다. 수락되지 않은 초대는 90일 후에 자동으로 삭제됩니다.  
사용자에게 GitLab 계정이 없는 경우, 초대장을 받은 이메일 주소를 사용하여 계정을 만들라는 메시지가 표시됩니다.

좀 더 상세한 내용은 [멤버](https://docs.gitlab.com/ee/user/project/members/) 문서를 참고하세요.

### 마일스톤 생성

> 마일스톤을 생성하려면 Developer 이상의 권한이 필요합니다.

마일스톤은 Agile 스프린트로 사용할 수 있어 특정 스프린트와 관련된 모든 이슈와 병합 요청을 추적할 수 있습니다. 마찬가지로, 마일스톤을 릴리즈로 사용할 수 있습니다.

#### 애자일 스프린트로서의 마일스톤

1. Agile 스프린트의 시작과 끝을 나타내는 마일스톤 시작일과 마감일을 설정합니다.
2. `2021 6월 sprint`와 같은 Agile 스프린트의 이름으로 마일스톤 제목을 설정합니다.
3. 이슈의 오른쪽 사이드 바에서 원하는 마일스톤을 연결하여 Agile 스프린트에 이슈를 추가합니다.

#### 릴리즈로서의 마일스톤

1. 릴리즈의 릴리즈 날짜를 나타내도록 마일스톤 마감일을 설정하고 마일스톤 시작 날짜를 비워 둡니다.
2. `Version 9.4`와 같은 릴리즈 버전으로 마일스톤 제목을 설정합니다.
3. 이슈의 오른쪽 사이드 바에서 원하는 마일스톤을 연결하여 릴리즈에 이슈를 추가합니다.

마일스톤을 생성하려면 :

1. 그룹 또는 프로젝트에서 **Issues > Milestones**로 이동합니다.
2. **New milestone**을 클릭합니다.
3. 제목, 설명(선택 사항), 시작일(선택 사항) 및 마감일(선택 사항)을 입력합니다.
4. **Create milestone** 버튼을 클릭합니다.

### 레이블 생성

> Reporter 이상의 권한 수준을 가진 사용자는 레이블을 만들고 수정할 수 있습니다.

레이블은 이슈 보드의 핵심 부분입니다. 레이블을 사용하여 다음을 수행할 수 있습니다.

* 색상 및 `bug`, `feature request` 또는 `docs`와 같은 설명 제목을 사용하여 에픽, 이슈, 병합 요청을 분류합니다.
* 에픽, 이슈 및 병합 요청을 동적으로 필터링하고 관리합니다.
* 이슈 보드뿐만 아니라 [이슈, 병합 요청 및 에픽의 목록을 검색합니다](https://docs.gitlab.com/ee/user/search/index.html#issues-and-merge-requests).

#### 프로젝트 레이블 및 그룹 레이블

GitLab에는 두 가지 유형의 레이블이 있습니다.

* **프로젝트 레이블**은 해당 프로젝트의 이슈 및 병합 요청에만 할당할 수 있습니다.
* **그룹 레이블**은 선택한 그룹 또는 하위 그룹의 모든 프로젝트에서 이슈 및 병합 요청에 할당할 수 있습니다.
  * 선택한 그룹 또는 하위 그룹의 에픽에 할당할 수도 있습니다. **(ULTIMATE)**

##### 프로젝트 레이블

프로젝트 레이블 목록을 보려면, 프로젝트로 이동하여 **Issues > Labels**을 클릭합니다. 목록에는 프로젝트 수준에서 정의된 모든 레이블과 상위 그룹에서 정의한 모든 레이블이 포함됩니다. 각 레이블에 대해 생성된 프로젝트 또는 그룹 경로를 볼 수 있습니다. 상단에 검색어를 입력하고 검색 아이콘을 클릭하면 목록을 필터링할 수 있습니다.

새 프로젝트 레이블을 만들려면 :

1. 프로젝트에서 **Issues > Labels**로 이동합니다.
2. **New label** 버튼을 클릭합니다.
3. **Title** 필드에 레이블을 짧게 설명하는 이름을 입력합니다.
4. (선택 사항) **Description** 필드에 이 레이블을 사용하는 방법과 시기에 대한 추가 정보를 입력할 수 있습니다.
5. (선택 사항) 사용 가능한 색상 중 하나를 선택하거나 **Background color** 필드에 Hex 색상 값을 입력하여 레이블의 배경 색상을 선택합니다.
6. **Create label**를 클릭합니다.

만든 후에는 연필 아이콘을 클릭하여 레이블을 편집하거나 **Subscribe** 버튼 옆에 있는 세 개의 점(⋮)을 클릭하고 **Delete**를 선택하여 레이블을 삭제할 수 있습니다.

> 주의 : 레이블을 삭제하면 영구적으로 삭제됩니다. 레이블에 대한 모든 참조가 시스템에서 제거되며 삭제를 취소할 수 없습니다.

##### 그룹 레이블

그룹 레이블 목록을 보려면, 그룹으로 이동하여 **Issues > Labels**을 클릭합니다. 목록에는 그룹 수준에서 정의된 모든 레이블만 포함되고 프로젝트에 정의된 레이블은 나열되지 않습니다. 상단에 검색어를 입력하고 검색 아이콘을 클릭하면 목록을 필터링할 수 있습니다.

그룹 레이블을 만들려면, 그룹에서 **Issues> Labels**로 이동하고 프로젝트 레이블을 만드는 것과 동일한 프로세스를 따릅니다.

### 에픽 생성 (PREMIUM)

이슈가 프로젝트와 마일스톤 간에 테마를 공유할 때, 에픽을 사용하여 테마를 관리할 수 있습니다.  
하위 에픽을 만들고 시작 및 종료 날짜를 할당하여 진행 상황을 볼 수 있는 시각적 로드맵을 만들 수도 있습니다.

에픽 사용 :

* 팀이 한 그룹의 여러 프로젝트에서 서로 다른 이슈에 대한 여러 토론을 포함하는 대규모 기능을 작업하는 경우
* 이슈 그룹에 대한 작업이 시작 및 종료되는 시기를 추적하려는 경우
* 상위 수준에서 기능 아이디어와 범위에 대해 논의하고 협력하려는 경우

소속 그룹에서 에픽을 만들려면 :

1. 다음 중 하나의 방법으로 **New Epic** 폼(form)으로 이동합니다.
    * 그룹으로 이동하여 왼쪽 사이드 바에서 **Epics**을 선택합니다. 그런 다음 **New epic**을 선택합니다.
    * 그룹의 에픽에서 **New epic**을 선택합니다.
    * 어디에서나 상단 메뉴에서 **New… ( [+] ) > New epic**을 선택합니다.
    * 빈 [로드맵](https://docs.gitlab.com/ee/user/group/roadmap/index.html)에서 **New epic**을 선택합니다.
2. **Title** 필드에 제목을 입력합니다.
3. (선택사항) **Description** 필드에 설명을 입력합니다.
4. (선택사항) 에픽을 기밀로 만들려면 [Confidentiality 체크박스](https://docs.gitlab.com/ee/user/group/epics/manage_epics.html#make-an-epic-confidential)를 선택합니다.
5. (선택사항) 레이블을 선택합니다.
6. (선택사항) 시작 및 마감 날짜를 선택하거나 [상속](https://docs.gitlab.com/ee/user/group/epics/manage_epics.html#start-and-due-date-inheritance)합니다. (비워 두면 마일스톤 날짜로부터 상속됨)
7. **Create epic**을 선택합니다.

### 이슈 생성

이슈를 사용하여 아이디어를 협업하고 문제를 해결하며 작업을 계획합니다. 팀 및 외부 협업자와 제안을 공유하고 논의합니다.

필요와 워크플로우에 맞게 사용자 정의된 다양한 목적으로 이슈를 사용할 수 있습니다.

* 새로운 아이디어의 구현 논의
* Task 및 작업 상태 추적
* 기능 제안, 질문, 지원 요청 또는 버그 보고서 수락
* 코드 구현에 대한 자세한 설명

이슈는 항상 특정 프로젝트와 연관되지만, 그룹에 여러 프로젝트가 있는 경우, 그룹 수준에서 모든 이슈를 한꺼번에 볼 수도 있습니다.

#### 새 이슈 폼(form)에 액세스

프로젝트 내에서 새 이슈 폼으로 이동하는 방법에는 여러 가지가 있습니다.

* 프로젝트의 대시보드에서 **Issues > New Issue**로 이동합니다.

  ![New issue from tracker list](images/06/new_issue_from_tracker_list.png "New issue from tracker list")

* 프로젝트의 **open 이슈**에서 세로 줄임표(⋮) 버튼을 클릭하여 드롭다운 메뉴를 연 다음, **New Issue**를 클릭하여 동일한 프로젝트에서 새 이슈를 생성합니다.

  ![New issue from open issue](images/06/new_issue_from_open_issue.png "New issue from open issue")

* **이슈 보드**에서, 목록 맨 위에 있는 플러스 기호(+)를 클릭하여 새 이슈를 생성합니다. 해당 프로젝트에 대한 새 이슈가 오픈되고, 각각의 목록에 미리 레이블이 붙여집니다.

  ![New issue from issue board](images/06/new_issue_from_issue_board.png "New issue from issue board")

#### 새 이슈 폼의 요소

![New Issue form](images/06/new_issue.png "New Issue form")

새로운 이슈를 생성할 때 채울 수 있는 필드는 다음과 같습니다.

* 제목
* 설명
* 이슈를 기밀로 만들기 위한 체크박스
* 피할당인 (담당자)
* 중요도
* 에픽 **(PREMIUM)**
* 마감일
* 마일스톤
* 레이블

### 이슈 보드

이슈 보드는 기존 이슈 추적 기능과 레이블을 기반으로 합니다. 이슈는 할당된 레이블, 마일스톤 또는 담당자별로 구성된 세로 목록의 카드로 나타납니다.  
이슈 보드는 GitLab에서 전체 프로세스를 시각화하고 관리하는 데 도움이 됩니다. 레이블을 추가한 다음, 기존 이슈에 대한 해당 목록을 만듭니다. 준비가 되면, 이슈 카드를 한 단계에서 다른 단계로 드래그 할 수 있습니다.  
이슈 보드는 팀이 작업 중인 이슈, 각 이슈에 할당된 사람, 워크플로우에서 이슈가 있는 위치를 보여줄 수 있습니다.  
팀원이 자신의 워크플로우를 구성할 수 있도록 하려면, [멀티 이슈 보드](https://docs.gitlab.com/ee/user/project/issue_board.html#use-cases-for-multiple-issue-boards)(PREMIUM)를 사용하세요. 이를 통해 동일한 프로젝트에서 여러 이슈 보드를 만들 수 있습니다.

![Issue Boards](images/06/issue_boards.png "Issue Boards")

### Feature 브랜치 생성

기능 브랜치는 개발자가 새 기능에 대한 작업을 시작할 때 브랜치를 생성하는 소스 코드 브랜치 패턴 입니다. 이 브랜치에서 앞서 생성한 이슈에 대한 모든 작업을 수행하고 기능이 완료되면 변경사항을 기본(`master`) 브랜치에 병합합니다.

기능 브랜치를 통해 여러 개발자가 기본 코드베이스를 방해하지 않고, 변경사항을 격리하여 특정 기능에 대해 쉽게 작업할 수 있습니다. 또한 기본 브랜치에 손상된 코드가 포함되지 않으므로 지속적인 통합 환경에 큰 이점이 됩니다.

정해진 브랜치 네이밍 규칙은 없으나, `feature/` + `<Issue_Number>` + `_` + `<Feature_Name>` 형식으로 브랜치를 생성하면 [Sourcetree](https://www.sourcetreeapp.com/)와 같은 Git GUI 클라이언트에서 기능 브랜치를 그룹화하여 볼 수 있습니다.

* 사이드 바에서 **Repository > Branches**를 클릭합니다.
* **New branch** 버튼을 클릭합니다.
* **Branch name** 필드에 브랜치 이름을 입력합니다. (예: 이슈 번호가 1이고 주문 기능을 작업하는 경우 `feature/1_order`)
* 필요에 따라 **Create from** 필드를 변경하여 이 새 브랜치가 시작될 브랜치, 태그 또는 커밋 SHA를 선택합니다.
**Create branch** 버튼을 클릭합니다.

### 기능 브랜치에서 개발

아직 로컬에 개발 환경이 구성되지 않았다면, `git clone <repository path>` 명령을 사용하여 복제합니다. 선호하는 인증 방법에 따라 HTTPS 또는 SSH를 통해 복제할 수 있습니다.

HTTPS를 통해 복제하려면 :

```bash
git clone https://gitlab.com/gitlab-tests/sample-project.git
```

SSH를 통해 복제하려면 :

```bash
git clone git@gitlab.com:gitlab-tests/sample-project.git
```

> SSH를 사용하려면 [SSH 문서](https://docs.gitlab.com/ee/ssh/README.html)의 지침에 따라 GitLab에 SSH Key를 등록해야 합니다.

`git checkout` 명령을 실행하여 기능 브랜치로 전환합니다.

```bash
git checkout feature/1_order
```

코드를 작성한 다음, 변경사항을 Feature 브랜치에 푸시합니다.

```bash
git status
git add .
git commit -m "주문 API 기능 구현 및 테스트 코드 추가 #1"
git push
```

> 커밋 메시지에 `#xxx`와 같이 관련 이슈 번호를 추가하면 GitLab UI의 커밋 내역에 [크로스링크](https://docs.gitlab.com/ee/user/project/issues/crosslinking_issues.html)가 생성됩니다.

작업이 완료될 때까지 기능 브랜치에 여러 번 커밋하고 푸시할 수 있습니다.

### CI 파이프라인

> 사전에 프로젝트의 **Maintainer** 또는 **Owner** 권한이 있는 사용자가 리포지토리 루트에 `.gitlab-ci.yml` 파일을 생성하고 CI 파이프라인을 정의해야 합니다. 아직 구성하지 않았다면, [GitLab CI 기초 가이드](07_GitLab_Basic_CI.md), [GitLab CI/CD](https://docs.gitlab.com/ee/ci/README.html) 문서를 참고하여 CI 파이프라인을 구성합니다.  
> 또한, 프로젝트에서 사용할 수 있는 [하나 이상의 Runner가 있어야 합니다](https://docs.gitlab.com/ee/ci/quick_start/#ensure-you-have-runners-available).

기능 브랜치에 변경사항이 푸시 되면 프로젝트의 CI 파이프라인이 트리거 되고, `.gitlab-ci.yml` 파일에 정의되어 있는 Job들이 실행됩니다.  
애플리케이션을 빌드하고 테스트합니다.

사이드 바에서 **CI/CD > Pipelines**을 클릭하여 확인합니다.

### 병합 요청(Merge request)

병합 요청은 한 브랜치를 다른 브랜치로 병합하기 위한 요청입니다. 병합 요청을 사용하여 소스 코드에 대해 제안된 변경사항을 시각화하고 협업합니다.

#### 병합 요청 생성

기능 브랜치의 CI 파이프라인 실행 결과에 이상이 없고 기능 개발이 완료되면, 다음을 수행하여 Feature 브랜치를 `master` 브랜치에 병합(Merge)하기 위한 Merge Request을 생성합니다.

* 프로젝트의 사이드 바에서 **Merge requests**을 클릭한 다음, **New merge request** 버튼을 클릭합니다.
* **New merge request** 페이지에서 아래 항목을 선택하고 **Compare branch and continue** 버튼을 클릭합니다.
  * **Source branch**의 Select source branch 콤보박스에서 `feature/1_order`을 선택합니다.
  * **Target branch**의 Select target branch 콤보박스에서 `master`을 선택합니다.
* **New merge request** 폼에서 **Title** 필드에 제목을 입력합니다. 브랜치에 이미 커밋이 있는 경우 제목은 첫 번째 커밋 메시지의 첫 번째 라인으로 미리 채워집니다. 제목은 모든 경우에 필수인 유일한 필드입니다.
* **Description** 필드에 변경의 목표와 리뷰어(검토자)가 알아야 할 내용을 입력합니다. 브랜치에 이미 커밋이 있는 경우 설명은 커밋 메시지의 추가 라인으로 미리 채워집니다.
* (선택사항) 담당자(Assignees), 검토자(Reviewers), 마일스톤, 레이블, 승인자(Approvers)를 선택합니다.
* **Create merge request** 버튼을 클릭합니다.

**New merge request** 페이지에서, 병합 요청을 제출하기 전에 브랜치에 푸시된 모든 커밋, 파일 변경사항을 볼 수도 있습니다.

![New merge request](images/06/new_merge_request.png "New merge request")

#### 병합 요청 검토

병합 요청이 생성되면 리뷰어는 다음과 같이 수행하여 병합 요청을 검토합니다.

1. 검토하려는 병합 요청으로 이동하여 변경사항(Changes) 탭을 선택합니다.
2. 코드 줄의 좌측에 마우스를 올리면 말풍선 아이콘이 나타납니다.
3. 말풍선 아이콘을 클릭하여 첫 번째 코멘트를 작성하고, 코멘트 아래에 **Start a review** 버튼을 클릭합니다.
  ![Review merge request](images/06/merge_request_review.png "Review merge request")
4. 계속해서 코드 줄에 코멘트를 작성합니다.
5. 리뷰가 완료되면 **Submit review** 버튼을 클릭합니다.

#### 병합 요청 승인

자격이 있는 승인자(Approver)가 오픈 병합 요청의 상세 페이지에 방문하면, 병합 요청의 본문 아래에 다음 버튼 중 하나가 표시됩니다.

* **Approve** : 병합 요청에 필요한 승인 수가 더 없는 경우
* **Approve additionally** : 병합 요청에 승인 수가 더 필요한 경우
* **Revoke approval** : 병합 요청을 보고 있는 사용자가 이미 병합 요청을 승인한 경우

병합 요청은 사용자가 구성한 [승인 수와 유형](https://docs.gitlab.com/ee/user/project/merge_requests/approvals/rules.html)을 받아들이면 다른 이유로 차단되지 않는 한 병합할 수 있습니다. 병합 충돌, 보류중인 토론 또는 실패한 CI/CD 파이프 라인과 같은 다른 문제로 인해 병합 요청이 차단될 수 있습니다.

병합하기 위해 필요한 수의 승인을 받고나면 **Merge** 버튼이 활성화되고, 버튼을 클릭하여 Merge를 실행할 수 있습니다.  
Merge를 실행하기 전 두가지 옵션을 체크 할 수 있습니다. **Delete source branch**에 체크하면 현재 MR의 브랜치를 제거하면서 Merge를 실행합니다. **Squash commits**에 체크하면 MR에 쌓여있는 커밋 리스트를 하나의 커밋으로 묶어서 Merge를 실행합니다.

### CD 파이프라인

CI 파이프라인과 마찬가지로 사전에 Runner가 구성되어 있고, 아래와 유사하게 `.gitlab-ci.yml` 파일이 준비되어 있어야 합니다.

```yaml
test:
  services:
  - postgres:alpine
  variables:
    POSTGRES_DB: custom_db
    POSTGRES_USER: custom_user
    POSTGRES_PASSWORD: custom_pass
  script:
  - export DATABASE_URL=postgres://$POSTGRES_USER:$POSTGRES_PASSWORD@postgres:5432/$POSTGRES_DB
  - apt-get update -qy
  - apt-get install -y python-dev python-pip
  - pip install -r requirements.txt
  - python manage.py test

production:
  type: deploy
  script:
  - apt-get update -qy
  - apt-get install -y ruby-dev
  - gem install dpl
  - dpl --provider=heroku --app=$HEROKU_PRODUCTION_APP --api-key=$HEROKU_PRODUCTION_API_KEY --skip-cleanup
  only:
  - master
```

기본 브랜치에 병합이 완료되면 CD 파이프라인이 트리거 됩니다.  
`master` 브랜치의 CI 파이프라인이 실행되는데, 사이드 바에서 **CI/CD > Pipelines**을 클릭하여 확인합니다.  
CD 파이프라인 실행이 성공하면 변경사항이 프로덕션 환경에 배포됩니다.
