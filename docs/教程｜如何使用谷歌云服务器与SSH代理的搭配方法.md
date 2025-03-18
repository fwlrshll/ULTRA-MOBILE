# 教程｜如何使用谷歌云服务器与SSH代理的搭配方法

## 引言

许多用户在搭建服务器或使用代理时会遇到一些疑问，比如如何结合谷歌云服务器使用SSH代理，或者如何正确配置才能确保连接成功。本文将详细介绍如何利用**谷歌云服务器**搭配**SSH代理**，并提供清晰的步骤指南，帮助您快速上手。除了常见的HTTP、HTTPS、Socks5代理协议外，SSH代理因其安全性和稳定性也备受青睐。接下来，我们将从谷歌云服务器的配置开始，一步步讲解如何实现这一目标。

## 第一步：创建谷歌云服务器实例

谷歌云提供90天免费试用和300美元的试用额度，非常适合初学者。您可以登录谷歌云控制台，进入实例创建页面。具体操作如下：

1. **登录谷歌云**：访问谷歌云控制台并登录您的账号。
2. **创建虚拟机实例**：在控制台中选择“创建实例”，进入配置页面。

![创建实例](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*crURdSYNgZ5WnUkJ)

## 第二步：配置虚拟机实例

在配置虚拟机时，您可以根据需求选择合适的设置：

- **最低配置即可**：对于SSH代理使用，最低配置通常就足够。
- **磁盘映像**：推荐选择熟悉的系统，例如Ubuntu。
- **防火墙设置**：勾选“允许HTTP流量”和“允许HTTPS流量”，确保网络访问顺畅。

![配置实例](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*h_w5JIYBkn7nC3Ta)
![防火墙设置](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*cqQDfZIaDKVp902Z)

## 第三步：设置外部IP地址

为了通过SSH连接服务器，您需要在创建实例时为虚拟机分配一个**外部IP地址**：

- 在实例配置页面，找到“网络”选项。
- 选择“创建外部IP”并保存，确保后续SSH连接时可以使用。

![外部IP设置](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*7iRgmHqf0xcPKkcM)
![IP确认](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*G47_0s2L5ze0-jFe)

*特别提示*：如果您需要管理多个账号并确保安全性，推荐使用AdsPower指纹浏览器。这款工具专为多账号运营设计，能够有效防止关联和封号，帮助您安全管理账号矩阵。目前，它已通过市面上100%的指纹安全检测！

👉 [【限时福利】点击此处或使用邀请码：VIPFreeTrial 即可免费体验VIP会员专业功能！](https://bit.ly/adspower_free)

## 第四步：连接并配置服务器

实例创建完成后，接下来需要通过谷歌云自带的浏览器窗口连接服务器并进行配置：

1. **打开实例终端**：在控制台中选择刚刚创建的实例，点击“打开浏览器窗口”。
2. **切换root权限**：输入命令 `sudo -i`（注意“o”后的空格），按回车切换至root用户。

![连接实例](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*Nr8MEzZVh57Vx10l)
![切换root](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*K5O3dD-4XApTzRws)

## 第五步：修改SSH配置文件

为了启用SSH代理功能，需要调整服务器的SSH配置文件：

1. **编辑配置文件**：输入 `vi /etc/ssh/sshd_config`（注意“vi”后的空格），按回车进入编辑模式。
2. **进入编辑状态**：按下 `i` 键开始编辑。
3. **修改参数**：
   - 将 `PermitRootLogin` 改为 `yes`，以允许root用户登录。
   - 将 `PasswordAuthentication` 改为 `yes`，启用密码登录。
4. **保存退出**：编辑完成后，按 `Esc` 键退出编辑模式，输入 `:wq` 并回车保存。

![编辑配置文件](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*xvYANtQ9OvLPdfdD)
![修改参数](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*zZwpYxUFBTGwGbTM)

## 第六步：设置root密码并重启服务

完成SSH配置后，设置密码并重启服务以生效：

1. **设置root密码**：输入 `passwd root`，按回车后按提示输入新密码。
2. **重启SSH服务**：输入命令重启服务，确保配置生效。

![设置密码](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*XiuFrIj3FNvGX5LZ)
![重启服务](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*RbuCLu3l1ge5fsJS)

## 第七步：在AdsPower中配置SSH代理

谷歌云服务器配置完成后，您可以在AdsPower中设置SSH代理：

1. **选择代理类型**：在导入账号时，将代理类型设置为“SSH”。
2. **填写信息**：
   - **代理主机**：输入之前设置的外部IP地址。
   - **代理端口**：默认使用22。
   - **代理账号**：输入“root”。
   - **代理密码**：输入上一步设置的root密码。
3. **验证连接**：保存配置后，测试代理是否连接成功。

![配置SSH代理](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*IZ3UQ_gqs3MNFmfu)
![连接成功](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*lVDM0vigg6hz5RGk)

## 总结

通过以上步骤，您已经成功将**谷歌云服务器**与**SSH代理**结合使用。这种方法不仅简单易行，还能有效提升网络访问的安全性与稳定性。如果您在配置过程中遇到问题，不妨仔细检查外部IP、防火墙设置以及SSH配置文件，确保每一步都正确无误。现在，您可以轻松享受SSH代理带来的便利了！