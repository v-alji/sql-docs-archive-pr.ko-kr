---
title: 쿼리 바인딩 세부 정보 (파티션 원본 대화 상자) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitionfilterexpression.f1
ms.assetid: 697874d4-3f7a-4126-96f5-37cc8e2ee306
author: minewiskan
ms.author: owend
ms.openlocfilehash: 59d2ae1fed9d22366786e21a287a621f08418a5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651289"
---
# <a name="query-binding-detail-partition-source-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="a4d32-102">쿼리 바인딩 세부 정보(파티션 원본 대화 상자)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="a4d32-102">Query Binding Detail (Partition Source Dialog Box) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="a4d32-103">**파티션 원본** 대화 상자의 **쿼리 바인딩** 옵션을 사용하여 파티션에 대한 데이터를 제공하는 쿼리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4d32-103">Use the **Query Binding** option in the **Partition Source** dialog box to specify the query that provides the data for the partition.</span></span> <span data-ttu-id="a4d32-104">**파티션 원본** 대화 상자의 **바인딩 유형** 옵션에서 **쿼리 바인딩** 을 선택하여 이 창을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4d32-104">You can display this pane by selecting **Query Binding** from the **Binding type** option in the **Partition Source** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a4d32-105">옵션</span><span class="sxs-lookup"><span data-stu-id="a4d32-105">Options</span></span>  
 <span data-ttu-id="a4d32-106">**데이터 원본**</span><span class="sxs-lookup"><span data-stu-id="a4d32-106">**Data source**</span></span>  
 <span data-ttu-id="a4d32-107">파티션에 대한 팩트 데이터를 제공하기 위해 쿼리를 실행할 데이터 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a4d32-107">Select the data source on which the query is executed to provide fact data for the partition.</span></span>  
  
 <span data-ttu-id="a4d32-108">**쿼리**</span><span class="sxs-lookup"><span data-stu-id="a4d32-108">**Query**</span></span>  
 <span data-ttu-id="a4d32-109">파티션 처리 시 팩트 데이터를 검색할 때 사용되는 SQL 문을 입력하거나 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="a4d32-109">Type or modify the SQL statement used when retrieving fact data when the partition is processed.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a4d32-110">WHERE 절을 지정하여 레코드 하위 집합을 이 파티션에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4d32-110">By specifying a WHERE clause, a subset of records can be used for this partition.</span></span> <span data-ttu-id="a4d32-111">이것은 여러 개의 파티션이 단일 팩트 테이블을 기반으로 하는 경우 데이터 복제를 방지하기 위해 반드시 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a4d32-111">This is essential to prevent duplication of data when multiple partitions are based on a single fact table.</span></span> <span data-ttu-id="a4d32-112">자세한 내용은 [파티션 원본 대화 상자 &#40;Analysis Services 다차원 데이터&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a4d32-112">For more information, see [Partition Source Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="a4d32-113">**확인**</span><span class="sxs-lookup"><span data-stu-id="a4d32-113">**Check**</span></span>  
 <span data-ttu-id="a4d32-114">**쿼리** 의 문이 유효한 SQL 문인지 확인하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a4d32-114">Click to verify that the statement in **Query** is a valid SQL statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4d32-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a4d32-115">See Also</span></span>  
 [<span data-ttu-id="a4d32-116">파티션 원본 대화 상자 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="a4d32-116">Partition Source Dialog Box &#40;Analysis Services - Multidimensional Data&#41;</span></span>](partition-source-dialog-box-analysis-services-multidimensional-data.md)  
  
  
