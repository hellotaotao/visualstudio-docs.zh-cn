---
title: CA2219:在异常子句中不引发异常
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f8e949e21530654882cba99a7d9fedad8b5b59b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920269"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219:在异常子句中不引发异常

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|CheckId|CA2219|
|类别|Microsoft.Usage|
|是否重大更改|不间断, 中断|

## <a name="cause"></a>原因
`finally`、Filter 或 fault 子句引发了异常。

## <a name="rule-description"></a>规则说明
当异常子句中引发异常时, 这会大大增加调试的难度。

在`finally`或 fault 子句中引发异常时, 新异常会隐藏活动异常 (如果存在)。 这会使原始错误难以检测和调试。

如果在筛选子句中引发了异常, 则运行时将以无提示方式捕获异常, 并使筛选器的计算结果为 false。 无法判断筛选器评估为 false 与从筛选器引发的异常之间的差异。 这使得难以检测和调试筛选器的逻辑中的错误。

## <a name="how-to-fix-violations"></a>如何解决冲突
若要修复此规则的冲突, 请不要从`finally`、filter 或 fault 子句显式引发异常。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
请勿禁止显示此规则的警告。 在不存在的情况下, 在异常子句中引发的异常可为执行代码带来好处。

## <a name="related-rules"></a>相关规则
[CA1065不要在意外的位置引发异常](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>请参阅
[设计警告](../code-quality/design-warnings.md)