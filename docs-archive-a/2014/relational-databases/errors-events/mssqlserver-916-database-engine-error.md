---
title: MSSQLSERVER_916 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 916 (Database Engine error)
ms.assetid: 73eb6581-99fe-49a5-9b42-e239d7ffe27f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ee67c1e2f67c3c7903c67082ec3793d9d9820061
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650036"
---
# <a name="mssqlserver_916"></a><span data-ttu-id="9fad2-102">MSSQLSERVER_916</span><span class="sxs-lookup"><span data-stu-id="9fad2-102">MSSQLSERVER_916</span></span>
    
## <a name="details"></a><span data-ttu-id="9fad2-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="9fad2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9fad2-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="9fad2-104">Product Name</span></span>|<span data-ttu-id="9fad2-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9fad2-105">SQL Server</span></span>|  
|<span data-ttu-id="9fad2-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="9fad2-106">Event ID</span></span>|<span data-ttu-id="9fad2-107">916</span><span class="sxs-lookup"><span data-stu-id="9fad2-107">916</span></span>|  
|<span data-ttu-id="9fad2-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="9fad2-108">Event Source</span></span>|<span data-ttu-id="9fad2-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9fad2-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9fad2-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="9fad2-110">Component</span></span>|<span data-ttu-id="9fad2-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9fad2-111">SQLEngine</span></span>|  
|<span data-ttu-id="9fad2-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="9fad2-112">Symbolic Name</span></span>|<span data-ttu-id="9fad2-113">NOTUSER</span><span class="sxs-lookup"><span data-stu-id="9fad2-113">NOTUSER</span></span>|  
|<span data-ttu-id="9fad2-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="9fad2-114">Message Text</span></span>|<span data-ttu-id="9fad2-115">현재 보안 컨텍스트로는 서버 보안 주체 "%.\*ls"이(가) 데이터베이스 "%.\*ls"에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9fad2-115">The server principal "%.\*ls" is not able to access the database "%.\*ls" under the current security context.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9fad2-116">설명</span><span class="sxs-lookup"><span data-stu-id="9fad2-116">Explanation</span></span>  
 <span data-ttu-id="9fad2-117">해당 로그인에는 명명된 데이터베이스에 연결할 수 있는 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9fad2-117">The login does not have sufficient permissions to connect to the named database.</span></span> <span data-ttu-id="9fad2-118">이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결할 수 있지만 데이터베이스의 특정 권한이 없는 로그인은 게스트 사용자 권한을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="9fad2-118">Logins that can connect to this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] but that do not have specific permissions in a database receive the permissions of the guest user.</span></span> <span data-ttu-id="9fad2-119">이는 한 데이터베이스의 사용자가 사용 권한이 없는 다른 데이터베이스에 연결하지 못하도록 방지하는 보안 수단입니다.</span><span class="sxs-lookup"><span data-stu-id="9fad2-119">This is a security measure to prevent users in one database from connecting to other databases where they do not have privileges.</span></span> <span data-ttu-id="9fad2-120">게스트 사용자에게 명명된 데이터베이스에 대한 CONNECT 권한이 없고 trustworthy 속성이 설정되지 않은 경우 이 오류 메시지가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fad2-120">This error message can occur when the guest user does not have CONNECT permission to the named database and the trustworthy property is not set.</span></span> <span data-ttu-id="9fad2-121">게스트 사용자에게 명명된 데이터베이스에 대한 CONNECT 권한이 없으면 이 오류 메시지가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fad2-121">This error message can occur when the guest user does not have CONNECT permission to the named database.</span></span>  
  
 <span data-ttu-id="9fad2-122">msdb 데이터베이스에 대한 CONNECT 권한이 거부되거나 취소되면 개체 탐색기에서 각 데이터베이스의 정책 기반 관리 상태를 표시하려고 할 때 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 이러한 오류를 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fad2-122">When CONNECT permission to the msdb database is denied or revoked, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] can receive this error when Object Explorer tries to show the Policy Based Management status of each database.</span></span> <span data-ttu-id="9fad2-123">개체 탐색기가 현재 로그인의 권한을 사용하여 msdb 데이터베이스에서 해당 정보를 쿼리하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="9fad2-123">Object Explorer uses the permissions of the current login to query the msdb database for this information, which causes the error.</span></span> <span data-ttu-id="9fad2-124">다음과 같은 오류 메시지도 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="9fad2-124">The following error message also occurs:</span></span>  
  
 <span data-ttu-id="9fad2-125">이 요청에 대한 데이터를 검색하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="9fad2-125">Failed to retrieve data for this request.</span></span> <span data-ttu-id="9fad2-126">(Microsoft.SqlServer.Management.Sdk.Sfc)</span><span class="sxs-lookup"><span data-stu-id="9fad2-126">(Microsoft.SqlServer.Management.Sdk.Sfc)</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9fad2-127">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="9fad2-127">User Action</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="9fad2-128">이 보안 수단을 무시하기 전에 사용자가 다양한 데이터베이스에서 인증된다는 것을 분명히 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fad2-128">Before circumventing this security measure be sure to have a clear understanding of users are authenticated in various databases.</span></span> <span data-ttu-id="9fad2-129">다음 방법을 사용하면 한 데이터베이스의 사용 권한을 가진 사용자가 다른 데이터베이스에 연결할 수 있어 악의적 사용자에게 데이터가 노출될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fad2-129">The following methods may allow users that have permissions in one database to connect to other databases which could expose data to a malicious user.</span></span> <span data-ttu-id="9fad2-130">포함된 데이터베이스를 사용하도록 설정하면 다음 단계에서는 한 데이터베이스의 데이터베이스 소유자가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 다른 데이터베이스에 대한 액세스 권한을 부여하도록 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fad2-130">When contained databases are enabled, the following steps can allow database owners in one database to grant access to other database on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="9fad2-131">다음 방법 중 하나로 데이터베이스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fad2-131">You can connect to the database in one of the following ways:</span></span>  
  
-   <span data-ttu-id="9fad2-132">명명된 데이터베이스에 대한 특정 로그인 액세스 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="9fad2-132">Grant the specific login access to the named database.</span></span> <span data-ttu-id="9fad2-133">다음 예에서는 `Adventure-Works\Larry` 데이터베이스에 대한 로그인 `msdb` 액세스 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="9fad2-133">The following example grants the login `Adventure-Works\Larry` access to the `msdb` database.</span></span>  
  
     <span data-ttu-id="9fad2-134">USE msdb ;</span><span class="sxs-lookup"><span data-stu-id="9fad2-134">USE msdb ;</span></span>  
  
     <span data-ttu-id="9fad2-135">이동</span><span class="sxs-lookup"><span data-stu-id="9fad2-135">GO</span></span>  
  
     <span data-ttu-id="9fad2-136">GRANT CONNECT TO [Adventure-Works\Larry] ;</span><span class="sxs-lookup"><span data-stu-id="9fad2-136">GRANT CONNECT TO [Adventure-Works\Larry] ;</span></span>  
  
-   <span data-ttu-id="9fad2-137">게스트 사용자에 대해 오류 메시지에 명명된 데이터베이스에 대한 CONNECT 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="9fad2-137">Grant the CONNECT permission to the database named in the error message for the guest user.</span></span> <span data-ttu-id="9fad2-138">다음 예에서는 사용자 `CONNECT`에 대해 `msdb` 데이터베이스에 대한 `guest` 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="9fad2-138">The following example grants the `CONNECT` permission to the `msdb` database for the user `guest`.</span></span>  
  
     <span data-ttu-id="9fad2-139">USE msdb ;</span><span class="sxs-lookup"><span data-stu-id="9fad2-139">USE msdb ;</span></span>  
  
     <span data-ttu-id="9fad2-140">이동</span><span class="sxs-lookup"><span data-stu-id="9fad2-140">GO</span></span>  
  
     <span data-ttu-id="9fad2-141">GRANT CONNECT TO guest ;</span><span class="sxs-lookup"><span data-stu-id="9fad2-141">GRANT CONNECT TO guest ;</span></span>  
  
-   <span data-ttu-id="9fad2-142">사용자를 인증한 데이터베이스에 TRUSTWORTHY 속성을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9fad2-142">Enable the TRUSTWORTHY property on the database that has authenticated the user.</span></span>  
  
     `ALTER DATABASE AdventureWorks SET TRUSTWORTHY ON;`  
  
  
