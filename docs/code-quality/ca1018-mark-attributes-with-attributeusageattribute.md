---
title: CA1018:用 AttributeUsageAttribute 标记特性
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 78917bcd4c67e1da205595bac07c8e0e5947318d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923057"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018:用 AttributeUsageAttribute 标记特性

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|类别|Microsoft.Design|
|是否重大更改|重大|

## <a name="cause"></a>原因
自<xref:System.AttributeUsageAttribute?displayProperty=fullName>定义特性中不存在该特性。

## <a name="rule-description"></a>规则说明
定义自定义属性时, 请使用<xref:System.AttributeUsageAttribute>标记该属性, 以指示源代码中可应用自定义属性的位置。 特性的含义和预定用法将决定它在代码中的有效位置。 例如, 你可以定义一个属性, 该属性标识负责维护和增强库中的每个类型的人员, 并且始终在类型级别分配责任。 在这种情况下, 编译器应启用类、枚举和接口上的属性, 但不应在方法、事件或属性上启用它。 组织策略和过程将规定是否应在程序集上启用该属性。

<xref:System.AttributeTargets?displayProperty=fullName>枚举定义可为自定义属性指定的目标。 如果省略<xref:System.AttributeUsageAttribute>, 则自定义属性将对所有目标有效, 如<xref:System.AttributeTargets>枚举的值所`All`定义。

## <a name="how-to-fix-violations"></a>如何解决冲突
若要修复与此规则的冲突, 请使用<xref:System.AttributeUsageAttribute>指定属性的目标。 请参见以下示例。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
应修复与此规则的冲突, 而不是排除消息。 即使属性继承<xref:System.AttributeUsageAttribute>, 也应该提供属性以简化代码维护。

## <a name="example"></a>示例
下面的示例定义了两个特性。 `BadCodeMaintainerAttribute`错误地省略<xref:System.AttributeUsageAttribute>了语句, `GoodCodeMaintainerAttribute`并正确实现了本部分前面所述的属性。 请注意, 设计`DeveloperName`规则[CA1019 需要属性:定义特性参数](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)的访问器, 出于完整性考虑, 包括在内。

[!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
[!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>相关规则
[CA1019定义特性参数的访问器](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

[CA1813避免未密封的特性](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>请参阅

- [特性](/dotnet/standard/design-guidelines/attributes)