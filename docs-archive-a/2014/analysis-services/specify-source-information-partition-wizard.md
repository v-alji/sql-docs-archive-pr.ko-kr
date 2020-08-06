---
title: 원본 정보 지정 (파티션 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.specifydsvandfacttables.f1
ms.assetid: b6c13587-c690-45d9-af90-b3d652afc55b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 088a8abf7b143b68766f22af37f8ff4fa2065d65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653544"
---
# <a name="specify-source-information-partition-wizard"></a><span data-ttu-id="40d38-102">원본 정보 지정(파티션 마법사)</span><span class="sxs-lookup"><span data-stu-id="40d38-102">Specify Source Information (Partition Wizard)</span></span>
  <span data-ttu-id="40d38-103">**원본 정보 지정** 페이지를 사용하여 파티션이 생성될 측정값 그룹과 파티션에 대한 데이터 원본 뷰를 선택할 수 있을 뿐만 아니라 파티션에 대한 테이블을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40d38-103">Use the **Specify Source Information** page to select the measure group in which to create the partition, and also the data source view and filter tables for your partition.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="40d38-104">**사용 가능한 테이블** 에서 다른 파티션에서 사용하는 테이블을 지정하는 경우 **행 제한** 페이지에서 쿼리를 제공하지 않으면 큐브의 데이터가 중복될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40d38-104">If you specify a table in **Available Tables** that is used by another partition, you must provide a query in the **Restrict Rows** page or risk duplicating data in the cube.</span></span>  
  
## <a name="options"></a><span data-ttu-id="40d38-105">옵션</span><span class="sxs-lookup"><span data-stu-id="40d38-105">Options</span></span>  
 <span data-ttu-id="40d38-106">**측정값 그룹**</span><span class="sxs-lookup"><span data-stu-id="40d38-106">**Measure group**</span></span>  
 <span data-ttu-id="40d38-107">이 파티션에 대한 측정값 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="40d38-107">Select a measure group for this partition.</span></span>  
  
 <span data-ttu-id="40d38-108">**찾는 위치**</span><span class="sxs-lookup"><span data-stu-id="40d38-108">**Look in**</span></span>  
 <span data-ttu-id="40d38-109">이 파티션의 원본 테이블이 들어 있는 데이터 원본 또는 데이터 원본 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="40d38-109">Select the data source or data source view that contains the source tables for this partition.</span></span> <span data-ttu-id="40d38-110">기본적으로 측정값 그룹에서 사용하는 데이터 원본 뷰가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="40d38-110">The data source view used by the measure group is selected by default.</span></span>  
  
 <span data-ttu-id="40d38-111">**테이블 필터**</span><span class="sxs-lookup"><span data-stu-id="40d38-111">**Filter tables**</span></span>  
 <span data-ttu-id="40d38-112">**사용 가능한 테이블**에 표시되는 테이블의 이름을 제한하는 데 사용할 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="40d38-112">Type the string used to restrict, by table name, the tables displayed in **Available tables**.</span></span>  
  
 <span data-ttu-id="40d38-113">**테이블 찾기**</span><span class="sxs-lookup"><span data-stu-id="40d38-113">**Find tables**</span></span>  
 <span data-ttu-id="40d38-114">**사용 가능한 테이블**의 테이블 목록을 새로 고치고 **테이블 필터**에 문자열이 지정된 경우 목록을 추가로 제한하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="40d38-114">Select to refresh the list of tables in **Available tables**, further restricting the list if a string was specified in **Filter tables**.</span></span>  
  
 <span data-ttu-id="40d38-115">**사용 가능한 테이블**</span><span class="sxs-lookup"><span data-stu-id="40d38-115">**Available tables**</span></span>  
 <span data-ttu-id="40d38-116">파티션의 원본 테이블로 사용할 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="40d38-116">Select the tables to use as source tables for partitions.</span></span> <span data-ttu-id="40d38-117">**파티션 마법사** 는 **사용 가능한 테이블**에서 선택한 각 테이블에 대해 하나의 파티션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="40d38-117">The **Partition Wizard** creates one partition for each table selected in **Available tables**.</span></span>  
  
 <span data-ttu-id="40d38-118">**테이블 필터**에서 필터를 지정하지 않으면 이 옵션은 **찾는 위치** 에서 지정한 것 중 **측정값 그룹**에서 지정한 측정값 그룹이 사용하는 팩트 테이블과 구조가 비슷한 데이터 원본 또는 데이터 원본 뷰의 모든 테이블을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="40d38-118">If no filter is specified in **Filter tables**, this option lists all tables in the data source or data source view that are specified in **Look in** and that are similar in structure to the fact table used by the measure group specified in **Measure group**.</span></span>  
  
 <span data-ttu-id="40d38-119">**테이블 필터**에서 필터를 지정하면 이전 조건을 만족하는 테이블 이름과 이 필터를 비교하여 목록을 보다 엄격하게 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="40d38-119">If a filter is specified in **Filter tables**, the list is further restricted by comparing the filter against the table names that meet the previous criteria.</span></span> <span data-ttu-id="40d38-120">**테이블 필터** 에 지정한 문자열을 포함하고 있는 테이블만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="40d38-120">Only those tables that contain the string specified in **Filter tables** are displayed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="40d38-121">테이블을 두 개 이상 선택하면 **행 제한** 페이지가 표시되지 않고 선택한 테이블에서 생성된 파티션에 대해 행을 제한할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="40d38-121">If more than one table is selected, the **Restrict Rows** page cannot be displayed and rows cannot be restricted for the partitions created from the selected tables.</span></span> <span data-ttu-id="40d38-122">각 파티션에 대한 행을 제한하려면 파티션이 생성될 각 테이블마다 파티션 마법사를 한 번씩 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="40d38-122">To restrict rows for each partition, run the Partition Wizard once for each table from which a partition is to be created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40d38-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="40d38-123">See Also</span></span>  
 [<span data-ttu-id="40d38-124">파티션&#40;Analysis Services - 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="40d38-124">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
