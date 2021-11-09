- [Git 설치 및 구성](#git-설치-및-구성)
  - [Git 로컬 환경 구성](#git-로컬-환경-구성)
    - [Git 설치](#git-설치)
    - [Git 설치 확인](#git-설치-확인)
    - [(선택 사항) Git GUI Client](#선택-사항-git-gui-client)
  - [GitLab에 SSH Key 등록](#gitlab에-ssh-key-등록)
    - [SSH 키 옵션](#ssh-키-옵션)
    - [SSH 키 페어 생성](#ssh-키-페어-생성)
      - [ED25519 SSH 키](#ed25519-ssh-키)
      - [RSA SSH 키](#rsa-ssh-키)
    - [GitLab 계정에 SSH 키 추가](#gitlab-계정에-ssh-키-추가)
  - [Git에 사용자 이름 및 이메일 설정](#git에-사용자-이름-및-이메일-설정)
  - [Git 인증 방법](#git-인증-방법)

# Git 설치 및 구성

## Git 로컬 환경 구성

### Git 설치

[Git Downloads](https://git-scm.com/downloads) 페이지에서 **Windows**를 클릭하면 [Git for Windows](https://git-scm.com/download/win) 페이지로 이동하며 자동으로 다운로드가 시작됩니다.  
본인 Windows 운영 체제 버전(32-bit or 64-bit)에 해당하는 바이너리 파일인지 확인하고 설치합니다.

### Git 설치 확인

Git Bash 또는 명령 프롬프트(CMD)를 엽니다.
정상적으로 설치되었는지 아래 명령을 실행하여 버전을 확인합니다.

```bash
git --version
```

### (선택 사항) Git GUI Client

Git CLI를 사용하는 대신 GUI 클라이언트를 설치하여 사용할 수 있습니다.  
다양한 [GUI Clients](https://git-scm.com/downloads/guis)가 있으며, SourceTree, GitHub Desktop이 많이 사용되고 있습니다.


## Git에 사용자 이름 및 이메일 설정

Git은 작성자 식별 정보로 사용자 이름과 이메일 주소를 사용하여 커밋 ID에 연결합니다.
`git config` 명령을 사용하여 변경할 수 있으며, Git은 커밋할 때마다 이 정보를 사용합니다.  
한 번 커밋한 후에는 커밋 로그에 있는 이 정보를 변경할 수 없습니다.

`git log` 명령을 사용하여 커밋 히스토리를 확인하면, **Author**에 설정한 정보가 있는 것을 확인할 수 있습니다.

PC의 모든 Repository에 대한 Git 사용자 이름과 이메일 주소를 설정하려면 아래 명령을 실행합니다.

```bash
git config --global user.name "Gildong Hong"
git config --global user.email "gdhong@example.com"
```

단일 리포지토리에 대해서만 Git 사용자 이름과 이메일 주소를 설정하려면 `--global` 옵션을 제거하고 실행합니다.

```bash
git config user.name "Gildong Hong"
git config user.email "gdhong@example.com"
```

Git 사용자 이름과 이메일 주소를 올바르게 설정했는지 확인합니다.

```bash
$ git config --global user.name
Gildong Hong
$ git config --global user.email
gdhong@example.com
```

또는

```bash
$ git config user.name
Gildong Hong
$ git config user.email
gdhong@example.com
```

아래 명령을 실행하면 Git 구성 정보를 확인할 수 있습니다.

```bash
git config --list
```

## Git 인증 방법

PC를 GitLab에 연결하려면, 자신을 식별할 수 있는 자격 증명을 추가해야 합니다. 두 가지 옵션이 있습니다.

* HTTPS를 통해 프로젝트 별로 인증하고 PC와 GitLab 간에 작업을 수행할 때마다 자격 증명을 입력합니다.
* SSH를 통해 한 번 인증하면 GitLab은 사용자가 clone, pull 및 push 할 때마다 자격 증명을 요청하지 않습니다.

인증 프로세스를 시작하기 위해, 기존 리포지토리를 PC에 clone 합니다.

* **SSH**를 사용하여 인증하려면, [GitLab에 SSH Key 등록](#gitlab에-ssh-key-등록) 지침에 따라 clone 하기 전에 설정하십시오.
* **HTTPS**를 사용하려면, GitLab에서 사용자 이름과 비밀번호를 요청합니다.
  * 계정에 2FA를 활성화한 경우, 계정의 비밀번호 대신 **read_repository** 또는 **write_repository** 권한이 있는 [개인 액세스 토큰](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html)을 사용해야 합니다. Clone 하기 전에 하나를 만드십시오.
  * 2FA를 활성화하지 않은 경우, 계정의 암호를 사용하십시오.

> 참고 : SSH를 통한 인증은 GitLab에서 권장하는 방법입니다. 자격 증명 저장소에 대한 자세한 내용은 [Git 자격 증명 문서](https://git-scm.com/book/en/v2/Git-Tools-Credential-Storage)에서 확인할 수 있습니다.
