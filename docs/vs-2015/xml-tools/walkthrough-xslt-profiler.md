---
title: 演练： XSLT Profiler |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5a52682dbbec3f4e1cdc50027ca365cd9a1ca44b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "47468885"
---
# <a name="walkthrough-xslt-profiler"></a>演练：XSLT 探查器
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主题的最新版本，请参阅[演练： XSLT Profiler](https://docs.microsoft.com/visualstudio/xml-tools/walkthrough-xslt-profiler)。  
  
  
XSLT 探查器可创建详细的 XSLT 性能报告，有助于度量、评估和锁定 XSLT 代码中与性能相关的问题。 XSLT 探查器包含有关 XSL 和 XSLT 样式表优化的有用提示。 对于需要最佳性能的 XSLT 应用程序，此工具必不可少。  
  
## <a name="prerequisites"></a>系统必备  
 以下演练过程中需要 Visual Studio 2010 和 .NET Framework 4.0 版。 XSLT 探查器仅在已安装分析工具的 Microsoft Visual Studio Team System 中可用。  
  
### <a name="create-the-performance-report"></a>创建性能报告  
  
1.  在 Visual Studio 中打开 XSLT 文档。  
  
2.  单击**探查 XSLT** XML 菜单中提供的选项。  
  
3.  提供一个输入 XML 文档。 如果尚未打开 XML 文档，系统会提示您提供该文件。  
  
4.  分析开始，进度栏会显示编辑器中的进度。  
  
5.  XSLT 输出将显示在输出窗格中。  
  
6.  性能会话结束后，请检查性能报告。 通过保存在性能报告中的数据，您可以查看和分析 XSLT 性能。  
  
### <a name="get-all-the-available-views"></a>获取所有可用视图  
  
1.  单击**当前视图**下拉列表，以获取所有可用视图。  
  
2.  选择**摘要视图**选项**当前视图**下拉列表。 默认情况下，性能报告显示在**摘要视图**。 此视图是确定 XSLT 文档性能问题的起始点。 **摘要视图**列出下列数据点：  
  
    -   最频繁调用的函数  
  
    -   执行单独工作最多的函数  
  
    -   执行时间最长的函数  
  
3.  默认情况下，每个数据点有以下三列：函数的名称、调用次数的绝对值和命名函数调用相对总函数调用的百分比值。 从每个数据点**摘要视图**，可以通过右击函数数据点上导航到更详细的视图。  
  
4.  选择**函数视图**选项**当前视图**下拉列表。 **函数视图**列出分析过程中调用的函数。 可以通过单击列名对数据进行排序。 默认情况下，显示的列有：  
  
    -   **函数名**  
  
    -   **已用非独占时间**  
  
    -   **已用独占时间**  
  
    -   **应用程序非独占时间**  
  
    -   **应用程序独占时间**  
  
    -   **调用数**  
  
5.  所有时间列以绝对值和百分比形式显示。 术语**独占**指在排除其他函数所用时间的所用执行此函数的执行期间调用的函数的总时间。  
  
6.  术语**Inclusive**调用和任何这些被调用函数调用的其他函数是否是指执行，包括所有函数的执行时间的函数所用的总时间。  
  
### <a name="select-callercallee-view"></a>选择“调用方/被调用方”视图  
  
1.  选择**调用方/被调用方**中查看**当前视图**下拉列表。  
  
2.  **调用方/被调用方**视图具有以下三个不同部分：  
  
    -   **调用的函数**： 调用特定函数的所有函数都列在视图的上半部分。  
  
    -   **当前函数**: 视图的中间部分中列出的特定函数调用。  
  
    -   **函数调用的**： 函数调用的特定函数的所有函数都列在视图的底部。  
  
3.  如果名为 `SyncToNavigator` 的函数显示在视图的中间部分，则调用 `SyncToNavigator` 函数的所有函数会显示在视图顶部，而 `SyncToNavigator` 函数调用的所有函数显示在视图底部。  
  
4.  您可以通过双击列在视图的其他两个部分中的任何函数，更改视图中间部分的函数。 然后，该视图会自动更新，以反映所做的更改。  
  
5.  您也可以通过单击列名对数据进行排序。  
  
### <a name="select-calltree-view"></a>选择“调用关系树”视图  
  
1.  选择**调用树视图**中**当前视图**下拉列表。 此视图为程序执行的关系树视图。  
  
2.  **调用树视图**显示进程名称作为树的根。 函数为关系树中的节点。 此视图允许深化到特定调用跟踪并分析对性能影响最大的跟踪。 视图是类似于**调用堆栈视图**在调试过程中可用。 除了中的列**函数视图**，在**调用树视图**，还有一个额外的列以显示**模块名称**。  
  
3.  选择**标记**中**当前视图**下拉列表。  
  
4.  使用 SLT 探查器时，在数据收集流中会显示一些标记，并带有关联的注释。 标记是代码中放置有计数器的位置。 当您指示 XSLT 探查器收集 XSLT 性能计数器时，每当执行其中一个标记时就会收集这些计数器。 数据显示在一个表，其中包含**标记 ID**，**标记名**(**启动程序**，**结束程序**)，和**时间戳**。 标记不聚合和显示在按时间顺序**标记视图**性能报告。  
  
### <a name="select-modules-in-the-current-view"></a>选择当前视图中的模块  
  
1.  选择**模块**中**当前视图**下拉列表。  
  
2.  模块视图是聚合到模块级别的所有函数的平面列表。 展开或折叠模块名称可显示或关闭模块性能数据的视图。 可以通过单击列名对数据进行排序。 默认情况下，有绝对值和百分比的编号**已用非独占时间**，**已用独占时间**，**应用程序非独占时间**， **应用程序独占时间**，并**的调用次数**。  
  
3.  选择**进程**中**当前视图**下拉列表。  
  
4.  进程视图显示包含的表**进程 ID**，**进程名称**，**开始时间**，以及**结束时间**。 可以通过单击列名对数据进行排序。  
  
## <a name="see-also"></a>请参阅  
 [演练：使用 XSLT 层次结构](../xml-tools/walkthrough-using-xslt-hierarchy.md)


