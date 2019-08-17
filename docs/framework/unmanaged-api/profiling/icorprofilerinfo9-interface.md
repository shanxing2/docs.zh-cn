---
title: ICorProfilerInfo9 接口
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 0ba4f2b4a515143d50bc812f04ea75d821b69471
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973797"
---
# <a name="icorprofilerinfo9-interface"></a><span data-ttu-id="118b3-102">ICorProfilerInfo9 接口</span><span class="sxs-lookup"><span data-stu-id="118b3-102">ICorProfilerInfo9 Interface</span></span>

<span data-ttu-id="118b3-103">[ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)的子类, 提供用于查询有关具有多个本机代码版本的函数的信息的方法。</span><span class="sxs-lookup"><span data-stu-id="118b3-103">A subclass of [ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.</span></span>  

## <a name="methods"></a><span data-ttu-id="118b3-104">方法</span><span class="sxs-lookup"><span data-stu-id="118b3-104">Methods</span></span>  

| <span data-ttu-id="118b3-105">方法</span><span class="sxs-lookup"><span data-stu-id="118b3-105">Method</span></span>|<span data-ttu-id="118b3-106">描述</span><span class="sxs-lookup"><span data-stu-id="118b3-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="118b3-107">GetNativeCodeStartAddresses 方法</span><span class="sxs-lookup"><span data-stu-id="118b3-107">GetNativeCodeStartAddresses Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md)| <span data-ttu-id="118b3-108">给定一个 functionId 和 rejitId, 枚举此代码当前存在的所有实时编译版本的本机代码起始地址。</span><span class="sxs-lookup"><span data-stu-id="118b3-108">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span> |
|[<span data-ttu-id="118b3-109">GetILToNativeMapping3 方法</span><span class="sxs-lookup"><span data-stu-id="118b3-109">GetILToNativeMapping3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getiltonativemapping3-method.md)| <span data-ttu-id="118b3-110">给定本机代码起始地址, 返回此实时编译版本的代码的本机到 IL 映射信息。</span><span class="sxs-lookup"><span data-stu-id="118b3-110">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span> |
|[<span data-ttu-id="118b3-111">GetCodeInfo4 方法</span><span class="sxs-lookup"><span data-stu-id="118b3-111">GetCodeInfo4 Method</span></span>](icorprofilerinfo9-getcodeinfo4-method.md)| <span data-ttu-id="118b3-112">给定本机代码起始地址, 返回存储此代码的虚拟内存块。</span><span class="sxs-lookup"><span data-stu-id="118b3-112">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span> |

## <a name="requirements"></a><span data-ttu-id="118b3-113">要求</span><span class="sxs-lookup"><span data-stu-id="118b3-113">Requirements</span></span>  
<span data-ttu-id="118b3-114">**适用**请参阅[支持 .Net Core 的操作系统](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)。</span><span class="sxs-lookup"><span data-stu-id="118b3-114">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
<span data-ttu-id="118b3-115">**标头：** Corprof.idl, Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="118b3-115">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="118b3-116">**.Net 版本:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="118b3-116">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span></span>  
## <a name="see-also"></a><span data-ttu-id="118b3-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="118b3-117">See also</span></span>
- [<span data-ttu-id="118b3-118">Profiling 接口</span><span class="sxs-lookup"><span data-stu-id="118b3-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)