---
title: 活动脚本分析概述 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Active Script Profiling
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 777d20ecb51b09b282f88dc08464727b9ff2a945
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432979"
---
# <a name="active-script-profiling-overview"></a>活动脚本分析概述
[活动脚本探查器接口](../winscript/reference/active-script-profiler-interfaces.md)启用分析脚本引擎。 活动脚本分析由以下部分组成：  
  
- 语言引擎  
  
- Host  
  
- 探查器  
  
## <a name="language-engine"></a>语言引擎  
 语言引擎执行该脚本。 它提供在执行脚本代码时对该代码启用分析的方法。 启用分析后，语言引擎采用探查器 COM 对象的类标识符 (CLSID) 作为参数。 它会创建探查器 COM 对象的一个实例，然后在发生各种事件时调用到探查器中。  
  
 语言引擎实现 [IActiveScriptProfilerControl 接口](../winscript/reference/iactivescriptprofilercontrol-interface.md)。  
  
> [!NOTE]
> [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 语言运行时在创建时检查 JS_PROFILER 环境变量，以确定是否应启用分析。 如果此变量设置为探查器的 CLSID，语言运行时创建探查器 COM 对象的实例，从而使用此变量的值来确定要创建的探查器。  
  
## <a name="host"></a>Host  
 主机创建语言引擎并为语言引擎提供要执行的脚本。 智能主机还可以提供文档上下文，调试器或探查器在你进行调试或分析时可以用它更好地提供信息。  
  
## <a name="profiler"></a>探查器  
 发生各种事件时，探查器会收到来自语言引擎的调用。 探查器必须注册为 COM 对象，并且必须实现 [IActiveScriptProfilerCallback](../winscript/reference/iactivescriptprofilercallback-interface.md) 接口。  
  
## <a name="see-also"></a>请参阅  
 [Active Script Profiler 接口](../winscript/reference/active-script-profiler-interfaces.md)