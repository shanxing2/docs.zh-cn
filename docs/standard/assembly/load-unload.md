---
title: 如何：加载和卸载程序集
ms.date: 08/19/2019
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: 77ea97c2fc324287e9c697d630def98241432c9f
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972671"
---
# <a name="how-to-load-and-unload-assemblies"></a><span data-ttu-id="cc099-102">如何：加载和卸载程序集</span><span class="sxs-lookup"><span data-stu-id="cc099-102">How to: Load and unload assemblies</span></span>
<span data-ttu-id="cc099-103">公共语言运行时会自动加载程序所引用的程序集，但也可以将特定的程序集动态加载到当前的应用程序域。</span><span class="sxs-lookup"><span data-stu-id="cc099-103">The assemblies referenced by your program will automatically be loaded by the common language runtime, but it is also possible to dynamically load specific assemblies into the current application domain.</span></span> <span data-ttu-id="cc099-104">有关详细信息，请参阅[如何：将程序集加载到应用程序域中](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="cc099-104">For more information, see [How to: Load assemblies into an application domain](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>

<span data-ttu-id="cc099-105">在 .NET Framework 中，只有在卸载完所有包含单个程序集的应用程序域之后，才能卸载此程序集。</span><span class="sxs-lookup"><span data-stu-id="cc099-105">In .NET Framework, there is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="cc099-106">即使程序集不在范围之内，在卸载包含它的所有应用程序域之前，实际的程序集文件都将保持加载状态。</span><span class="sxs-lookup"><span data-stu-id="cc099-106">Even if the assembly goes out of scope, the actual assembly file will remain loaded until all application domains that contain it are unloaded.</span></span> <span data-ttu-id="cc099-107">在 .NET Core 中，<xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> 类处理程序集的卸载。</span><span class="sxs-lookup"><span data-stu-id="cc099-107">In .NET Core, the <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> class handles the unloading of assemblies.</span></span> <span data-ttu-id="cc099-108">有关详细信息，请参阅[如何在 .NET Core 中使用和调试程序集可卸载性](unloadability.md)。</span><span class="sxs-lookup"><span data-stu-id="cc099-108">For more information, see [How to use and debug assembly unloadability in .NET Core](unloadability.md).</span></span>

## <a name="load-and-unload-assemblies"></a><span data-ttu-id="cc099-109">加载和卸载程序集</span><span class="sxs-lookup"><span data-stu-id="cc099-109">Load and unload assemblies</span></span>

<span data-ttu-id="cc099-110">要将程序集加载到应用程序域中，请使用 <xref:System.AppDomain> 和 <xref:System.Reflection.Assembly> 类中包含的几种加载方法中的一种。</span><span class="sxs-lookup"><span data-stu-id="cc099-110">To load an assembly into an application domain, use one of the several load methods contained in the classes <xref:System.AppDomain> and <xref:System.Reflection.Assembly>.</span></span> <span data-ttu-id="cc099-111">有关详细信息，请参阅[如何：将程序集加载到应用程序域中](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="cc099-111">For more information, see [How to: Load assemblies into an application domain](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span> <span data-ttu-id="cc099-112">请注意，.NET Core 仅支持单个应用程序域。</span><span class="sxs-lookup"><span data-stu-id="cc099-112">Note that .NET Core supports only a single application domain.</span></span> 

<span data-ttu-id="cc099-113">若要在 .NET Framework 中卸载程序集，必须卸载包含它的所有应用程序域。</span><span class="sxs-lookup"><span data-stu-id="cc099-113">To unload an assembly in the .NET Framework, you must unload all of the application domains that contain it.</span></span> <span data-ttu-id="cc099-114">要卸载应用程序域，请使用 <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="cc099-114">To unload an application domain, use the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="cc099-115">有关详细信息，请参阅[如何：卸载应用程序域](../../framework/app-domains/how-to-unload-an-application-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="cc099-115">For more information, see [How to: Unload an application domain](../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>

<span data-ttu-id="cc099-116">如果想要卸载 .NET Framework 应用程序中的某些程序集而不是其他程序集，请考虑创建一个新的应用程序域，在此域中执行代码，然后卸载此应用程序域。</span><span class="sxs-lookup"><span data-stu-id="cc099-116">If you want to unload some assemblies but not others in a .NET Framework application, consider creating a new application domain, executing the code inside that domain, and then unloading that application domain.</span></span> <span data-ttu-id="cc099-117">有关详细信息，请参阅[如何：卸载应用程序域](../../framework/app-domains/how-to-unload-an-application-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="cc099-117">For more information, see [How to: Unload an application domain](../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  

## <a name="see-also"></a><span data-ttu-id="cc099-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="cc099-118">See also</span></span>

- [<span data-ttu-id="cc099-119">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="cc099-119">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="cc099-120">编程概念 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc099-120">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="cc099-121">.NET 中的程序集</span><span class="sxs-lookup"><span data-stu-id="cc099-121">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="cc099-122">如何：将程序集加载到应用程序域中</span><span class="sxs-lookup"><span data-stu-id="cc099-122">How to: Load assemblies into an application domain</span></span>](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)