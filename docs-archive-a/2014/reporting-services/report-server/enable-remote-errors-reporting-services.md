---
title: 원격 오류 활성화(Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- remote data source [Reporting Services]
- EnableRemoteError server property
ms.assetid: 5f05022b-d557-43e0-b50a-f5e2a1846b83
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9d2a7e7e0b38b38bf563dfc2a8cff65c897c5293
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652573"
---
# <a name="enable-remote-errors-reporting-services"></a><span data-ttu-id="3842a-102">원격 오류 활성화(Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="3842a-102">Enable Remote Errors (Reporting Services)</span></span>
  <span data-ttu-id="3842a-103">원격 서버에서 발생되는 오류 조건에 대한 추가 정보를 반환하도록 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서 서버에 대한 서버 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-103">You can set server properties on a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server to return additional information about error conditions that occur on remote servers.</span></span> <span data-ttu-id="3842a-104">오류 메시지에 "이 오류에 대한 자세한 내용을 보려면 로컬 서버 컴퓨터의 보고서 서버를 탐색하거나 원격 오류를 활성화하십시오"라는 텍스트가 포함되어 있으면 문제 해결에 도움이 되는 추가 정보에 액세스할 수 있도록 `EnableRemoteErrors` 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-104">If an error message contains the text "For more information about this error, navigate to the report server on the local server machine, or enable remote errors", you can set the `EnableRemoteErrors` property to access additional information that can help you troubleshoot the problem.</span></span> <span data-ttu-id="3842a-105">자세한 내용은 [온라인 설명서에서](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md) 보고서 서버 시스템 속성 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3842a-105">For more information, see [Report Server System Properties](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="3842a-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="3842a-106">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="3842a-107">SharePoint 모드에 대한 원격 오류 사용</span><span class="sxs-lookup"><span data-stu-id="3842a-107">Enable Remote Errors for SharePoint Mode</span></span>](#bkmk_sharepoint)  
  
-   [<span data-ttu-id="3842a-108">SQL Server Management Studio를 통한 원격 오류 사용(기본 모드)</span><span class="sxs-lookup"><span data-stu-id="3842a-108">Enable remote errors through SQL Server Management Studio (Native Mode)</span></span>](#bkmk_mgtStudio)  
  
-   [<span data-ttu-id="3842a-109">스크립트를 통한 원격 오류 사용(기본 모드)</span><span class="sxs-lookup"><span data-stu-id="3842a-109">Enable remote errors through script (Native Mode)</span></span>](#bkmk_script)  
  
-   [<span data-ttu-id="3842a-110">ConfigurationInfo 테이블 수정(기본 모드)</span><span class="sxs-lookup"><span data-stu-id="3842a-110">Modifying the ConfigurationInfo table (Native Mode)</span></span>](#bkmk_ConfigurationInfo)  
  
##  <a name="enable-remote-errors-for-sharepoint-mode"></a><a name="bkmk_sharepoint"></a> <span data-ttu-id="3842a-111">SharePoint 모드에 대한 원격 오류 사용</span><span class="sxs-lookup"><span data-stu-id="3842a-111">Enable Remote Errors for SharePoint Mode</span></span>  
 <span data-ttu-id="3842a-112">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드에 대한 원격 오류 사용에는 두 가지 다른 프로시저가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-112">There are two different procedures for enabling remote errors for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span> <span data-ttu-id="3842a-113">서로 다른 두 보고서 서버 아키텍처에 따라 프로시저가 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-113">The procedure is different for the two different report server architectures.</span></span> <span data-ttu-id="3842a-114">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 릴리스에서 도입된 새 SharePoint 서비스 기반 아키텍처는 각 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션에 대해 구성될 수 있는 설정을 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-114">The newer SharePoint service based architecture that was introduced in the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] release, utilizes a setting that can be configured for each [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="3842a-115">이전 아키텍처는 단일 사이트 수준 설정을 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-115">The older architecture utilizes a single site level setting.</span></span>  
  
#### <a name="enable-remote-errors-for-a-reporting-services-service-application"></a><span data-ttu-id="3842a-116">Reporting Services 서비스 애플리케이션에 대한 원격 오류 사용</span><span class="sxs-lookup"><span data-stu-id="3842a-116">Enable Remote errors for a Reporting Services Service Application</span></span>  
  
1.  <span data-ttu-id="3842a-117">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 또는 새 버전의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]와 함께 설치되는 SharePoint 모드 보고서 서버의 경우 서비스 애플리케이션 설정 **원격 오류 사용**을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-117">For a SharePoint mode report server installed with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] or a newer version of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], enable the service application setting **Enable remote errors**.</span></span> <span data-ttu-id="3842a-118">각 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션에 대해 이 설정을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-118">The setting can be configured for each [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
2.  <span data-ttu-id="3842a-119">SharePoint 중앙 관리의 **애플리케이션 관리** 그룹에서 **서비스 애플리케이션 관리** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-119">In SharePoint Central Administration, click **Manage service applications** in the **Application Management** group.</span></span>  
  
3.  <span data-ttu-id="3842a-120">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션을 찾아 해당 서비스 애플리케이션의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-120">Find your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application and click the name of your service application.</span></span>  
  
4.  <span data-ttu-id="3842a-121">**시스템 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-121">Click **System Settings**.</span></span>  
  
5.  <span data-ttu-id="3842a-122">**보안** 섹션에서 **원격 오류 사용** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-122">Click **Enable Remote Errors** in the **Security** section.</span></span>  
  
6.  <span data-ttu-id="3842a-123">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-123">Click **OK**.</span></span>  
  
#### <a name="enable-remote-errors-for-a-sharepoint-site"></a><span data-ttu-id="3842a-124">SharePoint 사이트에 대한 원격 오류 사용</span><span class="sxs-lookup"><span data-stu-id="3842a-124">Enable Remote Errors for a SharePoint Site</span></span>  
  
1.  <span data-ttu-id="3842a-125">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 이전의 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]버전과 함께 설치되는 SharePoint 모드 보고서 서버의 경우 사이트 설정 **로컬 모드에서 원격 오류 사용**을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-125">For a SharePoint mode report server installed with a version of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] prior to [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], enable the site setting **Enable remote errors in local mode**.</span></span>  
  
2.  <span data-ttu-id="3842a-126">**사이트 작업** 에서 수정할 사이트의 **사이트 설정** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-126">In **Site Actions** click **Site Settings** for the site you want to modify.</span></span>  
  
3.  <span data-ttu-id="3842a-127">**Reporting Services** 그룹에서 **Reporting Services 사이트 설정** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-127">Click **Reporting Services Site Settings** in the **Reporting Services** group.</span></span>  
  
4.  <span data-ttu-id="3842a-128">**로컬 모드에서 원격 오류 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-128">Click **Enable remote errors in local mode**.</span></span>  
  
5.  <span data-ttu-id="3842a-129">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-129">Click **OK**</span></span>  
  
##  <a name="enable-remote-errors-through-sql-server-management-studio-native-mode"></a><a name="bkmk_mgtStudio"></a> <span data-ttu-id="3842a-130">SQL Server Management Studio를 통한 원격 오류 사용(기본 모드)</span><span class="sxs-lookup"><span data-stu-id="3842a-130">Enable remote errors through SQL Server Management Studio (Native Mode)</span></span>  
  
1.  <span data-ttu-id="3842a-131">Management Studio를 시작하여 보고서 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-131">Start Management Studio and connect to a report server instance.</span></span> <span data-ttu-id="3842a-132">자세한 내용은 [온라인 설명서에서](../tools/connect-to-a-report-server-in-management-studio.md) Management Studio에서 보고서 서버에 연결 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3842a-132">For more information, see [Connect to a Report Server in Management Studio](../tools/connect-to-a-report-server-in-management-studio.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
2.  <span data-ttu-id="3842a-133">보고서 서버 노드를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-133">Right-click the report server node, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="3842a-134">**고급** 을 클릭하여 속성 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-134">Click **Advanced** to open the properties page.</span></span> <span data-ttu-id="3842a-135">자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 [서버 속성&#40;고급 페이지&#41; - Reporting Services](../tools/server-properties-advanced-page-reporting-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3842a-135">For more information, see [Server Properties &#40;Advanced Page&#41; - Reporting Services](../tools/server-properties-advanced-page-reporting-services.md)in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
4.  <span data-ttu-id="3842a-136">에서 `EnableRemoteErrors` 을 선택 `True` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-136">In `EnableRemoteErrors`, select `True`.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="enable-remote-errors-through-script-native-mode"></a><a name="bkmk_script"></a> <span data-ttu-id="3842a-137">스크립트를 통한 원격 오류 사용(기본 모드)</span><span class="sxs-lookup"><span data-stu-id="3842a-137">Enable remote errors through script (Native Mode)</span></span>  
  
1.  <span data-ttu-id="3842a-138">텍스트 파일을 만들고 다음 스크립트를 파일에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-138">Create a text file and copy the following script into the file.</span></span>  
  
    ```  
    Public Sub Main()  
      Dim P As New [Property]()  
      P.Name = "EnableRemoteErrors"  
      P.Value = True  
      Dim Properties(0) As [Property]  
      Properties(0) = P  
      Try  
        rs.SetSystemProperties(Properties)  
        Console.WriteLine("Remote errors enabled.")  
      Catch SE As SoapException  
        Console.WriteLine(SE.Detail.OuterXml)  
      End Try  
    End Sub  
    ```  
  
2.  <span data-ttu-id="3842a-139">파일을 EnableRemoteErrors.rss로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-139">Save the file as EnableRemoteErrors.rss.</span></span>  
  
3.  <span data-ttu-id="3842a-140">**시작**을 클릭하고 **실행**을 클릭한 다음 **cmd**를 입력하고 **확인** 을 클릭하여 명령 프롬프트 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-140">Click **Start**, point to **Run**, type **cmd**, and click **OK** to open a command prompt window.</span></span>  
  
4.  <span data-ttu-id="3842a-141">방금 만든 .rss 파일이 포함된 디렉터리로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-141">Navigate to the directory that contains the .rss file you just created.</span></span>  
  
5.  <span data-ttu-id="3842a-142">다음 명령줄을 입력합니다. *servername* 은 서버의 실제 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-142">Type the following command line, replacing *servername* with the actual name of your server:</span></span>  
  
    ```  
    rs -i EnableRemoteErrors.rss -s http://servername/ReportServer  
    ```  
  
6.  <span data-ttu-id="3842a-143">자세한 내용은 [RS.exe 유틸리티&#40;SSRS&#41;](../tools/rs-exe-utility-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3842a-143">For more information, see [RS.exe Utility &#40;SSRS&#41;](../tools/rs-exe-utility-ssrs.md)</span></span>  
  
##  <a name="modifying-the-configurationinfo-table-native-mode"></a><a name="bkmk_ConfigurationInfo"></a> <span data-ttu-id="3842a-144">ConfigurationInfo 테이블 수정(기본 모드)</span><span class="sxs-lookup"><span data-stu-id="3842a-144">Modifying the ConfigurationInfo table (Native Mode)</span></span>  
  
1.  > [!NOTE]  
    >  <span data-ttu-id="3842a-145">보고서 서버 데이터베이스의 **Configurationinfo** 테이블을로 설정 하 여 편집할 수 `EnableRemoteErrors` `True` 있지만 보고서 서버가 현재 사용 중인 경우에는 SQL Server Management Studio 또는 스크립트를 사용 하 여 설정을 수정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-145">You can edit the **ConfigurationInfo** table in the report server database to set `EnableRemoteErrors` to `True`, but if the report server is actively used, you should use SQL Server Management Studio or script to modify the settings.</span></span> <span data-ttu-id="3842a-146">데이터베이스에서 이 설정을 수정하는 경우 변경 내용을 적용하려면 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3842a-146">If you modify the setting in the database, you need to restart the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service before the changes take effect.</span></span>  
  
  
