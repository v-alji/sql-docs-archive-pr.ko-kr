---
title: 올바른 선호도 마스크 및 선호도 입력 출력 마스크 겹침 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1a0da6df-57ff-4f3f-aae9-2fbc4897508c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 486b4441a20db7630082344fb1f277bba053f3ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743223"
---
# <a name="correct-affinity-mask-and-affinity-input-output-mask-overlap"></a><span data-ttu-id="22e51-102">올바른 선호도 마스크 및 선호도 입력 출력 마스크 겹침</span><span class="sxs-lookup"><span data-stu-id="22e51-102">Correct Affinity Mask and Affinity Input Output Mask Overlap</span></span>
  <span data-ttu-id="22e51-103">이 규칙은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 선호도 마스크 및 선호도 I/O 마스크 옵션을 모두 사용하도록 지정된 하나 이상의 프로세서가 있는지 여부를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="22e51-103">This rule checks whether the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has one or more processors that are assigned to be used with both the affinity mask and the affinity I/O mask options.</span></span> <span data-ttu-id="22e51-104">프로세서가 두 개 이상인 컴퓨터에서 선호도 마스크 및 선호도 I/O 마스크 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 사용되는 CPU를 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="22e51-104">On a computer that has more than one processor, the affinity mask and the affinity I/O mask options are used to designate which CPUs are used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="22e51-105">선호도 마스크 및 선호도 I/O 마스크를 모두 사용하도록 CPU를 지정하면 프로세서가 과도하게 사용되어 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22e51-105">Enabling a CPU with both the affinity mask and the affinity I/O mask can slow performance by forcing the processor to be overused.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="22e51-106">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="22e51-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="22e51-107">선호도 마스크 또는 선호도 I/O 마스크 옵션을 지정할 때는 두 옵션을 모두 지정하되 각 CPU를 한 번만 활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22e51-107">When you specify either the affinity mask or the affinity I/O mask options, you should specify both, but only enable each CPU no more than once.</span></span>  
  
 <span data-ttu-id="22e51-108">선호도 마스크 옵션과 선호도 I/O 마스크 옵션 모두에 대해 동일한 CPU를 활성화하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22e51-108">Do not enable the same CPU in both the affinity mask option and the affinity I/O mask option.</span></span> <span data-ttu-id="22e51-109">각 CPU에 해당하는 비트의 상태는 다음 중 하나여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22e51-109">The bits that correspond to each CPU should be in one of the following states:</span></span>  
  
-   <span data-ttu-id="22e51-110">선호도 마스크 옵션과 선호도 I/O 마스크 옵션에서 모두 0</span><span class="sxs-lookup"><span data-stu-id="22e51-110">0 in both the affinity mask option and the affinity I/O mask option</span></span>  
  
-   <span data-ttu-id="22e51-111">선호도 마스크 옵션에서는 0, 선호도 I/O 마스크 옵션에서는 1</span><span class="sxs-lookup"><span data-stu-id="22e51-111">0 in the affinity mask option and 1 in the affinity I/O mask option</span></span>  
  
-   <span data-ttu-id="22e51-112">선호도 마스크 옵션에서는 1, 선호도 I/O 마스크 옵션에서는 0</span><span class="sxs-lookup"><span data-stu-id="22e51-112">1 in the affinity mask option and 0 in the affinity I/O mask option</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="22e51-113">참조 항목</span><span class="sxs-lookup"><span data-stu-id="22e51-113">For More Information</span></span>  
 [<span data-ttu-id="22e51-114">선호도 마스크 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="22e51-114">affinity mask Server Configuration Option</span></span>](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)  
  
 [<span data-ttu-id="22e51-115">선호도 입력-출력 마스크 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="22e51-115">affinity Input-Output mask Server Configuration Option</span></span>](../../database-engine/configure-windows/affinity-input-output-mask-server-configuration-option.md)  
  
 [<span data-ttu-id="22e51-116">affinity64 mask 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="22e51-116">affinity64 mask Server Configuration Option</span></span>](../../database-engine/configure-windows/affinity64-mask-server-configuration-option.md)  
  
 [<span data-ttu-id="22e51-117">affinity64 Input-Output mask 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="22e51-117">affinity64 Input-Output mask Server Configuration Option</span></span>](../../database-engine/configure-windows/affinity64-input-output-mask-server-configuration-option.md)  
  
## <a name="see-also"></a><span data-ttu-id="22e51-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="22e51-118">See Also</span></span>  
 [<span data-ttu-id="22e51-119">정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용</span><span class="sxs-lookup"><span data-stu-id="22e51-119">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
