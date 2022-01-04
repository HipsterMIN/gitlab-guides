# 시스템별 CoDY 파일배포적용 가이드

본 가이드에서는 기존 CVS/SVN으로 버전 관리하고 있던 각 시스템의 코드베이스(소스 코드)를 CoDY-SCM(GitLab)에 등록한 다음 파일만 배포할 경우 적용하는 가이드입니다.

본 가이드에 따라 시스템별 CoDY 적용하기에 앞서 [GitLab 사용 가이드](07_GitLab_Basic_CI.md)와 [GitLab CI 기초 가이드](07_GitLab_Basic_CI.md) 문서를 읽어 보길 바랍니다.

* 각 시스템의 소스코드는 Cody-SCM(Gitlab)에 등록되어 있다고 가정합니다.
* 해당 가이드 적용 시 프로젝트마다 Push/Merge 시 추가/변경된 파일만 지정한 배포서버로 업로드합니다. 

1. master, dev 브랜치가 있는지 확인합니다.
소스코드를 등록하면 기본적으로 master 브랜치로 설정되어 있고, 만약 dev 브랜치가 없다면 각 프로젝트 대쉬보드에서 dev 브랜치 생성이 가능하고, 또한 로컬PC 작업환경에서 생성 가능합니다.

2. 로컬PC 환경에서 dev 브랜치를 확인 후 프로젝트 최상단 경로에 .gitlab-ci.yml 파일을 추가합니다. 파일내용은 아래 링크를 참고합니다.<br>
https://cody-scm.autoever.com/guides/ci-cd-examples/file-base-deploy-exam/-/blob/dev/.gitlab-ci.yml

3. 해당 파일 내용 중 아래 정보는 각 시스템에 맞게 수정 필요합니다
dev_deploy 부분은 dev 브랜치가 commit 되는 경우 실행되며, 개발서버 정보 기입 필요합니다.
dev_prod 부분에는 dev 브랜치에서 master 브랜치로 merge 되는경우 실행되며, 운영서버 정보 기입 필요합니다.
```
dev_prod:
  stage: deploy
  only:
    - merge_requests
  script:
    - DEPLOY_SERVER="배포서버IP주소"
    - LOGIN_USER="OS로그인계정명"
    - LOGIN_PASSWORD="OS로그인패스워드"

dev_deploy:
  stage: deploy
  only:
    - dev
  script:
    - DEPLOY_SERVER="배포서버IP주소"
    - LOGIN_USER="OS로그인계정명"
    - LOGIN_PASSWORD="OS로그인패스워드"
```

4. 프로젝트에서 추가/변경된 파일이 서버의 /home/"로그인계정"/tmp 위치로 복사가 되며 실제 배포위치 복사는 각 시스템 담당자분들께서 OS에 로그인 후 복사가 필요합니다.

5. (개선점) 실제 배포위치로 복사는 OS 보안 정책 이슈 확인 후 공유드리겠습니다.

6. (개선점) 스크립트에 작성하신 Credential 정보는 추후 Gitlab 변수 관리 기능을 사용하겠습니다.
