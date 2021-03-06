---
title: 在项目中包括 NuGet 包
description: 本文档介绍如何使用 Visual Studio for Mac 在项目中包含 NuGet 包。 文档将介绍如何查找和下载包，同时介绍 IDE 集成功能。
author: jmatthiesen
ms.author: jomatthi
ms.date: 09/17/2019
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: conceptual
ms.openlocfilehash: 22b2e07509403d8e19e3a3e920d45b064c2e51c0
ms.sourcegitcommit: 541a0556958201ad6626bc8638406ad02640f764
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2019
ms.locfileid: "71079539"
---
# <a name="install-and-manage-nuget-packages-in-visual-studio-for-mac"></a>在 Visual Studio for Mac 中安装和管理 NuGet 包

通过 Visual Studio for Mac 中的 NuGet 包管理器 UI，可轻松安装、卸载和更新项目和解决方案中的 NuGet 包。 可以搜索包和将包添加到 .NET Core、ASP.NET Core 和 Xamarin 项目。

本文介绍如何在项目中包括 NuGet 包并演示实现此流程无缝的工具链。

有关在 Visual Studio for Mac 中使用 NuGet 的简介，请参阅[快速入门：在 Visual Studio for Mac 中安装和使用包](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

## <a name="find-and-install-a-package"></a>查找和安装包

1. 对于 Visual Studio for Mac 中打开的项目，右键单击“Solution Pad”中的“依赖项”文件夹（如果使用 Xamarin 项目，则为“包”文件夹）并选择“添加包”     。

    ![添加新的 NuGet 包上下文操作](media/nuget-walkthrough-PackagesMenu.png)

2. 此操作将启动“添加包”窗口  。 确保对话框左上角的“源”下拉框设置为 `nuget.org`。

    ![列出 NuGet 包](media/nuget-walkthrough-AddPackages1.png)

3. 使用右上角的搜索框查找特定的包，如 `EntityFramework`。 找到希望使用的包后，请选择它并单击“添加包”按钮以开始安装  。

    ![添加 Azure NuGet 包](media/nuget-walkthrough-AddPackages2.png)

4. 包下载完毕后会添加到项目中。 解决方案将根据正在编辑的项目类型而发生变化：

    **Xamarin 项目**
    * “引用”节点包含属于 NuGet 包的所有程序集列表  。
    * “包”节点显示每个已下载的 NuGet 包  。 可以更新该列表中的包，或从列表中删除包。
    
    **.NET Core 项目**

    “NuGet”节点（“依赖项”>“NuGet”）显示每个已下载的 NuGet 包  。 可以更新该列表中的包，或从列表中删除包。

## <a name="using-nuget-packages"></a>使用 NuGet 包

添加 NuGet 包并更新项目引用后，可以如针对任何项目引用一样根据 API 对其进行编程。

请确保将任何所需的 `using` 指令添加到文件顶部：

```csharp
using Newtonsoft.Json;
```

<a name="Package_Updates" class="injected"></a>

## <a name="updating-packages"></a>更新包

通过右键单击“依赖项”节点（对于 Xamarin 项目为“包”节点）可以一次性完成所有包更新，也可以在每个组件上单独进行包更新   。

右键单击“依赖项”以访问上下文菜单： 

![包菜单](media/nuget-walkthrough-PackagesMenu.png)

* **管理 NuGet 包** - 打开窗口，将更多包添加到项目。
* 更新  - 检查每个包的源服务器并下载任何更新版本。
* 还原  - 下载任何缺少的包（无需将现有包升级到更新版本）。

现在也提供解决方案级别的“更新”和“还原”选项，这些选项可影响该解决方案中的所有项目。

在 Solution Pad 中，可以查看当前已安装包的版本，可右键单击包进行更新。

![包含“更新”、“删除”和“刷新”选项的包菜单](media/nuget-walkthrough-PackageMenu.png)

包存在可用新版本时，包名称旁会显示通知，你可以决定是否更新包。

![包存在可用新版本时显示的通知](media/nuget-walkthrough-package-update-available.png)

显示的菜单中包含两个选项：

* 更新  - 检查源服务器并下载更新版本（如果存在）。
* 删除  - 从此项目中删除包，并从项目引用中删除相关的程序集。

## <a name="adding-package-sources"></a>添加包源

最初从 nuget.org 检索安装包。然而，可以将其他包位置添加到 Visual Studio for Mac。 这有助于测试自己正在开发的 NuGet 包，或有助于使用公司或组织内的专用 NuGet 服务器。

在 Visual Studio for Mac 中，导航到“Visual Studio”>“首选项”>“NuGet”>“源”，查看和编辑包源的列表  。 请注意，源可以是（由 URL 指定的）远程服务器或本地目录。

![包源](media/nuget-walkthrough-PackageSource.png)

单击“添加”设置新源  。 向包源输入友好名称和 URL（或文件路径）。 如果源是安全的 Web 服务器，则同时输入用户名和密码，否则请将这些条目留空：

![添加包源](media/nuget-walkthrough-PackageSource2.png)

搜索包时可以选择不同的源：

![添加包源](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>版本控制

NuGet 文档讨论了[在不将包提交到源控件的情况下使用 NuGet](/nuget/consume-packages/packages-and-source-control)。 如果不希望将二进制文件和未使用信息存储到源代码管理中，可以将 Visual Studio for Mac 配置为自动从服务器还原包。 这意味着当开发人员首次从源代码管理检索项目时，Visual Studio for Mac 将自动下载安装所需的包。

![自动还原包](media/nuget-walkthrough-AutoRestore.png)

有关如何使 `packages` 目录不受跟踪的详细信息，请参阅特定的源控件文档。

## <a name="related-video"></a>相关视频

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>请参阅

* [在 Visual Studio 中安装和使用包 (Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)
