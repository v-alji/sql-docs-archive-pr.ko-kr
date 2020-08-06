---
title: 이 통합 문서에는 외부 데이터를 새로 고치는 쿼리가 하나 이상 포함되어 있습니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: aa65c992-eb41-4032-9e11-a9ba871b6a3c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 25b2095e13d6151c68eb4a3507400dfdb1739564
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650307"
---
# <a name="this-workbook-contains-one-or-more-queries-that-refresh-external-data"></a><span data-ttu-id="16ceb-103">이 통합 문서에는 외부 데이터를 새로 고치는 쿼리가 하나 이상 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16ceb-103">This workbook contains one or more queries that refresh external data.</span></span>
  <span data-ttu-id="16ceb-104">PowerPivot 데이터를 포함하는 Excel 통합 문서의 경우 Excel Services는 연결 정보가 검색되면 이 경고를 표시하고 이 통합 문서에 대해 쿼리를 사용할지 여부를 묻는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="16ceb-104">For Excel workbooks that contain PowerPivot data, Excel Services shows this warning when it detects connection information and prompts you to enable or disable queries for this workbook.</span></span>  
  
## <a name="details"></a><span data-ttu-id="16ceb-105">세부 정보</span><span class="sxs-lookup"><span data-stu-id="16ceb-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="16ceb-106">제품 이름</span><span class="sxs-lookup"><span data-stu-id="16ceb-106">Product Name</span></span>|<span data-ttu-id="16ceb-107">SharePoint용 PowerPivot</span><span class="sxs-lookup"><span data-stu-id="16ceb-107">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="16ceb-108">제품 버전</span><span class="sxs-lookup"><span data-stu-id="16ceb-108">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="16ceb-109">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16ceb-109">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="16ceb-110">원인</span><span class="sxs-lookup"><span data-stu-id="16ceb-110">Cause</span></span>|<span data-ttu-id="16ceb-111">Excel Services가 데이터를 새로 고칠 때 경고하도록 구성된 경우</span><span class="sxs-lookup"><span data-stu-id="16ceb-111">Excel Services is configured to warn on data refresh.</span></span>|  
|<span data-ttu-id="16ceb-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="16ceb-112">Message Text</span></span>|<span data-ttu-id="16ceb-113">이 통합 문서에는 외부 데이터를 새로 고치는 쿼리가 하나 이상 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16ceb-113">This workbook contains one or more queries that refresh external data.</span></span> <span data-ttu-id="16ceb-114">악의적인 사용자가 쿼리를 디자인하여 기밀 정보에 액세스하고 다른 사용자에게 이러한 정보를 배포하거나 다른 유해한 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16ceb-114">A malicious user can design a query to access confidential information and distribute it to other users or perform other harmful actions.</span></span><br /><br /> <span data-ttu-id="16ceb-115">이 통합 문서의 원본을 신뢰하는 경우 예를 클릭하여 이 통합 문서에서 외부 데이터에 대한 쿼리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="16ceb-115">If you trust the source of this workbook, click Yes to enable queries to external data in this workbook.</span></span> <span data-ttu-id="16ceb-116">통합 문서의 출처를 신뢰할 수 있는지 모르는 경우 변경 내용이 통합 문서에 적용되지 않도록 아니요를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="16ceb-116">If you are not sure, click No so that changes are not applied to your workbook.</span></span><br /><br /> <span data-ttu-id="16ceb-117">이 통합 문서의 외부 데이터에 대한 쿼리를 사용하시겠습니까?</span><span class="sxs-lookup"><span data-stu-id="16ceb-117">Do you want to enable queries to external data in this workbook?</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="16ceb-118">설명</span><span class="sxs-lookup"><span data-stu-id="16ceb-118">Explanation</span></span>  
 <span data-ttu-id="16ceb-119">PowerPivot 통합 문서에는 Excel에서 데이터를 로드하고 계산하는 외부 PowerPivot 서버와 통신하는 데 사용하는 포함된 데이터 연결 문자열이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16ceb-119">PowerPivot workbooks contain embedded data connection strings that are used by Excel to communicate with an external PowerPivot server that loads and calculates the data.</span></span> <span data-ttu-id="16ceb-120">새로 고칠 때 경고가 설정된 경우 Excel 서비스에서 이 연결 문자열을 검색하고 이에 따라 사용자에게 경고를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="16ceb-120">When warn on data refresh is enabled, Excel Services detects this connection string and warns the user accordingly.</span></span>  
  
 <span data-ttu-id="16ceb-121">통합 문서의 PowerPivot 데이터를 필터링하고 조각화하려면 쿼리를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="16ceb-121">To filter and slice PowerPivot data in the workbook, queries must be enabled.</span></span> <span data-ttu-id="16ceb-122">신뢰하는 PowerPivot 통합 문서에 대해서만 쿼리를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="16ceb-122">Be sure that you enable queries for only those PowerPivot workbooks that you trust.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="16ceb-123">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="16ceb-123">User Action</span></span>  
 <span data-ttu-id="16ceb-124">쿼리를 사용하려면 **예** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="16ceb-124">Click **Yes** to enable queries.</span></span>  
  
 <span data-ttu-id="16ceb-125">또한 다음과 같이 새로 고칠 때 경고가 더 이상 나타나지 않도록 구성 설정을 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16ceb-125">You can also change the configuration settings so that warn on refresh no longer occurs:</span></span>  
  
1.  <span data-ttu-id="16ceb-126">중앙 관리의 애플리케이션 관리에서 **서비스 애플리케이션 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="16ceb-126">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="16ceb-127">**Excel 서비스 애플리케이션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="16ceb-127">Click **Excel Services Application**.</span></span>  
  
3.  <span data-ttu-id="16ceb-128">**신뢰할 수 있는 파일 위치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="16ceb-128">Click **Trusted File Location**.</span></span>  
  
4.  <span data-ttu-id="16ceb-129">**http://** 또는 구성할 위치를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="16ceb-129">Click **http://** or the location you want to configure.</span></span>  
  
5.  <span data-ttu-id="16ceb-130">외부 데이터에서 **새로 고칠 때 경고**확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="16ceb-130">In External Data, clear the checkbox for **Warn on data refresh**.</span></span>  
  
6.  <span data-ttu-id="16ceb-131">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="16ceb-131">Click **OK**.</span></span>  
  
 <span data-ttu-id="16ceb-132">또는 PowerPivot 통합 문서를 포함하는 사이트에 대한 신뢰할 수 있는 위치를 새로 만든 다음 해당 사이트에 대한 구성 설정을 수정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16ceb-132">Alternatively, you can create a new trusted location for sites that contain PowerPivot workbooks, and then modify the configuration settings for just that site.</span></span> <span data-ttu-id="16ceb-133">자세한 내용은 [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="16ceb-133">For more information, see [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).</span></span>  
  
  
