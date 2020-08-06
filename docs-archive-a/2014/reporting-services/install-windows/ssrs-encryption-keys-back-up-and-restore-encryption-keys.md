---
title: Reporting Services 암호화 키 백업 및 복원 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- backing up encryption keys [Reporting Services]
- restoring encryption keys [Reporting Services]
- encryption keys [Reporting Services]
- symmetric keys [Reporting Services]
ms.assetid: 6773d5df-03ef-4781-beb7-9f6825bac979
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c8e7e61f58632898fc6150210598a671157639a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742943"
---
# <a name="back-up-and-restore-reporting-services-encryption-keys"></a><span data-ttu-id="86bfd-102">Reporting Services 암호화 키 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="86bfd-102">Back Up and Restore Reporting Services Encryption Keys</span></span>
  <span data-ttu-id="86bfd-103">보고서 서버 구성의 중요한 부분은 중요한 정보의 암호화에 사용되는 대칭 키의 백업 복사본을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-103">An important part of report server configuration is creating a backup copy of the symmetric key used for encrypting sensitive information.</span></span> <span data-ttu-id="86bfd-104">대칭 키의 백업 복사본은 여러 일상 작업에 필요하며 새 설치에서 기존 보고서 서버 데이터베이스를 다시 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-104">A backup copy of the key is required for many routine operations, and enables you to reuse an existing report server database in a new installation.</span></span>  
  
 <span data-ttu-id="86bfd-105">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기본 모드 | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드</span><span class="sxs-lookup"><span data-stu-id="86bfd-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native Mode | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>  
  
 <span data-ttu-id="86bfd-106">다음 이벤트가 발생할 경우 암호화 키의 백업 복사본을 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-106">It is necessary to restore the backup copy of the encryption key when any of the following events occur:</span></span>  
  
-   <span data-ttu-id="86bfd-107">보고서 서버 Windows 서비스 계정 이름 변경 또는 암호 다시 설정.</span><span class="sxs-lookup"><span data-stu-id="86bfd-107">Changing the Report Server Windows service account name or resetting the password.</span></span> <span data-ttu-id="86bfd-108">Reporting Services 구성 관리자를 사용할 경우 서비스 계정 이름 변경 작업의 일부로 키가 백업됩니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-108">When you use the Reporting Services Configuration Manager, backing up the key is part of a service account name change operation.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="86bfd-109">암호를 다시 설정하는 것은 암호를 변경하는 것과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-109">Resetting the password is not the same as changing the password.</span></span> <span data-ttu-id="86bfd-110">암호를 다시 설정하려면 도메인 컨트롤러의 계정 정보를 덮어쓸 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-110">A password reset requires permission to overwrite account information on the domain controller.</span></span> <span data-ttu-id="86bfd-111">특정 암호를 잊어버리거나 알지 못할 경우 시스템 관리자가 암호를 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-111">Password resets are performed by a system administrator when you forget or do not know a particular password.</span></span> <span data-ttu-id="86bfd-112">대칭 키의 복원 작업은 암호를 다시 설정할 때만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-112">Only password resets require symmetric key restoration.</span></span> <span data-ttu-id="86bfd-113">계정 정보를 주기적으로 변경할 경우에는 대칭 키를 다시 설정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-113">Periodically changing an account password does not require you to reset the symmetric key.</span></span>  
  
-   <span data-ttu-id="86bfd-114">보고서 서버를 호스팅하는 컴퓨터나 인스턴스 이름 바꾸기(보고서 서버 인스턴스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 이름을 기반으로 함)</span><span class="sxs-lookup"><span data-stu-id="86bfd-114">Renaming the computer or instance that hosts the report server (a report server instance is based on a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name).</span></span>  
  
-   <span data-ttu-id="86bfd-115">보고서 서버 설치 마이그레이션 또는 다른 보고서 서버 데이터베이스를 사용하도록 보고서 서버 구성</span><span class="sxs-lookup"><span data-stu-id="86bfd-115">Migrating a report server installation or configuring a report server to use a different report server database.</span></span>  
  
-   <span data-ttu-id="86bfd-116">하드웨어 오류로 인한 보고서 서버 설치 복구</span><span class="sxs-lookup"><span data-stu-id="86bfd-116">Recovering a report server installation due to hardware failure.</span></span>  
  
 <span data-ttu-id="86bfd-117">대칭 키 복사본을 하나만 백업하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-117">You only need to back up one copy of the symmetric key.</span></span> <span data-ttu-id="86bfd-118">보고서 서버 데이터베이스와 대칭 키 간에는 일 대 일 상관 관계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-118">There is a one-to-one correspondence between a report server database and a symmetric key.</span></span> <span data-ttu-id="86bfd-119">따라서 대칭 키 복사본을 1개만 백업하면 되지만 스케일 아웃 배포 모델에서 여러 보고서 서버를 실행할 경우에는 키를 여러 번 복원해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-119">Although you only need to back up one copy, you might need to restore the key multiple times if you are running multiple report servers in a scale-out deployment model.</span></span> <span data-ttu-id="86bfd-120">각 보고서 서버 인스턴스는 보고서 서버 데이터베이스의 데이터를 잠그거나 잠금을 해제하기 위해 대칭 키 복사본이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-120">Each report server instance will need its copy of the symmetric key to lock and unlock data in the report server database.</span></span>  
  
  
## <a name="backing-up-the-encryption-keys"></a><span data-ttu-id="86bfd-121">암호화 키 백업</span><span class="sxs-lookup"><span data-stu-id="86bfd-121">Backing Up the Encryption Keys</span></span>  
 <span data-ttu-id="86bfd-122">대칭 키를 백업하면 사용자가 지정한 파일에 키가 기록된 후 사용자가 제공한 암호를 사용하여 키가 스크램블됩니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-122">Backing up the symmetric key is a process that writes the key to a file that you specify, and then scrambles the key using a password that you provide.</span></span> <span data-ttu-id="86bfd-123">대칭 키는 암호화되지 않은 상태로는 저장될 수 없으므로 디스크에 저장할 때 암호를 제공하여 키를 암호화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-123">The symmetric key can never be stored in an unencrypted state so you must provide a password to encrypt the key when you save it to disk.</span></span> <span data-ttu-id="86bfd-124">파일이 생성되면 해당 파일을 안전한 위치에 저장하고 파일 잠금을 해제하는 데 사용되는 **암호를 기억해야** 합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-124">After the file is created, you must store it in a secure location **and remember the password** that is used to unlock the file.</span></span> <span data-ttu-id="86bfd-125">대칭 키를 백업하려면 다음과 같은 도구를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-125">To backup the symmetric key, you can use the following tools:</span></span>  
  
 <span data-ttu-id="86bfd-126">**기본 모드:** Reporting Services 구성 관리자 또는 **rskeymgmt** 유틸리티</span><span class="sxs-lookup"><span data-stu-id="86bfd-126">**Native mode:** Either the Reporting Services Configuration Manager or the **rskeymgmt** utility.</span></span>  
  
 <span data-ttu-id="86bfd-127">**SharePoint 모드:** SharePoint 중앙 관리 페이지 또는 PowerShell</span><span class="sxs-lookup"><span data-stu-id="86bfd-127">**SharePoint mode:** SharePoint Central Administration pages or PowerShell.</span></span>  
  
####  <a name="backup-sharepoint-mode-report-servers"></a><a name="bkmk_backup_sharepoint"></a> <span data-ttu-id="86bfd-128">SharePoint 모드 보고서 서버 백업</span><span class="sxs-lookup"><span data-stu-id="86bfd-128">Backup SharePoint Mode Report Servers</span></span>  
 <span data-ttu-id="86bfd-129">SharePoint 모드 보고서 서버의 경우 PowerShell 명령을 사용하거나 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션용 관리 페이지를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-129">For SharePoint mode report servers you can either use PowerShell commands or use the management pages for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="86bfd-130">자세한 내용은 [Reporting Services SharePoint 서비스 애플리케이션 관리](../manage-a-reporting-services-sharepoint-service-application.md)의 “키 관리” 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="86bfd-130">For more information, see the "Key Management" section of [Manage a Reporting Services SharePoint Service Application](../manage-a-reporting-services-sharepoint-service-application.md)</span></span>  
  
####  <a name="back-up-encryption-keys--reporting-services-configuration-manager-native-mode"></a><a name="bkmk_backup_configuration_manager"></a> <span data-ttu-id="86bfd-131">암호화 키 백업 - Reporting Services 구성 관리자(기본 모드)</span><span class="sxs-lookup"><span data-stu-id="86bfd-131">Back up encryption keys -Reporting Services Configuration Manager (Native Mode)</span></span>  
  
1.  <span data-ttu-id="86bfd-132">Reporting Services 구성 관리자를 시작한 후 구성하려는 보고서 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-132">Start the Reporting Services Configuration Manager, and then connect to the report server instance you want to configure.</span></span>  
  
2.  <span data-ttu-id="86bfd-133">**암호화 키**를 클릭한 후 **백업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-133">Click **Encryption Keys**, and then click **Back Up**.</span></span>  
  
3.  <span data-ttu-id="86bfd-134">강력한 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-134">Type a strong password.</span></span>  
  
4.  <span data-ttu-id="86bfd-135">저장된 키를 보관할 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-135">Specify a file to contain the stored key.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="86bfd-136">는 해당 파일에 .snk 파일 확장명을 붙입니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-136">appends a .snk file extension to the file.</span></span> <span data-ttu-id="86bfd-137">보고서 서버와는 분리되도록 해당 파일을 디스크에 저장하세요.</span><span class="sxs-lookup"><span data-stu-id="86bfd-137">Consider storing the file on a disk separate from the report server.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
####  <a name="back-up-encryption-keys--rskeymgmt-native-mode"></a><a name="bkmk_backup_rskeymgmt"></a> <span data-ttu-id="86bfd-138">암호화 키 백업 - rskeymgmt(기본 모드)</span><span class="sxs-lookup"><span data-stu-id="86bfd-138">Back up encryption keys -rskeymgmt (Native Mode)</span></span>  
  
1.  <span data-ttu-id="86bfd-139">보고서 서버를 호스팅하는 컴퓨터에서 **rskeymgmt.exe** 를 로컬로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-139">Run **rskeymgmt.exe** locally on the computer that hosts the report server.</span></span> <span data-ttu-id="86bfd-140">`-e` 추출 인수를 사용하여 키를 복사하고 파일 이름을 제공하고 암호를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-140">You must use the `-e` extract argument to copy the key, provide a file name, and specify a password.</span></span> <span data-ttu-id="86bfd-141">다음은 인수 지정 예입니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-141">The following example illustrates the arguments you must specify:</span></span>  
  
    ```cmd
    rskeymgmt -e -f d:\rsdbkey.snk -p<password>  
    ```  
  
## <a name="restore-encryption-keys"></a><span data-ttu-id="86bfd-142">암호화 키 복원</span><span class="sxs-lookup"><span data-stu-id="86bfd-142">Restore Encryption Keys</span></span>  
 <span data-ttu-id="86bfd-143">대칭 키를 복원하면 보고서 서버 데이터베이스에 저장되어 있는 기존 대칭 키를 덮어쓰게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-143">Restoring the symmetric key overwrites the existing symmetric key that is stored in the report server database.</span></span> <span data-ttu-id="86bfd-144">암호화 키를 복원하면 사용할 수 없는 키가 이전에 디스크에 저장한 복사본으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-144">Restoring an encryption key replaces an unusable key with a copy that you previously saved to disk.</span></span> <span data-ttu-id="86bfd-145">암호화 키를 복원하면 다음 동작이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-145">Restoring encryption keys results in the following actions:</span></span>  
  
-   <span data-ttu-id="86bfd-146">암호로 보호된 백업 파일에서 대칭 키가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-146">The symmetric key is opened from the password protected backup file.</span></span>  
  
-   <span data-ttu-id="86bfd-147">보고서 서버 Windows 서비스의 공개 키를 사용하여 대칭 키가 암호화됩니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-147">The symmetric key is encrypted using the public key of the Report Server Windows service.</span></span>  
  
-   <span data-ttu-id="86bfd-148">암호화된 대칭 키가 보고서 서버 데이터베이스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-148">The encrypted symmetric key is stored in the report server database.</span></span>  
  
-   <span data-ttu-id="86bfd-149">이전에 저장한 대칭 키 데이터(예: 이전 배포의 보고서 서버 데이터베이스에 이미 있던 키 정보)가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-149">The previously stored symmetric key data (for example, key information that was already in the report server database from a previous deployment) is deleted.</span></span>  
  
 <span data-ttu-id="86bfd-150">암호화 키를 복원하려면 파일에 암호화 키 복사본이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-150">To restore the encryption key, you must have a copy of the encryption key on file.</span></span> <span data-ttu-id="86bfd-151">또한 저장된 파일의 잠금을 해제할 암호를 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-151">You must also know the password that unlocks the stored copy.</span></span> <span data-ttu-id="86bfd-152">키와 암호가 있으면 Reporting Services 구성 도구나 **rskeymgmt** 유틸리티를 실행하여 키를 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-152">If you have the key and the password, you can run the Reporting Services Configuration tool or **rskeymgmt** utility to restore the key.</span></span> <span data-ttu-id="86bfd-153">대칭 키는 보고서 서버 데이터베이스에 현재 저장되어 있는 암호화된 데이터를 잠그거나 잠금을 해제하는 키와 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-153">The symmetric key must be the same one that locks and unlocks encrypted data currently stored in the report server database.</span></span> <span data-ttu-id="86bfd-154">유효하지 않은 복사본을 복원하면 보고서 서버에서 보고서 서버 데이터베이스에 현재 저장되어 있는 암호화된 데이터에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-154">If you restore a copy that is not valid, the report server cannot access the encrypted data currently stored in the report server database.</span></span> <span data-ttu-id="86bfd-155">이 경우 유효한 키를 복원할 수 없으면 암호화된 값을 모두 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-155">If this occurs, you might need to delete all encrypted values if you cannot restore a valid key.</span></span> <span data-ttu-id="86bfd-156">백업 복사본이 없는 경우와 같이 여타의 이유로 암호화 키를 복원할 수 없으면 기존 키 및 암호화된 내용을 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-156">If for some reason you cannot restore the encryption key (for example, if you do not have a backup copy), you must delete the existing key and encrypted content.</span></span> <span data-ttu-id="86bfd-157">자세한 내용은 [암호화 키 삭제 및 다시 만들기&#40;SSRS 구성 관리자&#41;](ssrs-encryption-keys-delete-and-re-create-encryption-keys.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="86bfd-157">For more information, see [Delete and Re-create Encryption Keys  &#40;SSRS Configuration Manager&#41;](ssrs-encryption-keys-delete-and-re-create-encryption-keys.md).</span></span> <span data-ttu-id="86bfd-158">대칭 키를 만드는 방법은 [보고서 서버 초기화&#40;SSRS 구성 관리자&#41;](ssrs-encryption-keys-initialize-a-report-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="86bfd-158">For more information about creating symmetric keys, see [Initialize a Report Server &#40;SSRS Configuration Manager&#41;](ssrs-encryption-keys-initialize-a-report-server.md).</span></span>  
  
####  <a name="restore-encryption-keys--reporting-services-configuration-manager-native-mode"></a><a name="bkmk_restore_configuration_manager"></a> <span data-ttu-id="86bfd-159">암호화 키 복원 - Reporting Services 구성 관리자(기본 모드)</span><span class="sxs-lookup"><span data-stu-id="86bfd-159">Restore encryption keys -Reporting Services Configuration Manager (Native Mode)</span></span>  
  
1.  <span data-ttu-id="86bfd-160">Reporting Services 구성 관리자를 시작한 후 구성하려는 보고서 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-160">Start the Reporting Services Configuration Manager, and then connect to the report server instance you want to configure.</span></span>  
  
2.  <span data-ttu-id="86bfd-161">암호화 키 페이지에서 **복원**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-161">On the Encryption Keys page, click **Restore**.</span></span>  
  
3.  <span data-ttu-id="86bfd-162">백업 복사본이 들어 있는 .snk 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-162">Select the .snk file that contains the back up copy.</span></span>  
  
4.  <span data-ttu-id="86bfd-163">파일의 잠금을 해제하는 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-163">Type the password that unlocks the file.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
####  <a name="restore-encryption-keys---rskeymgmt-native-mode"></a><a name="bkmk_restore_rskeymgmt"></a><span data-ttu-id="86bfd-164">암호화 키 복원-rskeymgmt (기본 모드)</span><span class="sxs-lookup"><span data-stu-id="86bfd-164">Restore encryption keys - rskeymgmt (Native Mode)</span></span>  
  
1.  <span data-ttu-id="86bfd-165">보고서 서버를 호스팅하는 컴퓨터에서 **rskeymgmt.exe** 를 로컬로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-165">Run **rskeymgmt.exe** locally on the computer that hosts the report server.</span></span> <span data-ttu-id="86bfd-166">`-a` 인수를 사용하여 키를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-166">Use the `-a` argument to restore the keys.</span></span> <span data-ttu-id="86bfd-167">정규화된 파일 이름을 제공하고 암호를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-167">You must provide a fully-qualified file name and specify a password.</span></span> <span data-ttu-id="86bfd-168">다음은 인수 지정 예입니다.</span><span class="sxs-lookup"><span data-stu-id="86bfd-168">The following example illustrates the arguments you must specify:</span></span>  
  
    ```cmd
    rskeymgmt -a -f d:\rsdbkey.snk -p<password>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="86bfd-169">참고 항목</span><span class="sxs-lookup"><span data-stu-id="86bfd-169">See Also</span></span>  
 [<span data-ttu-id="86bfd-170">암호화 키 구성 및 관리&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="86bfd-170">Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-manage-encryption-keys.md)  
