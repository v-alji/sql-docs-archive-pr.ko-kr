---
title: 라이브러리에 보고서 서버 콘텐츠 형식 추가 (SharePoint 통합 모드의 Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ac9136c8-9ef4-484c-8e9d-05008a186db5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9e0ee56c235a54920fba5389a61f300eeaa65329
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739604"
---
# <a name="add-report-server-content-types-to-a-library-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="40960-102">Add Report Server Content Types to a Library (Reporting Services in SharePoint Integrated Mode)</span><span class="sxs-lookup"><span data-stu-id="40960-102">Add Report Server Content Types to a Library (Reporting Services in SharePoint Integrated Mode)</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="40960-103">공유 데이터 원본(.rsds) 파일, 보고서 모델(.smdl) 및 보고서 작성기 보고서 정의(.rdl) 파일을 관리하는 데 사용되는 미리 정의된 SharePoint 콘텐츠 형식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-103">provides predefined SharePoint content types that are used to manage shared data source (.rsds) files, report models (.smdl), and Report Builder report definition (.rdl) files.</span></span> <span data-ttu-id="40960-104">**보고서 작성기 보고서**, **보고서 모델**및 **보고서 데이터 원본** 콘텐츠 형식을 라이브러리에 추가하면 해당 유형의 새 문서를 만들 수 있도록 **새로 만들기** 명령이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="40960-104">Adding a **Report Builder Report**, **Report Model**, and **Report Data Source** content type to a library enables the **New** command so that you can create new documents of that type.</span></span>  
  
 <span data-ttu-id="40960-105">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]SharePoint 모드</span><span class="sxs-lookup"><span data-stu-id="40960-105">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>  
  
 <span data-ttu-id="40960-106">라이브러리에 콘텐츠 형식을 추가하려면 사이트 관리자이거나 모든 권한 수준의 사용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-106">To add content types to a library, you must be a site administrator or have Full Control level of permission.</span></span>  
  
 <span data-ttu-id="40960-107">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 콘텐츠 형식 및 콘텐츠 형식 관리가 다음 **비즈니스 인텔리전스 센터** 사이트 템플릿 형식에서 생성된 기존 사이트 모음의 모든 문서 라이브러리에서 자동으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="40960-107">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content types and content type management will automatically be enabled in all document libraries for existing site collections created from the following **Business Intelligence Center** site template.</span></span>  
  
 <span data-ttu-id="40960-108">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 통합 후에 생성된 사이트에는 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 콘텐츠 형식이 설정되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40960-108">Sites created after the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] integration will not have the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content types enabled.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="40960-109">라이브러리에 이전에 구성한 콘텐츠 형식이 **없는** 경우 먼저 콘텐츠 형식 관리를 설정한 다음 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 콘텐츠 형식을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-109">If you have **not** previously configured content types for a library, first enable management of content types, then enable the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content types.</span></span> <span data-ttu-id="40960-110">단일 문서 라이브러리에서 콘텐츠 형식 관리 설정에 대한 절차를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="40960-110">See the procedures on enabling content type management in a single document library.</span></span>  
  
 <span data-ttu-id="40960-111">**짧은 비디오:** [(SSRS)Enabling Content Types in SharePoint2010.wmv](http://www.youtube.com/watch?v=yqhm3DrtT1w)(http://www.youtube.com/watch?v=yqhm3DrtT1w).</span><span class="sxs-lookup"><span data-stu-id="40960-111">**Short video:** [(SSRS) Enabling Content Types in SharePoint2010.wmv](http://www.youtube.com/watch?v=yqhm3DrtT1w) (http://www.youtube.com/watch?v=yqhm3DrtT1w).</span></span>  
  
 <span data-ttu-id="40960-112">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="40960-112">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="40960-113">기존 BI 센터에서 모든 문서 라이브러리의 콘텐츠 형식 설정</span><span class="sxs-lookup"><span data-stu-id="40960-113">Enable content types in all document libraries in an existing BI center</span></span>](#bkmk_enable_all)  
  
-   [<span data-ttu-id="40960-114">단일 문서 라이브러리에 대해 콘텐츠 형식 관리를 설정하려면(SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="40960-114">To enable content type management for a single document library (SharePoint 2013)</span></span>](#bkmk_enable_content_management)  
  
-   [<span data-ttu-id="40960-115">Reporting Services 콘텐츠 형식을 추가 하려면 (SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="40960-115">To add Reporting Services content types (SharePoint 2013)</span></span>](#bkmk_add_single)  
  
-   [<span data-ttu-id="40960-116">단일 문서 라이브러리에 대해 콘텐츠 형식 관리를 설정하려면(SharePoint 2010)</span><span class="sxs-lookup"><span data-stu-id="40960-116">To enable content type management for a single document library (SharePoint 2010)</span></span>](#bkmk_enable_content_management_2010)  
  
-   [<span data-ttu-id="40960-117">보고서 서버 콘텐츠 형식을 추가하려면(SharePoint 2010)</span><span class="sxs-lookup"><span data-stu-id="40960-117">To add report server content types (SharePoint 2010)</span></span>](#bkmk_add_single_2010)  
  
-   [<span data-ttu-id="40960-118">여러 BI 사이트에 대해 콘텐츠 형식 및 콘텐츠 관리를 사용 하도록 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="40960-118">To enable Content types and content management for multiple BI sites</span></span>](#bkmk_enable_multiple_sites)  
  
##  <a name="enable-content-types-in-all-document-libraries-in-an-existing-bi-center"></a><a name="bkmk_enable_all"></a><span data-ttu-id="40960-119">기존 BI 센터의 모든 문서 라이브러리에서 콘텐츠 형식 사용</span><span class="sxs-lookup"><span data-stu-id="40960-119">Enable content types in all document libraries in an existing BI center</span></span>  
  
1.  <span data-ttu-id="40960-120">기존 **비즈니스 인텔리전스 센터** 사이트의 모든 문서 라이브러리에서 콘텐츠 형식 및 콘텐츠 관리를 설정하려면 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 통합 기능을 설정/해제하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40960-120">To enable the content types and content management in all document libraries in an existing **Business Intelligence Center** site, you can toggle the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] integration feature.</span></span>  
  
2.  <span data-ttu-id="40960-121">**사이트 설정**으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-121">Go to **Site settings**.</span></span>  
  
    -   <span data-ttu-id="40960-122">SharePoint 2013에서 **설정** 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-122">In SharePoint 2013, click the **Settings** icon.</span></span> <span data-ttu-id="40960-123">![SharePoint 설정](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 설정")</span><span class="sxs-lookup"><span data-stu-id="40960-123">![SharePoint Settings](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings")</span></span>  
  
    -   <span data-ttu-id="40960-124">SharePoint 2010에서 **사이트 동작**을 클릭한 다음 **사이트 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-124">In SharePoint 2010, click **Site Actions**, then click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="40960-125">**사이트 모음 기능**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-125">Click **Site collection features**.</span></span>  
  
4.  <span data-ttu-id="40960-126">**보고서 서버 통합 기능** 을 찾고 **비활성화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-126">Find the **Report Server Integration Feature** and click **Deactivate**.</span></span>  
  
     <span data-ttu-id="40960-127">![rs_reportserver_integration_active](media/rs-reportserver-integration-active.gif "rs_reportserver_integration_active")</span><span class="sxs-lookup"><span data-stu-id="40960-127">![rs_reportserver_integration_active](media/rs-reportserver-integration-active.gif "rs_reportserver_integration_active")</span></span>  
  
5.  <span data-ttu-id="40960-128">브라우저를 새로 고친 다음 **보고서 서버 통합 기능** 에 대해 **활성화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-128">Refresh the browser then click **Activate** for the **Report Server Integration Feature**.</span></span>  
  
    <span data-ttu-id="40960-129">![Deactivate](media/rs-reportserver-integration-deactivate.gif "rs_reportserver_integration_deactive")</span><span class="sxs-lookup"><span data-stu-id="40960-129">![Deactivate](media/rs-reportserver-integration-deactivate.gif "rs_reportserver_integration_deactive")</span></span>  
  
##  <a name="to-enable-content-type-management-for-a-single-document-library-sharepoint-2013"></a><a name="bkmk_enable_content_management"></a><span data-ttu-id="40960-130">단일 문서 라이브러리에 대해 콘텐츠 형식 관리를 설정 하려면 (SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="40960-130">To enable content type management for a single document library (SharePoint 2013)</span></span>  
  
1.  <span data-ttu-id="40960-131">여러 개의 콘텐츠 형식을 설정할 라이브러리를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="40960-131">Open the library for which you want to enable multiple content types.</span></span>  
  
2.  <span data-ttu-id="40960-132">리본에서 **라이브러리** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-132">Click **Library** in the ribbon.</span></span>  
  
     <span data-ttu-id="40960-133">![rs_SharePoint2013_LibraryRibbon](media/rs-sharepoint2013-libraryribbon.gif "rs_SharePoint2013_LibraryRibbon")</span><span class="sxs-lookup"><span data-stu-id="40960-133">![rs_SharePoint2013_LibraryRibbon](media/rs-sharepoint2013-libraryribbon.gif "rs_SharePoint2013_LibraryRibbon")</span></span>  
  
3.  <span data-ttu-id="40960-134">**라이브러리** 리본에서 **라이브러리 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-134">On the **Library** ribbon, click **Library Settings**.</span></span> <span data-ttu-id="40960-135">**라이브러리 설정** 이 표시되지 않거나 단추가 비활성화되는 경우 콘텐츠 형식을 비롯하여 라이브러리 설정을 구성할 수 있는 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="40960-135">If you do not see **Library Settings** or the button is disabled, you do not have permission to configure library settings, including content types.</span></span>  
  
     <span data-ttu-id="40960-136">![rs_SharePoint2013_LibrarySettings](media/rs-sharepoint2013-librarysettings.gif "rs_SharePoint2013_LibrarySettings")</span><span class="sxs-lookup"><span data-stu-id="40960-136">![rs_SharePoint2013_LibrarySettings](media/rs-sharepoint2013-librarysettings.gif "rs_SharePoint2013_LibrarySettings")</span></span>  
  
4.  <span data-ttu-id="40960-137">**일반 설정** 섹션에서 **고급 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-137">In the **General Settings** section, click **Advanced settings**.</span></span>  
  
     <span data-ttu-id="40960-138">![rs_SharePoint2013_LibrarySettings_AdvancedSettings](media/rs-sharepoint2013-librarysettings-advancedsettings.gif "rs_SharePoint2013_LibrarySettings_AdvancedSettings")</span><span class="sxs-lookup"><span data-stu-id="40960-138">![rs_SharePoint2013_LibrarySettings_AdvancedSettings](media/rs-sharepoint2013-librarysettings-advancedsettings.gif "rs_SharePoint2013_LibrarySettings_AdvancedSettings")</span></span>  
  
5.  <span data-ttu-id="40960-139">**콘텐츠 형식** 섹션에서 **예** 를 선택하여 콘텐츠 형식 관리를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-139">In the **Content Types** section, select **Yes** to allow management of content types.</span></span>  
  
6.  <span data-ttu-id="40960-140">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-140">Click **OK**.</span></span>  
  
##  <a name="to-add-reporting-services-content-types-sharepoint-2013"></a><a name="bkmk_add_single"></a> <span data-ttu-id="40960-141">Reporting Services 콘텐츠 형식을 추가하려면(SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="40960-141">To add Reporting Services content types (SharePoint 2013)</span></span>  
  
1.  <span data-ttu-id="40960-142">Reporting Services 콘텐츠 형식을 추가할 라이브러리를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="40960-142">Open the library for which you want to add Reporting Services content types.</span></span>  
  
2.  <span data-ttu-id="40960-143">리본에서 **라이브러리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-143">On the ribbon, click **Library**.</span></span>  
  
3.  <span data-ttu-id="40960-144">**라이브러리 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-144">Click **Library Settings**.</span></span>  
  
4.  <span data-ttu-id="40960-145">**콘텐츠 형식**에서 **기존 사이트 콘텐츠 형식에서 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-145">Under **Content Types**, click **Add from existing site content types**.</span></span>  
  
5.  <span data-ttu-id="40960-146">**사이트 콘텐츠 형식을 선택**에서 **SQL Server Reporting Services 콘텐츠 형식**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-146">In **Select site content types from**, select **SQL Server Reporting Services Content Types**.</span></span>  
  
6.  <span data-ttu-id="40960-147">**사용 가능한 사이트 콘텐츠 형식** 목록에서 **보고서 작성기**를 클릭한 다음 **추가** 를 클릭하여 선택한 콘텐츠 형식을 **추가할 콘텐츠 형식** 목록으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-147">In the **Available Site Content Types** list, click **Report Builder**, and then click **Add** to move the selected content type to the **Content types to add** list.</span></span>  
  
7.  <span data-ttu-id="40960-148">**보고서 모델** 및 **보고서 데이터 원본** 콘텐츠 형식을 추가하려면 이전 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-148">To add **Report Model** and **Report Data Source** content types, repeat the previous step.</span></span>  
  
8.  <span data-ttu-id="40960-149">콘텐츠 형식 추가를 완료하면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-149">When you finish adding content types, click **OK**.</span></span>  
  
9. > [!NOTE]  
    >  <span data-ttu-id="40960-150">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 콘텐츠 형식 그룹 **SQL Server Reporting Services 콘텐츠 형식** 이 **콘텐츠 형식 추가** 페이지에 표시되지 않는 경우 다음 조건 중 하나에 해당하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="40960-150">If the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content type group **SQL Server Reporting Services Content Types** is not visible on the **Add Content Types** page, one of the following conditions is true:</span></span>  
  
    -   <span data-ttu-id="40960-151">SharePoint 제품의 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 추가 기능이 설치되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="40960-151">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] add-in for SharePoint products has not been installed.</span></span> <span data-ttu-id="40960-152">자세한 내용은 sharepoint [2010 및 sharepoint 2013&#41;&#40;Reporting Services 추가 기능 설치 또는 제거 ](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="40960-152">For more information, see [Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).</span></span> <span data-ttu-id="40960-153">이 항목에는 문제를 해결하기 위한 추가 기능 설치 및 추가 기능 설치 파일의 단계별 실행에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="40960-153">The topic includes information on installing the add-in and stepping through a files only installation of the add-in to work around issues.</span></span>  
  
    -   <span data-ttu-id="40960-154">추가 기능은 설치되지만 사이트 모음 기능 **보고서 서버 통합 기능** 은 활성화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40960-154">The add-in is installed but the site collection feature **Report Server Integration Feature** is not active.</span></span> <span data-ttu-id="40960-155">**사이트 설정**에서 사이트 모음 기능을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-155">Verify the site collection feature in **Site Settings**.</span></span>  
  
    -   <span data-ttu-id="40960-156">모든 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 콘텐츠 형식이 라이브러리에 이미 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="40960-156">All of the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content types have already been added to the library.</span></span> <span data-ttu-id="40960-157">모든 콘텐츠 유형이 라이브러리의 일부인 경우 그룹이 **콘텐츠 형식 추가** 페이지에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="40960-157">If all the content types are part of a library, then the group is removed from the **Add Content Types** page.</span></span> <span data-ttu-id="40960-158">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 콘텐츠 형식 중 하나 이상을 제거하는 경우 **SQL Server Reporting Services 콘텐츠 형식** 그룹이 **콘텐츠 형식 추가** 페이지에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="40960-158">If you delete one or more of the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content types, then the group **SQL Server Reporting Services Content Types** will be visible on the **Add Content Types** page.</span></span>  
  
##  <a name="to-enable-content-type-management-for-a-single-document-library-sharepoint-2010"></a><a name="bkmk_enable_content_management_2010"></a><span data-ttu-id="40960-159">단일 문서 라이브러리에 대해 콘텐츠 형식 관리를 설정 하려면 (SharePoint 2010)</span><span class="sxs-lookup"><span data-stu-id="40960-159">To enable content type management for a single document library (SharePoint 2010)</span></span>  
  
1.  <span data-ttu-id="40960-160">여러 개의 콘텐츠 형식을 설정할 라이브러리를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="40960-160">Open the library for which you want to enable multiple content types.</span></span> <span data-ttu-id="40960-161">라이브러리 메뉴 모음에 **새로 만들기**, **업로드**, **동작**및 **설정**메뉴가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="40960-161">On the library menu bar, you should see the following menus: **New**, **Upload**, **Actions**, and **Settings**.</span></span> <span data-ttu-id="40960-162">**설정**이 표시되지 않는 경우 콘텐츠 형식을 추가할 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="40960-162">If you do not see **Settings**, you do not have permission to add a content type.</span></span>  
  
2.  <span data-ttu-id="40960-163">**라이브러리 도구** 리본에서 **라이브러리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-163">On the **Library Tools** ribbon, click **Library**.</span></span>  
  
     <span data-ttu-id="40960-164">![rs_SharePoint2010_LibraryRibbon](media/rs-sharepoint2010-libraryribbon.gif "rs_SharePoint2010_LibraryRibbon")</span><span class="sxs-lookup"><span data-stu-id="40960-164">![rs_SharePoint2010_LibraryRibbon](media/rs-sharepoint2010-libraryribbon.gif "rs_SharePoint2010_LibraryRibbon")</span></span>  
  
3.  <span data-ttu-id="40960-165">**설정** 리본 그룹에서 **라이브러리 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-165">On the **Settings** ribbon group, click **Library Settings**.</span></span>  
  
4.  <span data-ttu-id="40960-166">**일반 설정**에서 **고급 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-166">Under **General Settings**, click **Advanced settings**.</span></span>  
  
5.  <span data-ttu-id="40960-167">**콘텐츠 형식** 섹션에서 **예** 를 선택하여 콘텐츠 형식 관리를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-167">In the **Content Types** section, select **Yes** to allow management of content types.</span></span>  
  
6.  <span data-ttu-id="40960-168">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-168">Click **OK**.</span></span>  
  
##  <a name="to-add-report-server-content-types-sharepoint-2010"></a><a name="bkmk_add_single_2010"></a><span data-ttu-id="40960-169">보고서 서버 콘텐츠 형식을 추가 하려면 (SharePoint 2010)</span><span class="sxs-lookup"><span data-stu-id="40960-169">To add report server content types (SharePoint 2010)</span></span>  
  
1.  <span data-ttu-id="40960-170">Reporting Services 콘텐츠 형식을 추가할 라이브러리를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="40960-170">Open the library for which you want to add Reporting Services content types.</span></span>  
  
2.  <span data-ttu-id="40960-171">**라이브러리 도구** 리본 탭에서 **라이브러리 탭**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-171">On the **Library Tools** ribbon tabs, click the **Library tab**.</span></span>  
  
3.  <span data-ttu-id="40960-172">**설정** 리본 그룹에서 **라이브러리 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-172">On the **Settings** ribbon group, click **Library Settings**.</span></span>  
  
4.  <span data-ttu-id="40960-173">**콘텐츠 형식**에서 **기존 사이트 콘텐츠 형식에서 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-173">Under **Content Types**, click **Add from existing site content types**.</span></span>  
  
5.  <span data-ttu-id="40960-174">**콘텐츠 형식 선택** 섹션의 **사이트 콘텐츠 형식 선택**에서 화살표를 클릭하여 **SQL Server Reporting Services 콘텐츠 형식**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-174">In the **Select Content Types** section, in **Select site content types from**, click the arrow to select **SQL Server Reporting Services Content Types**.</span></span>  
  
6.  <span data-ttu-id="40960-175">**사용 가능한 사이트 콘텐츠 형식** 목록에서 **보고서 작성기**를 클릭한 다음 **추가** 를 클릭하여 선택한 콘텐츠 형식을 **추가할 콘텐츠 형식** 목록으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-175">In the **Available Site Content Types** list, click **Report Builder**, and then click **Add** to move the selected content type to the **Content types to add** list.</span></span>  
  
7.  <span data-ttu-id="40960-176">**보고서 모델** 및 **보고서 데이터 원본** 콘텐츠 형식을 추가하려면 이전 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-176">To add **Report Model** and **Report Data Source** content types, repeat the previous step.</span></span>  
  
8.  <span data-ttu-id="40960-177">콘텐츠 형식 추가를 완료하면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-177">When you finish adding content types, click **OK**.</span></span>  
  
##  <a name="to-enable-content-types-and-content-management-for-multiple-bi-sites"></a><a name="bkmk_enable_multiple_sites"></a><span data-ttu-id="40960-178">여러 BI 사이트에 대해 콘텐츠 형식 및 콘텐츠 관리를 사용 하도록 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="40960-178">To enable Content types and content management for multiple BI sites</span></span>  
  
1.  <span data-ttu-id="40960-179">SQL Server Reporting Services 2008 및 2008 R2 보고서 서버의 경우 여러 비즈니스 인텔리전스 센터 사이트에 대한 콘텐츠 형식 및 콘텐츠 관리를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40960-179">For SQL Server Reporting Services 2008 and 2008 R2 report servers, you can enable content types and content management for multiple Business Intelligence Center sites:</span></span>  
  
2.  <span data-ttu-id="40960-180">SharePoint 중앙 관리에서 **일반 애플리케이션 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-180">In SharePoint Central Administration, click **General Applications settings**.</span></span> <span data-ttu-id="40960-181">**SQL Server Reporting Services(2008 및 2008 R2)** 섹션에서 **Reporting Services 통합**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-181">In the **SQL Server Reporting Services (2008 and 2008 R2)** section, click **Reporting Services Integration**.</span></span>  
  
     <span data-ttu-id="40960-182">![rs_general_app_settings](media/rs-general-app-settings.gif "rs_general_app_settings")</span><span class="sxs-lookup"><span data-stu-id="40960-182">![rs_general_app_settings](media/rs-general-app-settings.gif "rs_general_app_settings")</span></span>  
  
3.  <span data-ttu-id="40960-183">**모든 흥미로운 사이트 모음에서 기능 활성화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-183">Click **Activate feature in all exciting site collections**.</span></span>  
  
     <span data-ttu-id="40960-184">![rs_general_app_settings_old_integrations](media/rs-general-app-settings-old-integrations.gif "rs_general_app_settings_old_integrations")</span><span class="sxs-lookup"><span data-stu-id="40960-184">![rs_general_app_settings_old_integrations](media/rs-general-app-settings-old-integrations.gif "rs_general_app_settings_old_integrations")</span></span>  
  
4.  <span data-ttu-id="40960-185">**Ok**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40960-185">Click **Ok**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40960-186">참고 항목</span><span class="sxs-lookup"><span data-stu-id="40960-186">See Also</span></span>  
 <span data-ttu-id="40960-187">[보고서 서버 항목에 대 한 SharePoint 사이트 및 목록 사용 권한 참조](security/sharepoint-site-and-list-permission-reference-for-report-server-items.md) </span><span class="sxs-lookup"><span data-stu-id="40960-187">[SharePoint Site and List Permission Reference for Report Server Items](security/sharepoint-site-and-list-permission-reference-for-report-server-items.md) </span></span>  
 [<span data-ttu-id="40960-188">&#41;&#40;보고서 작성기를 시작 보고서 작성기</span><span class="sxs-lookup"><span data-stu-id="40960-188">Start Report Builder &#40;Report Builder&#41;</span></span>](report-builder/start-report-builder.md)  
  
  
