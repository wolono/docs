# Ubuntu 24 安装教程

本教程适用于Ubuntu 24

## 更新和升级包

```sh
sudo apt-get update -y
```

```sh
sudo apt-get upgrade -y
```
## 在Ubuntu上创建新用户

```sh
sudo adduser [frappe-user]
usermod -a -G sudo [frappe-user]
su [frappe-user] 
cd /home/[frappe-user]
```


## 安装git

```sh
sudo apt-get install git
```
## 安装python和setuptools以及开发环境

```sh
sudo apt-get install python3-dev python3.12-dev python3-setuptools python3-pip
```

## 安装Python 3.12虚拟环境

```sh
sudo apt-get install python3.12-venv
```

## 安装通用软件

```sh
sudo apt-get install software-properties-common

```

## 安装mariaDB

```sh
sudo apt install mariadb-server mariadb-client

```

## 安装redis server

```sh
sudo apt-get install redis-server
```

## 安装wkhtmltopdf

```sh
sudo apt-get install xvfb libfontconfig wkhtmltopdf
```

```sh
sudo apt-get install libmysqlclient-dev
```

## 安装和设置MySql server
 
```sh
sudo mysql_secure_installation
```

 * Enter your current password for root (enter for none):
   * if you have root pass then input otherwise you can press "Enter" key
 * Switch to unix_socket authentication [Y/N]: Y
 * Change the root password [Y/n]: 
   * 'Y' if you want to change
 * Remove anonymous user [Y/N]: Y
 * Disallow root login remotely? [Y/n]: N
 * Remove test database and access to it? [Y/n]: Y
 * Reload privilege tables now? [Y/n]: Y

## 编辑MySql config文件 

```sh
sudo nano /etc/mysql/my.cnf
```

Copy this below section and past in to your config file

```sh
[mysqld]
character-set-client-handshake = FALSE
character-set-server = utf8mb4
collation-server = utf8mb4_unicode_ci

[mysql]
default-character-set = utf8mb4
```

## 安装Curl

```sh
sudo apt install curl
```

## 安装node

::: tip 注意！
下列安装方法任选其一
:::

### NVM(Github)

::: code-group

```sh [步骤1]
curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash
```

```sh [步骤2]
source ~/.profile
```

```sh [步骤3]
nvm install 18
```

:::

### NVM(国内源) <Badge type="danger" text="推荐" />

::: code-group

```sh [步骤1]
export NVM_DIR="$HOME/.nvm" && (
  git clone https://github.com/nvm-sh/nvm.git "$NVM_DIR"
  cd "$NVM_DIR"
) && \. "$NVM_DIR/nvm.sh"
```

```sh [步骤2]
sudo nano ~/.profile
```

```sh [步骤3]
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"
```

:::

### Nodesource安装

::: code-group

```sh [步骤1]
curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash -
```

```sh [步骤2]
sudo apt-get install nodejs -y
```

:::

## 配置npm国内加速镜像

```sh
npm config set registry https://registry.npmmirror.com
```

## 安装yarn

```sh
npm install -g yarn
```

## 配置yarn国内加速镜像

```sh
yarn config set registry https://registry.npmmirror.com/ --global
```

## 配置pip国内加速镜像

```sh
pip config set global.index-url https://mirrors.aliyun.com/pypi/simple/
pip config set install.trusted-host mirrors.aliyun.com
```

## 安装frappe-bench

```sh
sudo pip3 install frappe-bench --break-system-packages
```

## 初始化指定版本的 frappe-bench

### version-15

::: code-group

```sh [官方源]
bench init --frappe-branch version-15 frappe-bench
```

```sh [国内源Atomgit]
bench init --frappe-branch version-15 frappe-bench --frappe-path=https://atomgit.com/frappe/frappe --verbose
```

:::

### develop

::: code-group

```sh [官方源]
bench init --frappe-branch develop frappe-bench
```

```sh [国内源Atomgit]
bench init --frappe-branch develop frappe-bench --frappe-path=https://atomgit.com/frappe/frappe --verbose
```

:::

```sh
cd frappe-bench
```

## 应用权限到用户目录

```sh
chmod -R o+rx /home/[frappe-user]
```

## 创建新站点

```sh
bench new-site [site-name]
```

## 获取并安装ERPNext

### version-15

::: code-group

```sh [官方源]
bench get-app --branch version-15 erpnext
```

```sh [国内源Atomgit]
bench get-app --branch version-15 https://atomgit.com/frappe/erpnext
```

:::

### develop

::: code-group

```sh [官方源]
bench get-app --branch develop erpnext
```

```sh [国内源Atomgit]
bench get-app --branch develop https://atomgit.com/frappe/erpnext
```

:::

```sh
bench install-app erpnext
```

## 设置虚拟环境

```sh
sudo apt install python3-venv
```

```sh
python3 -m venv env
```

## 激活虚拟环境

```sh
source env/bin/activate
```

## 安装ansible

```sh
sudo /usr/bin/python3 -m pip install ansible --break-system-packages
```

## 安装fail2ban

```sh
sudo apt install fail2ban
```

## 设置生产模式

```sh
sudo bench setup production [frappe-user]
```

## 常见问题

如遇PDF乱码安装下面的字体

```sh
sudo apt-get install ttf-wqy-zenhei -y
sudo apt-get install ttf-wqy-microhei -y
```