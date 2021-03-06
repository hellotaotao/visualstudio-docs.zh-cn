---
title: CA2126:类型链接请求需要继承请求
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2be42519f87c3c040c1f80c80d53d490853d986e
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920755"
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126:类型链接请求需要继承请求

|||
|-|-|
|TypeName|TypeLinkDemandsRequireInheritanceDemands|
|CheckId|CA2126|
|类别|Microsoft.Security|
|是否重大更改|重大|

## <a name="cause"></a>原因
公共的非密封类型受链接要求保护, 具有可重写的方法, 并且类型和方法都不受继承要求保护。

## <a name="rule-description"></a>规则说明
对方法或其声明类型的链接需求要求方法的直接调用方具有指定的权限。 对方法的继承要求需要重写方法才能具有指定的权限。 对类型的继承需求要求派生类具有指定的权限。

## <a name="how-to-fix-violations"></a>如何解决冲突
若要修复与此规则的冲突, 请使用与链接要求相同的权限的继承请求来保护类型或方法。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
不禁止显示此规则发出的警告。

## <a name="example"></a>示例
下面的示例演示违反规则的类型。

[!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
[!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
[!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]

## <a name="related-rules"></a>相关规则
[CA2108查看值类型的声明性安全](../code-quality/ca2108-review-declarative-security-on-value-types.md)

[CA2112受保护的类型不应公开字段](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

[CA2122不要通过链接要求间接公开方法](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

[CA2123重写链接请求应与基相同](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>请参阅

- [安全编码准则](/dotnet/standard/security/secure-coding-guidelines)
- [链接需求](/dotnet/framework/misc/link-demands)