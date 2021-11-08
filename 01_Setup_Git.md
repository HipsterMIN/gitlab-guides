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

## GitLab에 SSH Key 등록

GitLab은 SSH 키를 사용하여 Git과 서버 간의 보안 통신을 지원합니다. SSH 프로토콜은 이 보안을 제공하며 매번 username이나 비밀번호를 제공하지 않고도 GitLab 원격 서버에 인증할 수 있습니다.

SSH를 지원하려면 GitLab은 OpenSSH 클라이언트 설치를 필요로 합니다. Windows 10뿐만 아니라 GNU/Linux 및 macOS에는 사전 설치되어 제공됩니다.
시스템에 SSH 버전 6.5 이상이 포함되어 있는지 확인하십시오. 현재 안전하지 않은 MD5 서명 체계는 제외됩니다. 다음 명령은 시스템에 설치된 SSH 버전을 반환합니다.

```
ssh -V
```

### SSH 키 옵션

GitLab은 RSA, DSA, ECDSA 및 ED25519 키 사용을 지원합니다.
* GitLab은 GitLab 11.0에서 DSA 키를 더 이상 사용하지 않습니다.
* [Practical Cryptography With Go](https://leanpub.com/gocrypto/read#leanpub-auto-ecdsa)에서 언급했듯이 DSA와 관련된 보안 문제는 ECDSA에도 적용됩니다.

> 참고 : 사용 가능한 문서는 ED25519가 더 안전하다고 제안합니다. RSA 키를 사용하는 경우, 미국 국립 과학 기술 연구소는 [간행물 800-57 Part 3 (PDF)](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57Pt3r1.pdf)에서 최소 2048 비트의 키 사이즈를 권장합니다.

따라서, 본 문서는 ED25519 및 RSA 키 사용에 중점을 둡니다.

### SSH 키 페어 생성

#### ED25519 SSH 키

[Practical Cryptography With Go](https://leanpub.com/gocrypto/read#leanpub-auto-chapter-5-digital-signatures)라는 책은 ED25519 키가 RSA 키보다 더 안전하고 성능이 뛰어나다고 제안합니다. OpenSSH 6.5는 2014년에 ED25519 SSH 키를 도입했으므로, 현재 운영 체제에서 사용할 수 있습니다.

다음 명령을 사용하여 ED25519 키를 만들고 구성할 수 있습니다.

```
ssh-keygen -t ed25519 -C "<comment>"
```

이메일 주소와 같은 인용부호(“)로 감싼 코멘트를 함께 사용하는 `-C` 플래그는 SSH 키에 레이블을 지정하는 선택적 방법입니다.

다음과 유사한 응답이 표시됩니다.

```bash
Generating public/private ed25519 key pair.
Enter file in which to save the key (/c/Users/Administrator/.ssh/id_ed25519):
Created directory '/c/Users/Administrator/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved /c/Users/Administrator/.ssh/id_ed25519
Your public key has been saved in /c/Users/Administrator/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:VX+u82OemBn0Gv4/xiLwJ+omqFf0OINNzmxRMPT63vI email@exmaple.com
The key's randomart image is:
+--[ED25519 256]--+
|      .+.   .    |
|        o. . .   |
|        ...   . .|
|       +..     o |
|      O.S    .  .|
|     . @.o  . .. |
|      + o.o  o+. |
|     o ..o.+.oBO.|
|   .o   +++E+**+*|
+----[SHA256]-----+
```

> SSH 키를 저장할 파일 입력 요청 시 입력하지 않고 Enter 키를 누르면 제안된 디렉토리 및 파일에 저장됩니다. 또한 SSH 키에 대한 [문장형 암호(passphrase)](https://www.ssh.com/ssh/passphrase) 입력을 요청하는데, 입력하지 않고 Enter 키를 누르면, 암호 입력 없이 사용할 수 있습니다.

#### RSA SSH 키

SSH에 RSA 키를 사용하는 경우, US National Institute of Standards and Technology에서는 최소 2048 비트의 키 사이즈를 사용하도록 권장합니다. 기본적 `ssh-keygen` 명령은 1024 비트 RSA 키를 만듭니다.

다음 명령을 사용하여 RSA 키를 만들고 구성할 수 있습니다. 필요한 경우 최소 권장 키 사이즈인 `2048`을 대체합니다.

```
ssh-keygen -t rsa -b 2048 -C "email@example.com"
```

이메일 주소와 같은 인용부호(“)로 감싼 코멘트를 함께 사용하는 -C 플래그는 SSH 키에 레이블을 지정하는 선택적 방법입니다.

다음과 유사한 응답이 표시됩니다.

```
Generating public/private rsa key pair.
Enter file in which to save the key (/home/user/.ssh/id_rsa):
```

이후 진행은 ED25519 방식과 유사합니다.

### GitLab 계정에 SSH 키 추가

이제 생성한 SSH 키를 GitLab 계정에 복사할 수 있습니다.  
다음과 같이 수행하여 SSH 키를 GitLab 계정에 추가합니다.

1. 정보를 텍스트 형식으로 저장하는 위치에 public SSH 키를 복사합니다. 다음 옵션은 ED25519 키에 대한 정보를  클립 보드에 저장합니다.

  ```bash
  cat ~/.ssh/id_ed25519.pub | clip
  ```

  > RSA 키를 사용하는 경우, `id_rsa.pub`으로 대체합니다.

2. GitLab 인스턴스 URL로 이동하여 로그인합니다.
3. 오른쪽 상단에서 아바타를 선택하고 **Settings**을 클릭합니다.
4. **SSH Keys**를 클릭합니다.
5. 복사한 공개 키를 Key 텍스트 박스에 붙여 넣습니다.
6. **Title** 텍스트 박스에 SSH Key 생성 시 `-C` 플래그로 입력한 이메일과 같은 설명 이름이 포함되어 있는지 확인하십시오.
7. "Expires at" 섹션 아래에 키의 만료일을 포함합니다. (선택 사항)
8. **Add key** 버튼을 클릭합니다.

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
