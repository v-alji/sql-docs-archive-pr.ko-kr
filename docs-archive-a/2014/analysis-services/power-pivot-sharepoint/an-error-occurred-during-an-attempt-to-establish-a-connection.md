---
title: 외부 데이터 원본에 대한 연결을 설정하는 동안 오류가 발생했습니다. PowerPivot 데이터 연결을 새로 고치지 못했습니다. Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1b951da1-f62d-43d2-b40b-270a4a9ab92c
author: minewiskan
ms.author: owend
ms.openlocfilehash: eb4329440b69d1bdfdbb96fbcc3926fa000d8877
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732088"
---
# <a name="an-error-occurred-during-an-attempt-to-establish-a-connection-to-the-external-data-source-the-following-connections-failed-to-refresh-powerpivot-data"></a><span data-ttu-id="385c2-103">외부 데이터 원본에 대한 연결을 설정하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="385c2-103">An error occurred during an attempt to establish a connection to the external data source.</span></span> <span data-ttu-id="385c2-104">PowerPivot 데이터 연결을: PowerPivot 데이터</span><span class="sxs-lookup"><span data-stu-id="385c2-104">The following connections failed to refresh: PowerPivot Data</span></span>
  <span data-ttu-id="385c2-105">이 오류는 SharePoint용 PowerPivot이 설치되어 있지 않은 서버에서 PowerPivot 데이터를 쿼리하면 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="385c2-105">This error occurs if you query PowerPivot data on a server that does not have PowerPivot for SharePoint installed.</span></span> <span data-ttu-id="385c2-106">이 오류는 SQL Server Analysis Services(PowerPivot) 서비스가 중지되었거나 이전 버전에서 PowerPivot 데이터를 보려고 시도하는 경우에도 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="385c2-106">It also occurs if the SQL Server Analysis Services (PowerPivot) service is stopped, or if you are attempting to view PowerPivot data from an earlier version.</span></span>  
  
## <a name="details"></a><span data-ttu-id="385c2-107">세부 정보</span><span class="sxs-lookup"><span data-stu-id="385c2-107">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="385c2-108">적용 대상</span><span class="sxs-lookup"><span data-stu-id="385c2-108">Applies to</span></span>|<span data-ttu-id="385c2-109">SharePoint용 PowerPivot</span><span class="sxs-lookup"><span data-stu-id="385c2-109">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="385c2-110">제품 버전</span><span class="sxs-lookup"><span data-stu-id="385c2-110">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="385c2-111">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="385c2-111">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="385c2-112">원인</span><span class="sxs-lookup"><span data-stu-id="385c2-112">Cause</span></span>|<span data-ttu-id="385c2-113">데이터 연결이 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="385c2-113">The data connection failed.</span></span>|  
|<span data-ttu-id="385c2-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="385c2-114">Message Text</span></span>|<span data-ttu-id="385c2-115">외부 데이터 원본에 대한 연결을 설정하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="385c2-115">An error occurred during an attempt to establish a connection to the external data source.</span></span> <span data-ttu-id="385c2-116">PowerPivot 데이터 연결을: PowerPivot 데이터</span><span class="sxs-lookup"><span data-stu-id="385c2-116">The following connections failed to refresh: PowerPivot Data</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="385c2-117">설명</span><span class="sxs-lookup"><span data-stu-id="385c2-117">Explanation</span></span>  
 <span data-ttu-id="385c2-118">SharePoint에 게시된 Excel 통합 문서에서 PowerPivot 데이터를 쿼리할 때 SharePoint 환경에 SharePoint용 PowerPivot 서버가 없거나 SQL Server Analysis Services(PowerPivot) 서비스가 중지된 경우 Excel Services가 이 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="385c2-118">Excel Services returns this error when you query PowerPivot data in an Excel workbook that is published to SharePoint, and the SharePoint environment does not have a PowerPivot for SharePoint server, or the SQL Server Analysis Services (PowerPivot) service is stopped.</span></span>  
  
 <span data-ttu-id="385c2-119">쿼리 엔진을 사용할 수 없을 때 PowerPivot 데이터를 필터링하거나 조각을 생성하면 이 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="385c2-119">The error occurs when you slice or filter PowerPivot data when the query engine is not available.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="385c2-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="385c2-120">User Action</span></span>  
 <span data-ttu-id="385c2-121">SharePoint용 PowerPivot을 설치하거나 SharePoint용 PowerPivot이 설치된 SharePoint 환경으로 PowerPivot 통합 문서를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="385c2-121">Install PowerPivot for SharePoint or move the PowerPivot workbook to a SharePoint environment that has PowerPivot for SharePoint installed.</span></span> <span data-ttu-id="385c2-122">자세한 내용은 [PowerPivot for SharePoint 2010 Installation](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="385c2-122">For more information, see [PowerPivot for SharePoint 2010 Installation](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md).</span></span>  
  
 <span data-ttu-id="385c2-123">소프트웨어가 설치되어 있는 경우 SQL Server Analysis Services(PowerPivot) 인스턴스가 실행되고 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="385c2-123">If the software is installed, verify that the SQL Server Analysis Services (PowerPivot) instance is running.</span></span> <span data-ttu-id="385c2-124">중앙 관리에서 **서버의 서비스 관리** 를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="385c2-124">Check **Manage services on server** in Central Administration.</span></span> <span data-ttu-id="385c2-125">또한 관리 도구에서 서비스 콘솔 애플리케이션을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="385c2-125">Also check the Services console application in Administrative Tools.</span></span>  
  
 <span data-ttu-id="385c2-126">SQL Server 2008 R2 버전의 PowerPivot for Excel에서 만든 PowerPivot 통합 문서의 경우 SQL Server 2008 R2 버전의 Analysis Services OLE DB 공급자를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="385c2-126">For PowerPivot workbooks that were created in a SQL Server 2008 R2 version of PowerPivot for Excel, you must install the SQL Server 2008 R2 version of the Analysis Services OLE DB provider.</span></span> <span data-ttu-id="385c2-127">이 오류는 공급자를 설치했지만 Microsoft.AnalysisServices.ChannelTransport.dll 파일을 등록하지 않은 경우 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="385c2-127">This error will occur if you installed the provider, but did not register the Microsoft.AnalysisServices.ChannelTransport.dll file.</span></span> <span data-ttu-id="385c2-128">파일 등록에 대한 자세한 내용은 [SharePoint 서버에서 Analysis Services OLE DB 공급자 설치](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="385c2-128">For more information about file registration, see [Install the Analysis Services OLE DB Provider on SharePoint Servers](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="385c2-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="385c2-129">See Also</span></span>  
 [<span data-ttu-id="385c2-130">데이터 연결에서 Windows 인증을 사용 하 고 사용자 자격 증명을 위임할 수 없습니다. PowerPivot 데이터 연결을 새로 고치지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="385c2-130">The data connection uses Windows Authentication and user credentials could not be delegated. The following connections failed to refresh: PowerPivot Data</span></span>](the-data-connection-user-could-not-be-delegated.md)  
  
  
