---
title: Reporting Services 제거 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 5c764a00-d4bc-465d-b32e-e4efce052ce4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2870f7f84ea626b96560af586602996de3657276
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650430"
---
# <a name="uninstall-reporting-services"></a><span data-ttu-id="a5efe-102">Reporting Services 제거</span><span class="sxs-lookup"><span data-stu-id="a5efe-102">Uninstall Reporting Services</span></span>
  <span data-ttu-id="a5efe-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 제거해도 사용자가 만든 콘텐츠나 수정한 구성은 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5efe-103">Uninstalling [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] does not remove the content you have created or configuration you have modified.</span></span> <span data-ttu-id="a5efe-104">그러나 제거를 완료한 후에도 필요한 콘텐츠가 있는 경우 제거 프로세스를 시작하기 전에 콘텐츠를 복사하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a5efe-104">However, if there is content you need after the uninstall is complete, it is recommended you make copies of content before you begin the uninstallation process.</span></span>

## <a name="uninstall-sharepoint-mode"></a><span data-ttu-id="a5efe-105">SharePoint 모드 제거</span><span class="sxs-lookup"><span data-stu-id="a5efe-105">Uninstall SharePoint Mode</span></span>
 <span data-ttu-id="a5efe-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드를 제거하면</span><span class="sxs-lookup"><span data-stu-id="a5efe-106">When you uninstall [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode, the following are removed:</span></span>

-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="a5efe-107">서비스 및 서비스 프록시 항목이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5efe-107">service and service proxy.</span></span>

-   <span data-ttu-id="a5efe-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치에 사용된 파일</span><span class="sxs-lookup"><span data-stu-id="a5efe-108">Files used for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation.</span></span>

 <span data-ttu-id="a5efe-109">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션은 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5efe-109">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications are not removed.</span></span> <span data-ttu-id="a5efe-110">더 이상 사용하지 않으려는 서비스 애플리케이션은 Windows PowerShell 또는 SharePoint 중앙 관리를 사용하여 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="a5efe-110">If you no longer want the service applications, delete them by using Windows PowerShell or SharePoint Central Administration.</span></span>

 <span data-ttu-id="a5efe-111">보고서 항목 및 관련 메타데이터는 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5efe-111">The report items and related meta data are not removed.</span></span> <span data-ttu-id="a5efe-112">이 정보는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션과 관련된 콘텐츠 및 구성 데이터베이스에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5efe-112">This information is contained in the content and configuration databases related to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications.</span></span> <span data-ttu-id="a5efe-113">데이터베이스는 제거되지 않으며 SharePoint 모드의 다른 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치에 데이터베이스를 수동으로 마이그레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5efe-113">The databases are not removed and you can manually migrate the databases to another installation of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="a5efe-114">해당 정보가 더 이상 필요하지 않으면 데이터베이스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="a5efe-114">If you no longer want the information, delete the databases.</span></span> <span data-ttu-id="a5efe-115">자세한 내용은 [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a5efe-115">For more information, see [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).</span></span>

 <span data-ttu-id="a5efe-116">다음은 제거되지 않는 세 가지 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 데이터베이스의 이름 예입니다.</span><span class="sxs-lookup"><span data-stu-id="a5efe-116">The following are example names of the three [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] databases that are not removed.</span></span>

-   <span data-ttu-id="a5efe-117">**보고서 서버 데이터베이스:** eportingService_7f616e2d253040e8ab5653b3c09a065e</span><span class="sxs-lookup"><span data-stu-id="a5efe-117">**Report server database:** ReportingService_7f616e2d253040e8ab5653b3c09a065e</span></span>

-   <span data-ttu-id="a5efe-118">**보고서 서버 임시 데이터베이스:** portingService_7f616e2d253040e8ab5653b3c09a065eTempDB</span><span class="sxs-lookup"><span data-stu-id="a5efe-118">**Report server temp database:** ReportingService_7f616e2d253040e8ab5653b3c09a065eTempDB</span></span>

-   <span data-ttu-id="a5efe-119">**보고서 서버 경고 데이터베이스:** ReportingService_7f616e2d253040e8ab5653b3c09a065e_Alerting</span><span class="sxs-lookup"><span data-stu-id="a5efe-119">**Report server alerting database:** ReportingService_7f616e2d253040e8ab5653b3c09a065e_Alerting</span></span>

### <a name="uninstall-the-add-in-for-sharepoint-products"></a><span data-ttu-id="a5efe-120">SharePoint 제품을 위한 추가 기능을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="a5efe-120">Uninstall the Add-in for SharePoint Products.</span></span>
 <span data-ttu-id="a5efe-121">컴퓨터에서 추가 기능을 제거할 때는 파일만 제거하거나 팜에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기능도 제거할지를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5efe-121">When you uninstall the add-in from a computer, you can choose to only uninstall the files or to also remove the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] feature from the farm.</span></span> <span data-ttu-id="a5efe-122">SharePoint 제품용 추가 기능을 제거 하는 방법에 대 한 자세한 내용은 sharepoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [2010 및 sharepoint 2013&#41;&#40;Reporting Services 추가 기능 설치 또는 제거 ](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a5efe-122">For information on uninstalling the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint products, see [Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).</span></span>

## <a name="uninstall-native-mode"></a><span data-ttu-id="a5efe-123">기본 모드 제거</span><span class="sxs-lookup"><span data-stu-id="a5efe-123">Uninstall Native Mode</span></span>
 <span data-ttu-id="a5efe-124">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기본 모드를 제거하면 설치 후에 **만들었거나** 또는 **수정한** 내용은 그대로 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5efe-124">When you uninstall [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] native mode, anything that was **created** or **modified** after the installation is left in place.</span></span> <span data-ttu-id="a5efe-125">예를 들어 데이터베이스 파일, 로그 파일, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 파일 및 보고서와 데이터 원본 파일과 같은 콘텐츠 항목이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5efe-125">For example database files, log files, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] configuration files, and content items such as reports and datasource files.</span></span>

 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="a5efe-126">는 인스턴스 기능이므로 Windows 제어판, 프로그램 및 기능 목록에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5efe-126">is an instance feature and therefore is not listed in Windows Control Panel, Programs and Features.</span></span> <span data-ttu-id="a5efe-127">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native 모드를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="a5efe-127">To uninstall [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode:</span></span>

1.  <span data-ttu-id="a5efe-128">Windows 제어판에서 **프로그램 및 기능**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a5efe-128">In Windows Control Panel, click **Programs and Features**.</span></span>

2.  <span data-ttu-id="a5efe-129">**프로그램 및 기능** 에서 **Microsoft SQL Server 2012**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a5efe-129">In **Programs and Features** select **Microsoft SQL Server 2012**.</span></span>

3.  <span data-ttu-id="a5efe-130">제거 마법사에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스 기능 **RS**를 포함하는 인스턴스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a5efe-130">In the uninstall wizard, select the instance that includes the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance feature **RS**.</span></span>

     <span data-ttu-id="a5efe-131">![rs_nativemode_uninstall_selectinstance](../../../2014/sql-server/install/media/rs-nativemode-uninstall-selectinstance.gif "rs_nativemode_uninstall_selectinstance")</span><span class="sxs-lookup"><span data-stu-id="a5efe-131">![rs_nativemode_uninstall_selectinstance](../../../2014/sql-server/install/media/rs-nativemode-uninstall-selectinstance.gif "rs_nativemode_uninstall_selectinstance")</span></span>

4.  <span data-ttu-id="a5efe-132">인스턴스를 선택한 후 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기능을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a5efe-132">After you select the instance, select the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] feature.</span></span>

     <span data-ttu-id="a5efe-133">![rs_nativemode_uninstall_selectfeatures](../../../2014/sql-server/install/media/rs-nativemode-uninstall-selectfeatures.gif "rs_nativemode_uninstall_selectfeatures")</span><span class="sxs-lookup"><span data-stu-id="a5efe-133">![rs_nativemode_uninstall_selectfeatures](../../../2014/sql-server/install/media/rs-nativemode-uninstall-selectfeatures.gif "rs_nativemode_uninstall_selectfeatures")</span></span>

5.  <span data-ttu-id="a5efe-134">마법사를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="a5efe-134">Complete the wizard.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5efe-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a5efe-135">See Also</span></span>
 <span data-ttu-id="a5efe-136">[설치 &#40;SQL Server의 기존 인스턴스를 제거&#41;](../../../2014/sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md) sharepoint 2013 &#40;추가 기능을 [설치 또는 SharePoint용 PowerPivot 제거&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) sharepoint [2010 및 sharepoint 2013 Reporting Services 추가 기능을 설치 하거나 제거](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md) &#40;</span><span class="sxs-lookup"><span data-stu-id="a5efe-136">[Uninstall an Existing Instance of SQL Server &#40;Setup&#41;](../../../2014/sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md) [Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) [Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)</span></span>


