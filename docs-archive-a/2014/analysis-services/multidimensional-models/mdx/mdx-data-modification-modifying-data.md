---
title: 데이터 수정 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying data [MDX]
- Multidimensional Expressions [Analysis Services], data modifications
- MDX [Analysis Services], data modifications
- data modifications [MDX]
ms.assetid: 363b662c-b839-4971-bbd7-1842f73ce141
author: minewiskan
ms.author: owend
ms.openlocfilehash: 01df67471753922e3e7db39c56a9ed50aae900dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651921"
---
# <a name="modifying-data-mdx"></a><span data-ttu-id="cb456-102">데이터 수정(MDX)</span><span class="sxs-lookup"><span data-stu-id="cb456-102">Modifying Data (MDX)</span></span>
  <span data-ttu-id="cb456-103">MDX를 사용하여 차원과 큐브의 데이터를 검색하고 처리하는 방법 외에도, MDX를 사용하여 차원과 큐브 데이터를 업데이트하거나 *쓰기 저장* 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb456-103">Besides using Multidimensional Expressions (MDX) to retrieve and handle data from dimensions and cubes, you can use MDX to update or *writeback* dimension and cube data.</span></span> <span data-ttu-id="cb456-104">이 업데이트는 이론적 분석이나 "가정(what if)" 분석에서와 같이 임시적이거나 데이터 분석을 기반으로 변화가 발생해야 하는 때와 같이 영구적일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb456-104">These updates can be temporary, as with speculative, or "what if", analysis, or permanent, as when changes must occur based upon data analysis.</span></span>  
  
 <span data-ttu-id="cb456-105">데이터에 대한 업데이트는 차원 또는 큐브 수준에서 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb456-105">Updates to data can occur at the dimension or cube level:</span></span>  
  
 <span data-ttu-id="cb456-106">**차원 쓰기 저장**</span><span class="sxs-lookup"><span data-stu-id="cb456-106">**Dimension writebacks**</span></span>  
 <span data-ttu-id="cb456-107">쓰기 가능한 차원의 데이터를 변경하려면 [ALTER CUBE 문(MDX)](/sql/mdx/mdx-data-definition-alter-cube) 을 사용하고, 특성 값의 삭제, 생성 및 업데이트를 반영하려면 [REFRESH CUBE 문(MDX)](/sql/mdx/mdx-data-definition-refresh-cube) 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cb456-107">You use the [ALTER CUBE Statement (MDX)](/sql/mdx/mdx-data-definition-alter-cube) statement to change a write-enabled dimension's data and the [REFRESH CUBE Statement (MDX)](/sql/mdx/mdx-data-definition-refresh-cube) to reflect the deletion, creation, and updating of attribute values.</span></span> <span data-ttu-id="cb456-108">ALTER CUBE 문을 사용하여 계층의 전체 하위 트리를 삭제하고 삭제된 멤버의 자식을 승격시키는 것과 같은 복잡한 연산을 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb456-108">You can also use the ALTER CUBE statement to perform complex operations, such as deleting a whole sub-tree in a hierarchy and promoting the children of a deleted member.</span></span>  
  
 <span data-ttu-id="cb456-109">**큐브 쓰기 저장**</span><span class="sxs-lookup"><span data-stu-id="cb456-109">**Cube writebacks**</span></span>  
 <span data-ttu-id="cb456-110">쓰기 가능한 큐브를 업데이트하려면 [UPDATE CUBE](/sql/mdx/mdx-data-manipulation-update-cube) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cb456-110">You use the [UPDATE CUBE](/sql/mdx/mdx-data-manipulation-update-cube) statement to make updates to a write-enabled cube.</span></span> <span data-ttu-id="cb456-111">UPDATE CUBE 문을 사용하여 특정 값을 가진 튜플을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb456-111">The UPDATE CUBE statement lets you update a tuple with a specific value.</span></span> <span data-ttu-id="cb456-112">서버의 업데이트된 데이터로 클라이언트 세션의 데이터를 새로 고치려면 [REFRESH CUBE 문(MDX)](/sql/mdx/mdx-data-definition-refresh-cube) 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cb456-112">You use the [REFRESH CUBE Statement (MDX)](/sql/mdx/mdx-data-definition-refresh-cube) to refresh data in a client session with updated data from the server.</span></span>  
  
 <span data-ttu-id="cb456-113">자세한 내용은 [큐브 쓰기 저장 사용&#40;MDX&#41;](mdx-data-modification-using-cube-writebacks.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb456-113">For more information, see [Using Cube Writebacks &#40;MDX&#41;](mdx-data-modification-using-cube-writebacks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb456-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cb456-114">See Also</span></span>  
 [<span data-ttu-id="cb456-115">MDX 쿼리 기본 사항&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cb456-115">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
