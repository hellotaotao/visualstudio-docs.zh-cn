---
title: CA2234:传递 System.Uri 对象，而不传递字符串
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 74484c5f014c9a677c321a0d9fed649f016ea3c9
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/16/2019
ms.locfileid: "69546880"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234:传递 System.Uri 对象，而不传递字符串

|||
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|类别|Microsoft.Usage|
|是否重大更改|非重大更改|

## <a name="cause"></a>原因

调用了一个方法, 该方法具有一个字符串参数, 该参数的名称包含 "uri"、"uri"、"urn"、"urn"、"url" 或 "url", 方法的声明类型包含具有<xref:System.Uri?displayProperty=fullName>参数的对应方法重载。

默认情况下, 此规则仅查看外部可见的方法和类型, 但这是[可配置](#configurability)的。

## <a name="rule-description"></a>规则说明

参数名称根据 camel 大小写约定拆分为标记, 然后检查每个标记, 以查看其是否等于 "uri"、"Uri"、"urn"、"Urn"、"url" 或 "Url"。 如果存在匹配项, 则假定参数表示统一资源标识符 (URI)。 URI 的字符串表示形式容易导致分析和编码错误，并且可造成安全漏洞。 <xref:System.Uri>类以安全安全的方式提供这些服务。 如果在两个重载之间进行选择, 而这两个重载只是与 URI 的表示形式不同, 则用户应选择<xref:System.Uri>采用自变量的重载。

## <a name="how-to-fix-violations"></a>如何解决冲突

若要修复与此规则的冲突, 请调用采用<xref:System.Uri>参数的重载。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告

如果 string 参数不表示 URI, 则可以安全地禁止显示此规则发出的警告。

## <a name="configurability"></a>配置

如果从[FxCop 分析器](install-fxcop-analyzers.md)(而不是传统分析) 运行此规则, 则可以根据其可访问性, 将基本代码的哪些部分配置为在上运行此规则。 例如, 若要指定规则只应针对非公共 API 图面运行, 请在项目中的 editorconfig 文件中添加以下键/值对:

```ini
dotnet_code_quality.ca2234.api_surface = private, internal
```

您可以为此规则、所有规则或此类别中的所有规则 (使用情况) 配置此选项。 有关详细信息, 请参阅[配置 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>示例

下面的示例演示了一个方法`ErrorProne`, 该方法违反了正确调用<xref:System.Uri>重载的`SaferWay`规则和方法:

[!code-vb[FxCop.Usage.PassUri#1](../code-quality/codesnippet/VisualBasic/ca2234-pass-system-uri-objects-instead-of-strings_1.vb)]
[!code-cpp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CPP/ca2234-pass-system-uri-objects-instead-of-strings_1.cpp)]
[!code-csharp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CSharp/ca2234-pass-system-uri-objects-instead-of-strings_1.cs)]

## <a name="related-rules"></a>相关规则

- [CA1057字符串 URI 重载调用 system.exception 重载](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
- [CA1056URI 属性不应是字符串](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1054URI 参数不应为字符串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
- [CA1055URI 返回值不应是字符串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)