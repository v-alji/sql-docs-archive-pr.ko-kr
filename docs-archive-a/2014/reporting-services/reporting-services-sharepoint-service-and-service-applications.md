---
title: Reporting Services SharePoint 서비스 및 서비스 응용 프로그램 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 501aa9ee-8c13-458c-bf6f-24e00c82681b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5654764f7913002cdae58d3264848250a292c585
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661526"
---
# <a name="reporting-services-sharepoint-service-and-service-applications"></a><span data-ttu-id="3fa7f-102">Reporting Services SharePoint Service 및 서비스 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="3fa7f-102">Reporting Services SharePoint Service and Service Applications</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="3fa7f-103">SharePoint 모드는 SharePoint 서비스 아키텍처에 맞게 구축되었으며 SharePoint 서비스와 일대다 서비스 애플리케이션을 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-103">SharePoint mode is architected on the SharePoint service architecture and utilizes a SharePoint service and one to many service applications.</span></span> <span data-ttu-id="3fa7f-104">서비스 애플리케이션을 만들면 서비스를 사용할 수 있게 되며 서비스 애플리케이션 데이터베이스가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-104">Creating a service application makes the service available and generates the service application database.</span></span> <span data-ttu-id="3fa7f-105">Reporting Services 서비스 애플리케이션은 여러 개 만들 수 있지만 대부분의 배포 시나리오에서 서비스 애플리케이션은 하나면 충분합니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-105">You can create multiple Reporting Services service applications but one service application is sufficient for most deployment scenarios.</span></span>  
  
 <span data-ttu-id="3fa7f-106">이 항목에는 다음과 같은 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-106">This topic covers the following information:</span></span>  
  
-   [<span data-ttu-id="3fa7f-107">Reporting Services 서비스 응용 프로그램 만들기</span><span class="sxs-lookup"><span data-stu-id="3fa7f-107">Creating a Reporting Services Service Application</span></span>](#bkmk_createapp)  
  
-   [<span data-ttu-id="3fa7f-108">프록시 그룹과 서비스 응용 프로그램의 연결 수정</span><span class="sxs-lookup"><span data-stu-id="3fa7f-108">Modify the Associations of the Service Application with a proxy group</span></span>](#bkmk_associations)  
  
-   [<span data-ttu-id="3fa7f-109">서비스 응용 프로그램 속성 편집</span><span class="sxs-lookup"><span data-stu-id="3fa7f-109">Edit Service Application Properties</span></span>](#bkmk_editserviceapplication)  
  
-   [<span data-ttu-id="3fa7f-110">PowerShell을 사용하여 Reporting Services 서비스 애플리케이션을 만들려면</span><span class="sxs-lookup"><span data-stu-id="3fa7f-110">To create a Reporting Services Service Application using PowerShell</span></span>](#bkmk_powershell_create_ssrs_serviceapp)  
  
-   [<span data-ttu-id="3fa7f-111">관련 작업</span><span class="sxs-lookup"><span data-stu-id="3fa7f-111">Related Tasks</span></span>](#bkmk_related)  
  
##  <a name="creating-a-reporting-services-service-application"></a><a name="bkmk_createapp"></a><span data-ttu-id="3fa7f-112">Reporting Services 서비스 응용 프로그램 만들기</span><span class="sxs-lookup"><span data-stu-id="3fa7f-112">Creating a Reporting Services Service Application</span></span>  
 <span data-ttu-id="3fa7f-113">SharePoint 중앙 관리 또는 PowerShell 스크립트를 사용하여 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스 애플리케이션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-113">You can use SharePoint Central Administration or PowerShell scripts to create the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] services applications.</span></span> <span data-ttu-id="3fa7f-114">SharePoint 중앙 관리를 사용하는 방법에 대한 자세한 내용은 [SharePoint 2010용 Reporting Services SharePoint 모드 설치](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)에서 "Reporting Services 서비스 애플리케이션 만들기" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-114">For more information on using SharePoint Central Administration, see the "Create a Reporting Services Service Application" section in [Install Reporting Services SharePoint Mode for SharePoint 2010](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).</span></span> <span data-ttu-id="3fa7f-115">서비스 애플리케이션을 만들기 위한 예제 PowerShell 스크립트는 이 항목의 뒷부분에 나오는 PowerShell 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-115">See the PowerShell section later in this topic for a sample PowerShell script for creating service applications.</span></span>  
  
##  <a name="modify-the-associations-of-the-service-application-with-a-proxy-group"></a><a name="bkmk_associations"></a><span data-ttu-id="3fa7f-116">프록시 그룹과 서비스 응용 프로그램의 연결 수정</span><span class="sxs-lookup"><span data-stu-id="3fa7f-116">Modify the Associations of the Service Application with a proxy group</span></span>  
 <span data-ttu-id="3fa7f-117">서비스 애플리케이션을 만들기 위한 새 페이지에는 **웹 애플리케이션 연결**섹션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-117">The New page for creating a services application contains the section **Web Application Association**.</span></span> <span data-ttu-id="3fa7f-118">이 섹션에서 만들어지는 서비스 애플리케이션에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-118">The section allows you to associate your service application as you create it.</span></span> <span data-ttu-id="3fa7f-119">다음 단계를 사용하여 연결을 변경하고 사용자 구성을 서비스 애플리케이션에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-119">Use the following steps to change the association and assign a customer configuration to the service application.</span></span> <span data-ttu-id="3fa7f-120">사용자 지정 그룹에 대한 서비스 애플리케이션의 연결을 변경하지 않고 동일한 일반 프로세스를 사용하여 기본 그룹에 프록시를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-120">The same general process can also be used to add the proxy to the default group rather than changing the association of the service application to a custom group.</span></span>  
  
1.  <span data-ttu-id="3fa7f-121">SharePoint 중앙 관리의 애플리케이션 관리에서 **서비스 애플리케이션 연결 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-121">In SharePoint Central Administration, in the Application Management, click **Configure Service Application Associations**.</span></span>  
  
2.  <span data-ttu-id="3fa7f-122">서비스 애플리케이션 연결 페이지에서 보기를 **서비스 애플리케이션**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-122">On the Service application Associations page, change the view to **Service Applications**.</span></span>  
  
3.  <span data-ttu-id="3fa7f-123">새 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스 애플리케이션의 이름을 찾아서 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-123">Find and click the name of your new [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Service application.</span></span> <span data-ttu-id="3fa7f-124">또한 애플리케이션 프록시 그룹 이름인 **기본값** 을 클릭하여 다음 단계를 완료하는 대신 기본 그룹에 프록시를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-124">You could also click the application proxy group name **default** to add the proxy to default group rather than completing the following steps.</span></span>  
  
4.  <span data-ttu-id="3fa7f-125">**다음 연결 그룹 편집** 선택 상자에서 **사용자 지정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-125">Select **Custom** in the selection box **Edit the following group of connections**.</span></span>  
  
5.  <span data-ttu-id="3fa7f-126">해당 프록시의 상자를 선택하고 **확인**클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-126">Check the box for your proxy and click **Ok**.</span></span>  
  
##  <a name="edit-service-application-properties"></a><a name="bkmk_editserviceapplication"></a><span data-ttu-id="3fa7f-127">서비스 응용 프로그램 속성 편집</span><span class="sxs-lookup"><span data-stu-id="3fa7f-127">Edit Service Application Properties</span></span>  
 <span data-ttu-id="3fa7f-128">서비스 애플리케이션의 속성 페이지를 다시 열어서 속성을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-128">You can reopen the property page of the service application to modify the properties.</span></span>  
  
1.  <span data-ttu-id="3fa7f-129">SharePoint 중앙 관리의 응용 프로그램 관리 그룹에서 **서비스 응용 프로그램 관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-129">In SharePoint Central Administration, in the Application Management group, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="3fa7f-130">전체 행을 선택하려면 유형 열을 클릭하여 서비스 애플리케이션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-130">Select the service application by clicking the type column to select the entire row.</span></span> <span data-ttu-id="3fa7f-131">애플리케이션 이름을 클릭하면 서비스 애플리케이션의 속성을 여는 대신 서비스에 대한 관리 옵션 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-131">If you click the name of the application it, the Management options page for the service opens instead of opening the properties of the service application.</span></span>  
  
3.  <span data-ttu-id="3fa7f-132">서비스 애플리케이션 리본에서 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-132">In the Service Applications ribbon, click **Properties**.</span></span>  
  
##  <a name="to-create-a-reporting-services-service-application-using-powershell"></a><a name="bkmk_powershell_create_ssrs_serviceapp"></a><span data-ttu-id="3fa7f-133">PowerShell을 사용 하 여 Reporting Services 서비스 응용 프로그램을 만들려면</span><span class="sxs-lookup"><span data-stu-id="3fa7f-133">To create a Reporting Services Service Application using PowerShell</span></span>  
 <span data-ttu-id="3fa7f-134">PowerShell을 사용하여 서비스 애플리케이션과 프록시를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-134">You can use PowerShell to create the Service application and proxy.</span></span> <span data-ttu-id="3fa7f-135">아래 예제에서는 서비스 애플리케이션에서 사용하도록 구성할 애플리케이션 풀을 알고 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-135">The sample below assumes that you know what application pool you want to configure the service application to use.</span></span>  
  
1.  <span data-ttu-id="3fa7f-136">애플리케이션 풀 이름의 애플리케이션 풀 개체를 새 동작으로 전달되는 변수에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-136">Add the application pool object of your application pool name to a variable that is passed into the New action.</span></span>  
  
    ```powershell
    $appPoolName = Get-SPServiceApplicationPool "<application pool name>"  
    ```  
  
2.  <span data-ttu-id="3fa7f-137">제공한 이름 및 애플리케이션 풀 이름을 사용하여 서비스 애플리케이션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-137">Create the service application with a name and application pool name you provide.</span></span>  
  
    ```powershell
    New-SPRSServiceApplication -Name 'MyServiceApplication' -ApplicationPool $appPoolName -DatabaseName 'MyServiceApplicationDatabase' -DatabaseServer '<Server Name>'  
    ```  
  
3.  <span data-ttu-id="3fa7f-138">새 서비스 애플리케이션 개체를 가져오고 개체를 새 프록시 파이프 지정 cmdlet으로 파이프합니다.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-138">Get the new service application object, and pipe the object into the Pipe the new proxy cmdlet.</span></span>  
  
    ```powershell
    Get-SPRSServiceApplication -name MyServiceApplication | New-SPRSServiceApplicationProxy "MyServiceApplicationProxy"  
    ```  
  
##  <a name="related-tasks"></a><a name="bkmk_related"></a> <span data-ttu-id="3fa7f-139">관련 작업</span><span class="sxs-lookup"><span data-stu-id="3fa7f-139">Related Tasks</span></span>  
  
|<span data-ttu-id="3fa7f-140">Task</span><span class="sxs-lookup"><span data-stu-id="3fa7f-140">Task</span></span>|<span data-ttu-id="3fa7f-141">링크</span><span class="sxs-lookup"><span data-stu-id="3fa7f-141">Link</span></span>|  
|----------|----------|  
|<span data-ttu-id="3fa7f-142">서비스 애플리케이션의 설정 관리</span><span class="sxs-lookup"><span data-stu-id="3fa7f-142">Manage the settings of your Service Application.</span></span>|[<span data-ttu-id="3fa7f-143">Reporting Services SharePoint 서비스 응용 프로그램 관리</span><span class="sxs-lookup"><span data-stu-id="3fa7f-143">Manage a Reporting Services SharePoint Service Application</span></span>](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)|  
|<span data-ttu-id="3fa7f-144">서비스 애플리케이션과 관련 구성 요소(예: 암호화 키 및 프록시) 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="3fa7f-144">Backup and restore the service application and related components such as encryption keys and proxy.</span></span>|[<span data-ttu-id="3fa7f-145">Reporting Services SharePoint 서비스 애플리케이션 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="3fa7f-145">Backup and Restore Reporting Services SharePoint Service Applications</span></span>](../../2014/reporting-services/backup-and-restore-reporting-services-sharepoint-service-applications.md)|  
