---
title: 게시 액세스 목록에서 로그인 관리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server replication], publication access list
- publications [SQL Server replication], publication access lists
- publication access list (PAL)
- PAL (publication access list)
- logins [SQL Server replication], managing
ms.assetid: fceb216b-0b18-4e3b-8ae0-13e35920dcbc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b96e6f46403cf3a482f00a3f5155527177920967
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648918"
---
# <a name="manage-logins-in-the-publication-access-list"></a><span data-ttu-id="050c2-102">게시 액세스 목록에서 로그인 관리</span><span class="sxs-lookup"><span data-stu-id="050c2-102">Manage Logins in the Publication Access List</span></span>
  <span data-ttu-id="050c2-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 게시 액세스 목록의 로그인을 관리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="050c2-103">This topic describes how to manage logins in the Publication Access List in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="050c2-104">게시에 대한 액세스는 PAL(게시 액세스 목록)에서 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="050c2-104">Access to a publication is controlled by the publication access list (PAL).</span></span> <span data-ttu-id="050c2-105">로그인 및 그룹을 추가하고 PAL에서 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="050c2-105">Logins and groups can be added and removed from the PAL.</span></span>  
  
 <span data-ttu-id="050c2-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="050c2-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="050c2-107">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="050c2-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="050c2-108">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="050c2-108">Prerequisites</span></span>](#Prerequisites)  
  
-   <span data-ttu-id="050c2-109">**다음을 사용하여 게시 액세스 목록에서 로그인을 관리하려면**</span><span class="sxs-lookup"><span data-stu-id="050c2-109">**To manage logins in the Publication Access List, using:**</span></span>  
  
     [<span data-ttu-id="050c2-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="050c2-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="050c2-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="050c2-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="050c2-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="050c2-112">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="050c2-113">필수 조건</span><span class="sxs-lookup"><span data-stu-id="050c2-113">Prerequisites</span></span>  
  
-   <span data-ttu-id="050c2-114">PAL에 로그인을 추가하려면 먼저 게시 데이터베이스의 데이터베이스 사용자와 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 로그인을 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="050c2-114">You must associate the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login with a database user in the publication database before you add the login to the PAL.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="050c2-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="050c2-115">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="050c2-116">**게시 속성 - \<Publication>** 대화 상자의 **게시 액세스 목록** 페이지에서 PAL(게시 액세스 목록)을 사용하여 로그인을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="050c2-116">You use the publication access list (PAL) on the **Publication Access List** page of the **Publication Properties - \<Publication>** dialog box to manage logins.</span></span> <span data-ttu-id="050c2-117">이 대화 상자에 액세스하는 방법은 [게시 속성 보기 및 수정](../publish/view-and-modify-publication-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="050c2-117">For more information about how to access this dialog box, see [View and Modify Publication Properties](../publish/view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-manage-logins-in-the-pal"></a><span data-ttu-id="050c2-118">PAL에서 로그인을 관리하려면</span><span class="sxs-lookup"><span data-stu-id="050c2-118">To manage logins in the PAL</span></span>  
  
1.  <span data-ttu-id="050c2-119">**게시 속성 - \<Publication>** 대화 상자의 **게시 액세스 목록** 페이지에서 **추가**, **제거** 및 **모두 제거** 단추를 사용하여 PAL에서 로그인과 그룹을 추가 및 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="050c2-119">On the **Publication Access List** page of the **Publication Properties - \<Publication>** dialog box, use the **Add**, **Remove**, and **Remove All** buttons to add and remove logins and groups from the PAL.</span></span> <span data-ttu-id="050c2-120">PAL에서 **distributor_admin** 은 제거하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="050c2-120">Do not remove **distributor_admin** from the PAL.</span></span> <span data-ttu-id="050c2-121">이 계정은 복제에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="050c2-121">This account is used by replication.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="050c2-122">원격 배포자를 사용할 경우 PAL의 계정을 게시자와 배포자에서 모두 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="050c2-122">If a remote Distributor is used, accounts in the PAL must be available at both the Publisher and the Distributor.</span></span> <span data-ttu-id="050c2-123">이 계정은 두 서버 모두에 정의된 도메인 계정이나 로컬 계정이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="050c2-123">The account must be either a domain account or a local account that is defined at both servers.</span></span> <span data-ttu-id="050c2-124">또한 두 로그인과 연결된 암호는 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="050c2-124">The passwords that are associated with both logins must be the same.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="050c2-125">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="050c2-125">Using Transact-SQL</span></span>  
  
#### <a name="to-view-groups-and-logins-that-belong-to-the-pal"></a><span data-ttu-id="050c2-126">PAL에 속한 그룹 및 로그인을 보려면</span><span class="sxs-lookup"><span data-stu-id="050c2-126">To view groups and logins that belong to the PAL</span></span>  
  
1.  <span data-ttu-id="050c2-127">게시 데이터베이스의 게시자에서 [sp_help_publication_access](/sql/relational-databases/system-stored-procedures/sp-help-publication-access-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="050c2-127">At the Publisher on the publication database, execute [sp_help_publication_access](/sql/relational-databases/system-stored-procedures/sp-help-publication-access-transact-sql).</span></span> <span data-ttu-id="050c2-128">\*\* \@ 게시\*\*의 경우 게시 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="050c2-128">For **\@publication**, specify the publication name.</span></span> <span data-ttu-id="050c2-129">그러면 PAL의 그룹 및 로그인에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="050c2-129">This displays information about the groups and logins in the PAL.</span></span>  
  
#### <a name="to-add-groups-and-logins-to-the-pal"></a><span data-ttu-id="050c2-130">PAL에 그룹 및 로그인을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="050c2-130">To add groups and logins to the PAL</span></span>  
  
1.  <span data-ttu-id="050c2-131">게시 데이터베이스의 게시자에서 [sp_grant_publication_access](/sql/relational-databases/system-stored-procedures/sp-grant-publication-access-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="050c2-131">At the Publisher on the publication database, execute [sp_grant_publication_access](/sql/relational-databases/system-stored-procedures/sp-grant-publication-access-transact-sql).</span></span> <span data-ttu-id="050c2-132">\*\* \@ 게시**의 경우 게시 이름을 지정 하 고 \*\* \@ 로그인**에는 추가할 로그인 또는 그룹의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="050c2-132">For **\@publication**, specify the publication name; and for **\@login**, specify the name of the login or group that is being added.</span></span>  
  
#### <a name="to-remove-groups-and-logins-from-the-pal"></a><span data-ttu-id="050c2-133">PAL에서 그룹 및 로그인을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="050c2-133">To remove groups and logins from the PAL</span></span>  
  
1.  <span data-ttu-id="050c2-134">게시 데이터베이스의 게시자에서 [sp_revoke_publication_access](/sql/relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="050c2-134">At the Publisher on the publication database, execute [sp_revoke_publication_access](/sql/relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql).</span></span> <span data-ttu-id="050c2-135">\*\* \@ 게시**의 경우 게시 이름을 지정 하 고, \*\* \@ 로그인**의 경우 제거할 로그인 또는 그룹의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="050c2-135">For **\@publication**, specify the publication name; and for **\@login**, specify the name of the login or group that is being removed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="050c2-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="050c2-136">See Also</span></span>  
 <span data-ttu-id="050c2-137">[복제 에이전트 보안 모델](replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="050c2-137">[Replication Agent Security Model](replication-agent-security-model.md) </span></span>  
 <span data-ttu-id="050c2-138">[복제 토폴로지 보안 설정](view-and-modify-replication-security-settings.md) </span><span class="sxs-lookup"><span data-stu-id="050c2-138">[Secure a Replication Topology](view-and-modify-replication-security-settings.md) </span></span>  
 [<span data-ttu-id="050c2-139">게시자 보안 설정</span><span class="sxs-lookup"><span data-stu-id="050c2-139">Secure the Publisher</span></span>](secure-the-publisher.md)  
  
  
