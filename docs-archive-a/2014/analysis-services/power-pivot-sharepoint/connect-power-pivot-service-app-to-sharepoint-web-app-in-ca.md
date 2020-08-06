---
title: 중앙 관리에서 SharePoint 웹 응용 프로그램에 PowerPivot 서비스 응용 프로그램 연결 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a5da8e29-7ffd-44e7-bf61-344fa5bea8ce
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5fc6dcde4cc2d18c3650adbab0ec71ef5c6265cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653583"
---
# <a name="connect-a-powerpivot-service-application-to-a-sharepoint-web-application-in-central-administration"></a><span data-ttu-id="82338-102">중앙 관리에서 SharePoint 웹 애플리케이션에 PowerPivot 서비스 애플리케이션 연결</span><span class="sxs-lookup"><span data-stu-id="82338-102">Connect a PowerPivot Service Application to a SharePoint Web Application in Central Administration</span></span>
  <span data-ttu-id="82338-103">팜의 여러 SharePoint 웹 애플리케이션에서 PowerPivot 서비스 애플리케이션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82338-103">A PowerPivot service application can be used by any number of SharePoint Web applications in the farm.</span></span> <span data-ttu-id="82338-104">PowerPivot 서비스 애플리케이션을 사용할 수 있도록 하려면 서비스 연결 목록에 이를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="82338-104">To make a PowerPivot service application available, you add it to a service association list.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="82338-105">기본 그룹에 PowerPivot 서비스 애플리케이션이 하나 있어야 PowerPivot 관리 대시보드가 제대로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="82338-105">You must have one PowerPivot service application in the default group to ensure that PowerPivot Management Dashboard works properly.</span></span> <span data-ttu-id="82338-106">기본 그룹에 PowerPivot 서비스 애플리케이션을 여러 개 추가하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="82338-106">Do not add more than one PowerPivot service application to the default group.</span></span> <span data-ttu-id="82338-107">같은 서비스 애플리케이션 유형의 여러 항목을 추가하는 구성은 지원되지 않으며 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82338-107">Adding multiple entries of the same service application type is not a supported configuration and might cause errors.</span></span> <span data-ttu-id="82338-108">추가 서비스 애플리케이션을 만들 경우 사용자 지정 목록에 추가하십시오.</span><span class="sxs-lookup"><span data-stu-id="82338-108">If you are creating additional service applications, add them to custom lists.</span></span>  
  
 <span data-ttu-id="82338-109">이 항목에는 다음과 같은 섹션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82338-109">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="82338-110">기본 그룹에 PowerPivot 서비스 애플리케이션 추가</span><span class="sxs-lookup"><span data-stu-id="82338-110">Add PowerPivot Services Application to the Default Group</span></span>](#default)  
  
 [<span data-ttu-id="82338-111">사용자 지정 서비스 연결 목록에 PowerPivot 서비스 애플리케이션 추가</span><span class="sxs-lookup"><span data-stu-id="82338-111">Add PowerPivot Services Application a Custom Service Association List</span></span>](#custom)  
  
##  <a name="add-powerpivot-services-application-to-the-default-group"></a><a name="default"></a><span data-ttu-id="82338-112">기본 그룹에 PowerPivot 서비스 응용 프로그램 추가</span><span class="sxs-lookup"><span data-stu-id="82338-112">Add PowerPivot Services Application to the Default Group</span></span>  
 <span data-ttu-id="82338-113">서비스 연결 목록은 팜의 다른 SharePoint 웹 애플리케이션에 리소스를 제공하는 공유 서비스의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="82338-113">A service association list is a list of shared services that provide resources to other SharePoint Web applications in the farm.</span></span> <span data-ttu-id="82338-114">팜에는 하나의 기본 서비스 연결 그룹이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82338-114">There is one default group of service associations for the farm.</span></span>  
  
 <span data-ttu-id="82338-115">PowerPivot 서비스 애플리케이션을 목록에 추가하려면 애플리케이션을 만들 때 또는 나중에 다음 단계를 사용하여 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82338-115">To be on the list, a PowerPivot service application can either be added when you create the application or afterwards by using the following steps.</span></span>  
  
1.  <span data-ttu-id="82338-116">중앙 관리의 **애플리케이션 관리**에서 **서비스 애플리케이션 연결 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82338-116">In Central Administration, in **Application Management**, click **Configure service application associations**.</span></span>  
  
2.  <span data-ttu-id="82338-117">애플리케이션 프록시 그룹에서 **기본값**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82338-117">In Application Proxy Group, click **default**.</span></span>  
  
3.  <span data-ttu-id="82338-118">PowerPivot 서비스 애플리케이션(유형 이름 `PowerPivot Service Application Proxy`로 표시) 옆에 있는 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82338-118">Select the checkbox next to the PowerPivot service application (indicated by type name `PowerPivot Service Application Proxy`).</span></span> <span data-ttu-id="82338-119">둘 이상의 PowerPivot 서비스 애플리케이션이 있는 경우 하나만 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82338-119">If you have more than one PowerPivot service application, choose just one.</span></span>  
  
4.  <span data-ttu-id="82338-120">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82338-120">Click **OK**.</span></span>  
  
##  <a name="add-powerpivot-services-application-a-custom-service-association-list"></a><a name="custom"></a><span data-ttu-id="82338-121">사용자 지정 서비스 연결 목록에 PowerPivot 서비스 응용 프로그램 추가</span><span class="sxs-lookup"><span data-stu-id="82338-121">Add PowerPivot Services Application a Custom Service Association List</span></span>  
 <span data-ttu-id="82338-122">기본 그룹을 사용자 지정 목록으로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82338-122">The default group can be replaced by a custom list.</span></span> <span data-ttu-id="82338-123">특히 하나의 SharePoint 웹 애플리케이션에 대해 사용자 지정 목록이 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="82338-123">A custom list is created specifically for a single SharePoint Web application.</span></span> <span data-ttu-id="82338-124">기본 그룹이 무시되고 팜 또는 서비스 관리자가 지정한 서비스 연결만으로 기본 그룹이 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="82338-124">It overrides the default group and replaces it with only those service associations that a farm or service administrator specifies.</span></span> <span data-ttu-id="82338-125">여러 PowerPivot 서비스 애플리케이션을 만든 경우 사용자 지정 목록을 사용하여 사용할 애플리케이션을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82338-125">If you created multiple PowerPivot service applications, you must use a custom list to specify which one to use.</span></span> <span data-ttu-id="82338-126">사용자 지정 목록을 다른 웹 애플리케이션에서 다시 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82338-126">A custom list cannot be reused by other Web applications.</span></span> <span data-ttu-id="82338-127">이는 작성된 웹 애플리케이션에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="82338-127">It applies only to the Web application for which it was created.</span></span>  
  
1.  <span data-ttu-id="82338-128">중앙 관리의 **애플리케이션 관리**에서 **웹 애플리케이션 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82338-128">In Central Administration, in **Application Management**, click **Manage web applications**.</span></span>  
  
2.  <span data-ttu-id="82338-129">애플리케이션(예: SharePoint -80)을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82338-129">Select the application (for example, SharePoint -80).</span></span>  
  
3.  <span data-ttu-id="82338-130">웹 애플리케이션의 관리에서 **서비스 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82338-130">In Web Applications, in Manage, click **Service Connections**.</span></span>  
  
4.  <span data-ttu-id="82338-131">**다음 연결 그룹 편집**에서 **[사용자 지정]** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82338-131">In **Edit the following group of connections**, select **[custom]**.</span></span>  
  
5.  <span data-ttu-id="82338-132">사용할 각 서비스 애플리케이션 연결 옆에 있는 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82338-132">Select the checkbox next to each service application connection you want to use.</span></span> <span data-ttu-id="82338-133">여러 PowerPivot 서비스 애플리케이션이 있는 경우(`PowerPivot Service Application Proxy` 유형 설정으로 표시) 하나만 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82338-133">If you have multiple PowerPivot service applications (indicated by Type set to `PowerPivot Service Application Proxy`), be sure to choose only one.</span></span>  
  
6.  <span data-ttu-id="82338-134">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82338-134">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82338-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="82338-135">See Also</span></span>  
 <span data-ttu-id="82338-136">[중앙 관리에서 PowerPivot 서비스 응용 프로그램 만들기 및 구성](create-and-configure-power-pivot-service-application-in-ca.md) </span><span class="sxs-lookup"><span data-stu-id="82338-136">[Create and Configure a PowerPivot Service Application in Central Administration](create-and-configure-power-pivot-service-application-in-ca.md) </span></span>  
 [<span data-ttu-id="82338-137">초기 구성 &#40;SharePoint용 PowerPivot&#41;</span><span class="sxs-lookup"><span data-stu-id="82338-137">Initial Configuration &#40;PowerPivot for SharePoint&#41;</span></span>](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)  
  
  
