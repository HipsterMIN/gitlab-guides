# 시스템별 CoDY 파일배포적용 가이드

본 가이드에서는 기존 CVS/SVN으로 버전 관리하고 있던 각 시스템의 코드베이스(소스 코드)를 CoDY-SCM(GitLab)에 등록(Push) 한다음 파일만 배포할 경우 적용하는 가이드입니다.

본 가이드에 따라 시스템별 CoDY 적용하기에 앞서 [GitLab 사용 가이드](07_GitLab_Basic_CI.md)와 [GitLab CI 기초 가이드](07_GitLab_Basic_CI.md) 문서를 읽어 보길 바랍니다.

* 각 시스템의 소스코드는 Cody-SCM(Gitlab)에 등록되어 있다고 가정합니다.
* 해당 가이드 적용 시 프로젝트마다 Push/Merge 시 추가/변경된 파일만 지정한 배포서버로 업로드합니다. 

1. master, dev 브랜치가 있는지 확인합니다.
소스코드를 등록하면 기본적으로 master 브랜치로 설정되어 있고, 만약 dev 브랜치가 없다면 각 프로젝트 대쉬보드에서 dev 브랜치 생성이 가능하고, 또한 로컬PC 작업환경에서 생성 가능합니다.
2. 로컬PC 환경에서 dev 브랜치를 확인 후 프로젝트 최상단 경로에 .gitlab-ci.yml 파일을 추가합니다. 파일내용은 아래 링크를 참고합니다.
https://cody-scm.autoever.com/guides/ci-cd-examples/file-base-deploy-exam/-/blob/dev/.gitlab-ci.yml
3. 해당 파일 내용 중 각 시스템에 맞게 수정 필요합니다
```
dev_deploy:
  stage: deploy
  only:
    - dev
  before_script:
    #- cat /etc/*release*
    #- cat /etc/shells
  script:
    #- echo $CI_COMMIT_SHA
    #- echo $CI_BUILDS_DIR
    #- echo $CI_PROJECT_DIR
    - DEPLOY_SERVER="배포서버IP주소"
    - LOGIN_USER="OS로그인계정명"
    - LOGIN_PASSWORD="OS로그인패스워드"
```




.gitlab-ci.yml
