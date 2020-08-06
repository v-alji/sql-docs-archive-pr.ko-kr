---
title: 다른 팩트 테이블을 사용 하도록 파티션 원본 변경 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- fact tables [Analysis Services]
- partitions [Analysis Services], fact tables
ms.assetid: 5508312f-8e46-4802-9362-6688ca03d098
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0063a6023d769dc6dccd616655d10e0bd3c65a98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737155"
---
# <a name="change-a-partition-source-to-use-a-different-fact-table"></a><span data-ttu-id="d40c6-102">다른 팩트 테이블을 사용하도록 파티션 원본 변경</span><span class="sxs-lookup"><span data-stu-id="d40c6-102">Change a partition source to use a different fact table</span></span>
  <span data-ttu-id="d40c6-103">큐브에 대한 파티션을 만들 때 다양한 팩트 테이블을 사용하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d40c6-103">When you create a partition for a cube, you can choose to use a different fact table.</span></span> <span data-ttu-id="d40c6-104">이러한 테이블은 단일 데이터 원본 뷰, 여러 개의 데이터 원본 뷰 또는 여러 개의 데이터 원본에서 가져온 테이블일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d40c6-104">Different tables may be from a single data source view, from different data source views, or from different data sources.</span></span> <span data-ttu-id="d40c6-105">데이터 원본 뷰에는 둘 이상의 데이터 원본에서 가져온 여러 테이블이 포함될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d40c6-105">A data source view may also contain different tables from more than one data source.</span></span>  
  
 <span data-ttu-id="d40c6-106">큐브의 파티션에 대한 모든 팩트 테이블 및 차원은 해당 큐브의 팩트 테이블 및 차원과 구조가 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d40c6-106">All fact tables and dimensions for a cube's partitions must have the same structure as the fact table and dimensions of the cube.</span></span> <span data-ttu-id="d40c6-107">예를 들어 서로 다른 팩트 테이블이 구조는 같지만 서로 다른 연도나 제품 라인에 대한 데이터를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d40c6-107">For example, different fact tables can have the same structure but contain data for different years or different product lines.</span></span>  
  
 <span data-ttu-id="d40c6-108">파티션 마법사의 **원본 정보 지정** 페이지에서 팩트 테이블을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d40c6-108">You specify a fact table on the **Specify Source Information** page of the Partition Wizard.</span></span> <span data-ttu-id="d40c6-109">이 페이지의 **찾는 위치**옆의 파티션 원본 그룹에서 찾을 위치로 데이터 원본 또는 데이터 원본 뷰를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d40c6-109">On this page, in the Partition Source group next to **Look in**, specify a data source or data source view in which to look.</span></span> <span data-ttu-id="d40c6-110">다음으로 **테이블 찾기**를 클릭한 다음 **사용 가능한 테이블**에서 사용할 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d40c6-110">Next, click **Find Tables**, and then, under **Available Tables**, select the table you want to use.</span></span>  
  
 <span data-ttu-id="d40c6-111">여러 팩트 테이블을 사용하는 경우 파티션 간에 데이터가 중복되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d40c6-111">When you use different fact tables, ensure that no data is duplicated among the partitions.</span></span> <span data-ttu-id="d40c6-112">예를 들어 특정 팩트 테이블에는 2012년의 트랜잭션만 포함되고 다른 팩트 테이블에는 2013년의 트랜잭션만 포함되는 경우 두 테이블의 데이터는 서로 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="d40c6-112">For example, if one fact table contains transactions for 2012 only, and another fact table contains transactions for 2013 only, these tables contain independent data.</span></span> <span data-ttu-id="d40c6-113">마찬가지로 특정 제품 라인 또는 지리적인 특정 영역에 대한 팩트 테이블도 서로 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="d40c6-113">Similarly, fact tables for distinct product lines or distinct geographical areas are independent.</span></span>  
  
 <span data-ttu-id="d40c6-114">중복 데이터가 포함된 여러 개의 서로 다른 팩트 테이블을 사용할 수는 있지만 권장하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d40c6-114">It is possible, but not recommended, to use different fact tables that contain duplicated data.</span></span> <span data-ttu-id="d40c6-115">이러한 경우에는 파티션에서 필터를 사용하여 한 파티션에서 사용되는 데이터가 다른 어떤 파티션에서도 사용되지 않게 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d40c6-115">In this case, you must use filters in the partitions to ensure that data used by one partition is not used by any other partition.</span></span> <span data-ttu-id="d40c6-116">자세한 내용은 [로컬 파티션 만들기 및 관리&#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d40c6-116">For more information, see [Create and Manage a Local Partition &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d40c6-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d40c6-117">See Also</span></span>  
 [<span data-ttu-id="d40c6-118">로컬 파티션 만들기 및 관리&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d40c6-118">Create and Manage a Local Partition &#40;Analysis Services&#41;</span></span>](create-and-manage-a-local-partition-analysis-services.md)  
  
  
