---
title: CA2143:透明方法不应使用安全请求
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 532a10740b0617f32e4f970da8dc2a7e2807f792
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920473"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143:透明方法不应使用安全请求

|||
|-|-|
|TypeName|TransparentMethodsShouldNotDemand|
|CheckId|CA2143|
|类别|Microsoft.Security|
|是否重大更改|重大|

## <a name="cause"></a>原因
透明类型或方法以声明方式标记<xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand`为需求, <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>或方法调用方法。

## <a name="rule-description"></a>规则说明
安全透明代码不应负责验证某个操作的安全，因此不应要求权限。 安全透明代码应使用完整的需求来作出安全决策并且安全关键代码不应依赖透明代码以进行完全的请求。 执行安全检查的任何代码 (如安全要求) 应改为安全关键。

## <a name="how-to-fix-violations"></a>如何解决冲突
通常, 若要修复与此规则的冲突, 请使用<xref:System.Security.SecuritySafeCriticalAttribute>特性标记该方法。 你还可以删除该需求。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
不禁止显示此规则发出的警告。

## <a name="example"></a>示例
规则文件位于以下代码上, 因为透明方法会作出声明性安全要求。

[!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]

## <a name="see-also"></a>请参阅
[CA2142不应通过 Linkdemand 保护透明代码](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)