---
title: 테이블 및 뷰 선택 (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.seltablesviews.f1
ms.assetid: 5e8121cc-03f0-4168-98cf-63c5c032bb0b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 891da51478670122f5dbce8fdd7be55c98c898c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738889"
---
# <a name="select-tables-and-views-ssas"></a><span data-ttu-id="5ac2d-102">테이블 및 뷰 선택(SSAS)</span><span class="sxs-lookup"><span data-stu-id="5ac2d-102">Select Tables and Views (SSAS)</span></span>
  <span data-ttu-id="5ac2d-103">**테이블 가져오기 마법사** 의 이 페이지에서는 가져올 데이터가 포함되어 있는 테이블과 뷰를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac2d-103">This page of the **Table Import Wizard** enables you to select the tables and views that you want to import data from.</span></span> <span data-ttu-id="5ac2d-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 마법사에 액세스하려면 **모델** 메뉴에서 **데이터 원본에서 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac2d-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="5ac2d-105">이 페이지에 테이블과 뷰가 표시되었다고 해서 가져오기 작업이 반드시 성공하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="5ac2d-105">The appearance of tables and views on this page does not guarantee that import will succeed.</span></span> <span data-ttu-id="5ac2d-106">가장 정보 페이지에 지정된 사용자에게 선택한 데이터베이스를 읽을 수 있는 권한이 없는 경우 가져오기 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac2d-106">If the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database, import will fail.</span></span>  
  
 <span data-ttu-id="5ac2d-107">Windows 인증을 사용하는 데이터 원본의 경우 현재 사용자의 자격 증명을 사용하여 테이블 및 뷰 선택 대화 상자에서 테이블 및 뷰를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5ac2d-107">For data sources using Windows authentication, the credentials of the current user are used to fetch the tables and views in the Select Tables and Views dialog.</span></span> <span data-ttu-id="5ac2d-108">기타 데이터 원본의 경우 연결 문자열에 제공된 자격 증명을 사용하여 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5ac2d-108">For other data sources, the credentials supplied in the connection string are used to fetch the data.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="5ac2d-109">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="5ac2d-109">UI element list</span></span>  
 <span data-ttu-id="5ac2d-110">**Server**</span><span class="sxs-lookup"><span data-stu-id="5ac2d-110">**Server**</span></span>  
 <span data-ttu-id="5ac2d-111">연결된 서버를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac2d-111">Displays the server that you are connected to.</span></span>  
  
 <span data-ttu-id="5ac2d-112">**Database**</span><span class="sxs-lookup"><span data-stu-id="5ac2d-112">**Database**</span></span>  
 <span data-ttu-id="5ac2d-113">선택한 데이터베이스를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac2d-113">Displays the database that you selected.</span></span>  
  
 <span data-ttu-id="5ac2d-114">**테이블 및 뷰**</span><span class="sxs-lookup"><span data-stu-id="5ac2d-114">**Tables and Views**</span></span>  
 <span data-ttu-id="5ac2d-115">데이터베이스의 테이블 및 뷰를 목록으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac2d-115">Lists the tables and views in the database.</span></span> <span data-ttu-id="5ac2d-116">가져올 각 테이블 및 뷰 옆의 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac2d-116">Select the checkbox beside each table and view that you want to import.</span></span>  
  
 <span data-ttu-id="5ac2d-117">**원본 테이블**</span><span class="sxs-lookup"><span data-stu-id="5ac2d-117">**Source Table**</span></span>  
 <span data-ttu-id="5ac2d-118">데이터 원본의 유형에 따라 원본 테이블의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac2d-118">Specifies the name of the source table based on the type of data source.</span></span>  
  
 <span data-ttu-id="5ac2d-119">**스키마**</span><span class="sxs-lookup"><span data-stu-id="5ac2d-119">**Schema**</span></span>  
 <span data-ttu-id="5ac2d-120">원본 테이블이 포함된 스키마를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac2d-120">Specifies the schema in which the source table is contained.</span></span> <span data-ttu-id="5ac2d-121">데이터베이스 유형에 따라 스키마는 테이블과 같은 다른 개체의 컨테이너로 작동하며 해당 개체의 소유권을 나타낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac2d-121">Depending on the type of database, a schema functions as a container for other objects, such as tables, and can also indicate ownership of those objects.</span></span>  
  
 <span data-ttu-id="5ac2d-122">**식별 이름**</span><span class="sxs-lookup"><span data-stu-id="5ac2d-122">**Friendly Name**</span></span>  
 <span data-ttu-id="5ac2d-123">원본 테이블의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac2d-123">Specifies the friendly name of the source table.</span></span> <span data-ttu-id="5ac2d-124">기본적으로 이 열에는 **원본 테이블** 열에 나타나는 원본 테이블의 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ac2d-124">By default, the column displays the name of the source table that appears in the **Source Table** column.</span></span> <span data-ttu-id="5ac2d-125">원본 데이터베이스에 사용된 것과 다른 이름을 사용하려면 이름을 변경하십시오.</span><span class="sxs-lookup"><span data-stu-id="5ac2d-125">Change the name if you want to use a different name than the name used in the source database.</span></span>  
  
 <span data-ttu-id="5ac2d-126">**필터 세부 정보**</span><span class="sxs-lookup"><span data-stu-id="5ac2d-126">**Filter Details**</span></span>  
 <span data-ttu-id="5ac2d-127">가져오고 있는 데이터에 필터가 적용된 경우 **필터 세부 정보** 대화 상자에 데이터 가져오기 필터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac2d-127">When a filter has been applied to the data that is being imported, displays the data import filter in the **Filter Details** dialog box.</span></span> <span data-ttu-id="5ac2d-128">자세한 내용은 [필터 세부 정보&#40;SSAS&#41;](filter-details-ssas.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5ac2d-128">For more information, see [Filter Details &#40;SSAS&#41;](filter-details-ssas.md).</span></span>  
  
 <span data-ttu-id="5ac2d-129">**미리 보기 및 필터**</span><span class="sxs-lookup"><span data-stu-id="5ac2d-129">**Preview and Filter**</span></span>  
 <span data-ttu-id="5ac2d-130">가져오고 있는 데이터에 필터를 적용하는 데 사용되는 **선택한 테이블 미리 보기** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac2d-130">Displays the **Preview Selected Table** dialog box that is used to apply a filter to the data that is being imported.</span></span> <span data-ttu-id="5ac2d-131">자세한 내용은 [선택한 테이블 미리 보기&#40;SSAS&#41;](preview-selected-table-ssas.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5ac2d-131">For more information, see [Preview Selected Table &#40;SSAS&#41;](preview-selected-table-ssas.md).</span></span>  
  
 <span data-ttu-id="5ac2d-132">**관련 테이블 선택**</span><span class="sxs-lookup"><span data-stu-id="5ac2d-132">**Select Related Tables**</span></span>  
 <span data-ttu-id="5ac2d-133">이미 선택한 테이블 및 뷰와 관련된 가져올 테이블 및 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac2d-133">Selects for import those tables and views that are related to the tables and views that you have already selected.</span></span>  
  
  
