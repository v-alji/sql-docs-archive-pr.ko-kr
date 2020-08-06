---
title: MSSQLSERVER_21879 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21879 (Database Engine error)
ms.assetid: fcfab735-05ca-423a-89f1-fdee7e2ed8c0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 08c5d4f45faf94d555ed7acedd90cc55ec4791ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734104"
---
# <a name="mssqlserver_21879"></a><span data-ttu-id="704fd-102">MSSQLSERVER_21879</span><span class="sxs-lookup"><span data-stu-id="704fd-102">MSSQLSERVER_21879</span></span>
    
## <a name="details"></a><span data-ttu-id="704fd-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="704fd-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="704fd-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="704fd-104">Product Name</span></span>|<span data-ttu-id="704fd-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="704fd-105">SQL Server</span></span>|  
|<span data-ttu-id="704fd-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="704fd-106">Event ID</span></span>|<span data-ttu-id="704fd-107">21879</span><span class="sxs-lookup"><span data-stu-id="704fd-107">21879</span></span>|  
|<span data-ttu-id="704fd-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="704fd-108">Event Source</span></span>|<span data-ttu-id="704fd-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="704fd-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="704fd-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="704fd-110">Component</span></span>|<span data-ttu-id="704fd-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="704fd-111">SQLEngine</span></span>|  
|<span data-ttu-id="704fd-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="704fd-112">Symbolic Name</span></span>|<span data-ttu-id="704fd-113">SQLErrorNum21879</span><span class="sxs-lookup"><span data-stu-id="704fd-113">SQLErrorNum21879</span></span>|  
|<span data-ttu-id="704fd-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="704fd-114">Message Text</span></span>|<span data-ttu-id="704fd-115">%d 오류로 인해 원래 게시자 '%s' 및 게시자 데이터베이스 '%s'의 리디렉션된 서버 '%s'을(를) 쿼리하여 원격 서버 이름을 확인할 수 없습니다(오류 메시지 '%s').</span><span class="sxs-lookup"><span data-stu-id="704fd-115">Unable to query the redirected server '%s' for original publisher '%s' and publisher database '%s' to determine the name of the remote server; Error %d, Error message '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="704fd-116">설명</span><span class="sxs-lookup"><span data-stu-id="704fd-116">Explanation</span></span>  
 <span data-ttu-id="704fd-117">`sp_validate_redirected_publisher`는 원격 서버의 이름을 검색하기 위해 자체적으로 만든 임시 연결된 서버를 사용하여 리디렉션된 게시자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="704fd-117">`sp_validate_redirected_publisher` uses a temporary linked server that it creates to connect to the redirected publisher in order to discover the name of the remote server.</span></span> <span data-ttu-id="704fd-118">오류 21879는 연결된 서버 쿼리에 실패한 경우에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="704fd-118">Error 21879 is returned when the linked server query fails.</span></span> <span data-ttu-id="704fd-119">원격 서버 이름 요청을 위한 호출은 일반적으로 임시 연결된 서버를 처음 사용할 때 이루어지므로 연결 문제가 있을 경우 가장 먼저 이 호출에서 연결 문제가 나타날 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="704fd-119">The call to request the remote server name is typically the first use of the temporary linked server, so if there are connectivity problems they are likely to appear first with this call.</span></span> <span data-ttu-id="704fd-120">이 원격 호출은 원격 서버에서 `@@servername`을 선택하여 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="704fd-120">This remote call simply executes select `@@servername` at the remote server.</span></span>  
  
 <span data-ttu-id="704fd-121">리디렉션된 게시자를 쿼리하는 데 사용된 연결된 서버는 원래 게시자에 대해 `sp_adddistpublisher`가 호출될 때 제공된 보안 모드, 로그인 및 암호를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="704fd-121">The linked server used to query the redirected publisher uses the security mode, login, and password supplied when `sp_adddistpublisher` was called for the original publisher.</span></span>  
  
-   <span data-ttu-id="704fd-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증(보안 모드 0)이 사용된 경우에는 지정된 로그인 및 암호를 사용하여 원격 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="704fd-122">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentication was used (security mode 0) then the login and password specified are used to connect to the remote server.</span></span>  
  
-   <span data-ttu-id="704fd-123">Windows 인증(보안 모드 1)이 사용된 경우에는 트러스트된 연결을 사용하여 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="704fd-123">If Windows authentication was used (security mode 1) a trusted connection is used for the connection.</span></span>  
  
    -   <span data-ttu-id="704fd-124">사용자가 `sp_validate_redirected_publisher`를 명시적으로 호출한 경우에는 사용자가 실행되고 있는 Windows 로그인을 사용하여 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="704fd-124">If `sp_validate_redirected_publisher` is called explicitly by a user, the Windows login that the user is running under is used for the connection.</span></span>  
  
    -   <span data-ttu-id="704fd-125">`sp_validate_redirected_`publisher를 `sp_get_redirected_publisher`의 복제 에이전트에서 호출한 경우에는 해당 에이전트와 연관된 Windows 로그인이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="704fd-125">If `sp_validate_redirected_`publisher is called by a replication agent from `sp_get_redirected_publisher`, the Windows login associated with the agent is used.</span></span>  
  
 <span data-ttu-id="704fd-126">오류 21879는 리디렉션된 대상 게시자에 알려지지 않은 로그인을 사용하여 `sp_validate_redirected_publisher`가 호출되었음을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="704fd-126">Error 21879 can indicate that `sp_validate_redirected_publisher` was called using a login that is not known at the redirected target publisher.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="704fd-127">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="704fd-127">User Action</span></span>  
 <span data-ttu-id="704fd-128">모든 가용성 그룹 복제본에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증 로그인 또는 Windows 인증 로그인이 올바른지 및 인증 로그인이 게시자 데이터베이스에 있는 구독 메타데이터 테이블(syssubscriptions 및 sysmergesubscriptions)에 액세스할 수 있는 권한을 가지고 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="704fd-128">Make certain that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentication login or the Windows authentication login is valid at all of the availability group replicas and has sufficient authorization to access the subscription metadata tables (syssubscriptions and sysmergesubscriptions) in the publisher database.</span></span>  
  
 <span data-ttu-id="704fd-129">구독자에서 실행되는 병합 에이전트 같이 배포자와는 다른 노드에서 실행되는 복제 에이전트에서 시작한 `sp_get_redirected_publisher` 호출에서 오류 21879가 반환될 경우 특별히 고려해야 할 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="704fd-129">There are special considerations when error 21879 is returned from a call to `sp_get_redirected_publisher` that is initiated by a replication agent running on a node other that the distributor; such as a merge agent running at a subscriber.</span></span> <span data-ttu-id="704fd-130">Windows 인증을 사용하여 리디렉션된 게시자에 연결하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 Kerberos 인증이 구성되어 있어야만 성공적으로 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="704fd-130">If Windows authentication is used for the connection to the redirected publisher, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be configured for Kerberos authentication for the connection to be successfully established.</span></span> <span data-ttu-id="704fd-131">Windows 인증을 사용하지만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 Kerberos 인증이 구성되어 있지 않을 경우 구독자에서 실행되는 병합 에이전트는 'NT AUTHORITY\ANONYMOUS LOGON' 로그인이 실패했음을 나타내는 오류 18456을 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="704fd-131">When Windows authentication is used and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not configured for Kerberos authentication, error 18456 indicating that the 'NT AUTHORITY\ANONYMOUS LOGON' login failed, is received by a merge agent running at a subscriber.</span></span> <span data-ttu-id="704fd-132">다음 세 가지 방법으로 이 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="704fd-132">There are three possible ways to address this issue:</span></span>  
  
-   <span data-ttu-id="704fd-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 Kerberos 인증을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="704fd-133">Configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for Kerberos authentication.</span></span> <span data-ttu-id="704fd-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 **Kerberos 인증 및 SQL Server**를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="704fd-134">See **Kerberos Authentication and SQL Server** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
-   <span data-ttu-id="704fd-135">을 사용 `sp_changedistpublisher` 하 여 MSdistpublishers의 원래 게시자와 연결 된 보안 모드를 변경 하 고 연결에 사용할 로그인과 암호를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="704fd-135">Use `sp_changedistpublisher` to change the security mode associated with the original publisher in MSdistpublishers, as well as to specify a login and password to use for the connection.</span></span>  
  
-   <span data-ttu-id="704fd-136">배포자에서가 호출 될 때 유효성 검사를 무시 하도록 병합 에이전트 명령줄에서 명령줄 매개 변수 *BypassPublisherValidation* 를 지정 합니다 `sp_get_redirected_publisher` .</span><span class="sxs-lookup"><span data-stu-id="704fd-136">Specify the command line parameter *BypassPublisherValidation* on the merge agent command line to bypass validation when `sp_get_redirected_publisher` is called at the distributor.</span></span>  
  
  
