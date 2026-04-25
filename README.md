# DS2API

> 将 DeepSeek 网页版对话能力转换为 API，支持最新的 DeepSeek V4

![预览](./_resources/e919f3c1c3868acd3073174ff7fe8bfe.png)

---

## 目录

- [服务器推荐](#服务器推荐)
- [部署教程](#部署教程)
- [使用说明](#使用说明)

---

## 服务器推荐

推荐服务器部署，**不要选择国内地区**，选择 Linux 版本 + Docker 上手快。

| 云厂商 | 推荐地区 | 配置 | 价格 |
|--------|---------|------|------|
| 腾讯云 | **首尔**（推荐）/ 新加坡 / 硅谷 / 东京 | 2 核 4G · 30M 带宽 · 60GB SSD · 1.5T 月流量 | ￥199 / 年 |

> **系统选择 Ubuntu 24**，可以同样价格续费。

[购买地址](https://curl.qcloud.com/oyWDLkRJ)

![服务器](./_resources/72d493eab65af6588b3ed9cb7585b177.png)

---

## 部署教程

### 1. 安装 Docker（Ubuntu 24）

```bash
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

![Docker 安装成功](./_resources/c898f010045dc839f7ebec25c95df60b.png)

### 2. 下载项目

```bash
git clone https://github.com/CJackHwang/ds2api.git
```

![克隆项目](./_resources/2414d17af34b0cb71a860063dc6db2d2.png)

### 3. 进入项目目录

```bash
cd ds2api
```

![进入目录](./_resources/4abee5dd8dfcc0a887ba01201b4e8ae0.png)

### 4. 创建环境变量文件

在项目目录中创建 `.env` 文件，至少需要设置管理员密钥：

```bash
cat > .env <<'EOF'
DS2API_ADMIN_KEY=123456
EOF
```

> **注意：** 请将 `123456` 替换为一个强密码，以上仅为示例。

![创建 .env](./_resources/399f487b00fc1952a0f91ee25fd8b3b1.png)

### 5. 创建配置文件

```bash
cp config.example.json config.json
```

![创建配置](./_resources/f8385c51a800f9888b94a53df5bc4fe1.png)

### 6. 启动服务

```bash
sudo docker compose up -d
```

![启动服务](./_resources/f23ce29008fbb0be8e451e8d9e3a50cc.png)

### 7. 访问面板

浏览器打开以下地址：

```
http://你的公网IP:6011
```

> **提示：** 记得在防火墙中放通端口 **6011**。

![访问面板](./_resources/7185e9beb30769537afc0e0efb9425cc.png)

---

## 使用说明

### 登录管理面板

点击「管理面板」，输入之前创建的管理员密码。

![登录](./_resources/bbce0ac8626b4ea928b7012ec0d26cf8.png)

### 添加账号

输入 DeepSeek 手机号和密码：

![添加账号](./_resources/41aed22c96caa2bc99ad5025b75a4522.png)

### 添加成功

![成功](./_resources/b136562168fc3c547a73996f52531618.png)

### API 测试

点击「API 测试」验证接口是否正常：

![API 测试](./_resources/b98c8b4122987fea05192baa9c14e598.png)

### API 接口信息

| 项目 | 值 |
|------|----|
| 接口地址 | `http://你的公网IP:6011/v1` |
| 模型名称 | `deepseek-chat` |
