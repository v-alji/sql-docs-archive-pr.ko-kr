---
title: 데이터베이스 즉시 파일 초기화 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- initializing files [SQL Server]
- instant file initializations [SQL Server]
- fast file initialization (SQL Server)
- file initialization [SQL Server]
ms.assetid: 1ad468f5-4f75-480b-aac6-0b01b048bd67
author: stevestein
ms.author: sstein
ms.openlocfilehash: dedd2c5b8d075dee8aeeb438904137558c664d95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650101"
---
# <a name="database-instant-file-initialization"></a><span data-ttu-id="4df0a-102">데이터베이스 즉시 파일 초기화</span><span class="sxs-lookup"><span data-stu-id="4df0a-102">Database Instant File Initialization</span></span>
  <span data-ttu-id="4df0a-103">데이터 및 로그 파일이 초기화되어 이전에 삭제한 파일의 디스크에 남아 있는 기존 데이터를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-103">Data and log files are initialized to overwrite any existing data left on the disk from previously deleted files.</span></span> <span data-ttu-id="4df0a-104">데이터 및 로그 파일은 사용자가 다음 작업 중 하나를 수행할 때 0으로 채워져 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-104">Data and log files are first initialized by filling the files with zeros when you perform one of the following operations:</span></span>  
  
-   <span data-ttu-id="4df0a-105">데이터베이스 만들기</span><span class="sxs-lookup"><span data-stu-id="4df0a-105">Create a database.</span></span>  
  
-   <span data-ttu-id="4df0a-106">기존 데이터베이스에 파일, 로그 또는 데이터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-106">Add files, log or data, to an existing database.</span></span>  
  
-   <span data-ttu-id="4df0a-107">기존 파일의 크기를 늘립니다(자동 증가 작업 포함).</span><span class="sxs-lookup"><span data-stu-id="4df0a-107">Increase the size of an existing file (including autogrow operations).</span></span>  
  
-   <span data-ttu-id="4df0a-108">데이터베이스 또는 파일 그룹을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-108">Restore a database or filegroup.</span></span>  
  
 <span data-ttu-id="4df0a-109">파일 초기화는 이러한 작업의 수행 시간을 더 오래 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-109">File initialization causes these operations to take longer.</span></span> <span data-ttu-id="4df0a-110">그러나 데이터를 처음으로 파일에 기록할 때 운영 체제는 0으로 파일을 채울 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-110">However, when data is written to the files for the first time, the operating system does not have to fill the files with zeros.</span></span>  
  
## <a name="instant-file-initialization"></a><span data-ttu-id="4df0a-111">즉시 파일 초기화</span><span class="sxs-lookup"><span data-stu-id="4df0a-111">Instant File Initialization</span></span>  
 <span data-ttu-id="4df0a-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 데이터 파일을 즉시 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-112">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], data files can be initialized instantaneously.</span></span> <span data-ttu-id="4df0a-113">이를 통해 이전에 언급한 파일 작업을 신속히 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-113">This allows for fast execution of the previously mentioned file operations.</span></span> <span data-ttu-id="4df0a-114">즉시 파일 초기화는 디스크 공간을 0으로 채우지 않고 디스크 공간을 회수합니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-114">Instant file initialization reclaims used disk space without filling that space with zeros.</span></span> <span data-ttu-id="4df0a-115">대신, 새 데이터를 파일에 기록할 때 디스크 내용을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-115">Instead, disk content is overwritten as new data is written to the files.</span></span> <span data-ttu-id="4df0a-116">로그 파일은 즉시 초기화할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-116">Log files cannot be initialized instantaneously.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4df0a-117">인스턴트 파일 초기화는 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[winxppro](../../includes/winxppro-md.md)] 또는 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 이상 버전에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-117">Instant file initialization is available only on [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[winxppro](../../includes/winxppro-md.md)] or [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] or later versions.</span></span>  
  
 <span data-ttu-id="4df0a-118">즉시 파일 초기화는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) 서비스 계정에 SE_MANAGE_VOLUME_NAME을 부여받은 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-118">Instant file initialization is only available if the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) service account has been granted SE_MANAGE_VOLUME_NAME.</span></span> <span data-ttu-id="4df0a-119">Windows Administrator 그룹의 구성원은 이 권한을 가지고 있으며 다른 사용자에게 **볼륨 유지 관리 작업 수행** 보안 정책을 추가하여 이 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-119">Members of the Windows Administrator group have this right and can grant it to other users by adding them to the **Perform Volume Maintenance Tasks** security policy.</span></span> <span data-ttu-id="4df0a-120">사용자 권한 할당에 대한 자세한 내용은 Windows 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4df0a-120">For more information about assigning user rights, see the Windows documentation.</span></span>  
  
 <span data-ttu-id="4df0a-121">TDE를 사용하도록 설정되어 있으면 즉시 파일 초기화를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-121">Instant file initialization is not available when TDE is enabled.</span></span>  
  
 <span data-ttu-id="4df0a-122">계정에 `Perform volume maintenance tasks` 권한을 부여하려면</span><span class="sxs-lookup"><span data-stu-id="4df0a-122">To grant an account the `Perform volume maintenance tasks` permission:</span></span>  
  
1.  <span data-ttu-id="4df0a-123">백업 파일을 생성할 컴퓨터에서 `Local Security Policy` 애플리케이션(`secpol.msc`)을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-123">On the computer where the backup file will be created, open the `Local Security Policy` application (`secpol.msc`).</span></span>  
  
2.  <span data-ttu-id="4df0a-124">왼쪽 창에서 **로컬 정책**을 확장한 다음 **사용자 권한 할당**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-124">In the left pane, expand **Local Policies**, and then click **User Rights Assignment**.</span></span>  
  
3.  <span data-ttu-id="4df0a-125">오른쪽 창에서 **볼륨 유지 관리 작업 수행**을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-125">In the right pane, double-click **Perform volume maintenance tasks**.</span></span>  
  
4.  <span data-ttu-id="4df0a-126">**사용자 또는 그룹 추가** 를 클릭하고 백업에 사용되는 사용자 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-126">Click **Add User or Group** and add any user accounts that are used for backups.</span></span>  
  
5.  <span data-ttu-id="4df0a-127">**적용**을 클릭 한 다음 모든 `Local Security Policy` 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-127">Click **Apply**, and then close all `Local Security Policy` dialog boxes.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="4df0a-128">보안 고려사항</span><span class="sxs-lookup"><span data-stu-id="4df0a-128">Security Considerations</span></span>  
 <span data-ttu-id="4df0a-129">삭제된 디스크 내용은 새 데이터가 파일에 기록될 때만 덮어쓰기 때문에 권한 없는 사용자가 삭제된 내용에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-129">Because the deleted disk content is overwritten only as new data is written to the files, the deleted content might be accessed by an unauthorized principal.</span></span> <span data-ttu-id="4df0a-130">데이터베이스 파일이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 인스턴스에 연결되어 있는 동안 파일의 DACL(임의 액세스 제어 목록)에 의해 이러한 정보 공개 위협이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-130">While the database file is attached to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this information disclosure threat is reduced by the discretionary access control list (DACL) on the file.</span></span> <span data-ttu-id="4df0a-131">이 DACL은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 계정 및 로컬 관리자에게만 파일 액세스를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-131">This DACL allows file access only to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account and the local administrator.</span></span> <span data-ttu-id="4df0a-132">그러나 파일이 분리되면 SE_MANAGE_VOLUME_NAME이 없는 사용자 또는 서비스가 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-132">However, when the file is detached, it may be accessed by a user or service that does not have SE_MANAGE_VOLUME_NAME.</span></span> <span data-ttu-id="4df0a-133">데이터베이스가 백업될 때에도 유사한 위협이 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-133">A similar threat exists when the database is backed up.</span></span> <span data-ttu-id="4df0a-134">백업 파일이 적절한 DACL로 보호되지 않는 경우 권한이 없는 사용자 또는 서비스가 삭제된 내용을 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-134">The deleted content can become available to an unauthorized user or service if the backup file is not protected with an appropriate DACL.</span></span>  
  
 <span data-ttu-id="4df0a-135">삭제된 내용의 공개 가능성이 우려된다면 다음 중 하나 또는 둘 다를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-135">If the potential for disclosing deleted content is a concern, you should do one or both of the following:</span></span>  
  
-   <span data-ttu-id="4df0a-136">분리된 데이터 파일 및 백업 파일에 제한적인 DACL이 있는지 항상 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-136">Always make sure that any detached data files and backup files have restrictive DACLs.</span></span>  
  
-   <span data-ttu-id="4df0a-137">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 계정에서 SE_MANAGE_VOLUME_NAME을 취소하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 인스턴스에 대한 즉시 파일 초기화를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-137">Disable instant file initialization for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by revoking SE_MANAGE_VOLUME_NAME from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4df0a-138">즉시 파일 초기화 해제는 사용자 권한이 취소된 후 생성되거나 크기를 늘린 파일에만 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="4df0a-138">Disabling instant file initialization only affects files that are created or increased in size after the user right is revoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4df0a-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4df0a-139">See Also</span></span>  
 [<span data-ttu-id="4df0a-140">CREATE DATABASE&#40;SQL Server Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4df0a-140">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
  
