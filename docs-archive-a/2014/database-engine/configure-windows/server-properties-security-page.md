---
title: 서버 속성(보안 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.security.f1
ms.assetid: b8a131c7-e7bd-4203-bf26-234f1ebfe622
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5f45c0a04a0d7cc627901d8de24175f1d63a99fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661349"
---
# <a name="server-properties-security-page"></a><span data-ttu-id="4c312-102">서버 속성(보안 페이지)</span><span class="sxs-lookup"><span data-stu-id="4c312-102">Server Properties (Security Page)</span></span>
  <span data-ttu-id="4c312-103">이 페이지를 사용하여 서버 보안 옵션을 확인하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c312-103">Use this page to view or modify your server security options.</span></span>  
  
## <a name="server-authentication"></a><span data-ttu-id="4c312-104">서버 인증</span><span class="sxs-lookup"><span data-stu-id="4c312-104">Server Authentication</span></span>  
 <span data-ttu-id="4c312-105">**Windows 인증 모드**</span><span class="sxs-lookup"><span data-stu-id="4c312-105">**Windows Authentication mode**</span></span>  
 <span data-ttu-id="4c312-106">Windows 인증을 사용하여 연결 시도의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="4c312-106">Uses Windows Authentication to validate attempted connections.</span></span> <span data-ttu-id="4c312-107">보안 모드를 변경할 때 **sa** 암호가 공백이면 **sa** 암호를 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c312-107">If the **sa** password is blank when the security mode is being changed, the user is prompted to enter an **sa** password.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4c312-108">Windows 인증이 SQL Server 인증보다 훨씬 더 안전하므로</span><span class="sxs-lookup"><span data-stu-id="4c312-108">Windows Authentication is much more secure than SQL Server Authentication.</span></span> <span data-ttu-id="4c312-109">가능하면 Windows 인증을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c312-109">When possible, you should use Windows Authentication.</span></span>  
  
 <span data-ttu-id="4c312-110">**SQL Server 및 Windows 인증 모드**</span><span class="sxs-lookup"><span data-stu-id="4c312-110">**SQL Server and Windows Authentication mode**</span></span>  
 <span data-ttu-id="4c312-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]이전 버전과의 호환성을 위해 혼합 모드 인증을 사용하여 연결을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4c312-111">Uses mixed mode authentication to verify attempted connections, for backward compatibility with earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4c312-112">보안 모드를 변경할 때 **sa** 암호가 공백이면 **sa** 암호를 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c312-112">If the **sa** password is blank when the security mode is being changed, the user is prompted to enter an **sa** password.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4c312-113">보안 구성을 변경하면 서비스를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c312-113">Changing the security configuration requires a restart of the service.</span></span> <span data-ttu-id="4c312-114">서버 인증을 SQL Server 및 Windows 인증 모드로 변경해도 SA 계정이 자동으로 설정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4c312-114">When changing the Server Authentication to SQL Server and Windows Authentication mode the SA account is not automatically enabled.</span></span> <span data-ttu-id="4c312-115">SA 계정을 사용하려면 ENABLE 옵션과 함께 [ALTER LOGIN](/sql/t-sql/statements/alter-login-transact-sql) 을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4c312-115">To use the SA account, execute [ALTER LOGIN](/sql/t-sql/statements/alter-login-transact-sql) with the ENABLE option.</span></span>  
  
## <a name="login-auditing"></a><span data-ttu-id="4c312-116">로그인 감사</span><span class="sxs-lookup"><span data-stu-id="4c312-116">Login Auditing</span></span>  
 <span data-ttu-id="4c312-117">**없음**</span><span class="sxs-lookup"><span data-stu-id="4c312-117">**None**</span></span>  
 <span data-ttu-id="4c312-118">로그인 감사 기능을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="4c312-118">Turns off login auditing.</span></span>  
  
 <span data-ttu-id="4c312-119">**실패한 로그인만**</span><span class="sxs-lookup"><span data-stu-id="4c312-119">**Failed logins only**</span></span>  
 <span data-ttu-id="4c312-120">실패한 로그인만 감사합니다.</span><span class="sxs-lookup"><span data-stu-id="4c312-120">Audits unsuccessful logins only.</span></span>  
  
 <span data-ttu-id="4c312-121">**성공한 로그인만**</span><span class="sxs-lookup"><span data-stu-id="4c312-121">**Successful logins only**</span></span>  
 <span data-ttu-id="4c312-122">성공한 로그인만 감사합니다.</span><span class="sxs-lookup"><span data-stu-id="4c312-122">Audits successful logins only.</span></span>  
  
 <span data-ttu-id="4c312-123">**실패한 로그인과 성공한 로그인 모두**</span><span class="sxs-lookup"><span data-stu-id="4c312-123">**Both failed and successful logins**</span></span>  
 <span data-ttu-id="4c312-124">모든 로그인 시도를 감사합니다.</span><span class="sxs-lookup"><span data-stu-id="4c312-124">Audits all login attempts.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4c312-125">감사 수준을 변경하면 서비스를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c312-125">Changing the audit level requires restarting the service.</span></span>  
  
## <a name="server-proxy-account"></a><span data-ttu-id="4c312-126">서버 프록시 계정</span><span class="sxs-lookup"><span data-stu-id="4c312-126">Server Proxy Account</span></span>  
 <span data-ttu-id="4c312-127">**서버 프록시 계정 사용**</span><span class="sxs-lookup"><span data-stu-id="4c312-127">**Enable server proxy account**</span></span>  
 <span data-ttu-id="4c312-128">**xp_cmdshell**을 위한 계정을 사용할 수 있도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c312-128">Enables an account for use by **xp_cmdshell**.</span></span> <span data-ttu-id="4c312-129">프록시 계정을 사용하면 운영 체제 명령이 실행 중일 때 로그인, 서버 역할 및 데이터베이스 역할을 가장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c312-129">Proxy accounts allow for the impersonation of logins, server roles, and database roles when an operating system command is being executed.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="4c312-130">서버 프록시 계정에서 사용하는 로그인에는 작업을 수행하는 데 필요한 최소한의 권한만 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c312-130">The login used by the server proxy account should have the least privileges required to perform the intended work.</span></span> <span data-ttu-id="4c312-131">프록시 계정에 권한을 과도하게 부여하면 악의적인 사용자가 시스템 보안을 위협하는 데 이용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c312-131">Excessive privileges for the proxy account could be used by a malicious user to compromise your system security.</span></span>  
  
 <span data-ttu-id="4c312-132">**프록시 계정**</span><span class="sxs-lookup"><span data-stu-id="4c312-132">**Proxy account**</span></span>  
 <span data-ttu-id="4c312-133">사용할 프록시 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c312-133">Specify the proxy account used.</span></span>  
  
 <span data-ttu-id="4c312-134">**암호**</span><span class="sxs-lookup"><span data-stu-id="4c312-134">**Password**</span></span>  
 <span data-ttu-id="4c312-135">프록시 계정의 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c312-135">Specify the password for the proxy account.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4c312-136">옵션</span><span class="sxs-lookup"><span data-stu-id="4c312-136">Options</span></span>  
 <span data-ttu-id="4c312-137">**C2 감사 추적 설정**</span><span class="sxs-lookup"><span data-stu-id="4c312-137">**Enable C2 audit tracing**</span></span>  
 <span data-ttu-id="4c312-138">문과 개체에 대한 모든 액세스 시도를 감사하여 기본 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 사용되는 \MSSQL\Data 디렉터리 또는 명명된*인스턴스에 사용되는 \MSSQL$* instancename [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\Data 디렉터리의 파일에 결과를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="4c312-138">Audits all attempts to access statements and objects and records them to a file in the \MSSQL\Data directory for default instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or the \MSSQL$*instancename*\Data directory for named instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4c312-139">자세한 내용은 [c2 audit mode 서버 구성 옵션](c2-audit-mode-server-configuration-option.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4c312-139">For more information, see [c2 audit mode Server Configuration Option](c2-audit-mode-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="4c312-140">**데이터베이스 간 소유권 체인**</span><span class="sxs-lookup"><span data-stu-id="4c312-140">**Cross database ownership chaining**</span></span>  
 <span data-ttu-id="4c312-141">데이터베이스가 데이터베이스 간 소유권 체인의 원본이나 대상이 되도록 허용하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4c312-141">Select to allow the database to be the source or target of a cross-database ownership chain.</span></span> <span data-ttu-id="4c312-142">자세한 내용은 [cross db ownership chaining 서버 구성 옵션](cross-db-ownership-chaining-server-configuration-option.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4c312-142">For more information, see [cross db ownership chaining Server Configuration Option](cross-db-ownership-chaining-server-configuration-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c312-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4c312-143">See Also</span></span>  
 [<span data-ttu-id="4c312-144">서버 구성 옵션&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4c312-144">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
