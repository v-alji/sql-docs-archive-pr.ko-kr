---
title: 데이터 연결은 Windows 인증을 사용하지만 사용자 자격 증명을 위임할 수 없습니다. PowerPivot 데이터 연결을 새로 고치지 못했습니다. Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d2006df1-d244-4786-b272-49d8996cc88c
author: minewiskan
ms.author: owend
ms.openlocfilehash: be4c61ad4514f3aa4f6f1eda1fe44ad97c4c064f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649245"
---
# <a name="the-data-connection-uses-windows-authentication-and-user-credentials-could-not-be-delegated-the-following-connections-failed-to-refresh-powerpivot-data"></a><span data-ttu-id="2e40c-103">데이터 연결은 Windows 인증을 사용하지만 사용자 자격 증명을 위임할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2e40c-103">The data connection uses Windows Authentication and user credentials could not be delegated.</span></span> <span data-ttu-id="2e40c-104">PowerPivot 데이터 연결을: PowerPivot 데이터</span><span class="sxs-lookup"><span data-stu-id="2e40c-104">The following connections failed to refresh: PowerPivot Data</span></span>
  <span data-ttu-id="2e40c-105">Excel 서비스는 SharePoint의 PowerPivot 서버 인스턴스에 연결할 수 없는 경우 PowerPivot 데이터를 포함하는 Excel 통합 문서에 대해 이 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2e40c-105">For Excel workbooks that contain PowerPivot data, Excel Services returns this error if it cannot connect to a PowerPivot server instance in SharePoint.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2e40c-106">세부 정보</span><span class="sxs-lookup"><span data-stu-id="2e40c-106">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2e40c-107">적용 대상</span><span class="sxs-lookup"><span data-stu-id="2e40c-107">Applies to</span></span>|<span data-ttu-id="2e40c-108">SharePoint용 PowerPivot</span><span class="sxs-lookup"><span data-stu-id="2e40c-108">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="2e40c-109">제품 버전</span><span class="sxs-lookup"><span data-stu-id="2e40c-109">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="2e40c-110">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e40c-110">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="2e40c-111">원인</span><span class="sxs-lookup"><span data-stu-id="2e40c-111">Cause</span></span>|<span data-ttu-id="2e40c-112">PowerPoint 데이터 공급자 사용을 시도할 때 연결하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="2e40c-112">Connection failed when attempting to use a PowerPivot data provider.</span></span>|  
|<span data-ttu-id="2e40c-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="2e40c-113">Message Text</span></span>|<span data-ttu-id="2e40c-114">데이터 연결은 Windows 인증을 사용하지만 사용자 자격 증명을 위임할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2e40c-114">The data connection uses Windows Authentication and user credentials could not be delegated.</span></span> <span data-ttu-id="2e40c-115">PowerPivot 데이터 연결을: PowerPivot 데이터</span><span class="sxs-lookup"><span data-stu-id="2e40c-115">The following connections failed to refresh: PowerPivot Data</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2e40c-116">설명</span><span class="sxs-lookup"><span data-stu-id="2e40c-116">Explanation</span></span>  
 <span data-ttu-id="2e40c-117">이 오류 메시지는 여러 가지 원인으로 인해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e40c-117">There are multiple causes for this error message.</span></span> <span data-ttu-id="2e40c-118">이러한 모든 원인에 공통적으로 적용되는 요인은 Excel 서비스가 SharePoint의 클레임 토큰에서 유효한 Windows 사용자 ID를 가져올 수 없다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2e40c-118">The common factor behind all of them is that Excel Services cannot get a valid Windows user identity from a claims token in SharePoint.</span></span> <span data-ttu-id="2e40c-119">PowerPivot 데이터가 포함된 Excel 통합 문서의 경우 이 오류는 다음 조건 중 하나라도 해당하는 경우 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="2e40c-119">In the case of Excel workbooks that contain PowerPivot data, this error occurs when any of the following conditions exist:</span></span>  
  
-   <span data-ttu-id="2e40c-120">Windows 토큰 서비스에 대한 클레임이 실행 중이지 않은 경우.</span><span class="sxs-lookup"><span data-stu-id="2e40c-120">The Claims to Windows Token Service is not running.</span></span> <span data-ttu-id="2e40c-121">SharePoint 로그 파일을 통해 이 오류의 원인을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e40c-121">You can confirm the cause of this error by viewing the SharePoint log file.</span></span> <span data-ttu-id="2e40c-122">SharePoint 로그에 "파이프 엔드포인트 'net.pipe://localhost/s4u/022694f3-9fbd-422b-b4b2-312e25dae2a2'을(를) 로컬 컴퓨터에서 찾을 수 없습니다." 메시지가 포함되어 있으면 Windows 토큰 서비스에 대한 클레임이 실행 중이지 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2e40c-122">If the SharePoint logs include the message "The pipe endpoint 'net.pipe://localhost/s4u/022694f3-9fbd-422b-b4b2-312e25dae2a2' could not be found on your local machine", the Claims to Windows Token Service is not running.</span></span> <span data-ttu-id="2e40c-123">클레임을 시작하려면 중앙 관리를 통해 서비스 콘솔 애플리케이션에서 서비스가 실행 중인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2e40c-123">To start it, use Central Administration and then verify the service is running in the Services console application.</span></span>  
  
-   <span data-ttu-id="2e40c-124">도메인 컨트롤러로 사용자 ID의 유효성을 검사할 수 없는 경우.</span><span class="sxs-lookup"><span data-stu-id="2e40c-124">A domain controller is not available to validate the user identity.</span></span> <span data-ttu-id="2e40c-125">Windows 토큰 서비스에 대한 클레임은 캐시된 자격 증명을 사용하지 않으며,</span><span class="sxs-lookup"><span data-stu-id="2e40c-125">The Claims to Windows Token Service does not use cached credentials.</span></span> <span data-ttu-id="2e40c-126">각 연결에 대해 사용자 ID 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="2e40c-126">It validates the user identity for each connection.</span></span> <span data-ttu-id="2e40c-127">SharePoint 로그 파일을 통해 이 오류의 원인을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e40c-127">You can confirm the cause of this error by viewing the SharePoint log file.</span></span> <span data-ttu-id="2e40c-128">SharePoint 로그에 "IClaimsIdentity에서 WindowsIdentity을(를) 가져오지 못했습니다." 메시지가 포함되어 있으면 사용자 ID를 인증할 수 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2e40c-128">If the SharePoint logs include the message "Failed to get WindowsIdentity from IClaimsIdentity", the user identity could not be authenticated.</span></span>  
  
-   <span data-ttu-id="2e40c-129">컴퓨터가 같은 도메인 또는 양방향 신뢰 관계가 있는 도메인의 멤버여야 하는 경우</span><span class="sxs-lookup"><span data-stu-id="2e40c-129">The computers must be members of the same domain or in domains that have a two-way trust relationship.</span></span>  
  
-   <span data-ttu-id="2e40c-130">Windows 도메인 사용자 계정을 사용해야 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="2e40c-130">You must use Windows domain user accounts.</span></span> <span data-ttu-id="2e40c-131">계정의 이름은 UPN(Universal Principal Name)이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e40c-131">The accounts must have a Universal Principal Name (UPN).</span></span>  
  
-   <span data-ttu-id="2e40c-132">Excel 서비스의 서비스 계정에 개체 쿼리를 위한 Active Directory 사용 권한이 있어야 하는 경우</span><span class="sxs-lookup"><span data-stu-id="2e40c-132">The Excel Services service account must have Active Directory permissions to query the object.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2e40c-133">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="2e40c-133">User Action</span></span>  
 <span data-ttu-id="2e40c-134">다음 지침에 따라 Windows 토큰 서비스에 대한 클레임 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2e40c-134">Use the following instructions to check the status of the Claims to Windows Token Service.</span></span>  
  
 <span data-ttu-id="2e40c-135">다른 모든 시나리오의 경우에는 네트워크 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="2e40c-135">For all other scenarios, check with your network administrator.</span></span>  
  
#### <a name="enable-claims-to-windows-token-service"></a><span data-ttu-id="2e40c-136">Windows 토큰 서비스에 대한 클레임 설정</span><span class="sxs-lookup"><span data-stu-id="2e40c-136">Enable Claims to Windows Token Service</span></span>  
  
1.  <span data-ttu-id="2e40c-137">중앙 관리의 시스템 설정에서 **서버의 서비스 관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e40c-137">In Central Administration, in System Settings, click **Manage services on server**.</span></span>  
  
2.  <span data-ttu-id="2e40c-138">**Windows 토큰 서비스에 대한 클레임**을 선택하고 **시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2e40c-138">Select **Claims to Windows Token Service**, and then click **Start**.</span></span>  
  
3.  <span data-ttu-id="2e40c-139">서비스가 서비스 콘솔에서도 실행되고 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2e40c-139">Verify the service is also running in the Services console:</span></span>  
  
    1.  <span data-ttu-id="2e40c-140">관리 도구에서 서비스를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2e40c-140">In Administrative Tools, click Services.</span></span>  
  
    2.  <span data-ttu-id="2e40c-141">Windows 토큰 서비스에 대한 클레임이 실행 중이지 않으면 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2e40c-141">Start the Claims to Windows Token Service if it is not running.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e40c-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2e40c-142">See Also</span></span>  
 [<span data-ttu-id="2e40c-143">PowerPivot 서비스 계정 구성</span><span class="sxs-lookup"><span data-stu-id="2e40c-143">Configure PowerPivot Service Accounts</span></span>](configure-power-pivot-service-accounts.md)  
  
  
