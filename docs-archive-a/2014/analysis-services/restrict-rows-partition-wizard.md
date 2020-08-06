---
title: 행 제한 (파티션 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.typefilterexpression.f1
ms.assetid: eec8da8f-eab4-4ac4-a81d-995c814f88ca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b0acc9ab24cfe92877d9abcd86353c85b4f8905
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647937"
---
# <a name="restrict-rows-partition-wizard"></a><span data-ttu-id="449b3-102">행 제한(파티션 마법사)</span><span class="sxs-lookup"><span data-stu-id="449b3-102">Restrict Rows (Partition Wizard)</span></span>
  <span data-ttu-id="449b3-103">**행 제한** 페이지를 사용하여 지정한 테이블에서 검색한 다음 집계하여 파티션에 포함시킬 행을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="449b3-103">Use the **Restrict Rows** page to restrict the rows that will be retrieved from the specified table and will be aggregated and included in the partition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="449b3-104"> 이 페이지는 **원본 정보 지정** 페이지에서 단일 테이블을 선택한 경우에만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="449b3-104">This page is appears only if you selected a single table in the **Specify Source Information** page.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="449b3-105">**원본 정보 지정** 페이지의 **사용 가능한 테이블** 에서 다른 파티션이 사용하는 테이블을 지정한 경우 **행 제한** 페이지에서 쿼리를 제공하지 않으면 큐브에서 데이터가 중복될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="449b3-105">If you specified a table in **Available Tables** on the **Specify Source Information** page that is used by another partition, you must provide a query in the **Restrict Rows** page or risk duplicating data in the cube.</span></span>  
  
## <a name="options"></a><span data-ttu-id="449b3-106">옵션</span><span class="sxs-lookup"><span data-stu-id="449b3-106">Options</span></span>  
 <span data-ttu-id="449b3-107">**행을 제한하는 쿼리 지정**</span><span class="sxs-lookup"><span data-stu-id="449b3-107">**Specify a query to restrict rows**</span></span>  
 <span data-ttu-id="449b3-108">행을 제한하는 쿼리를 **쿼리** 입력란에 입력하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="449b3-108">Select to enter a query that restricts rows into the **Query** box.</span></span>  
  
 <span data-ttu-id="449b3-109">이 옵션을 선택할 때 **WHERE 절 제공** 이 비어 있으면 이전에 선택한 테이블에서 모든 열과 모든 행을 검색하는 SQL 문으로 해당 옵션이 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="449b3-109">If **Supply a WHERE clause** is empty when this option is selected, that option is populated with an SQL statement that retrieves all columns and all rows from the previously selected table.</span></span>  
  
 <span data-ttu-id="449b3-110">**쿼리**</span><span class="sxs-lookup"><span data-stu-id="449b3-110">**Query**</span></span>  
 <span data-ttu-id="449b3-111">파티션 처리 시 테이블에서 행을 검색할 때 사용되는 SQL 문을 입력하거나 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="449b3-111">Type or modify the SQL statement used when retrieving rows from the table when the partition is processed.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="449b3-112">WHERE 절을 지정하여 레코드 하위 집합을 이 파티션에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="449b3-112">By specifying a WHERE clause, a subset of records can be used for this partition.</span></span> <span data-ttu-id="449b3-113">이것은 여러 개의 파티션이 단일 팩트 테이블을 기반으로 하는 경우 데이터 복제를 방지하기 위해 반드시 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="449b3-113">This is essential to prevent duplication of data when multiple partitions are based on a single fact table.</span></span>  
  
 <span data-ttu-id="449b3-114">**확인**</span><span class="sxs-lookup"><span data-stu-id="449b3-114">**Check**</span></span>  
 <span data-ttu-id="449b3-115">**쿼리** 의 문이 유효한 SQL 문인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="449b3-115">Verifies that the statement in **Query** is a valid SQL statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="449b3-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="449b3-116">See Also</span></span>  
 [<span data-ttu-id="449b3-117">파티션&#40;Analysis Services - 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="449b3-117">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
