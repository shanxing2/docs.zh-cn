---
ms.openlocfilehash: 077eadb05ab16f5cec8817b89bc771de0c94aefa
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679314"
---
### <a name="publishdepsfilepath-behavior-change"></a><span data-ttu-id="9b14e-101">PublishDepsFilePath 行为变更</span><span class="sxs-lookup"><span data-stu-id="9b14e-101">PublishDepsFilePath behavior change</span></span>

<span data-ttu-id="9b14e-102">对于单文件应用程序，`PublishDepsFilePath` MSBuild 属性为空。</span><span class="sxs-lookup"><span data-stu-id="9b14e-102">The `PublishDepsFilePath` MSBuild property is empty for single-file applications.</span></span> <span data-ttu-id="9b14e-103">此外，对于非单文件应用程序，可能在生成后期才会将 deps.json 文件复制到输出目录。</span><span class="sxs-lookup"><span data-stu-id="9b14e-103">Additionally, for non single-file applications, the *deps.json* file may not be copied to the output directory until later in the build.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9b14e-104">引入的版本</span><span class="sxs-lookup"><span data-stu-id="9b14e-104">Version introduced</span></span>

<span data-ttu-id="9b14e-105">5.0</span><span class="sxs-lookup"><span data-stu-id="9b14e-105">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="9b14e-106">更改描述</span><span class="sxs-lookup"><span data-stu-id="9b14e-106">Change description</span></span>

<span data-ttu-id="9b14e-107">在以前的 .NET 版本中，对于非单文件应用程序，`PublishDepsFilePath` MSBuild 属性是指向应用的输出目录中 deps.json 文件的路径；对于单文件应用，该属性是中间目录中的路径。</span><span class="sxs-lookup"><span data-stu-id="9b14e-107">In previous .NET versions, the `PublishDepsFilePath` MSBuild property is the path to the app's *deps.json* file in the output directory for non single-file applications, and a path in the intermediate directory for single-file apps.</span></span>

<span data-ttu-id="9b14e-108">从 .NET 5.0 开始，对于单文件应用程序，`PublishDepsFilePath` 为空，并且新的 `IntermediateDepsFilePath` 属性指定 deps.json 在中间目录中的位置。</span><span class="sxs-lookup"><span data-stu-id="9b14e-108">Starting in .NET 5.0, `PublishDepsFilePath` is empty for single-file applications and a new `IntermediateDepsFilePath` property specifies the *deps.json* location in the intermediate directory.</span></span> <span data-ttu-id="9b14e-109">此外，对于非单文件应用程序，可能在生成后期才会将 deps.json 文件复制到输出目录（即 `PublishDepsFilePath` 指定的路径）。</span><span class="sxs-lookup"><span data-stu-id="9b14e-109">Additionally, for non single-file applications, the *deps.json* file may not be copied to the output directory (that is, the path specified by `PublishDepsFilePath`) until later in the build.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9b14e-110">更改原因</span><span class="sxs-lookup"><span data-stu-id="9b14e-110">Reason for change</span></span>

<span data-ttu-id="9b14e-111">进行此更改有以下几个原因：</span><span class="sxs-lookup"><span data-stu-id="9b14e-111">This change was made for a couple of reasons:</span></span>

- <span data-ttu-id="9b14e-112">在 .NET 5 中，为了支持[改进的单文件应用](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md)，重构了发布逻辑。</span><span class="sxs-lookup"><span data-stu-id="9b14e-112">Due to a refactoring of the publish logic in order to support [improved single-file apps](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md) in .NET 5.</span></span>

- <span data-ttu-id="9b14e-113">在单文件应用中，为了帮助保护在捆绑 deps.json 后尝试重写 deps.json 文件的目标，从而静默不影响该应用 。</span><span class="sxs-lookup"><span data-stu-id="9b14e-113">In single-file apps, to help guard against targets that try to rewrite the *deps.json* file after *deps.json* has already been bundled, thus silently not affecting the app.</span></span> <span data-ttu-id="9b14e-114">因此，对于单文件应用程序，`PublishDepsFilePath` 为空。</span><span class="sxs-lookup"><span data-stu-id="9b14e-114">For this reason, `PublishDepsFilePath` is empty for single-file applications.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9b14e-115">建议操作</span><span class="sxs-lookup"><span data-stu-id="9b14e-115">Recommended action</span></span>

<span data-ttu-id="9b14e-116">重写 deps.json 文件的目标通常应使用 `IntermediateDepsFilePath` 属性来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="9b14e-116">Targets that rewrite the *deps.json* file should generally do so using the `IntermediateDepsFilePath` property.</span></span>

#### <a name="category"></a><span data-ttu-id="9b14e-117">类别</span><span class="sxs-lookup"><span data-stu-id="9b14e-117">Category</span></span>

<span data-ttu-id="9b14e-118">MSBuild</span><span class="sxs-lookup"><span data-stu-id="9b14e-118">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9b14e-119">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="9b14e-119">Affected APIs</span></span>

<span data-ttu-id="9b14e-120">不可用</span><span class="sxs-lookup"><span data-stu-id="9b14e-120">N/A</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->