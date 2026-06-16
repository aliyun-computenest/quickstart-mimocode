# MiMoCode AI 编程助手 部署文档

## 概述

MiMoCode 是小米开源的探索性 AI 编程助手，运行在终端中作为 CLI 工具，与 MiMo 系列模型及专属 Harness 系统配套使用。通过阿里云计算巢服务，您可以快速在 ECS 实例上部署 MiMoCode，实现开箱即用。

## 前提条件

- ECS 实例必须处于**运行中**状态
- ECS 实例需具备**公网访问**能力（需连通 `registry.npmmirror.com`）
- 支持的操作系统：Alibaba Cloud Linux 3/4、Ubuntu 20.04/22.04/24.04、Debian 12/13、Rocky Linux 9、AlmaLinux 9/10

## 部署流程

### 1. 创建服务实例

访问 MiMoCode AI 编程助手 服务部署链接，根据界面提示选择部署方式：

- **选择ECS实例（Linux）**：在已有的 ECS 实例上安装 MiMoCode
- **新建ECS实例**：创建新的 ECS 实例并自动安装 MiMoCode

[部署链接](https://computenest.console.aliyun.com/service/instance/create/cn-hangzhou?type=user&ServiceId=service-3a7d40a74d2f4d29b633)

![创建服务实例](images/create-instance.png)

### 2. 确认订单并创建

参数填写完成后可以看到对应询价明细，确认参数后点击 **下一步：确认订单**。确认订单完成后同意服务协议并点击 **立即创建** 进入部署阶段。

### 3. 等待部署完成

等待部署完成后进入服务实例管理，可以看到 MiMoCode 已成功安装到目标 ECS 实例。

![服务实例详情](images/instance-detail.png)

### 4. 使用 MiMoCode

通过 SSH 登录到 ECS 实例，执行以下命令验证安装：

```bash
mimo --version
```

首次启动 MiMoCode 会引导您完成配置：

```bash
mimo
```

![使用 MiMoCode](images/service-page.png)

## 安装说明

计算巢服务会通过 OOS 扩展自动完成以下安装步骤：

1. 解压预置的 Node.js v22.13.1 二进制至 `/usr/local/`
2. 将 npm registry 切换到 `https://registry.npmmirror.com`（阿里云官方 npm 镜像）
3. 通过 `npm install -g @mimo-ai/cli` 全局安装 MiMoCode CLI

## 官方文档

更多信息请访问：[MiMoCode GitHub](https://github.com/XiaoMi/mimocode)
