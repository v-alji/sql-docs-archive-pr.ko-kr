---
title: 통합 문서가 저장된 신뢰할 수 있는 위치에서 외부 데이터 연결을 허용하지 않습니다. PowerPivot 데이터 연결을 새로 고치지 못했습니다. Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: dc0cedfd-a7d0-40ef-bdd6-ea508130640a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b7f6d335eac0bec0f67012cc413f3917c50348b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639016"
---
# <a name="the-trusted-location-where-the-workbook-is-stored-does-not-allow-external-data-connections-the-following-connections-failed-to-refresh-powerpivot-data"></a><span data-ttu-id="3d83f-103">통합 문서가 저장된 신뢰할 수 있는 위치에서 외부 데이터 연결을 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3d83f-103">The trusted location where the workbook is stored does not allow external data connections.</span></span> <span data-ttu-id="3d83f-104">PowerPivot 데이터 연결을: PowerPivot 데이터</span><span class="sxs-lookup"><span data-stu-id="3d83f-104">The following connections failed to refresh: PowerPivot Data</span></span>
  <span data-ttu-id="3d83f-105">Excel 서비스는 포함된 데이터 원본에 연결할 수 없는 경우 PowerPivot 데이터를 포함하는 Excel 통합 문서에 대해 이 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3d83f-105">For Excel workbooks that contain PowerPivot data, Excel Services returns this error if it cannot connect to embedded data sources.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3d83f-106">세부 정보</span><span class="sxs-lookup"><span data-stu-id="3d83f-106">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3d83f-107">적용 대상</span><span class="sxs-lookup"><span data-stu-id="3d83f-107">Applies to</span></span>|<span data-ttu-id="3d83f-108">SharePoint용 PowerPivot</span><span class="sxs-lookup"><span data-stu-id="3d83f-108">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="3d83f-109">제품 버전</span><span class="sxs-lookup"><span data-stu-id="3d83f-109">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="3d83f-110">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d83f-110">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="3d83f-111">원인</span><span class="sxs-lookup"><span data-stu-id="3d83f-111">Cause</span></span>|<span data-ttu-id="3d83f-112">Excel 서비스가 외부 데이터 액세스를 거부하도록 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d83f-112">Excel Services is configured to deny external data access.</span></span>|  
|<span data-ttu-id="3d83f-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="3d83f-113">Message Text</span></span>|<span data-ttu-id="3d83f-114">통합 문서가 저장된 신뢰할 수 있는 위치에서 외부 데이터 연결을 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3d83f-114">The trusted location where the workbook is stored does not allow external data connections.</span></span> <span data-ttu-id="3d83f-115">PowerPivot 데이터 연결을: PowerPivot 데이터</span><span class="sxs-lookup"><span data-stu-id="3d83f-115">The following connections failed to refresh: PowerPivot Data</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3d83f-116">설명</span><span class="sxs-lookup"><span data-stu-id="3d83f-116">Explanation</span></span>  
 <span data-ttu-id="3d83f-117">PowerPivot 통합 문서에는 포함된 데이터 연결이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d83f-117">PowerPivot workbooks contain embedded data connections.</span></span> <span data-ttu-id="3d83f-118">슬라이서 및 필터를 통한 통합 문서 상호 작용을 지원하려면 포함된 연결 정보를 통한 외부 데이터 액세스를 허용하도록 Excel 서비스를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d83f-118">To support workbook interaction through slicers and filters, Excel Services must be configured to allow external data access through embedded connection information.</span></span> <span data-ttu-id="3d83f-119">팜의 PowerPivot 서버에 로드된 PowerPivot 데이터를 검색하려면 외부 데이터에 액세스해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d83f-119">External data access is required for retrieving PowerPivot data that is loaded on PowerPivot servers in the farm.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3d83f-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="3d83f-120">User Action</span></span>  
 <span data-ttu-id="3d83f-121">포함된 데이터 원본을 허용하도록 구성 설정을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="3d83f-121">Change the configuration settings to allow embedded data sources.</span></span>  
  
1.  <span data-ttu-id="3d83f-122">중앙 관리의 애플리케이션 관리에서 **서비스 애플리케이션 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d83f-122">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="3d83f-123">**Excel 서비스 애플리케이션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d83f-123">Click **Excel Services Application**.</span></span>  
  
3.  <span data-ttu-id="3d83f-124">**신뢰할 수 있는 파일 위치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d83f-124">Click **Trusted File Location**.</span></span>  
  
4.  <span data-ttu-id="3d83f-125">**http://** 또는 구성할 위치를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d83f-125">Click **http://** or the location you want to configure.</span></span>  
  
5.  <span data-ttu-id="3d83f-126">외부 데이터의 외부 데이터 허용에서 **신뢰할 수 있는 데이터 연결 라이브러리 및 포함 라이브러리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d83f-126">In External Data, in Allow External Data, click **Trusted data connection libraries and embedded**.</span></span>  
  
6.  <span data-ttu-id="3d83f-127">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d83f-127">Click **OK**.</span></span>  
  
 <span data-ttu-id="3d83f-128">또는 PowerPivot 통합 문서를 포함하는 사이트에 대한 신뢰할 수 있는 위치를 새로 만든 다음 해당 사이트에 대한 구성 설정을 수정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d83f-128">Alternatively, you can create a new trusted location for sites that contain PowerPivot workbooks, and then modify the configuration settings for just that site.</span></span> <span data-ttu-id="3d83f-129">자세한 내용은 [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3d83f-129">For more information, see [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).</span></span>  
  
  
