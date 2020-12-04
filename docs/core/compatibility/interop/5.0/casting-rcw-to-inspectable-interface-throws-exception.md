---
title: 中断性变更：将 RCW 强制转换为 `InterfaceIsIInspectable` 会引发异常
description: 了解 .NET 5.0 中的以下互操作中断性变更：将 RCW 强制转换为 `InterfaceIsIInspectable` 接口会引发 PlatformNotSupportedException。
ms.date: 09/13/2020
ms.openlocfilehash: 7c0f37057aebcc41d0c00d949b921ec3a4bdf012
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759176"
---
# <a name="casting-rcw-to-an-interfaceisiinspectable-interface-throws-platformnotsupportedexception"></a><span data-ttu-id="8218a-103">将 RCW 强制转换为 `InterfaceIsIInspectable` 接口会引发 PlatformNotSupportedException</span><span class="sxs-lookup"><span data-stu-id="8218a-103">Casting RCW to an `InterfaceIsIInspectable` interface throws PlatformNotSupportedException</span></span>

<span data-ttu-id="8218a-104">将运行时可调用包装器 (RCW) 强制转换为标记为 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> 的接口现在会引发 <xref:System.PlatformNotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="8218a-104">Casting a runtime callable wrapper (RCW) to an interface marked as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> now throws a <xref:System.PlatformNotSupportedException>.</span></span> <span data-ttu-id="8218a-105">此更改是[从 .NET 删除 WinRT 支持](built-in-support-for-winrt-removed.md)的后续操作。</span><span class="sxs-lookup"><span data-stu-id="8218a-105">This change is a follow up to the [removal of WinRT support from .NET](built-in-support-for-winrt-removed.md).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="8218a-106">引入的版本</span><span class="sxs-lookup"><span data-stu-id="8218a-106">Version introduced</span></span>

<span data-ttu-id="8218a-107">5.0 RC2</span><span class="sxs-lookup"><span data-stu-id="8218a-107">5.0 RC2</span></span>

## <a name="change-description"></a><span data-ttu-id="8218a-108">更改描述</span><span class="sxs-lookup"><span data-stu-id="8218a-108">Change description</span></span>

<span data-ttu-id="8218a-109">在 .NET 5.0 预览版 6 之前的 .NET 版本中，将 RCW 强制转换为标记为 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> 的接口的行为符合预期。</span><span class="sxs-lookup"><span data-stu-id="8218a-109">In .NET versions prior to .NET 5.0 preview 6, casting an RCW to an interface marked as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> works as expected.</span></span> <span data-ttu-id="8218a-110">在 .NET 5.0 预览版 6-8 和 RC1 中，可以将 RCW 成功转换为 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> 接口。</span><span class="sxs-lookup"><span data-stu-id="8218a-110">In .NET 5.0 previews 6-8 and RC1, you can successfully cast an RCW to an <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> interface.</span></span> <span data-ttu-id="8218a-111">但是，对接口执行方法时，可能会出现访问冲突，因为[已在 .NET 5.0 预览版 6 中删除](built-in-support-for-winrt-removed.md)运行时中的基础支持。</span><span class="sxs-lookup"><span data-stu-id="8218a-111">However, you might get access violations when you execute methods on the interface, because the underlying support in the runtime [was removed in .NET 5.0 preview 6](built-in-support-for-winrt-removed.md).</span></span>

<span data-ttu-id="8218a-112">在 .NET 5.0 RC2 和更高版本中，将 RCW 强制转换为标记为 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> 的接口将在转换时引发 <xref:System.PlatformNotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="8218a-112">In .NET 5.0 RC2 and later versions, casting an RCW to an interface marked as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> throws a <xref:System.PlatformNotSupportedException> at cast time.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="8218a-113">更改原因</span><span class="sxs-lookup"><span data-stu-id="8218a-113">Reason for change</span></span>

<span data-ttu-id="8218a-114">在[以前的 .NET 5.0 预览版](built-in-support-for-winrt-removed.md)中删除了对 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> 的支持。</span><span class="sxs-lookup"><span data-stu-id="8218a-114">The support for <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> was [removed in a previous .NET 5.0 preview](built-in-support-for-winrt-removed.md).</span></span> <span data-ttu-id="8218a-115">但是，意外忽视了强制转换到 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> 接口的操作。</span><span class="sxs-lookup"><span data-stu-id="8218a-115">However, casting to an <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> interface was accidentally overlooked.</span></span> <span data-ttu-id="8218a-116">由于运行时中的基础支持不再存在，引发 <xref:System.PlatformNotSupportedException> 会启用正常故障路径。</span><span class="sxs-lookup"><span data-stu-id="8218a-116">Since the underlying support in the runtime no longer exists, throwing a <xref:System.PlatformNotSupportedException> enables a graceful failure path.</span></span> <span data-ttu-id="8218a-117">引发异常还让你更容易发现已不再支持此功能。</span><span class="sxs-lookup"><span data-stu-id="8218a-117">Throwing an exception also makes it more discoverable that this feature is no longer supported.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="8218a-118">建议的操作</span><span class="sxs-lookup"><span data-stu-id="8218a-118">Recommended action</span></span>

- <span data-ttu-id="8218a-119">如果可以在 Windows 运行时元数据 (WinMD) 文件中定义接口，请改用 C#/WinRT 工具。</span><span class="sxs-lookup"><span data-stu-id="8218a-119">If you can define the interface in a Windows runtime metadata (WinMD) file, use the C#/WinRT tool instead.</span></span>

- <span data-ttu-id="8218a-120">否则，请将接口标记为 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIUnknown> 而不是 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable>，并向 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> 方法接口的开头添加三个虚拟条目。</span><span class="sxs-lookup"><span data-stu-id="8218a-120">Otherwise, mark the interface as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIUnknown> instead of <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable>, and add three dummy entries to the start of the interface for the <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> methods.</span></span> <span data-ttu-id="8218a-121">以下代码片段演示了一个示例。</span><span class="sxs-lookup"><span data-stu-id="8218a-121">The following code snippet shows an example.</span></span>

  ```csharp
  [InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
  interface IMine
  {
      // Do not call these three methods.
      // They're exclusively to fill in the slots in the vtable.
      void GetIIdsSlot();
      void GetRuntimeClassNameSlot();
      void GetTrustLevelSlot();

      // The original members of the IMine interface go here.
      ...
  }
  ```

## <a name="affected-apis"></a><span data-ttu-id="8218a-122">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="8218a-122">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable?displayProperty=fullName>

<!--

### Affected APIs

- `F:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable`

### Category

Interop

-->