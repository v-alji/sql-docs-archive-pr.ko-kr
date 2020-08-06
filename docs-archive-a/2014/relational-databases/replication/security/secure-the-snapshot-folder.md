---
title: 스냅샷 폴더 보안 설정 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], security
ms.assetid: 3cd877d1-ffb8-48fd-a72b-98eb948aad27
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c977936ad2aca6e5a98ee685a15662a00b625494
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653267"
---
# <a name="secure-the-snapshot-folder"></a><span data-ttu-id="29598-102">스냅샷 폴더 보안 설정</span><span class="sxs-lookup"><span data-stu-id="29598-102">Secure the Snapshot Folder</span></span>
  <span data-ttu-id="29598-103">스냅샷 폴더는 스냅샷 파일을 저장하는 디렉터리입니다. 스냅샷 스토리지 전용 디렉터리를 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="29598-103">The snapshot folder is a directory that stores snapshot files; it is recommended that you dedicate the directory for snapshot storage.</span></span> <span data-ttu-id="29598-104">스냅샷 에이전트에 폴더에 대한 쓰기 권한을 부여하고 병합 에이전트 또는 배포 에이전트가 폴더에 액세스할 때 사용하는 Windows 계정에만 읽기 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="29598-104">Grant the Snapshot Agent write permission to the folder, and ensure that read permission is granted only to the Windows account that the Merge Agent or Distribution agent uses when accessing the folder.</span></span> <span data-ttu-id="29598-105">에이전트에 연결된 Windows 계정은 원격 컴퓨터에 있는 스냅샷 폴더에 액세스할 수 있는 도메인 계정이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="29598-105">The Windows account associated with the agent must be a domain account to access a snapshot folder that is located on a remote computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="29598-106">UAC(사용자 계정 컨트롤)는 관리자가 승격된 사용자 권한( *권한*이라고도 함)을 관리하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="29598-106">User Account Control (UAC)  helps administrators manage their elevated user rights (sometimes called *privileges*).</span></span> <span data-ttu-id="29598-107">UAC를 사용하도록 설정된 운영 체제에서 실행할 때는 관리자가 해당 관리자 권한을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="29598-107">When running on operating systems that have UAC enabled, administrators do not use their administrative rights.</span></span> <span data-ttu-id="29598-108">대신 대부분의 동작을 관리 권한이 없는 일반 사용자로 수행하며 필요한 경우에만 임시로 해당 관리자 권한을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="29598-108">Instead, they perform most actions as standard (non-administrative) users, temporarily assuming their administrative rights only when it is required.</span></span> <span data-ttu-id="29598-109">UAC에서는 스냅샷 공유에 대한 관리 액세스를 거부할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29598-109">UAC can prevent administrative access to the snapshot share.</span></span> <span data-ttu-id="29598-110">따라서 스냅샷 에이전트, 배포 에이전트 및 병합 에이전트에서 사용하는 Windows 계정에 스냅샷 공유 권한을 명시적으로 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="29598-110">You must therefore explicitly grant snapshot share permissions to the Windows accounts that are used by the Snapshot Agent, Distribution Agent, and Merge Agent.</span></span> <span data-ttu-id="29598-111">Windows 계정이 Administrators 그룹의 멤버인 경우에도 이 작업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="29598-111">You must do this even if the Windows accounts are members of the Administrators group.</span></span>  
  
 <span data-ttu-id="29598-112">배포 구성 마법사나 새 게시 마법사를 사용하여 배포자를 구성할 때 스냅샷 폴더의 기본값은 로컬 경로인 X:\Program Files\Microsoft SQL Server\\ *\<instance>* \MSSQL\ReplData입니다.</span><span class="sxs-lookup"><span data-stu-id="29598-112">When configuring a Distributor through the Configure Distribution Wizard or the New Publication Wizard, the snapshot folder defaults to a local path: X:\Program Files\Microsoft SQL Server\\*\<instance>* \MSSQL\ReplData.</span></span> <span data-ttu-id="29598-113">원격 배포자나 끌어오기 구독을 사용하는 경우에는 로컬 경로 대신 UNC 네트워크 공유(예: \\\\<*computername>* \snapshot)를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="29598-113">If you are using a remote Distributor or pull subscriptions, you must specify a UNC network share (such as \\\\<*computername>* \snapshot) rather than a local path.</span></span>  
  
 <span data-ttu-id="29598-114">스냅샷 폴더에 대한 액세스 권한을 부여할 때는 폴더가 액세스되는 방법에 따라 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="29598-114">When granting permissions to access the snapshot folder, you must grant them according to the way in which the folder is accessed.</span></span> <span data-ttu-id="29598-115">다음 대화 상자 탭은 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 2003에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="29598-115">The following dialog box tabs are used in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 2003:</span></span>  
  
-   <span data-ttu-id="29598-116">로컬 경로를 지정하는 경우 해당 폴더에 대한 **속성** 대화 상자의 **보안** 탭을 통해 사용 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="29598-116">If you specify a local path, grant permissions through the **Security** tab of the **Properties** dialog box for the folder.</span></span>  
  
-   <span data-ttu-id="29598-117">네트워크 공유를 지정하는 경우 해당 폴더에 대한 **속성** 대화 상자의 **공유** 탭을 통해 사용 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="29598-117">If you specify a network share, grant permissions through the **Sharing** tab of the **Properties** dialog box for the folder.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="29598-118">배포자에서 복제 에이전트를 실행하는 경우 폴더에 대한 **속성** 대화 상자의 **보안** 탭을 사용하여 에이전트를 실행하는 데 사용되는 Windows 계정에 사용 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="29598-118">If the replication agent runs on the Distributor, use the **Security** tab of the **Properties** dialog box for the folder to grant permissions to the Windows account used to run the agent.</span></span> <span data-ttu-id="29598-119">네트워크 공유가 사용되는 경우에도 이 작업을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="29598-119">Do this even when a network share is used.</span></span> <span data-ttu-id="29598-120">이 내용은 밀어넣기 구독의 경우 병합 에이전트와 배포 에이전트에 적용되며 게시자와 배포자가 같은 컴퓨터에 있는 경우 스냅샷 에이전트에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="29598-120">This applies to the Merge Agent and Distribution Agent for a push subscription and to the Snapshot Agent when the Publisher and Distributor are on the same computer.</span></span>  
  
 <span data-ttu-id="29598-121">로컬 경로 및 네트워크 공유에 대해 사용 권한을 설정하는 방법은 Windows 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="29598-121">For more information about setting permissions for local paths and network shares, see the Windows documentation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="29598-122">게시를 삭제하면 복제는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서비스 계정의 보안 컨텍스트에서 스냅샷 폴더를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="29598-122">If a publication is dropped, replication attempts to remove the snapshot folder under the security context of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account.</span></span> <span data-ttu-id="29598-123">이 계정에 충분한 권한이 없는 경우에는 적절한 권한이 있는 계정으로 로그인하여 해당 폴더를 수동으로 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="29598-123">If this account does not have sufficient privileges, log in with an account that does have sufficient privileges and remove the folder manually.</span></span> <span data-ttu-id="29598-124">폴더를 삭제하려면 폴더가 로컬 경로인 경우 **수정** 권한이 필요하고 네트워크 경로인 경우 **모든 권한** 이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="29598-124">Removing a folder requires the **Modify** privilege if the folder is a local path or the **Full Control** privilege if the folder is a network path.</span></span>  
  
## <a name="delivering-snapshots-through-ftp"></a><span data-ttu-id="29598-125">FTP를 통해 스냅샷 배달</span><span class="sxs-lookup"><span data-stu-id="29598-125">Delivering Snapshots Through FTP</span></span>  
 <span data-ttu-id="29598-126">보안상 스냅샷을 UNC 공유에 저장하는 것이 가장 좋지만 스냅샷을 FTP 공유에 저장한 다음 FTP를 통해 구독자로 배달할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29598-126">It is recommended as a security best practice that snapshots be stored in a UNC share, but snapshots can be stored in an FTP share and then delivered to a Subscriber through FTP.</span></span> <span data-ttu-id="29598-127">FTP 서버를 구성할 때는 스냅샷 에이전트가 게시에 대한 쓰기 권한을 가지도록 허용하는 기본 UNC 공유가 가상 디렉터리에 표시되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="29598-127">When configuring the FTP server, ensure that the virtual directory exposes an underlying UNC share that permits write access by the Snapshot Agent for the publication.</span></span>  
  
 <span data-ttu-id="29598-128">구독자를 구성하여 FTP를 통해 스냅샷을 검색하려면 먼저 FTP 서버에 FTP 로그인과 암호를 설정합니다. 이 로그인과 암호는 스냅샷 파일을 다운로드할 수 있도록 구독자에게 읽기(또는 "가져오기") 액세스 권한을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="29598-128">To configure a Subscriber to retrieve the Snapshot via FTP, first set up an FTP server with an FTP login and password that allows Subscribers read (or "get") access to allow the snapshot files to be downloaded.</span></span>  
  
 <span data-ttu-id="29598-129">FTP를 통해 스냅샷을 배달하려면 [FTP를 통해 스냅샷 배달](../publish/deliver-a-snapshot-through-ftp.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="29598-129">To deliver snapshots through FTP, see [Deliver a Snapshot Through FTP](../publish/deliver-a-snapshot-through-ftp.md).</span></span>  
  
 <span data-ttu-id="29598-130">FTP를 통해 스냅샷에 액세스하는 데 필요한 암호를 설정하고 변경하는 방법은 [Secure the Publisher](secure-the-publisher.md)항목의 "FTP 스냅샷 배달" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="29598-130">For information about setting and changing the password for access to snapshots through FTP, see the section "FTP Snapshot Delivery" in the topic [Secure the Publisher](secure-the-publisher.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29598-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="29598-131">See Also</span></span>  
 <span data-ttu-id="29598-132">[대체 스냅숏 폴더 위치](../alternate-snapshot-folder-locations.md) </span><span class="sxs-lookup"><span data-stu-id="29598-132">[Alternate Snapshot Folder Locations](../alternate-snapshot-folder-locations.md) </span></span>  
 <span data-ttu-id="29598-133">[스냅샷으로 구독 초기화](../initialize-a-subscription-with-a-snapshot.md) </span><span class="sxs-lookup"><span data-stu-id="29598-133">[Initialize a Subscription with a Snapshot](../initialize-a-subscription-with-a-snapshot.md) </span></span>  
 <span data-ttu-id="29598-134">[Replication Security Best Practices](replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="29598-134">[Replication Security Best Practices](replication-security-best-practices.md) </span></span>  
 <span data-ttu-id="29598-135">[SQL Server 복제 보안](view-and-modify-replication-security-settings.md) </span><span class="sxs-lookup"><span data-stu-id="29598-135">[SQL Server Replication Security](view-and-modify-replication-security-settings.md) </span></span>  
 [<span data-ttu-id="29598-136">FTP를 통해 스냅샷 전송</span><span class="sxs-lookup"><span data-stu-id="29598-136">Transfer Snapshots Through FTP</span></span>](../transfer-snapshots-through-ftp.md)  
  
  
