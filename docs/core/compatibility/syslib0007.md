---
title: SYSLIB0007 警告
description: 了解有关生成编译时警告 SYSLIB0007 的过时信息。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: d5410a3b3d33515e2ee6f578cad2f4deaec9c25d
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333052"
---
# <a name="syslib0007-default-implementations-of-cryptography-algorithms-not-supported"></a><span data-ttu-id="68b75-103">SYSLIB0007：不支持加密算法的默认实现</span><span class="sxs-lookup"><span data-stu-id="68b75-103">SYSLIB0007: Default implementations of cryptography algorithms not supported</span></span>

<span data-ttu-id="68b75-104">.NET Framework 中的加密配置系统不允许适当的加密灵活性，且不存在于 .NET Core 和 .NET 5+ 中。</span><span class="sxs-lookup"><span data-stu-id="68b75-104">The cryptographic configuration system in .NET Framework doesn't allow for proper cryptographic agility and isn't present in .NET Core and .NET 5+.</span></span> <span data-ttu-id="68b75-105">.NET 的后向兼容性要求也禁止框架更新某些加密 API 以跟上加密技术的发展。</span><span class="sxs-lookup"><span data-stu-id="68b75-105">.NET's backward-compatibility requirements also prohibit the framework from updating certain cryptographic APIs to keep up with advances in cryptography.</span></span> <span data-ttu-id="68b75-106">因此从 .NET 5.0 开始，以下 API 标记为已过时。</span><span class="sxs-lookup"><span data-stu-id="68b75-106">As a result, the following APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="68b75-107">使用这些 API 会在编译时生成警告 `SYSLIB0007`。</span><span class="sxs-lookup"><span data-stu-id="68b75-107">Use of these APIs generates warning `SYSLIB0007` at compile time.</span></span>

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HMAC.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=fullName>

## <a name="workaround"></a><span data-ttu-id="68b75-108">解决方法</span><span class="sxs-lookup"><span data-stu-id="68b75-108">Workaround</span></span>

- <span data-ttu-id="68b75-109">建议采取的操作是用对特定算法（例如 <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType>）的工厂方法的调用替换对现已过时的 API 的调用。</span><span class="sxs-lookup"><span data-stu-id="68b75-109">The recommended course of action is to replace calls to the now-obsolete APIs with calls to factory methods for specific algorithms, for example, <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType>.</span></span> <span data-ttu-id="68b75-110">这样，便可以完全控制要实例化哪些算法。</span><span class="sxs-lookup"><span data-stu-id="68b75-110">This gives you full control over which algorithms are instantiated.</span></span>

- <span data-ttu-id="68b75-111">如果需要保持与使用现已过时的 API 的 .NET Framework 应用生成的现有有效负载的兼容性，请使用下表中建议的替换项。</span><span class="sxs-lookup"><span data-stu-id="68b75-111">If you need to maintain compatibility with existing payloads generated by .NET Framework apps that use the now-obsolete APIs, use the replacements suggested in the following table.</span></span> <span data-ttu-id="68b75-112">该表提供了从 .NET Framework 默认算法到其 .NET 5+ 等效项的映射。</span><span class="sxs-lookup"><span data-stu-id="68b75-112">The table provides a mapping from .NET Framework default algorithms to their .NET 5+ equivalents.</span></span>

  | <span data-ttu-id="68b75-113">.NET framework</span><span class="sxs-lookup"><span data-stu-id="68b75-113">.NET Framework</span></span> | <span data-ttu-id="68b75-114">.NET Core/.NET 5.0+ 兼容替换项</span><span class="sxs-lookup"><span data-stu-id="68b75-114">.NET Core / .NET 5.0+ compatible replacement</span></span> | <span data-ttu-id="68b75-115">备注</span><span class="sxs-lookup"><span data-stu-id="68b75-115">Remarks</span></span> |
  | - | - | - |
  | <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.RSA.Create?displayProperty=nameWithType> | |
  | <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.SHA1.Create?displayProperty=nameWithType> | <span data-ttu-id="68b75-116">SHA-1 算法被认为已无效。</span><span class="sxs-lookup"><span data-stu-id="68b75-116">The SHA-1 algorithm is considered broken.</span></span> <span data-ttu-id="68b75-117">如果可能，请考虑使用更强大的算法。</span><span class="sxs-lookup"><span data-stu-id="68b75-117">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="68b75-118">请咨询安全顾问以获取进一步的指导。</span><span class="sxs-lookup"><span data-stu-id="68b75-118">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | <span data-ttu-id="68b75-119">对于大多数新式应用程序，不建议使用 HMACSHA1 算法。</span><span class="sxs-lookup"><span data-stu-id="68b75-119">The HMACSHA1 algorithm is discouraged for most modern applications.</span></span> <span data-ttu-id="68b75-120">如果可能，请考虑使用更强大的算法。</span><span class="sxs-lookup"><span data-stu-id="68b75-120">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="68b75-121">请咨询安全顾问以获取进一步的指导。</span><span class="sxs-lookup"><span data-stu-id="68b75-121">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | <span data-ttu-id="68b75-122">对于大多数新式应用程序，不建议使用 HMACSHA1 算法。</span><span class="sxs-lookup"><span data-stu-id="68b75-122">The HMACSHA1 algorithm is discouraged for most modern applications.</span></span> <span data-ttu-id="68b75-123">如果可能，请考虑使用更强大的算法。</span><span class="sxs-lookup"><span data-stu-id="68b75-123">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="68b75-124">请咨询安全顾问以获取进一步的指导。</span><span class="sxs-lookup"><span data-stu-id="68b75-124">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> |

## <a name="see-also"></a><span data-ttu-id="68b75-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="68b75-125">See also</span></span>

- [<span data-ttu-id="68b75-126">加密中断性变更</span><span class="sxs-lookup"><span data-stu-id="68b75-126">Cryptography breaking changes</span></span>](cryptography.md#instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported)