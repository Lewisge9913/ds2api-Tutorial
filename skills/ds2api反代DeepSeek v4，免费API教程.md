将 DeepSeek 网页版对话能力转换为 API，包括最新的deepseek v4

![e919f3c1c3868acd3073174ff7fe8bfe.png](../_resources/e919f3c1c3868acd3073174ff7fe8bfe.png)

推荐服务器部署，不要选择国内地区，选择Linux版本Docker上手快

腾讯云新加坡，硅谷，东京地区价格是199元一年，2核4G30M带宽，60GBSSD盘 1.5T月流量，推荐首尔地区↓↓↓，系统选Ubuntu24，可以同样价格续费

购买地址：https://curl.qcloud.com/oyWDLkRJ

![72d493eab65af6588b3ed9cb7585b177.png](../_resources/72d493eab65af6588b3ed9cb7585b177.png)

教程

1.Ubuntu24系统安装Docker

```
sudo apt update
sudo apt install -y ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
$(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo docker run hello-world
```

![c898f010045dc839f7ebec25c95df60b.png](../_resources/c898f010045dc839f7ebec25c95df60b.png)

2.下载项目

```
git clone https://github.com/CJackHwang/ds2api.git
```

![2414d17af34b0cb71a860063dc6db2d2.png](../_resources/2414d17af34b0cb71a860063dc6db2d2.png)

3.打开项目

```
cd ds2api
```

![4abee5dd8dfcc0a887ba01201b4e8ae0.png](../_resources/4abee5dd8dfcc0a887ba01201b4e8ae0.png)

4.在项目目录里创建一个 .env 文件，至少放入管理员密钥

```
cat > .env <<'EOF'
DS2API_ADMIN_KEY=123456
EOF
```

改成一个强密码，这里是教程示例

![399f487b00fc1952a0f91ee25fd8b3b1.png](../_resources/399f487b00fc1952a0f91ee25fd8b3b1.png)

5.创建配置文件

```
cp config.example.json config.json
```

![f8385c51a800f9888b94a53df5bc4fe1.png](../_resources/f8385c51a800f9888b94a53df5bc4fe1.png)

6.运行项目

```
sudo docker compose up -d
```

![f23ce29008fbb0be8e451e8d9e3a50cc.png](../_resources/f23ce29008fbb0be8e451e8d9e3a50cc.png)

7.浏览器访问，记得防火墙放通端口6011

```
http://你的公网IP:6011
```

![7185e9beb30769537afc0e0efb9425cc.png](../_resources/7185e9beb30769537afc0e0efb9425cc.png)

8.点击管理面板输入之前创建的密码

![bbce0ac8626b4ea928b7012ec0d26cf8.png](../_resources/bbce0ac8626b4ea928b7012ec0d26cf8.png)

9.添加账号，输入手机号和密码

![41aed22c96caa2bc99ad5025b75a4522.png](../_resources/41aed22c96caa2bc99ad5025b75a4522.png)

10.成功

![b136562168fc3c547a73996f52531618.png](../_resources/b136562168fc3c547a73996f52531618.png)

11.点击API测试，完美成功

![b98c8b4122987fea05192baa9c14e598.png](../_resources/b98c8b4122987fea05192baa9c14e598.png)

接口：http://43.203.222.146:6011/v1

模型：deepseek-chat