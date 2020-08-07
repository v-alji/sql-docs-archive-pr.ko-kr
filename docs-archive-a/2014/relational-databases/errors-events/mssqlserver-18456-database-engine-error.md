---
title: MSSQLSERVER_18456 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18456 (Database Engine error)
ms.assetid: c417631d-be1f-42e0-8844-9f92c77e11f7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f5addb6bfb9d056d9f1796749ae629d4150102a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731671"
---
# <a name="mssqlserver_18456"></a><span data-ttu-id="17e09-102">MSSQLSERVER_18456</span><span class="sxs-lookup"><span data-stu-id="17e09-102">MSSQLSERVER_18456</span></span>
    
## <a name="details"></a><span data-ttu-id="17e09-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="17e09-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="17e09-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="17e09-104">Product Name</span></span>|<span data-ttu-id="17e09-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="17e09-105">SQL Server</span></span>|  
|<span data-ttu-id="17e09-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="17e09-106">Event ID</span></span>|<span data-ttu-id="17e09-107">18456</span><span class="sxs-lookup"><span data-stu-id="17e09-107">18456</span></span>|  
|<span data-ttu-id="17e09-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="17e09-108">Event Source</span></span>|<span data-ttu-id="17e09-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="17e09-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="17e09-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="17e09-110">Component</span></span>|<span data-ttu-id="17e09-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="17e09-111">SQLEngine</span></span>|  
|<span data-ttu-id="17e09-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="17e09-112">Symbolic Name</span></span>|<span data-ttu-id="17e09-113">LOGON_FAILED</span><span class="sxs-lookup"><span data-stu-id="17e09-113">LOGON_FAILED</span></span>|  
|<span data-ttu-id="17e09-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="17e09-114">Message Text</span></span>|<span data-ttu-id="17e09-115">사용자 '%.\*ls'이(가) 로그인하지 못했습니다.%.\*ls</span><span class="sxs-lookup"><span data-stu-id="17e09-115">Login failed for user '%.\*ls'.%.\*ls</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="17e09-116">설명</span><span class="sxs-lookup"><span data-stu-id="17e09-116">Explanation</span></span>  
 <span data-ttu-id="17e09-117">잘못된 암호나 사용자 이름과 관련된 인증 실패로 인해 연결 시도가 거부되면 다음과 유사한 메시지가 클라이언트로 반환됩니다.  "사용자 '<user_name>'이(가) 로그인하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-117">When a connection attempt is rejected because of an authentication failure that involves a bad password or user name, a message similar to the following is returned to the client:  "Login failed for user '<user_name>'.</span></span> <span data-ttu-id="17e09-118">(Microsoft SQL Server, 오류: 18456)".</span><span class="sxs-lookup"><span data-stu-id="17e09-118">(Microsoft SQL Server, Error: 18456)".</span></span>  
  
 <span data-ttu-id="17e09-119">클라이언트로 반환되는 추가 정보는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-119">Additional information returned to the client includes the following:</span></span>  
  
 <span data-ttu-id="17e09-120">"사용자 '<user_name>'이(가) 로그인하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-120">"Login failed for user '<user_name>'.</span></span> <span data-ttu-id="17e09-121">(.Net SqlClient 데이터 공급자)"</span><span class="sxs-lookup"><span data-stu-id="17e09-121">(.Net SqlClient Data Provider)"</span></span>  
  
 -----------------------------\-  
  
 <span data-ttu-id="17e09-122">"서버 이름: <computer_name>"</span><span class="sxs-lookup"><span data-stu-id="17e09-122">"Server Name: <computer_name>"</span></span>  
  
 <span data-ttu-id="17e09-123">"오류 번호: 18456"</span><span class="sxs-lookup"><span data-stu-id="17e09-123">"Error Number: 18456"</span></span>  
  
 <span data-ttu-id="17e09-124">"심각도: 14"</span><span class="sxs-lookup"><span data-stu-id="17e09-124">"Severity: 14"</span></span>  
  
 <span data-ttu-id="17e09-125">"상태: 1"</span><span class="sxs-lookup"><span data-stu-id="17e09-125">"State: 1"</span></span>  
  
 <span data-ttu-id="17e09-126">"줄 번호: 65536"</span><span class="sxs-lookup"><span data-stu-id="17e09-126">"Line Number: 65536"</span></span>  
  
 <span data-ttu-id="17e09-127">다음 메시지가 반환될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-127">The following message might also be returned:</span></span>  
  
 <span data-ttu-id="17e09-128">"메시지 18456, 수준 14, 상태 1, 서버 <computer_name>, 줄 1"</span><span class="sxs-lookup"><span data-stu-id="17e09-128">"Msg 18456, Level 14, State 1, Server <computer_name>, Line 1"</span></span>  
  
 <span data-ttu-id="17e09-129">"사용자 '<user_name>'이(가) 로그인하지 못했습니다."</span><span class="sxs-lookup"><span data-stu-id="17e09-129">"Login failed for user '<user_name>'."</span></span>  
  
## <a name="additional-error-information"></a><span data-ttu-id="17e09-130">추가 오류 정보</span><span class="sxs-lookup"><span data-stu-id="17e09-130">Additional Error Information</span></span>  
 <span data-ttu-id="17e09-131">보안 향상을 위해 클라이언트로 반환되는 오류 메시지는 의도적으로 인증 오류의 특성을 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-131">To increase security, the error message that is returned to the client deliberately hides the nature of the authentication error.</span></span> <span data-ttu-id="17e09-132">그러나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그의 해당 오류에는 인증 실패 조건에 매핑되는 오류 상태가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-132">However, in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, a corresponding error contains an error state that maps to an authentication failure condition.</span></span> <span data-ttu-id="17e09-133">로그인 실패 이유를 확인하려면 오류 상태를 다음 목록과 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-133">Compare the error state to the following list to determine the reason for the login failure.</span></span>  
  
|<span data-ttu-id="17e09-134">시스템 상태</span><span class="sxs-lookup"><span data-stu-id="17e09-134">State</span></span>|<span data-ttu-id="17e09-135">설명</span><span class="sxs-lookup"><span data-stu-id="17e09-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="17e09-136">1</span><span class="sxs-lookup"><span data-stu-id="17e09-136">1</span></span>|<span data-ttu-id="17e09-137">오류 정보를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-137">Error information is not available.</span></span> <span data-ttu-id="17e09-138">일반적으로 이 상태는 오류 정보를 수신할 수 있는 권한이 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-138">This state usually means you do not have permission to receive the error details.</span></span> <span data-ttu-id="17e09-139">자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="17e09-139">Contact your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrator for more information.</span></span>|  
|<span data-ttu-id="17e09-140">2</span><span class="sxs-lookup"><span data-stu-id="17e09-140">2</span></span>|<span data-ttu-id="17e09-141">사용자 ID가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-141">User ID is not valid.</span></span>|  
|<span data-ttu-id="17e09-142">5</span><span class="sxs-lookup"><span data-stu-id="17e09-142">5</span></span>|<span data-ttu-id="17e09-143">사용자 ID가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-143">User ID is not valid.</span></span>|  
|<span data-ttu-id="17e09-144">6</span><span class="sxs-lookup"><span data-stu-id="17e09-144">6</span></span>|<span data-ttu-id="17e09-145">SQL Server 인증에 Windows 로그인 이름을 사용하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-145">An attempt was made to use a Windows login name with SQL Server Authentication.</span></span>|  
|<span data-ttu-id="17e09-146">7</span><span class="sxs-lookup"><span data-stu-id="17e09-146">7</span></span>|<span data-ttu-id="17e09-147">로그인을 사용할 수 없으며 암호가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-147">Login is disabled, and the password is incorrect.</span></span>|  
|<span data-ttu-id="17e09-148">8</span><span class="sxs-lookup"><span data-stu-id="17e09-148">8</span></span>|<span data-ttu-id="17e09-149">암호가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-149">The password is incorrect.</span></span>|  
|<span data-ttu-id="17e09-150">9</span><span class="sxs-lookup"><span data-stu-id="17e09-150">9</span></span>|<span data-ttu-id="17e09-151">암호가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-151">Password is not valid.</span></span>|  
|<span data-ttu-id="17e09-152">11</span><span class="sxs-lookup"><span data-stu-id="17e09-152">11</span></span>|<span data-ttu-id="17e09-153">올바른 로그인이지만 서버 액세스에 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-153">Login is valid, but server access failed.</span></span> <span data-ttu-id="17e09-154">예를 들어 Windows 사용자에게 로컬 Administrators 그룹의 멤버로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 액세스할 수 있는 권한이 있지만 Windows에서 관리자 자격 증명을 제공하지 않는 경우에 이 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-154">One possible cause of this error is when the Windows user has access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a member of the local administrators group, but Windows is not providing administrator credentials.</span></span> <span data-ttu-id="17e09-155">연결하려면 **관리자 권한으로 실행** 옵션을 사용하여 연결 프로그램을 시작하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 특정 로그인으로 Windows 사용자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-155">To connect, start the connecting program using the **Run as administrator** option, and then add the Windows user to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a specific login.</span></span>|  
|<span data-ttu-id="17e09-156">12</span><span class="sxs-lookup"><span data-stu-id="17e09-156">12</span></span>|<span data-ttu-id="17e09-157">올바른 로그인이지만 서버 액세스에 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-157">Login is valid login, but server access failed.</span></span>|  
|<span data-ttu-id="17e09-158">18</span><span class="sxs-lookup"><span data-stu-id="17e09-158">18</span></span>|<span data-ttu-id="17e09-159">암호를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-159">Password must be changed.</span></span>|  
  
 <span data-ttu-id="17e09-160">다른 오류 상태가 있으며 예기치 않은 내부 처리 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-160">Other error states exist and signify an unexpected internal processing error.</span></span>  
  
 <span data-ttu-id="17e09-161">**일반적이진 않지만 가능한 다른 원인**</span><span class="sxs-lookup"><span data-stu-id="17e09-161">**An additional unusual possible cause**</span></span>  
  
 <span data-ttu-id="17e09-162">다음과 같은 상황에서 **SQL Server 인증을 사용하여 로그인하지 못했습니다. 서버가 Windows 인증만 사용하도록 구성되어 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="17e09-162">The error reason **An attempt to login using SQL authentication failed. Server is configured for Windows authentication only.**</span></span> <span data-ttu-id="17e09-163">오류 원인이 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-163">can be returned in the following situations.</span></span>  
  
-   <span data-ttu-id="17e09-164">서버가 혼합 모드 인증으로 구성되고, ODBC 연결이 TCP 프로토콜을 사용하고, 신뢰할 수 있는 연결을 사용해야 한다고 연결에 명시적으로 지정되어 있지 않은 경우</span><span class="sxs-lookup"><span data-stu-id="17e09-164">When the server is configured for mixed mode authentication, and an ODBC connection uses the TCP protocol, and the connection does not explicitly specify that the connection should use a trusted connection.</span></span>  
  
-   <span data-ttu-id="17e09-165">서버가 혼합 모드 인증으로 구성되고, ODBC 연결이 명명된 파이프를 사용하고, 클라이언트가 명명된 파이프를 여는 데 사용한 자격 증명이 자동으로 사용자를 가장하는 데 사용되고, 신뢰할 수 있는 연결을 사용해야 한다고 연결에 명시적으로 지정되어 있지 않은 경우</span><span class="sxs-lookup"><span data-stu-id="17e09-165">When the server is configured for mixed mode authentication, and an ODBC connection uses named pipes, and the credentials the client used to open the named pipe are used to automatically impersonate the user, and the connection does not explicitly specify that the connection should use a trusted connection.</span></span>  
  
 <span data-ttu-id="17e09-166">이 문제를 해결하려면 연결 문자열에 `TRUSTED_CONNECTION = TRUE`를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-166">To resolve this issue, include `TRUSTED_CONNECTION = TRUE` in the connection string.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="17e09-167">예제</span><span class="sxs-lookup"><span data-stu-id="17e09-167">Examples</span></span>  
 <span data-ttu-id="17e09-168">이 예에서 인증 오류 상태는 8이며</span><span class="sxs-lookup"><span data-stu-id="17e09-168">In this example, the authentication error state is 8.</span></span> <span data-ttu-id="17e09-169">암호가 잘못되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-169">This indicates that the password is incorrect.</span></span>  
  
|<span data-ttu-id="17e09-170">Date</span><span class="sxs-lookup"><span data-stu-id="17e09-170">Date</span></span>|<span data-ttu-id="17e09-171">원본</span><span class="sxs-lookup"><span data-stu-id="17e09-171">Source</span></span>|<span data-ttu-id="17e09-172">메시지</span><span class="sxs-lookup"><span data-stu-id="17e09-172">Message</span></span>|  
|----------|------------|-------------|  
|<span data-ttu-id="17e09-173">2007-12-05 20:12:56.34</span><span class="sxs-lookup"><span data-stu-id="17e09-173">2007-12-05 20:12:56.34</span></span>|<span data-ttu-id="17e09-174">로그온</span><span class="sxs-lookup"><span data-stu-id="17e09-174">Logon</span></span>|<span data-ttu-id="17e09-175">오류: 18456, 심각도: 14, 상태: 8.</span><span class="sxs-lookup"><span data-stu-id="17e09-175">Error: 18456, Severity: 14, State: 8.</span></span>|  
|<span data-ttu-id="17e09-176">2007-12-05 20:12:56.34</span><span class="sxs-lookup"><span data-stu-id="17e09-176">2007-12-05 20:12:56.34</span></span>|<span data-ttu-id="17e09-177">로그온</span><span class="sxs-lookup"><span data-stu-id="17e09-177">Logon</span></span>|<span data-ttu-id="17e09-178">사용자 '<user_name>'이(가) 로그인하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-178">Login failed for user '<user_name>'.</span></span> <span data-ttu-id="17e09-179">[클라이언트: \<ip address>]</span><span class="sxs-lookup"><span data-stu-id="17e09-179">[CLIENT: \<ip address>]</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="17e09-180">Windows 인증 모드를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 설치하고 나중에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 Windows 인증 모드로 변경하면 처음에는 **sa** 로그인을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-180">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed using Windows Authentication mode and is later changed to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows Authentication mode, the **sa** login is initially disabled.</span></span> <span data-ttu-id="17e09-181">이 경우 상태 7 오류: "사용자 'sa'이(가) 로그인하지 못했습니다"가 발생합니다. **sa** 로그인을 사용하도록 설정하려면 [서버 인증 모드 변경](../../database-engine/configure-windows/change-server-authentication-mode.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17e09-181">This causes the state 7 error: "Login failed for user 'sa'." To enable the **sa** login, see [Change Server Authentication Mode](../../database-engine/configure-windows/change-server-authentication-mode.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="17e09-182">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="17e09-182">User Action</span></span>  
 <span data-ttu-id="17e09-183">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 연결하려고 하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 혼합 인증 모드로 구성되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-183">If you are trying to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, verify that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured in Mixed Authentication Mode.</span></span>  
  
 <span data-ttu-id="17e09-184">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 연결하려고 하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인이 있고 이 로그인 이름의 철자가 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-184">If you are trying to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, verify that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login exists and that you have spelled it properly.</span></span>  
  
 <span data-ttu-id="17e09-185">Windows 인증을 사용하여 연결하려고 하는 경우 올바른 도메인에 제대로 로그인되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-185">If you are trying to connect using Windows Authentication, verify that you are properly logged into the correct domain.</span></span>  
  
 <span data-ttu-id="17e09-186">오류 상태가 1일 경우에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관리자에게 문의합니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-186">If your error indicates state 1, contact your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrator.</span></span>  
  
 <span data-ttu-id="17e09-187">관리자 자격 증명을 사용하여 연결하려면 **관리자 권한으로 실행** 옵션을 사용하여 애플리케이션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-187">If you are trying to connect using your administrator credentials, start you application by using the **Run as Administrator** option.</span></span> <span data-ttu-id="17e09-188">연결되면 Windows 사용자를 개별 로그인으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-188">When connected, add your Windows user as an individual login.</span></span>  
  
 <span data-ttu-id="17e09-189">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에서 포함된 데이터베이스를 지원하는 경우 포함된 데이터베이스 사용자로 마이그레이션한 후 해당 로그인이 삭제되지 않았는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="17e09-189">If the [!INCLUDE[ssDE](../../includes/ssde-md.md)] supports contained databases, confirm that the login was not deleted after migration to a contained database user.</span></span>  
  
 <span data-ttu-id="17e09-190">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 로컬로 연결하는 경우 **NT AUTHORITY\NETWORK SERVICE**에서 실행되는 서비스의 연결도 컴퓨터의 정규화된 도메인 이름을 사용하여 인증해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e09-190">When connecting locally to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], connections from services running under **NT AUTHORITY\NETWORK SERVICE** must authenticate using the computers fully qualified domain name.</span></span> <span data-ttu-id="17e09-191">자세한 내용은 [방법: 네트워크 서비스 계정을 사용하여 ASP.NET의 리소스에 액세스](https://msdn.microsoft.com/library/ff647402.aspx)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="17e09-191">For more information, see [How To: Use the Network Service Account to Access Resources in ASP.NET](https://msdn.microsoft.com/library/ff647402.aspx)</span></span>  
  
  
