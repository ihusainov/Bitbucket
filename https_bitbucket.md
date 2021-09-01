# HTTPS in Bitbucket

Original  https://confluence.atlassian.com/bitbucketserver/personal-access-tokens-939515499.html

Personal access tokens can be used in place of passwords for Git over HTTPS, or to authenticate when using the Bitbucket Server REST API.

**Creating personal access tokens**
```
To create a personal access token:

Go to Profile picture > Manage account > Personal access tokens.
Click Create a token. 
Set the token name, permissions, and expiry.
```
![image](https://user-images.githubusercontent.com/62062799/131636818-f8d639a1-3b31-40be-ac96-c7dbd0631572.png)


**Permissions**
```
Permissions restrict what a token can do. 
As tokens are like passwords, your token’s permissions will be set at your current level of access by default. 
We recommend, however, restricting your token’s permissions to only the level it will need.

Here are the permission combinations you can assign to a token:
Repo permissions are inherited from the project permissions
A token’s repository permission must be as high as its project permission.
If you give a token project write permission, you cannot give it only repository read permissions (it must be write-level or higher).
You can modify a token’s permissions, or revoke a token, by going to Profile picture > Manage account > Personal access tokens.
```
![image](https://user-images.githubusercontent.com/62062799/131636969-e15ac3c4-26cf-4350-b83d-afae97ad20e5.png)


**Expiry**
```
For added security, when you’re creating a token you can also set it to automatically expire. 
This is optional, but if your administrator has made this a requirement you’ll need to choose an expiry date that’s within the limits they’ve set.

Once a token has been created, its expiry date cannot be changed. 
You can see the expiry dates for all your tokens by going to Profile picture > Manage account > Personal access tokens.
```


**After token create**
```
Настройка на git

Настройка производится на вашей ВМ
Заходим в каталог где будет производится работа с репозиторием и выполняем следующие комманды
Допустим вашь сгенерированные токен в Bitbucket  это  MzUyMzEyMTkxMjM4Om07GkOYXxr6dMPGtNNyk8
Выведем текущие настройки подключения:

git config --list --show-origin
git remote -v
```
```
Нам необходимо заменить значение ключа remote.origin.url   remote.origin.url=https://bitbucket.domain.ru/scm/dcr/myproject.git

Для этого выполняем следующие комманды:

git remote set-url origin https://username:jM4Om07GkOYXxr6dMPGtN8@https://bitbucket.domain.ru/scm/dcr/myproject.git

git remote set-url --push origin https://username:jM4Om07GkOYXxr6dMPGtN8@https://bitbucket.domain.ru/scm/dcr/myproject.git
```

```
Далее проверяем изменились ли поля и если мы видим наш токен в выдаче remote.origin.url 

Далее продолжить работу через https

git clone https://bitbucket.domain.ru/scm/dcr/myproject.git
```
