---
title: 테이블 및 뷰 선택 (데이터 피드) (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.seltablesviewsdf.f1
ms.assetid: 6c4fafe0-e02e-47d1-b8bc-e70e872690af
author: minewiskan
ms.author: owend
ms.openlocfilehash: 46c317ecf2a87adcde264e8d6d7e822eb833b8b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649717"
---
# <a name="select-tables-and-views-data-feeds-ssas"></a><span data-ttu-id="e6c5c-102">테이블 및 뷰 선택(데이터 피드)(SSAS)</span><span class="sxs-lookup"><span data-stu-id="e6c5c-102">Select Tables and Views (Data Feeds) (SSAS)</span></span>
  <span data-ttu-id="e6c5c-103">**테이블 가져오기 마법사** 의 이 페이지에서는 가져올 데이터가 포함되어 있는 테이블과 뷰를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6c5c-103">This page of the **Table Import Wizard** enables you to select the tables and views that you want to import data from.</span></span> <span data-ttu-id="e6c5c-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 마법사에 액세스하려면 **모델** 메뉴에서 **데이터 원본에서 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c5c-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="e6c5c-105">이 페이지에 테이블과 뷰가 표시되었다고 해서 가져오기 작업이 반드시 성공하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="e6c5c-105">The appearance of tables and views on this page does not guarantee that import will succeed.</span></span> <span data-ttu-id="e6c5c-106">가장 정보 페이지에 지정된 사용자에게 선택한 데이터베이스를 읽을 수 있는 권한이 없는 경우 가져오기 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c5c-106">If the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database, import will fail.</span></span>  
  
 <span data-ttu-id="e6c5c-107">Windows 인증을 사용하는 데이터 원본의 경우 현재 사용자의 자격 증명을 사용하여 테이블 및 뷰 선택 대화 상자에서 테이블 및 뷰를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e6c5c-107">For data sources using Windows authentication, the credentials of the current user are used to fetch the tables and views in the Select Tables and Views dialog.</span></span> <span data-ttu-id="e6c5c-108">기타 데이터 원본의 경우 연결 문자열에 제공된 자격 증명을 사용하여 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e6c5c-108">For other data sources, the credentials supplied in the connection string are used to fetch the data.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="e6c5c-109">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="e6c5c-109">UI element list</span></span>  
 <span data-ttu-id="e6c5c-110">**데이터 피드 URL**</span><span class="sxs-lookup"><span data-stu-id="e6c5c-110">**Data feed URL**</span></span>  
 <span data-ttu-id="e6c5c-111">선택한 데이터 피드의 URL을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c5c-111">Displays the URL for the data feed that you selected.</span></span>  
  
 <span data-ttu-id="e6c5c-112">**테이블 및 뷰**</span><span class="sxs-lookup"><span data-stu-id="e6c5c-112">**Tables and views**</span></span>  
 <span data-ttu-id="e6c5c-113">데이터 피드의 테이블 및 뷰를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c5c-113">Lists the tables and views in the data feed.</span></span> <span data-ttu-id="e6c5c-114">가져올 각 테이블 및 뷰 옆의 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c5c-114">Select the checkbox beside each table and view that you want to import.</span></span>  
  
 <span data-ttu-id="e6c5c-115">**원본 테이블**</span><span class="sxs-lookup"><span data-stu-id="e6c5c-115">**Source Table**</span></span>  
 <span data-ttu-id="e6c5c-116">데이터 원본의 유형에 따라 원본 테이블의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c5c-116">Specifies the name of the source table based on the type of data source.</span></span>  
  
 <span data-ttu-id="e6c5c-117">**식별 이름**</span><span class="sxs-lookup"><span data-stu-id="e6c5c-117">**Friendly Name**</span></span>  
 <span data-ttu-id="e6c5c-118">원본 테이블의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c5c-118">Specifies the friendly name of the source table.</span></span> <span data-ttu-id="e6c5c-119">기본적으로 이 열에는 **원본 테이블** 열에 나타나는 원본 테이블의 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6c5c-119">By default, the column displays the name of the source table that appears in the **Source Table** column.</span></span>  
  
 <span data-ttu-id="e6c5c-120">**필터 세부 정보**</span><span class="sxs-lookup"><span data-stu-id="e6c5c-120">**Filter Details**</span></span>  
 <span data-ttu-id="e6c5c-121">가져오고 있는 데이터에 필터가 적용된 경우 **필터 세부 정보** 대화 상자에 데이터 가져오기 필터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c5c-121">Displays the data import filter in the **Filter Details** dialog box, when a filter has been applied to the data that is being imported.</span></span> <span data-ttu-id="e6c5c-122">자세한 내용은 [필터 세부 정보&#40;SSAS&#41;](filter-details-ssas.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6c5c-122">For more information, see [Filter Details &#40;SSAS&#41;](filter-details-ssas.md).</span></span>  
  
 <span data-ttu-id="e6c5c-123">**미리 보기 및 필터**</span><span class="sxs-lookup"><span data-stu-id="e6c5c-123">**Preview and Filter**</span></span>  
 <span data-ttu-id="e6c5c-124">가져오고 있는 데이터에 필터를 적용하는 데 사용되는 **선택한 테이블 미리 보기** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c5c-124">Displays the **Preview Selected Table** dialog box that is used to apply a filter to the data that is being imported.</span></span> <span data-ttu-id="e6c5c-125">자세한 내용은 [선택한 테이블 미리 보기&#40;SSAS&#41;](preview-selected-table-ssas.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6c5c-125">For more information, see [Preview Selected Table &#40;SSAS&#41;](preview-selected-table-ssas.md).</span></span>  
  
 <span data-ttu-id="e6c5c-126">**관련 테이블 선택**</span><span class="sxs-lookup"><span data-stu-id="e6c5c-126">**Select Related Tables**</span></span>  
 <span data-ttu-id="e6c5c-127">선택한 테이블 및 뷰와 관련된 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c5c-127">Select tables that are related to the tables and views that you have selected.</span></span>  
  
  
