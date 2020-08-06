---
title: 네트워크 패킷 크기는 8060바이트를 초과할 수 없음 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 86db5da1-afe4-4fbb-8bf8-33cedc7e4361
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 01b500cbe65107767d73bc2901b6d5e028b94ee9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648997"
---
# <a name="network-packet-size-should-not-exceed-8060-bytes"></a><span data-ttu-id="29428-102">네트워크 패킷 크기는 8060바이트를 초과할 수 없음</span><span class="sxs-lookup"><span data-stu-id="29428-102">Network Packet Size Should Not Exceed 8060 Bytes</span></span>
  <span data-ttu-id="29428-103">sp_configure 'network packet size'에 지정된 값 또는 로그인된 사용자의 네트워크 패킷 크기가 8060바이트보다 큰 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 서로 다른 메모리 할당 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="29428-103">If the value specified for sp_configure 'network packet size' or if the network packet size of any logged-in user is more than 8060 bytes, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs different memory allocation operations.</span></span> <span data-ttu-id="29428-104">그 결과 버퍼 풀에 예약되지 않는 프로세스 가상 주소 공간이 증가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29428-104">This can cause an increase in the process virtual address space that is not reserved for the buffer pool.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="29428-105">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="29428-105">Best Practices Recommendations</span></span>  
 <span data-ttu-id="29428-106">네트워크 패킷 크기는 8060바이트를 초과하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="29428-106">The network packet size should not exceed 8060 bytes.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="29428-107">참조 항목</span><span class="sxs-lookup"><span data-stu-id="29428-107">For More Information</span></span>  
 [<span data-ttu-id="29428-108">Microsoft 기술 자료 문서 903002</span><span class="sxs-lookup"><span data-stu-id="29428-108">Microsoft Knowledge Base article 903002</span></span>](https://go.microsoft.com/fwlink/?linkid=117749)  
  
## <a name="see-also"></a><span data-ttu-id="29428-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="29428-109">See Also</span></span>  
 [<span data-ttu-id="29428-110">정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용</span><span class="sxs-lookup"><span data-stu-id="29428-110">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
