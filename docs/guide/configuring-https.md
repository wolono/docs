# 配置HTTPS

## 开启DNS多租户

```sh
bench config dns\_multitenant on
```

### 创建SSL文件夹

```sh
sudo mkdir /etc/nginx/conf.d/ssl
```

将域名证书文件上传到frappe根目录下

### 移动域名证书

将命令中的`private.key`与`certificate_bundle.crt`名称改为域名证书对应的名称

```sh
sudo mv private.key /etc/nginx/conf.d/ssl/private.key
sudo mv certificate_bundle.crt /etc/nginx/conf.d/ssl/certificate_bundle.crt
```

### 设置域名证书

```sh
bench set-ssl-certificate site1.local /etc/nginx/conf.d/ssl/certificate_bundle.crt
bench set-ssl-key site1.local /etc/nginx/conf.d/ssl/private.key
```

### 重新生成nginx配置

```sh
bench setup nginx
```

### 重新加载nginx

```sh
sudo service nginx reload
```