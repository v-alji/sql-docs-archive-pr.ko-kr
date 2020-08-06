---
title: Reporting Services SharePoint 서비스 응용 프로그램 백업 및 복원 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: dfb4ed77-90e5-4273-b690-89a945508ed2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 488659d269542381be9bcf1b1b6115acf89f8a98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650811"
---
# <a name="backup-and-restore-reporting-services-sharepoint-service-applications"></a><span data-ttu-id="733fe-102">Reporting Services SharePoint 서비스 애플리케이션 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="733fe-102">Backup and Restore Reporting Services SharePoint Service Applications</span></span>
  <span data-ttu-id="733fe-103">이 항목에서는 SharePoint 중앙 관리 또는 PowerShell을 사용하여 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스 애플리케이션을 백업하고 복원하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-103">This topic describes how to backup and restore a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] services application using SharePoint Central Administration or PowerShell.</span></span> <span data-ttu-id="733fe-104">이 항목에는 다음과 같은 내용이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-104">The topic contains:</span></span>  
  
-   [<span data-ttu-id="733fe-105">제한 사항</span><span class="sxs-lookup"><span data-stu-id="733fe-105">Limitations and Restrictions</span></span>](#bkmk_Restrictions)  
  
-   [<span data-ttu-id="733fe-106">서비스 응용 프로그램 백업</span><span class="sxs-lookup"><span data-stu-id="733fe-106">Backup The Service application</span></span>](#bkmk_backup)  
  
-   [<span data-ttu-id="733fe-107">서비스 응용 프로그램 복원</span><span class="sxs-lookup"><span data-stu-id="733fe-107">Restore the Service Application</span></span>](#bkmk_restore)  
  
##  <a name="before-you-begin"></a><a name="bkmk_BeforeYouBegin"></a> <span data-ttu-id="733fe-108">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="733fe-108">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="bkmk_Restrictions"></a> <span data-ttu-id="733fe-109">제한 사항</span><span class="sxs-lookup"><span data-stu-id="733fe-109">Limitations and Restrictions</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="733fe-110">서비스 애플리케이션은 SharePoint 백업 및 복원 기능을 사용하여 부분적으로 백업 및 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-110">service applications can partially be backed up and restored using the SharePoint backup and restore functionality.</span></span> <span data-ttu-id="733fe-111">**추가 단계를 수행해야 하며** 단계는 이 항목에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-111">**Additional steps are required** and the steps are documented in this topic.</span></span> <span data-ttu-id="733fe-112">현재는 백업 프로세스를 진행해도 **데이터베이스에 대한 Windows 인증 또는 UEA(무인 실행 계정)를 위한 암호화 키 및 자격 증명이 백업되지** 않습니다 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="733fe-112">Currently the backup process **does not** backup encryption keys and credentials for unattended execution accounts (UEA) or windows authentication to the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] database.</span></span>  
  
###  <a name="recommendations"></a><a name="bkmk_recommendations"></a> <span data-ttu-id="733fe-113">권장 사항</span><span class="sxs-lookup"><span data-stu-id="733fe-113">Recommendations</span></span>  
  
-   <span data-ttu-id="733fe-114">SharePoint 백업을 시작하기 전에 암호화 키를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-114">Backup the encryption keys before starting the SharePoint backup.</span></span> <span data-ttu-id="733fe-115">암호화 키를 백업하지 않으면 서비스 애플리케이션을 복원한 후 암호화된 데이터에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-115">If you do not backup the encryption keys, then you will not be able to access your encrypted data, following the restore of the service application.</span></span> <span data-ttu-id="733fe-116">이 경우 암호화된 데이터를 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-116">You will need to delete your encrypted data.</span></span>  
  
-   <span data-ttu-id="733fe-117">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스 애플리케이션에 데이터베이스 액세스를 위해 UEA 또는 Windows 인증이 사용되고 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-117">Verify if your [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application is using UEA or Windows authentication for database access.</span></span> <span data-ttu-id="733fe-118">둘 중 하나가 사용되고 있는 경우 복원 프로세스 후에 서비스 애플리케이션을 올바르게 구성할 수 있도록 적절한 자격 증명이 무엇인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-118">If it is using either, verify what the proper credentials are so you can correctly configure the service application after the restore process.</span></span>  
  
-   <span data-ttu-id="733fe-119">SharePoint 백업 로그가 백업 파일과 동일한 폴더에 생성되어 있는지 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-119">Review the SharePoint backup log is created in the same folder as the backup file.</span></span> <span data-ttu-id="733fe-120">이 파일의 이름은 일반적으로 **spbackup.log**입니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-120">The file is typically named **spbackup.log**</span></span>  
  
##  <a name="backup-the-service-application"></a><a name="bkmk_backup"></a><span data-ttu-id="733fe-121">서비스 응용 프로그램 백업</span><span class="sxs-lookup"><span data-stu-id="733fe-121">Backup The Service application</span></span>  
 <span data-ttu-id="733fe-122">다음 단계를 순서대로 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="733fe-122">Complete the following steps in order:</span></span>  
  
1.  <span data-ttu-id="733fe-123">암호화 키를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-123">Backup the encryption keys</span></span>  
  
2.  <span data-ttu-id="733fe-124">서비스 애플리케이션 백업</span><span class="sxs-lookup"><span data-stu-id="733fe-124">Backup the Service application</span></span>  
  
3.  <span data-ttu-id="733fe-125">서비스 애플리케이션에 데이터베이스 액세스를 위해 UEA 또는 Windows 인증이 사용되고 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-125">Verify if you service application uses an UEA or Windows authentication for database access.</span></span> <span data-ttu-id="733fe-126">둘 중 하나가 사용되고 있는 경우 복원 후에 서비스 애플리케이션을 구성하는 데 사용할 수 있도록 자격 증명을 기록해 둡니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-126">If it does, make a note of the credentials so you can use them to configure the service application after it is restored.</span></span>  
  
### <a name="backup-the-encryption-keys-using-central-administration"></a><span data-ttu-id="733fe-127">중앙 관리를 사용하여 암호화 키 백업</span><span class="sxs-lookup"><span data-stu-id="733fe-127">Backup the Encryption Keys using Central Administration</span></span>  
 <span data-ttu-id="733fe-128">암호화 키를 백업 하는 방법에 대 한 자세한 내용은 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [SharePoint 서비스 응용 프로그램 Reporting Services 관리](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)의 "암호화 키" 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="733fe-128">For information on backing up the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] encryption keys, see the "Encryption Keys" section of [Manage a Reporting Services SharePoint Service Application](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md).</span></span>  
  
###  <a name="backup-the-service-application-using-sharepoint-central-administration"></a><a name="bkmk_centraladmin"></a><span data-ttu-id="733fe-129">SharePoint 중앙 관리를 사용 하 여 서비스 응용 프로그램 백업</span><span class="sxs-lookup"><span data-stu-id="733fe-129">Backup the Service application Using SharePoint Central Administration</span></span>  
 <span data-ttu-id="733fe-130">서비스 애플리케이션을 백업하려면 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="733fe-130">To back up the Service Application, complete the following steps:</span></span>  
  
1.  <span data-ttu-id="733fe-131">SharePoint 중앙 관리의 **백업 및 복원** 그룹에서 **백업 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-131">In SharePoint Central Administration Click **Perform a backup** in the **Backup and Restore** group.</span></span>  
  
2.  <span data-ttu-id="733fe-132">**공유 서비스** 노드에서 **공유 서비스 애플리케이션** 을 확장하고 서비스 애플리케이션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-132">Under the **Shared Services** node, expand **Shared Service Applications** and select your service application.</span></span> <span data-ttu-id="733fe-133">유형은 **SQL Server Reporting Services 서비스 애플리케이션**입니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-133">It will have a type of **SQL Server Reporting Services Service Application**.</span></span>  
  
3.  <span data-ttu-id="733fe-134">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-134">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="733fe-135">**백업 위치:** 에 대한 경로를 입력하고 **백업 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-135">Type the path for the **Backup location:** and click **Start Backup**</span></span>  
  
5.  <span data-ttu-id="733fe-136">위 프로세스를 반복하되 서비스 애플리케이션을 선택하는 대신 **공유 서비스 프록시** 노드를 확장하고 서비스 애플리케이션 프록시를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-136">Repeat the process above but instead of selecting the service application, expand the **Shared Services Proxies** node, and select service application proxy.</span></span> <span data-ttu-id="733fe-137">유형은 **SQL Server Reporting Services 서비스 애플리케이션 프록시**입니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-137">It will have a type of **SQL Server Reporting Services Service Application Proxy**.</span></span>  
  
 <span data-ttu-id="733fe-138">자세한 내용은 SharePoint 설명서의 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="733fe-138">For more information, see the following topics in the SharePoint documentation:</span></span>  
  
 <span data-ttu-id="733fe-139">[SharePoint 설명서의 서비스 애플리케이션 백업(SharePoint Foundation 2010)](https://msdn.microsoft.com/library/ee748601.aspx)</span><span class="sxs-lookup"><span data-stu-id="733fe-139">[Back up a service application (SharePoint Foundation 2010) in the SharePoint documenttation](https://msdn.microsoft.com/library/ee748601.aspx).</span></span>  
  
 [<span data-ttu-id="733fe-140">서비스 애플리케이션 백업(SharePoint Server 2010)</span><span class="sxs-lookup"><span data-stu-id="733fe-140">Back up a service application (SharePoint Server 2010)</span></span>](https://technet.microsoft.com/library/ee428318.aspx)  
  
### <a name="verify-execution-account-and-database-authentication"></a><span data-ttu-id="733fe-141">실행 계정 및 데이터베이스 인증 확인</span><span class="sxs-lookup"><span data-stu-id="733fe-141">Verify Execution Account and Database Authentication</span></span>  
 <span data-ttu-id="733fe-142">**실행 계정:** 서비스 애플리케이션에 실행 계정이 사용되고 있는지 확인하려면</span><span class="sxs-lookup"><span data-stu-id="733fe-142">**Execution Account:** To verify if your service application is using an execution account:</span></span>  
  
1.  <span data-ttu-id="733fe-143">SharePoint 중앙 관리의 **응용 프로그램 관리** 그룹에서 **서비스 응용 프로그램 관리** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-143">In SharePoint Central Administration, click **Manage Service Applications** in the **Application Management** group.</span></span>  
  
2.  <span data-ttu-id="733fe-144">서비스 응용 프로그램의 이름을 클릭 한 다음 SharePoint 리본에서 **관리** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-144">Click the name of your service application and then click **Manage** in the SharePoint Ribbon.</span></span>  
  
3.  <span data-ttu-id="733fe-145">**실행 계정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-145">Click **Execution Account**.</span></span>  
  
4.  <span data-ttu-id="733fe-146">실행 계정이 구성된 경우 서비스 애플리케이션 백업을 복원할 때 자격 증명을 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-146">If an execution account is configured, you need to know the credentials when it is time to restore the service application backup.</span></span> <span data-ttu-id="733fe-147">올바른 자격 증명을 알 때까지 백업 및 복원 절차를 진행하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="733fe-147">Do not proceed with the backup and restore procedure until you know the correct credentials.</span></span>  
  
 <span data-ttu-id="733fe-148">**데이터베이스 인증:** 서비스 애플리케이션에 데이터베이스 인증을 위해 Windows 인증이 사용되고 있는지 확인하려면</span><span class="sxs-lookup"><span data-stu-id="733fe-148">**Database Authentication:** To verify if your service application is using Windows Authentication for the database authentication:</span></span>  
  
1.  <span data-ttu-id="733fe-149">SharePoint 중앙 관리의 **응용 프로그램 관리** 그룹에서 **서비스 응용 프로그램 관리** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-149">In SharePoint Central Administration, click **Manage Service Applications** in the **Application Management** group.</span></span>  
  
2.  <span data-ttu-id="733fe-150">서비스 애플리케이션의 이름을 클릭한 다음 SharePoint 리본에서 **속성** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-150">Click the name of your service application and then click **Properties** in the SharePoint Ribbon.</span></span>  
  
3.  <span data-ttu-id="733fe-151">**Reporting Services(SSRS) 서비스 데이터베이스** 섹션을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-151">Review the **Reporting Services (SSRS) Service Database** section.</span></span>  
  
4.  <span data-ttu-id="733fe-152">Windows 인증이 구성된 경우 복원 후 서비스 애플리케이션을 구성할 수 있도록 자격 증명을 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-152">If Windows Authentication is configured, you need to know the credentials so you can configure the service application after you restore it.</span></span> <span data-ttu-id="733fe-153">올바른 자격 증명을 알 때까지 백업 및 복원 절차를 진행하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="733fe-153">Do not proceed with the backup and restore procedure until you know the correct credentials.</span></span>  
  
##  <a name="restore-the-service-application"></a><a name="bkmk_restore"></a><span data-ttu-id="733fe-154">서비스 응용 프로그램 복원</span><span class="sxs-lookup"><span data-stu-id="733fe-154">Restore the Service Application</span></span>  
 <span data-ttu-id="733fe-155">다음 단계를 순서대로 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="733fe-155">Complete the following steps in order:</span></span>  
  
1.  <span data-ttu-id="733fe-156">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스 애플리케이션을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-156">Restore the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
2.  <span data-ttu-id="733fe-157">암호화 키를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-157">Restore the encryption keys</span></span>  
  
3.  <span data-ttu-id="733fe-158">서비스 애플리케이션에 데이터베이스 액세스를 위해 실행 계정 또는 Windows 인증이 사용되고 있었던 경우 자격 증명을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-158">If your service application was using an execution account or Windows authentication for database access, configure the credentials.</span></span>  
  
### <a name="restore-the-service-application-using-sharepoint-central-administration"></a><span data-ttu-id="733fe-159">SharePoint 중앙 관리를 사용하여 서비스 애플리케이션 복원</span><span class="sxs-lookup"><span data-stu-id="733fe-159">Restore the Service application Using SharePoint Central Administration</span></span>  
  
1.  <span data-ttu-id="733fe-160">SharePoint 중앙 관리의 **백업 및 복원** 그룹에서 **백업에서 복원**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-160">In SharePoint Central Administration Click **Restore from a backup** in the **Backup and Restore** group.</span></span>  
  
2.  <span data-ttu-id="733fe-161">**백업 디렉터리 위치** 입력란에 백업 파일에 대한 경로를 입력하고 **새로 고침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-161">Type the path to your backup file in **Backup Directory Location** box and click **Refresh**.</span></span>  
  
3.  <span data-ttu-id="733fe-162">**최상위 구성 요소** 목록에서 서비스 애플리케이션 백업을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-162">Select your service application backup from the **Top Component** list and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="733fe-163">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 애플리케이션을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-163">Select your [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] application and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="733fe-164">**로그인 이름 및 암호** 섹션에 로그인 이름의 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-164">In the **Login Names and Passwords** section type the password for the login name.</span></span> <span data-ttu-id="733fe-165">로그인 이름 입력란은 백업 전에 서비스 애플리케이션에 사용되던 로그인으로 채워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-165">The login name box should be populated with the login the service application was using prior to the backup.</span></span>  
  
6.  <span data-ttu-id="733fe-166">**복원 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-166">Click **Start Restore**.</span></span>  
  
7.  <span data-ttu-id="733fe-167">위 프로세스를 반복하되 서비스 애플리케이션을 복원하는 대신 **공유 서비스** 노드와 **공유 서비스 애플리케이션** 노드를 차례로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-167">Repeat the process above but instead of restoring the service application, expand the **Shared Services** node and then expand the **Shared Service Applications** node.</span></span>  
  
 <span data-ttu-id="733fe-168">자세한 내용은 SharePoint 설명서의 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="733fe-168">For more information, see the following topics in the SharePoint documentation:</span></span>  
  
 <span data-ttu-id="733fe-169">[서비스 애플리케이션 복원(SharePoint Foundation 2010)](https://msdn.microsoft.com/library/ee748615.aspx)</span><span class="sxs-lookup"><span data-stu-id="733fe-169">[Restore a service application (SharePoint Foundation 2010)](https://msdn.microsoft.com/library/ee748615.aspx).</span></span>  
  
 <span data-ttu-id="733fe-170">[서비스 애플리케이션 복원(SharePoint Server 2010)](https://technet.microsoft.com/library/ee428305.aspx)</span><span class="sxs-lookup"><span data-stu-id="733fe-170">[Restore a service application (SharePoint Server 2010)](https://technet.microsoft.com/library/ee428305.aspx).</span></span>  
  
### <a name="restore-the-encryption-keys-using-central-administration"></a><span data-ttu-id="733fe-171">중앙 관리를 사용하여 암호화 키 복원</span><span class="sxs-lookup"><span data-stu-id="733fe-171">Restore the Encryption Keys using Central Administration</span></span>  
 <span data-ttu-id="733fe-172">암호화 키를 복원 하는 방법에 대 한 자세한 내용은 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [SharePoint 서비스 응용 프로그램 Reporting Services 관리](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)의 "암호화 키" 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="733fe-172">For information on restoring the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] encryption keys, see the "Encryption Keys" section of [Manage a Reporting Services SharePoint Service Application](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md).</span></span>  
  
### <a name="configure-the-execution-account-and-database-authentication"></a><span data-ttu-id="733fe-173">실행 계정 및 데이터베이스 인증 구성</span><span class="sxs-lookup"><span data-stu-id="733fe-173">Configure the Execution Account and Database Authentication</span></span>  
 <span data-ttu-id="733fe-174">**실행 계정:** 서비스 애플리케이션에 실행 계정이 사용되고 있었던 경우 다음 단계를 수행하여 구성하세요.</span><span class="sxs-lookup"><span data-stu-id="733fe-174">**Execution Account:** If your service application was using an execution account complete the following steps to configure it:</span></span>  
  
1.  <span data-ttu-id="733fe-175">SharePoint 중앙 관리의 **응용 프로그램 관리** 그룹에서 **서비스 응용 프로그램 관리** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-175">In SharePoint Central Administration, click **Manage Service Applications** in the **Application Management** group.</span></span>  
  
2.  <span data-ttu-id="733fe-176">서비스 응용 프로그램의 이름을 클릭 한 다음 SharePoint 리본에서 **관리** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-176">Click the name of your service application and then click **Manage** in the SharePoint Ribbon.</span></span>  
  
3.  <span data-ttu-id="733fe-177">**실행 계정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-177">Click **Execution Account**.</span></span>  
  
4.  <span data-ttu-id="733fe-178">계정 및 암호를 입력하고 **실행 계정 지정** 입력란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-178">Type the account, password, and select the **Specify and Execution Account** box.</span></span>  
  
5.  <span data-ttu-id="733fe-179">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-179">Click **OK**.</span></span>  
  
 <span data-ttu-id="733fe-180">**데이터베이스 인증:** 서비스 애플리케이션에 데이터베이스 인증을 위해 Windows 인증이 사용되고 있었던 경우 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="733fe-180">**Database Authentication:** If your service application was using Windows Authentication for the database authentication complete the following steps:</span></span>  
  
1.  <span data-ttu-id="733fe-181">SharePoint 중앙 관리의 **응용 프로그램 관리** 그룹에서 **서비스 응용 프로그램 관리** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-181">In SharePoint Central Administration click **Manage Service Applications** in the **Application Management** group.</span></span>  
  
2.  <span data-ttu-id="733fe-182">서비스 애플리케이션의 이름을 클릭한 다음 SharePoint 리본에서 **속성** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-182">Click the name of your service application and then click **Properties** in the SharePoint Ribbon.</span></span>  
  
3.  <span data-ttu-id="733fe-183">**Reporting Services(SSRS) 서비스 데이터베이스** 섹션을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-183">Review the **Reporting Services (SSRS) Service Database** section.</span></span>  
  
4.  <span data-ttu-id="733fe-184">**Windows 인증**을 선택하고</span><span class="sxs-lookup"><span data-stu-id="733fe-184">Select **Windows Authentication**.</span></span>  
  
5.  <span data-ttu-id="733fe-185">계정 및 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-185">Type the account and password.</span></span> <span data-ttu-id="733fe-186">해당되는 경우 **Windows 자격 증명으로 사용** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-186">Select **Use as Windows Credentials** if appropriate.</span></span>  
  
6.  <span data-ttu-id="733fe-187">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="733fe-187">Click **Ok**</span></span>  
  
  
