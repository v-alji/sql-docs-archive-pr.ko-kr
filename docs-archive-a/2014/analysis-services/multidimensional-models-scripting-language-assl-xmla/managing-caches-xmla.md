---
title: 캐시 관리 (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XMLA, cache
- XML for Analysis, cache
- clearing cache
- cache [Analysis Services]
ms.assetid: afad5c39-d4c3-4307-b3b9-a06617da0028
author: minewiskan
ms.author: owend
ms.openlocfilehash: cdc5bcd2e0500749edfa298a871b6fec7243ddfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649770"
---
# <a name="managing-caches-xmla"></a><span data-ttu-id="a1128-102">캐시 관리(XMLA)</span><span class="sxs-lookup"><span data-stu-id="a1128-102">Managing Caches (XMLA)</span></span>
  <span data-ttu-id="a1128-103">XML for Analysis (XMLA)의 [clearcache](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/clearcache-element-xmla) 명령을 사용 하 여 지정 된 차원 또는 파티션의 캐시를 지울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1128-103">You can use the [ClearCache](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/clearcache-element-xmla) command in XML for Analysis (XMLA) to clear the cache of a specified dimension or partition.</span></span> <span data-ttu-id="a1128-104">캐시를 지우면 강제로 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 해당 개체에 대 한 캐시를 다시 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="a1128-104">Clearing the cache forces [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to rebuild the cache for that object.</span></span>  
  
## <a name="specifying-objects"></a><span data-ttu-id="a1128-105">개체 지정</span><span class="sxs-lookup"><span data-stu-id="a1128-105">Specifying Objects</span></span>  
 <span data-ttu-id="a1128-106">명령의 [개체](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) 속성은 `ClearCache` 다음 개체 중 하나에 대 한 개체 참조만 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1128-106">The [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) property of the `ClearCache` command can contain an object reference only for one of the following objects.</span></span> <span data-ttu-id="a1128-107">따라서 다음 개체 이외의 다른 개체에 대한 개체 참조인 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a1128-107">An error occurs if an object reference is for an object other than one of following objects:</span></span>  
  
 <span data-ttu-id="a1128-108">데이터베이스</span><span class="sxs-lookup"><span data-stu-id="a1128-108">Database</span></span>  
 <span data-ttu-id="a1128-109">데이터베이스 내의 모든 차원 및 파티션에 대한 캐시를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="a1128-109">Clears the cache for all dimensions and partitions contained in the database.</span></span>  
  
 <span data-ttu-id="a1128-110">차원</span><span class="sxs-lookup"><span data-stu-id="a1128-110">Dimension</span></span>  
 <span data-ttu-id="a1128-111">지정된 차원에 대한 캐시를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="a1128-111">Clears the cache for the specified dimension.</span></span>  
  
 <span data-ttu-id="a1128-112">큐브</span><span class="sxs-lookup"><span data-stu-id="a1128-112">Cube</span></span>  
 <span data-ttu-id="a1128-113">큐브의 측정값 그룹에 포함된 모든 파티션에 대한 캐시를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="a1128-113">Clears the cache for all partitions contained in the measure groups for the cube.</span></span>  
  
 <span data-ttu-id="a1128-114">측정값 그룹</span><span class="sxs-lookup"><span data-stu-id="a1128-114">Measure group</span></span>  
 <span data-ttu-id="a1128-115">측정값 그룹에 포함된 모든 파티션에 대한 캐시를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="a1128-115">Clears the cache for all partitions contained in the measure group.</span></span>  
  
 <span data-ttu-id="a1128-116">파티션</span><span class="sxs-lookup"><span data-stu-id="a1128-116">Partition</span></span>  
 <span data-ttu-id="a1128-117">지정된 파티션에 대한 캐시를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="a1128-117">Clears the cache for the specified partition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1128-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1128-118">See Also</span></span>  
 [<span data-ttu-id="a1128-119">Analysis Services에서 XMLA를 사용하여 개발</span><span class="sxs-lookup"><span data-stu-id="a1128-119">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
