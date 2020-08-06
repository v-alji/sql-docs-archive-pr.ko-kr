---
title: 증분 업데이트 대화 상자 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.incrementalupdate.f1
ms.assetid: d5a5ae27-44e7-4179-b9e2-efbf21d6c5f5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6115a5123fd6e72cee0ebccaac5f539be8aebfbe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660184"
---
# <a name="incremental-update-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="aa192-102">증분 업데이트 대화 상자(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="aa192-102">Incremental Update Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="aa192-103">**및** 의 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 증분 업데이트 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 대화 상자를 사용하여 측정값 그룹과 파티션을 증분 업데이트할 때 사용할 설정을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa192-103">Use the **Incremental Update** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to define the settings that are used when measure groups and partitions are incrementally updated.</span></span> <span data-ttu-id="aa192-104">**처리** 대화 상자에서 **개체 목록** 표의 **설정** 열에 있는 **구성** 을 클릭하여 **증분 업데이트** 대화 상자를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa192-104">You can display the **Incremental Update** dialog box by clicking **Configure** in the **Settings** column of the **Object list** grid in the **Process** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="aa192-105">옵션</span><span class="sxs-lookup"><span data-stu-id="aa192-105">Options</span></span>  
  
|<span data-ttu-id="aa192-106">용어</span><span class="sxs-lookup"><span data-stu-id="aa192-106">Term</span></span>|<span data-ttu-id="aa192-107">정의</span><span class="sxs-lookup"><span data-stu-id="aa192-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="aa192-108">**측정값 그룹**</span><span class="sxs-lookup"><span data-stu-id="aa192-108">**Measure Group**</span></span>|<span data-ttu-id="aa192-109">증분 업데이트할 측정값 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aa192-109">Select the measure group to incrementally update.</span></span><br /><br /> <span data-ttu-id="aa192-110">참고: 이 옵션은 큐브를 증분 업데이트하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa192-110">Note: This option is enabled only if you are incrementally updating a cube.</span></span> <span data-ttu-id="aa192-111">측정값 그룹이나 파티션을 증분 업데이트하는 경우에는 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aa192-111">If you are incrementally updating a measure group or partition, this option is disabled.</span></span>|  
|<span data-ttu-id="aa192-112">**파티션**</span><span class="sxs-lookup"><span data-stu-id="aa192-112">**Partition**</span></span>|<span data-ttu-id="aa192-113">업데이트할 파티션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aa192-113">Select the partition to update.</span></span><br /><br /> <span data-ttu-id="aa192-114">참고: 이 옵션은 큐브를 증분 업데이트하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa192-114">Note: This option is enabled only if you are incrementally updating a cube.</span></span> <span data-ttu-id="aa192-115">측정값 그룹이나 파티션을 증분 업데이트하는 경우에는 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aa192-115">If you are incrementally updating a measure group or partition, this option is disabled.</span></span>|  
|<span data-ttu-id="aa192-116">**테이블**</span><span class="sxs-lookup"><span data-stu-id="aa192-116">**Table**</span></span>|<span data-ttu-id="aa192-117">테이블의 개체를 업데이트하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aa192-117">Click to update the object from a table.</span></span>|  
|<span data-ttu-id="aa192-118">**데이터 원본 또는 뷰**</span><span class="sxs-lookup"><span data-stu-id="aa192-118">**Data source or view**</span></span>|<span data-ttu-id="aa192-119">원본 테이블이 들어 있는 데이터 원본 또는 데이터 원본 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aa192-119">Select the data source or data source view in which the source table is located.</span></span><br /><br /> <span data-ttu-id="aa192-120">참고: 이 옵션은 **테이블** 을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa192-120">Note: This option is enabled only if **Table** is selected.</span></span>|  
|<span data-ttu-id="aa192-121">**테이블 스키마 및 이름**</span><span class="sxs-lookup"><span data-stu-id="aa192-121">**Table schema and name**</span></span>|<span data-ttu-id="aa192-122">큐브, 측정값 그룹 또는 파티션을 증분 업데이트하는 데 필요한 데이터 검색에 사용할 원본 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aa192-122">Select the source table used to retrieve data for incrementally updating the cube, measure group, or partition.</span></span><br /><br /> <span data-ttu-id="aa192-123">참고: 이 옵션은 **테이블** 을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa192-123">Note: This option is enabled only if **Table** is selected.</span></span>|  
|<span data-ttu-id="aa192-124">**쿼리**</span><span class="sxs-lookup"><span data-stu-id="aa192-124">**Query**</span></span>|<span data-ttu-id="aa192-125">쿼리의 개체를 업데이트하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aa192-125">Click to update the object from a query.</span></span>|  
|<span data-ttu-id="aa192-126">**데이터 원본**</span><span class="sxs-lookup"><span data-stu-id="aa192-126">**Data Source**</span></span>|<span data-ttu-id="aa192-127">쿼리할 테이블이 들어 있는 데이터 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aa192-127">Select the data source in which the tables to be queried are located.</span></span><br /><br /> <span data-ttu-id="aa192-128">참고: 이 옵션은 **쿼리** 를 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa192-128">Note: This option is enabled only if **Query** is selected.</span></span>|  
|<span data-ttu-id="aa192-129">**쿼리 텍스트**</span><span class="sxs-lookup"><span data-stu-id="aa192-129">**Text of the query**</span></span>|<span data-ttu-id="aa192-130">큐브, 측정값 그룹 또는 파티션을 증분 업데이트하는 데 필요한 데이터 검색에 사용할 쿼리 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aa192-130">Type the text of the query used to retrieve data for incrementally updating the cube, measure group, or partition.</span></span><br /><br /> <span data-ttu-id="aa192-131">참고: 이 옵션은 **쿼리** 를 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa192-131">Note: This option is enabled only if **Query** is selected.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aa192-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aa192-132">See Also</span></span>  
 <span data-ttu-id="aa192-133">[Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="aa192-133">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="aa192-134">처리 대화 상자 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="aa192-134">Process Dialog Box &#40;Analysis Services - Multidimensional Data&#41;</span></span>](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  
