---
title: CA1809:避免过多的局部变量
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d1c2f76258be3b0be6409bffd002fd916883ab2
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921541"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809:避免过多的局部变量

|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|类别|Microsoft.Performance|
|是否重大更改|不间断|

## <a name="cause"></a>原因
成员包含64个以上的局部变量, 其中一些变量可能是编译器生成的。

## <a name="rule-description"></a>规则说明
常见的性能优化是将值存储在处理器寄存器中而不是存储在内存中, 这称为*局部变量*。 公共语言运行时最多可考虑64的 enregistration 局部变量。 不 enregistered 的变量会放置在堆栈上, 并且在操作之前必须移到寄存器。 若要允许所有本地变量获取 enregistered, 请将局部变量的数目限制为64。

## <a name="how-to-fix-violations"></a>如何解决冲突
若要修复与此规则的冲突, 请重构实现以使用不超过64的局部变量。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
如果性能不是问题, 则可以安全地禁止显示此规则发出的警告或禁用规则。

## <a name="related-rules"></a>相关规则
[CA1804删除未使用的局部变量](../code-quality/ca1804-remove-unused-locals.md)