---
title: 文件跟踪 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7770da734143b2b6185b266137eeb46ba25bd32a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968061"
---
# <a name="file-tracking"></a>文件跟踪
文件跟踪记录对某个进程及其子进程的 Windows 文件系统的调用。 通过调用下列函数，程序会控制打开和关闭此日志记录的时间，并指定要使用的日志文件。

- [EndTrackingContext](../msbuild/endtrackingcontext.md) 停止跟踪当前上下文。

- [ResumeTracking](../msbuild/resumetracking.md) 调用 [SuspendTracking](../msbuild/suspendtracking.md) 后继续跟踪。

- [SetThreadCount](../msbuild/setthreadcount.md) 设置用于跟踪的线程数。

- [StartTrackingContext](../msbuild/starttrackingcontext.md) 开始新的跟踪上下文。

- [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md) 使用指定的根开始新的跟踪上下文。

- [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md) 结束跟踪并释放占用的资源。

- [SuspendTracking](../msbuild/suspendtracking.md) 暂时暂停跟踪。

- [WriteAllTLogs](../msbuild/writealltlogs.md) 写出所有上下文的跟踪日志。

- [WriteContextTLogs](../msbuild/writecontexttlogs.md) 写出当前上下文的跟踪日志。