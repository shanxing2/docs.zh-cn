---
title: ICorProfilerInfo9::GetILToNativeMapping3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetILToNativeMapping3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 46ceef43806fda9956797935c5eeec61f865dc6e
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973787"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a><span data-ttu-id="b3281-102">ICorProfilerInfo9:: GetILToNativeMapping3 方法</span><span class="sxs-lookup"><span data-stu-id="b3281-102">ICorProfilerInfo9::GetILToNativeMapping3 Method</span></span>
  
 <span data-ttu-id="b3281-103">给定本机代码起始地址, 返回此实时编译版本的代码的本机到 IL 映射信息。</span><span class="sxs-lookup"><span data-stu-id="b3281-103">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span>   
  
## <a name="syntax"></a><span data-ttu-id="b3281-104">语法</span><span class="sxs-lookup"><span data-stu-id="b3281-104">Syntax</span></span>  
  
```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```  
  
#### <a name="parameters"></a><span data-ttu-id="b3281-105">参数</span><span class="sxs-lookup"><span data-stu-id="b3281-105">Parameters</span></span>  
 `pNativeCodeStartAddress` \
 <span data-ttu-id="b3281-106">中指向本机函数开头的指针。</span><span class="sxs-lookup"><span data-stu-id="b3281-106">[in] A pointer to the start of a native function.</span></span>

 `cMap` \
 <span data-ttu-id="b3281-107">[in] `map` 数组的最大大小。</span><span class="sxs-lookup"><span data-stu-id="b3281-107">[in] The maximum size of the `map` array.</span></span> 

 `pcMap` \
 <span data-ttu-id="b3281-108">弄可用的 COR_DEBUG_IL_TO_NATIVE_MAP 结构总数。</span><span class="sxs-lookup"><span data-stu-id="b3281-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>

 `map` \
 <span data-ttu-id="b3281-109">弄[COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md)结构的数组, 其中每个结构都指定了偏移量。</span><span class="sxs-lookup"><span data-stu-id="b3281-109">[out] An array of [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) structures, each of which specifies the offsets.</span></span> <span data-ttu-id="b3281-110">          `GetILToNativeMapping3` 方法返回后，`map` 将包含部分或全部 `COR_DEBUG_IL_TO_NATIVE_MAP` 结构。</span><span class="sxs-lookup"><span data-stu-id="b3281-110">After the `GetILToNativeMapping3` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>

## <a name="remarks"></a><span data-ttu-id="b3281-111">备注</span><span class="sxs-lookup"><span data-stu-id="b3281-111">Remarks</span></span>  
 <span data-ttu-id="b3281-112">当启用分层编译时, 一个方法可能有多个本机代码体。</span><span class="sxs-lookup"><span data-stu-id="b3281-112">When tiered compilation is enabled, a method may have more than one native code body.</span></span> <span data-ttu-id="b3281-113">[ICorProfilerInfo9:: GetNativeCodeStartAddresses](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md)将返回所有本机代码正文的开始地址。</span><span class="sxs-lookup"><span data-stu-id="b3281-113">[ICorProfilerInfo9::GetNativeCodeStartAddresses](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md) will return the start addresses for all of the native code bodies.</span></span>

## <a name="requirements"></a><span data-ttu-id="b3281-114">要求</span><span class="sxs-lookup"><span data-stu-id="b3281-114">Requirements</span></span>  
 <span data-ttu-id="b3281-115">**适用**请参阅[支持 .Net Core 的操作系统](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)。</span><span class="sxs-lookup"><span data-stu-id="b3281-115">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="b3281-116">**标头：** Corprof.idl, Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="b3281-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b3281-117">**类库**CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3281-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3281-118">**.NET Framework 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3281-118">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="b3281-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="b3281-119">See also</span></span>
- [<span data-ttu-id="b3281-120">ICorProfilerInfo9 接口</span><span class="sxs-lookup"><span data-stu-id="b3281-120">ICorProfilerInfo9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)
