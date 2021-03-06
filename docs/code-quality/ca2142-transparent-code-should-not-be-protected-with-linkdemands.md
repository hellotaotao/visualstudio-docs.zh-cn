---
title: CA2142:不应使用 LinkDemand 保护透明代码
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf5bb8320a8876582cc325ecf973c83593777193
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920499"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142:不应使用 LinkDemand 保护透明代码

|||
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2142|
|类别|Microsoft.Security|
|是否重大更改|重大|

## <a name="cause"></a>原因
透明方法需要<xref:System.Security.Permissions.SecurityAction>或其他安全要求。

## <a name="rule-description"></a>规则说明
此规则在需要 Linkdemand 来访问它们的透明方法上触发。 安全透明代码不应负责验证某个操作的安全，因此不应要求权限。 因为透明方法应为安全特定方法, 所以它们不应进行任何安全决策。 此外, 保证安全决策的安全关键代码不应依赖透明代码来进行此类决定。

## <a name="how-to-fix-violations"></a>如何解决冲突
若要修复与此规则的冲突, 请删除透明方法的链接要求, 或在执行安全<xref:System.Security.SecuritySafeCriticalAttribute>检查 (如安全要求) 时使用特性标记该方法。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
不禁止显示此规则发出的警告。

## <a name="example"></a>示例
在下面的示例中, 规则在方法上触发, 因为方法是透明的, 并标记有<xref:System.Security.PermissionSet> <xref:System.Security.Permissions.SecurityAction>包含的 LinkDemand。

[!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]

不禁止显示此规则发出的警告。