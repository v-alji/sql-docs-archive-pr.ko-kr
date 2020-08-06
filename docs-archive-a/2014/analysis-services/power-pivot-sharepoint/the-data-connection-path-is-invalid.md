---
title: 통합 문서의 데이터 연결 경로가 로컬 드라이브의 파일을 가리키거나 잘못된 URI입니다. PowerPivot 데이터 연결을 새로 고치지 못했습니다. Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: bd22e41a-0931-4d32-888a-633a3046fc5e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3349af08290e2ff659db1441d849b2afef51e95b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650306"
---
# <a name="the-data-connection-path-in-the-workbook-points-to-a-file-on-the-local-drive-or-is-an-invalid-uri-the-following-connections-failed-to-refresh-powerpivot-data"></a><span data-ttu-id="b8368-103">통합 문서의 데이터 연결 경로가 로컬 드라이브의 파일을 가리키거나 잘못된 URI입니다.</span><span class="sxs-lookup"><span data-stu-id="b8368-103">The data connection path in the workbook points to a file on the local drive or is an invalid URI.</span></span> <span data-ttu-id="b8368-104">PowerPivot 데이터 연결을: PowerPivot 데이터</span><span class="sxs-lookup"><span data-stu-id="b8368-104">The following connections failed to refresh: PowerPivot Data</span></span>
  <span data-ttu-id="b8368-105">Excel 서비스는 포함된 데이터 원본에 연결할 수 없는 경우 PowerPivot 데이터를 포함하는 Excel 통합 문서에 대해 이 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b8368-105">For Excel workbooks that contain PowerPivot data, Excel Services returns this error if it cannot connect to embedded data sources.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b8368-106">세부 정보</span><span class="sxs-lookup"><span data-stu-id="b8368-106">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b8368-107">적용 대상</span><span class="sxs-lookup"><span data-stu-id="b8368-107">Applies to</span></span>|<span data-ttu-id="b8368-108">SharePoint용 PowerPivot</span><span class="sxs-lookup"><span data-stu-id="b8368-108">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="b8368-109">제품 버전</span><span class="sxs-lookup"><span data-stu-id="b8368-109">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="b8368-110">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8368-110">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="b8368-111">원인</span><span class="sxs-lookup"><span data-stu-id="b8368-111">Cause</span></span>|<span data-ttu-id="b8368-112">Excel 서비스가 신뢰할 수 있는 데이터 연결 라이브러리에 있는 .odc 파일로부터의 데이터 연결만 허용하도록 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8368-112">Excel Services is configured to only allow data connections from .odc files that are in a trusted data connection library.</span></span>|  
|<span data-ttu-id="b8368-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="b8368-113">Message Text</span></span>|<span data-ttu-id="b8368-114">통합 문서의 데이터 연결 경로가 로컬 드라이브의 파일을 가리키거나 잘못된 URI입니다.</span><span class="sxs-lookup"><span data-stu-id="b8368-114">The data connection path in the workbook points to a file on the local drive or is an invalid URI.</span></span> <span data-ttu-id="b8368-115">PowerPivot 데이터 연결을: PowerPivot 데이터</span><span class="sxs-lookup"><span data-stu-id="b8368-115">The following connections failed to refresh: PowerPivot Data</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b8368-116">설명</span><span class="sxs-lookup"><span data-stu-id="b8368-116">Explanation</span></span>  
 <span data-ttu-id="b8368-117">PowerPivot 통합 문서에는 포함된 데이터 연결이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8368-117">PowerPivot workbooks contain embedded data connections.</span></span> <span data-ttu-id="b8368-118">슬라이서 및 필터를 통한 통합 문서 상호 작용을 지원하려면 포함된 연결 정보를 통한 외부 데이터 액세스를 허용하도록 Excel 서비스를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8368-118">To support workbook interaction through slicers and filters, Excel Services must be configured to allow external data access through embedded connection information.</span></span> <span data-ttu-id="b8368-119">팜의 PowerPivot 서버에 로드된 PowerPivot 데이터를 검색하려면 외부 데이터에 액세스해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8368-119">External data access is required for retrieving PowerPivot data that is loaded on PowerPivot servers in the farm.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b8368-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="b8368-120">User Action</span></span>  
 <span data-ttu-id="b8368-121">포함된 데이터 원본 연결을 허용하도록 구성 설정을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="b8368-121">Change the configuration settings to allow embedded data source connections.</span></span>  
  
1.  <span data-ttu-id="b8368-122">중앙 관리의 애플리케이션 관리에서 **서비스 애플리케이션 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8368-122">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="b8368-123">**Excel 서비스 애플리케이션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8368-123">Click **Excel Services Application**.</span></span>  
  
3.  <span data-ttu-id="b8368-124">**신뢰할 수 있는 파일 위치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8368-124">Click **Trusted File Location**.</span></span>  
  
4.  <span data-ttu-id="b8368-125">**http://** 또는 구성할 위치를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8368-125">Click **http://** or the location you want to configure.</span></span>  
  
5.  <span data-ttu-id="b8368-126">외부 데이터의 외부 데이터 허용에서 **신뢰할 수 있는 데이터 연결 라이브러리 및 포함 라이브러리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8368-126">In External Data, in Allow External Data, click **Trusted data connection libraries and embedded**.</span></span>  
  
6.  <span data-ttu-id="b8368-127">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8368-127">Click **OK**.</span></span>  
  
 <span data-ttu-id="b8368-128">또는 PowerPivot 통합 문서를 포함하는 사이트에 대한 신뢰할 수 있는 위치를 새로 만든 다음 해당 사이트에 대한 구성 설정을 수정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8368-128">Alternatively, you can create a new trusted location for sites that contain PowerPivot workbooks, and then modify the configuration settings for just that site.</span></span> <span data-ttu-id="b8368-129">자세한 내용은 [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b8368-129">For more information, see [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).</span></span>  
  
  
