---
title: CA1710:标识符应具有正确的后缀
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 93fd892baaf54d79c3a2387b8961a2f4c1bb2cdb
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547323"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710:标识符应具有正确的后缀

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|类别|Microsoft.Naming|
|是否重大更改|重大|

## <a name="cause"></a>原因

标识符的后缀不正确。

默认情况下, 此规则仅查看外部可见的标识符, 但这是[可配置](#configurability)的。

## <a name="rule-description"></a>规则说明

按照约定, 扩展某些基类型或实现某些接口的类型的名称或从这些类型派生的类型具有与基类型或接口关联的后缀。

命名约定为面向公共语言运行时的库提供了通用的外观。 这减少了新软件库所需的学习曲线, 并使客户可以放心地了解库是由具有开发托管代码的专业技能的人员开发的。

下表列出了具有关联后缀的基类型和接口。

|基类型/接口|Suffix|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|特性|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|例外|
|<xref:System.Collections.ICollection?displayProperty=fullName>|集合|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|词典|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|集合|
|<xref:System.Collections.Queue?displayProperty=fullName>|集合或队列|
|<xref:System.Collections.Stack?displayProperty=fullName>|集合或堆栈|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|集合|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|词典|
|<xref:System.Data.DataSet?displayProperty=fullName>|数据集|
|<xref:System.Data.DataTable?displayProperty=fullName>|集合或 DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|流|
|<xref:System.Security.IPermission?displayProperty=fullName>|权限|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|条件|
|事件处理程序委托。|EventHandler|

实现<xref:System.Collections.ICollection>并且是一种通用类型的数据结构 (如字典、堆栈或队列) 的类型是允许的名称, 这些名称提供有关类型的预期用法的有用信息。

实现<xref:System.Collections.ICollection>和的类型是特定项的集合, 其名称以单词 "collection" 结尾。 例如, <xref:System.Collections.Queue>对象的集合的名称为 "QueueCollection"。 "Collection" 后缀表示可以使用`foreach` (`For Each` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 语句枚举集合的成员。

实现<xref:System.Collections.IDictionary>的类型的名称以单词 "Dictionary" 结尾, 即使该类型还实现<xref:System.Collections.IEnumerable>了或<xref:System.Collections.ICollection>。 "集合" 和 "字典" 后缀命名约定使用户能够区分以下两个枚举模式。

具有 "Collection" 后缀的类型遵循此枚举模式。

```
foreach(SomeType x in SomeCollection) { }
```

带有 "Dictionary" 后缀的类型遵循此枚举模式。

```
foreach(SomeType x in SomeDictionary.Values) { }
```

对象包含<xref:System.Data.DataTable>对象的集合, <xref:System.Data.DataColumn?displayProperty=fullName>这些对象由和<xref:System.Data.DataRow?displayProperty=fullName>对象的集合组成。 <xref:System.Data.DataSet> 这些集合通过<xref:System.Collections.ICollection>基类<xref:System.Data.InternalDataCollectionBase?displayProperty=fullName>实现。

## <a name="how-to-fix-violations"></a>如何解决冲突

重命名该类型, 使其具有正确的字词后缀。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告

如果类型是可能被扩展的通用数据结构, 或者将保留任意一组不同的项, 则可以安全地禁止显示警告以使用 "集合" 后缀。 在这种情况下, 提供有关实现、性能或数据结构的其他特征的有用信息的名称可能有意义 (例如, BinaryTree)。 在类型表示特定类型的集合的情况下 (例如, StringCollection), 请勿禁止显示此规则的警告, 因为后缀指示可以使用`foreach`语句来枚举该类型。

对于其他后缀, 不要禁止显示此规则发出的警告。 后缀允许从类型名称中清晰地使用预期用法。

## <a name="configurability"></a>配置

如果从[FxCop 分析器](install-fxcop-analyzers.md)(而不是传统分析) 运行此规则, 则可以根据其可访问性, 将基本代码的哪些部分配置为在上运行此规则。 例如, 若要指定规则只应针对非公共 API 图面运行, 请在项目中的 editorconfig 文件中添加以下键/值对:

```ini
dotnet_code_quality.ca1710.api_surface = private, internal
```

您可以为此规则、所有规则或此类别中的所有规则 (命名) 配置此选项。 有关详细信息, 请参阅[配置 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="related-rules"></a>相关规则

[CA1711标识符不应具有正确的后缀](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>请参阅

- [特性](/dotnet/standard/design-guidelines/attributes)
- [处理和引发事件](/dotnet/standard/events/index)