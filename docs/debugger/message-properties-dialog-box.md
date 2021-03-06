---
title: 消息属性对话框 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options
- message options, General
ms.assetid: 58e9dc24-baf6-4ab8-916c-aea28b72e3b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f590f40e4e3361f4dbeb46a3a9b8758b8ab5075
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62846110"
---
# <a name="message-properties-dialog-box"></a>“消息属性”对话框
使用此对话框中，若要了解有关特定的消息的详细信息。 若要显示此对话框中，将焦点移至[消息视图](../debugger/messages-view.md)窗口。 在树中，选择消息的任何节点，然后选择**属性**从**视图**菜单。

 **常规**选项卡是显示唯一选项卡。 以下设置将可用：

 **窗口句柄**此窗口的唯一 ID。 重复使用窗口句柄号;它们仅对该窗口的生存期确定窗口。 单击此值以查看此窗口的属性。

 **嵌套级别**的此消息，其中 0 表示没有嵌套的嵌套深度。

 **消息**号、 状态和已选择的 windows 消息的名称。

 **lResult**的值*lResult*参数，如果有的话。

 **wParam**的值*wParam*参数，如果有的话。

 **lParam**的值*lParam*参数，如果有的话。 此值进行解码后，如果它是字符串或结构的指针。

## <a name="related-sections"></a>相关章节
 [消息选项对话框](../debugger/message-options-dialog-box.md)用于选择要在活动的消息视图中列出的消息。

 [消息搜索对话框](../debugger/message-search-dialog-box.md)用于查找特定的消息在消息视图中的节点。

 [Spy + + 参考](../debugger/spy-increment-reference.md)包括描述每个 Spy + + 菜单和对话框中的部分。

 [从查找窗口打开消息视图](../debugger/how-to-open-messages-view-from-find-window.md)介绍了如何从查找窗口对话框中打开消息视图。

 [消息在消息视图中搜索](../debugger/how-to-search-for-a-message-in-messages-view.md)介绍了如何在消息视图中查找特定的消息。

 [消息视图](../debugger/messages-view.md)显示与窗口、 进程或线程关联的消息流。

 [Spy + + 视图](../debugger/spy-increment-views.md)介绍的 windows、 消息、 进程和线程的 Spy + + 树视图。

 [使用 Spy + +](../debugger/using-spy-increment.md)介绍 Spy + + 工具，并说明如何使用它。