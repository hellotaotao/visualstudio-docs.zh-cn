---
title: CA1059:成员不应公开某些具体类型
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f24881d04599677c5d45c93fc940286f115d593
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922515"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059:成员不应公开某些具体类型

|||
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|类别|Microsoft.Design|
|是否重大更改|重大|

## <a name="cause"></a>原因
外部可见成员是特定类型的, 或者通过其参数或返回值公开某些具体类型。 目前, 此规则报告以下具体类型的公开:

- 派生自<xref:System.Xml.XmlNode?displayProperty=fullName>的类型。

## <a name="rule-description"></a>规则说明
具体类型是指具有一个完整实现因此可以实例化的类型。 若要允许广泛使用成员, 请将具体类型替换为建议的接口。 这允许成员接受任何实现接口的类型, 或在需要实现接口的类型的情况下使用。

下表列出了目标具体类型及其建议的替换项。

|具体类型|Replacement|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>。<br /><br /> 使用接口可将成员与 XML 数据源的特定实现分离。|

## <a name="how-to-fix-violations"></a>如何解决冲突
若要修复与此规则的冲突, 请将具体类型更改为建议的接口。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
如果需要具体类型提供的特定功能, 则可以安全地禁止显示此规则中的消息。

## <a name="related-rules"></a>相关规则
[CA1011考虑将基类型作为参数传递](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)