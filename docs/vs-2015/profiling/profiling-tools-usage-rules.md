---
title: 分析工具使用规则 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d508fdfe1845a75f0ef7e0ba36730afbaa4e157
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "47482031"
---
# <a name="profiling-tools-usage-rules"></a>分析工具使用规则
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主题的最新版本，请参阅[分析工具使用规则](https://docs.microsoft.com/visualstudio/profiling/profiling-tools-usage-rules)。  
  
分析工具使用类别中的性能规则提供有关最有效地使用探查器收集数据的指南。  
  
|||  
|-|-|  
|[DA0002：缺少 VSPerfCorProf.dll](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|命令行分析可能包含不完整的 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 二进制文件数据。 这可能由未设置正确环境变量所导致。|  
|[DA0003：大量内核样本](../profiling/da0003-many-kernel-samples.md)|记录了在目标二进制文件执行外部出现的大量分析样本。 若要收集更准确的数据，请考虑使用检测方法。|  
|[DA0004：处理器使用率很高](../profiling/da0004-high-processor-usage.md)|分析数据暗示处理器在分析运行期间一直繁忙。 若要收集更准确的数据，请考虑使用采样方法。|  
|[DA0008：收集的样本过少](../profiling/da0008-few-samples-collected.md)|在分析运行中收集的样本数不足以具有统计意义。 请考虑再次进行分析并较长时间地运行应用程序。 还可以考虑使用检测方法收集数据。|  
|[DA0026：处理过程的内核 CPU 时间过长](../profiling/da0026-excessive-kernel-cpu-time-processing.md)|分析运行中有大量时间处于处理器内核模式下。 请考虑通过将系统调用用作指标（而不是将时间用作指标）来进行采样。|  
|[DA0029：不支持的 CLR 版本](../profiling/da0029-unsupported-clr-version.md)|分析的二进制文件在使用探查器不支持的 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 版本。 探查器报告无法解析符号名称。|  
|[DA0030：收集数据库项目的层交互测量值](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|收集了大量对 <xref:System.Data?displayProperty=fullName> 命名空间中的方法进行的调用。 若要包含有关数据库调用的数据，请考虑在分析运行中收集层交互数据。|


