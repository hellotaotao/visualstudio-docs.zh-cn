---
title: 使用 VirtualBox 配置 Docker 主机 | Microsoft Docs
description: 使用 Docker Machine 和 VirtualBox 配置默认 Docker 实例的分步说明
services: azure-container-service
documentationcenter: na
author: mlearned
manager: jillfra
ms.assetid: 0b1335a2-7720-42a8-8260-4e06fc00c9f6
ms.service: multiple
ms.devlang: dotnet
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: multiple
ms.date: 06/08/2016
ms.author: mlearned
ms.openlocfilehash: a3c02d59021f7596c4c754e185782c591b71fd11
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2019
ms.locfileid: "55139322"
---
# <a name="configure-a-docker-host-with-virtualbox"></a>使用 VirtualBox 配置 Docker 主机
## <a name="overview"></a>概述
本文将引导完成使用 Docker Machine 和 VirtualBox 配置默认 Docker 实例的过程。
如果使用的是[用于 Windows 的 Docker](https://www.docker.com/products/docker-desktop)，则无需进行此配置。

## <a name="prerequisites"></a>系统必备
需要安装以下工具。

* [Docker 工具箱](https://github.com/docker/toolbox/releases)

## <a name="configuring-the-docker-client-with-windows-powershell"></a>使用 Windows PowerShell 配置 Docker 客户端
要配置 Docker 客户端，只需打开 Windows PowerShell，并执行以下步骤：

1. 创建默认 Docker 主机实例。

    ```PowerShell
    docker-machine create --driver virtualbox default
    ```
2. 验证默认实例是否已配置且在运行。 （应该会看到名为“default”的实例正在运行。

    ```PowerShell
    docker-machine ls
    ```

    ![docker-machine ls 的输出](media/vs-azure-tools-docker-setup/docker-machine-ls.png)
3. 将“default”设置为当前主机，并配置 Shell。

    ```PowerShell
    docker-machine env default | Invoke-Expression
    ```
4. 显示活动的 Docker 容器。 列表应为空。

    ```PowerShell
    docker ps
    ```

    ![docker ps 的输出](media/vs-azure-tools-docker-setup/docker-ps.png)

> [!NOTE]
> 每次重启开发计算机时，都需要重启本地 Docker 主机。
> 为此，请在命令提示符下发出以下命令：`docker-machine start default`。