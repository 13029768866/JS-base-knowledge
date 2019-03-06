# 一、配置账户信息

```
git config --global user.name "woodensRangerWZJ"     git config --global user.email "13029768866@163.com"
```

# 二、创建本地秘钥

```
1、ssh-keygen -t rsa -C"13029768866@163.com"
2、查看本地秘钥
cd ~/.ssh
ls
```

# 三、github配对

```
1、查看公钥
cat ~/.ssh/id_rsa.pub
2、登陆你的github帐户。点击你的头像，然后 Settings -> 左栏点击 SSH and GPG keys -> 点击 New SSH key
3、验证是否链接成功
ssh -T git@github.com

成功提示
Hi 13029768866! You've successfully authenticated, but GitHub does not provide shell access.
```

# 四、webstorm破解地址

```
IDEA license server 2018 phpstorm license server webstorm free license server https://licensez.com/
```