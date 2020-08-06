---
title: access check cache 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- access check cache option
- access check cache bucket count
- access check cache quota
ms.assetid: 0a992ea8-3ec6-4a4d-97b5-460ae7326247
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: feed895eeb7b11b4c41c51c4c26859a1057d2733
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638996"
---
# <a name="access-check-cache-server-configuration-options"></a><span data-ttu-id="7e09e-102">access check cache 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="7e09e-102">access check cache Server Configuration Options</span></span>
<span data-ttu-id="7e09e-103">데이터베이스 개체를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 액세스할 때 액세스 검사는 **access check result cache**라는 내부 구조에 캐시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e09e-103">When database objects are accessed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the access check is cached in an internal structure called the **access check result cache**.</span></span> 
  
<span data-ttu-id="7e09e-104">**액세스 검사 캐시 버킷 수** 옵션은 액세스 검사 결과 캐시에 사용되는 해시 버킷의 수를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="7e09e-104">The **access check cache bucket count** option controls the number of hash buckets that are used for the access check result cache.</span></span> 

<span data-ttu-id="7e09e-105">**액세스 검사 캐시 할당량** 옵션은 액세스 검사 결과 캐시에 저장된 항목 수를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="7e09e-105">The **access check cache quota** option controls the number of entries that are stored in the access check result cache.</span></span> <span data-ttu-id="7e09e-106">최대 항목 수에 도달하면 가장 오래된 항목이 액세스 검사 결과 캐시에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e09e-106">When the maximum number of entries is reached, the oldest entries are removed from the access check result cache.</span></span>
  
<span data-ttu-id="7e09e-107">기본값 0은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 이러한 옵션을 관리함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7e09e-107">The default values of 0 indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is managing these options.</span></span> <span data-ttu-id="7e09e-108">부터 [!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)] 의 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 기본값은 다음 내부 구성으로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e09e-108">From [!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)] through [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], the default values translate to the following internal configurations:</span></span>
-   <span data-ttu-id="7e09e-109">액세스 검사 캐시 버킷 수의 경우 값 0은 x86 아키텍처의 경우 256 버킷을, x64 및 IA-64 아키텍처의 경우 2048 버킷을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e09e-109">For access check cache bucket count, the value 0 sets a default value of 256 buckets for x86 architecture, and 2,048 buckets for x64 and IA-64 architectures.</span></span>
-   <span data-ttu-id="7e09e-110">액세스 검사 캐시 할당량의 경우 값 0은 x86 아키텍처의 경우 1024 항목, x64 및 IA-64 아키텍처의 경우 28192048 버킷에 대 한 기본값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e09e-110">For access check cache quota, the value 0 sets a default value of 1,024 entries for x86 architecture, and 28,192,048 buckets for x64 and IA-64 architectures.</span></span>

<span data-ttu-id="7e09e-111">드문 경우지만 이러한 옵션을 변경하여 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e09e-111">In rare circumstances, performance can be improved by changing these options.</span></span> <span data-ttu-id="7e09e-112">예를 들어 너무 많은 메모리가 사용되는 경우 액세스 검사 결과 캐시의 크기를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e09e-112">For example, you may want to reduce the size of the access check result cache if too much memory is used.</span></span> <span data-ttu-id="7e09e-113">또는 사용 권한이 다시 계산될 때 높은 CPU 사용량이 발생하는 경우 액세스 검사 결과 캐시의 크기를 늘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e09e-113">Or, you may want to increase the size of the access check result cache if you experience high CPU usage when permissions are recalculated.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7e09e-114">이러한 옵션은 Microsoft 고객 지원 서비스에서 안내하는 경우에만 변경하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7e09e-114">Microsoft recommends only changing these options when directed by Microsoft Customer Support Services.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7e09e-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7e09e-115">See Also</span></span>  
 <span data-ttu-id="7e09e-116">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7e09e-116">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="7e09e-117">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7e09e-117">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
