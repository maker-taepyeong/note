# 여러개의 ssh key 사용하기

GitHub에 SSH 공개키를 등록하면 암호를 매번 입력하지 않아도 인증할 수 있다.

여러 개의 계정에서 SSH 인증을 하려면 설정을 변경해야 한다.

## GitHub 계정에 SSH 공개키 등록하기

방법은 ["Adding a new SSH key to your account"](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account) 문서에 친절하게 설명되어 있다.

## 로컬 머신의 SSH 설정 변경하기

설정 파일의 기본 위치는 `$HOME/.ssh/config`이며, 예시를 참고해서 설정하면 된다.

설정을 커스터마이징하려면 ["SSH config file for OpenSSH client"](https://www.ssh.com/academy/ssh/config) 문서를 참고하면 된다.

```plaintext
#account: alex
Host github-alex.com
HostName github.com
AddKeysToAgent yes
UseKeychain yes
IdentityFile ~/.ssh/id_alex

#account: ben
Host github-ben.com
HostName github.com
User git
IdentityFile ~/.ssh/id_ben
IdentitiesOnly yes

#account: cameron
Host github-cameron.com
HostName github.com
User git
IdentityFile ~/.ssh/id_cameron
IdentitiesOnly yes
```

## 커맨드라인에서 사용하기

알렉스 계정으로 클론하려면

```bash
git clone git@github-alex.com:organization/repository.git
```

캐머론 계정으로 클론하려면

```bash
git clone git@github-cameron.com:organization/repository.git
```
