---
title: CA2111:指针应为不可见
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 416e45337dafd11a00e98b9adda9f16b02139f9c
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921658"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111:指针应为不可见

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|类别|Microsoft.Security|
|是否重大更改|重大|

## <a name="cause"></a>原因
公共或受保护<xref:System.IntPtr?displayProperty=fullName>的<xref:System.UIntPtr?displayProperty=fullName>或字段不是只读的。

## <a name="rule-description"></a>规则说明
 <xref:System.IntPtr>和<xref:System.UIntPtr>是用于访问非托管内存的指针类型。 如果指针不是私有、内部或只读, 则恶意代码可以更改指针的值, 这可能会允许访问内存中的任意位置或导致应用程序或系统故障。

如果要保护对包含指针字段的类型的访问, 请参阅[CA2112:受保护的类型不应](../code-quality/ca2112-secured-types-should-not-expose-fields.md)公开字段。

## <a name="how-to-fix-violations"></a>如何解决冲突
通过使指针成为只读的、内部的或私有的, 使其安全。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
如果不依赖指针的值, 则禁止显示此规则发出的警告。

## <a name="example"></a>示例
下面的代码显示了违反和满足规则的指针。 请注意, 非私有指针也违反规则[CA1051:不要声明可见实例字段](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)。

[!code-csharp[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]

## <a name="related-rules"></a>相关规则
[CA2112受保护的类型不应公开字段](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

[CA1051不要声明可见实例字段](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>请参阅

- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>