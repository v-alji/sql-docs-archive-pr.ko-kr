---
title: Microsoft.analysisservices.sharepoint.integration.dll&#39; &#39;파일 또는 어셈블리를 로드할 수 없습니다. Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6e350b67-5e18-4b90-8fb7-a0109cbb27b7
author: minewiskan
ms.author: owend
ms.openlocfilehash: b7ba75bdbd8e25f98d11d822c22fa7881352ad88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653582"
---
# <a name="could-not-load-file-or-assembly-39microsoftanalysisservicessharepointintegration39"></a><span data-ttu-id="021f4-102">Microsoft.analysisservices.sharepoint.integration.dll &#39;파일 또는 어셈블리를 로드할 수 없습니다.&#39;</span><span class="sxs-lookup"><span data-stu-id="021f4-102">Could not load file or assembly &#39;Microsoft.AnalysisServices.SharePoint.Integration&#39;</span></span>
  <span data-ttu-id="021f4-103">SharePoint용 PowerPivot이 설치된 SharePoint 2010 환경에서는 PowerPivot용 애플리케이션 수준 솔루션이 제대로 배포되지 않은 경우 이 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="021f4-103">In SharePoint 2010 environments that have PowerPivot for SharePoint, this error will occur if the application-level solution for PowerPivot did not deploy correctly.</span></span>  
  
## <a name="details"></a><span data-ttu-id="021f4-104">세부 정보</span><span class="sxs-lookup"><span data-stu-id="021f4-104">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="021f4-105">적용 대상</span><span class="sxs-lookup"><span data-stu-id="021f4-105">Applies to</span></span>|<span data-ttu-id="021f4-106">SharePoint용 PowerPivot</span><span class="sxs-lookup"><span data-stu-id="021f4-106">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="021f4-107">제품 버전</span><span class="sxs-lookup"><span data-stu-id="021f4-107">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="021f4-108">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="021f4-108">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="021f4-109">원인</span><span class="sxs-lookup"><span data-stu-id="021f4-109">Cause</span></span>|<span data-ttu-id="021f4-110">Powerpivotwebapp 솔루션이 배포되지 않았거나 올바르게 배포되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="021f4-110">Powerpivotwebapp solution is not deployed or did not deploy correctly.</span></span>|  
|<span data-ttu-id="021f4-111">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="021f4-111">Message Text</span></span>|<span data-ttu-id="021f4-112">'Microsoft.AnalysisServices.SharePoint.Integration' 파일 또는 어셈블리를 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="021f4-112">Could not load file or assembly 'Microsoft.AnalysisServices.SharePoint.Integration'</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="021f4-113">설명</span><span class="sxs-lookup"><span data-stu-id="021f4-113">Explanation</span></span>  
 <span data-ttu-id="021f4-114">SharePoint용 PowerPivot에서는 솔루션 패키지를 사용하여 SharePoint 서버에서 해당 기능을 배포하는데,</span><span class="sxs-lookup"><span data-stu-id="021f4-114">PowerPivot for SharePoint uses solution packages to deploy its features on a SharePoint server.</span></span> <span data-ttu-id="021f4-115">이러한 솔루션 중 하나가 올바르게 배포되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="021f4-115">One of the solutions is not deployed correctly.</span></span> <span data-ttu-id="021f4-116">그 결과 SharePoint 사이트에서 PowerPivot에 갤러리 또는 기타 PowerPivot 애플리케이션 페이지를 열려고 할 때마다 이 오류가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="021f4-116">As a result, this error appears whenever you try to open PowerPivot Gallery or other PowerPivot application pages on a SharePoint site.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="021f4-117">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="021f4-117">User Action</span></span>  
 <span data-ttu-id="021f4-118">솔루션 패키지를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="021f4-118">Deploy the solution package.</span></span>  
  
1.  <span data-ttu-id="021f4-119">중앙 관리의 시스템 설정에서 **팜 솔루션 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="021f4-119">In Central Administration, in System Settings, click **Manage farm solutions**.</span></span>  
  
2.  <span data-ttu-id="021f4-120">**Powerpivotwebapp**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="021f4-120">Click **Powerpivotwebapp**.</span></span>  
  
3.  <span data-ttu-id="021f4-121">**솔루션 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="021f4-121">Click **Deploy Solution**.</span></span>  
  
4.  <span data-ttu-id="021f4-122">이 오류가 발생하는 웹 애플리케이션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="021f4-122">Choose the web application for which this error is occurring.</span></span> <span data-ttu-id="021f4-123">웹 애플리케이션이 여러 개인 경우에는 모든 웹 애플리케이션에 대해 솔루션을 다시 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="021f4-123">If there is more than one web application, redeploy the solution for all of hem.</span></span>  
  
5.  <span data-ttu-id="021f4-124">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="021f4-124">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="021f4-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="021f4-125">See Also</span></span>  
 [<span data-ttu-id="021f4-126">SharePoint에 PowerPivot 솔루션 배포</span><span class="sxs-lookup"><span data-stu-id="021f4-126">Deploy PowerPivot Solutions to SharePoint</span></span>](deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
