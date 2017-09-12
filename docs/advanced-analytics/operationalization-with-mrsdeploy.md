---
title: "部署和使用使用 mrsdeploy 分析 |Microsoft 文档"
ms.custom: 
ms.date: 08/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a8b090a9d5a9ed0a9f63b8f666fa9985089305ed
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---

# <a name="deploy-and-consume-analytics-using-mrsdeploy"></a>部署和使用使用 mrsdeploy 分析

Microsoft R Server 包括一项操作化功能， **mrsdeploy**，支持这些任务：

+ 发布和管理 R 和 Python 的模型和 web 服务形式的代码
+ 使用这些客户端应用程序中的服务

本主题提供有关如何启用和配置功能的信息。

有关支持的方案的常规信息**mrsdeploy**，请参阅[与 R 服务器的操作化](https://docs.microsoft.com/r-server/what-is-operationalization)。

## <a name="using-mrsdeploy-for-operationalization"></a>Mrsdeploy 用于操作化

Word*操作化*可能表示许多事情：

+ 能够将模型发布到 web 服务以供使用，由应用程序
+ 支持可缩放或分布式计算
+ 一次开发、 部署多次
+ 快速评分，这两个单行和批处理评分

如果在安装了与 SQL Server 的计算机学习服务*操作化*是一种 R 或 Python 代码包装在存储过程。 然后，任何应用程序可以调用存储的过程以重新训练模型、 生成评分，或创建报表。 你还可以自动执行使用 SQL Server 中的现有计划机制的作业。

但是，Microsoft R Server 提供了有关部署支持，另一种机制使用用于运行分布式的 R 作业中支持的 R 作业和管理实用程序的发布的 web 服务。 Microsoft R Server 使用中的函数**mrsdeploy**程序包，以建立与远程计算节点的会话和一个控制台应用程序中执行 R 代码。

R Server 此部署功能可以提供这些优势：

+ 对分析 web 服务的基于角色的访问控制

    确定谁可以发布、 更新和删除其自己的 web 服务，也可以更新和删除 web 服务的人员发布的其他用户，以及警报的人员可以仅列表并使用 web 服务。

+ 更快地评分
  
  可以使用实时的一个受支持的 R 模型对象评分来提高评分操作的速度。

+ 作为 web 服务中发布的 Python 代码

  有关示例，请参阅[发布和使用的 Python 代码](./python/publish-consume-python-code.md)。

+ 异步批处理消耗

  现在可以通过批处理执行以异步方式使用大量的输入数据调用的 web 服务。

+ Web 和计算节点的网格的自动缩放

  提供了一个脚本模板，以便你可以轻松地启动 R Server Vm 在 Azure 中，一组，然后将其配置为一个网格，用于实现分析和远程执行。 此网格可以向上扩展或向下根据 CPU 使用情况。

+ 异步远程执行

    现在支持使用**mrsdeploy** R 包。 若要继续在远程脚本执行期间在你的开发环境中工作，请执行 R 脚本使用以异步方式`async`参数。 如果您运行的脚本执行时间太长，这是特别有用。

## <a name="requirements-and-configuration"></a>要求和配置

SQL Server 自 2017 年 1 CTP 2.0 及更高版本包括此功能，因此只能使用 R Server 以前提供并不与 SQL Server R Services 一起安装。 **Mrsdeploy**安装包的 SQL Server 计算机上，如果选择此选项以安装**Microsoft 机器学习 Server**，从**共享功能**SQL Server 安装程序的部分。

通常情况下，我们不建议你在运行 SQL Server 计算机学习 Services 的同一台计算机上安装机学习服务器。 我们建议你安装**Microsoft 机器学习 Server**从 SQL Server 的单独计算机上，然后在该计算机上配置的操作化功能。

但是，如果你需要将其安装在一起，请按照这些附加步骤来成功配置该服务。

1. 安装 DotNetCore 1.1

    如果.NET 核心未作为 SQL 服务器的一部分进行安装，则必须在开始 R Server 安装程序之前安装它。

2. 安装 Microsoft 机器学习服务器。

3. 完成的安装程序后**Microsoft 机器学习 Server**，请手动添加的以下注册表项**mrsdeploy**，它指定 R_SERVER 文件的基本文件夹。 

    + 创建新的注册表项`H_KEY_LOCAL_MACHINE\SOFTWARE\R Server\Path`
    + 设置的关键值`"C:\Program Files\Microsoft SQL Server\140\R_SERVER"`。

4. 完成后，打开[管理员实用工具](https://docs.microsoft.com/r-server/operationalize/configure-use-admin-utility)。

5. 以继续配置**mrsdeploy**服务如下所述：[管理员配置](https://docs.microsoft.com/r-server/operationalize/configure-start-for-administrators)

6. 有关详细信息，请参阅[mrsdeploy 函数](https://docs.microsoft.com/r-server/r-reference/mrsdeploy/mrsdeploy-package)。