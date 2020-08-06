---
title: 보안 로그에 SQL Server Audit 이벤트 쓰기 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], Security Log
- server audit [SQL Server]
- audits [SQL Server], writing to Security Log
- security logs [SQL Server]
ms.assetid: 6fabeea3-7a42-4769-a0f3-7e04daada314
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: d59134b278f29c9b604208d8cab7e982144b9c9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647567"
---
# <a name="write-sql-server-audit-events-to-the-security-log"></a><span data-ttu-id="7a41f-102">보안 로그에 SQL Server Audit 이벤트 쓰기</span><span class="sxs-lookup"><span data-stu-id="7a41f-102">Write SQL Server Audit Events to the Security Log</span></span>
  <span data-ttu-id="7a41f-103">보안 수준이 높은 환경에서는 Windows 보안 로그에 개체 액세스를 기록하는 이벤트를 쓰는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-103">In a high security environment, the Windows Security log is the appropriate location to write events that record object access.</span></span> <span data-ttu-id="7a41f-104">다른 감사 위치도 지원되지만 변조될 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-104">Other audit locations are supported but are more subject to tampering.</span></span>  
  
 <span data-ttu-id="7a41f-105">Windows 보안 로그에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서버 감사를 쓰려면 두 가지 주요 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-105">There are two key requirements for writing [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] server audits to the Windows Security log:</span></span>  
  
-   <span data-ttu-id="7a41f-106">감사 개체 액세스 설정이 이벤트를 캡처하도록 구성되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-106">The audit object access setting must be configured to capture the events.</span></span> <span data-ttu-id="7a41f-107">이 감사 정책 도구(`auditpol.exe`)는 **감사 개체 액세스** 범주의 여러 하위 정책 설정을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-107">The audit policy tool (`auditpol.exe`) exposes a variety of sub-policies settings in the **audit object access** category.</span></span> <span data-ttu-id="7a41f-108">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 가 개체 액세스를 감사하도록 허용하려면 **애플리케이션에서 생성된** 설정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-108">To allow [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to audit object access, configure the **application generated** setting.</span></span>  
  
-   <span data-ttu-id="7a41f-109">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서비스를 실행 중인 계정이 Windows 보안 로그에 쓰려면 **보안 감사 생성** 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-109">The account that the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service is running under must have the **generate security audits** permission to write to the Windows Security log.</span></span> <span data-ttu-id="7a41f-110">기본적으로 LOCAL SERVICE 및 NETWORK SERVICE 계정에는 이 권한이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-110">By default, the LOCAL SERVICE and the NETWORK SERVICE accounts have this permission.</span></span> <span data-ttu-id="7a41f-111">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 가 이러한 계정 중 하나로 실행 중인 경우에는 이 단계가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-111">This step is not required if [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is running under one of those accounts.</span></span>  
  
 <span data-ttu-id="7a41f-112">Windows 감사 정책은 Windows 보안 로그에 기록하도록 구성된 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 감사에 영향을 줄 수 있으며 감사 정책이 잘못 구성된 경우 이벤트가 손실될 가능성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-112">The Windows audit policy can affect [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auditing if it is configured to write to the Windows Security log, with the potential of losing events if the audit policy is incorrectly configured.</span></span> <span data-ttu-id="7a41f-113">일반적으로 Windows 보안 로그는 이전 이벤트를 덮어쓰도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-113">Typically, the Windows Security log is set to overwrite the older events.</span></span> <span data-ttu-id="7a41f-114">이렇게 하면 가장 최신 이벤트를 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-114">This preserves the most recent events.</span></span> <span data-ttu-id="7a41f-115">하지만 Windows 보안 로그가 이전 이벤트를 덮어쓰도록 설정되지 않으면 보안 로그가 꽉 찰 경우 시스템에서 Windows 이벤트 1104(로그가 꽉 참)가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-115">However, if the Windows Security log is not set to overwrite older events, then if the Security log is full, the system will issue Windows event 1104 (Log is full).</span></span> <span data-ttu-id="7a41f-116">그러면 다음과 같이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-116">At that point:</span></span>  
  
-   <span data-ttu-id="7a41f-117">보안 이벤트가 더 이상 기록되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-117">No further security events will be recorded</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="7a41f-118">에서 시스템이 보안 로그에 이벤트를 기록할 수 없다는 것을 감지하지 못하고 따라서 감사 이벤트가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-118">will not be able to detect that the system is not able to record the events in the Security log, resulting in the potential loss of audit events</span></span>  
  
-   <span data-ttu-id="7a41f-119">시스템 관리자가 보안 로그를 수정하면 로깅 동작이 정상으로 돌아옵니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-119">After the box administrator fixes the Security log, the logging behavior will return to normal.</span></span>  
  
 <span data-ttu-id="7a41f-120">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="7a41f-120">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7a41f-121">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="7a41f-121">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7a41f-122">제한 사항</span><span class="sxs-lookup"><span data-stu-id="7a41f-122">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="7a41f-123">보안</span><span class="sxs-lookup"><span data-stu-id="7a41f-123">Security</span></span>](#Security)  
  
-   <span data-ttu-id="7a41f-124">**보안 로그에 SQL Server Audit 이벤트를 쓰려면**</span><span class="sxs-lookup"><span data-stu-id="7a41f-124">**To write SQL Server audit events to the Security Log:**</span></span>  
  
     [<span data-ttu-id="7a41f-125">Windows에서 auditpol을 사용하여 감사 개체 액세스 설정 구성</span><span class="sxs-lookup"><span data-stu-id="7a41f-125">Configure the audit object access setting in Windows using auditpol</span></span>](#auditpolAccess)  
  
     [<span data-ttu-id="7a41f-126">Windows에서 secpol을 사용하여 감사 개체 액세스 설정 구성</span><span class="sxs-lookup"><span data-stu-id="7a41f-126">Configure the audit object access setting in Windows using secpol</span></span>](#secpolAccess)  
  
     [<span data-ttu-id="7a41f-127">secpol을 사용하여 계정에 보안 감사 생성 권한 부여</span><span class="sxs-lookup"><span data-stu-id="7a41f-127">Grant the generate security audits permission to an account using secpol</span></span>](#secpolPermission)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7a41f-128">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="7a41f-128">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="7a41f-129">제한 사항</span><span class="sxs-lookup"><span data-stu-id="7a41f-129">Limitations and Restrictions</span></span>  
 <span data-ttu-id="7a41f-130">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 컴퓨터 관리자는 도메인 정책이 보안 로그에 대한 로컬 설정을 덮어쓸 수 있다는 점을 유의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-130">Administrators of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] computer should understand that local settings for the Security log can be overwritten by a domain policy.</span></span> <span data-ttu-id="7a41f-131">이 경우에 도메인 정책은 하위 범주 설정을 덮어쓸 수 있습니다(**auditpol /get /subcategory:"application generated"** ).</span><span class="sxs-lookup"><span data-stu-id="7a41f-131">In this case, the domain policy might overwrite the subcategory setting (**auditpol /get /subcategory:"application generated"**).</span></span> <span data-ttu-id="7a41f-132">이는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에서 감사하려는 이벤트가 기록되지 않는다는 점을 감지할 필요 없이 이벤트를 로깅할 수 있는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 기능에 영향을 미칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-132">This can affect [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ability to log events without having any way to detect that the events that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is trying to audit are not going to be recorded.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7a41f-133">보안</span><span class="sxs-lookup"><span data-stu-id="7a41f-133">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7a41f-134">권한</span><span class="sxs-lookup"><span data-stu-id="7a41f-134">Permissions</span></span>  
 <span data-ttu-id="7a41f-135">이러한 설정을 구성하려면 Windows 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-135">You must be a Windows administrator to configure these settings.</span></span>  
  
##  <a name="to-configure-the-audit-object-access-setting-in-windows-using-auditpol"></a><a name="auditpolAccess"></a> <span data-ttu-id="7a41f-136">Windows에서 auditpol을 사용하여 감사 개체 액세스 설정을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="7a41f-136">To configure the audit object access setting in Windows using auditpol</span></span>  
  
1.  <span data-ttu-id="7a41f-137">관리자 권한으로 명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-137">Open a command prompt with administrative permissions.</span></span>  
  
    1.  <span data-ttu-id="7a41f-138">**시작** 메뉴에서 **모든 프로그램**, **보조프로그램**을 차례로 가리키고 **명령 프롬프트**를 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-138">On the **Start** menu, point to **All Programs**, point to **Accessories**, right-click **Command Prompt**, and then click **Run as administrator**.</span></span>  
  
    2.  <span data-ttu-id="7a41f-139">**사용자 계정 컨트롤** 대화 상자가 열리면 **계속**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-139">If the **User Account Control** dialog box opens, click **Continue**.</span></span>  
  
2.  <span data-ttu-id="7a41f-140">다음 문을 실행하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 감사를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-140">Execute the following statement to enable auditing from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
    ```  
    auditpol /set /subcategory:"application generated" /success:enable /failure:enable  
    ```  
  
3.  <span data-ttu-id="7a41f-141">명령 프롬프트 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-141">Close the command prompt window.</span></span>  
  
##  <a name="to-grant-the-generate-security-audits-permission-to-an-account-using-secpol"></a><a name="secpolAccess"></a> <span data-ttu-id="7a41f-142">secpol을 사용하여 계정에 보안 감사 생성 권한을 부여하려면</span><span class="sxs-lookup"><span data-stu-id="7a41f-142">To grant the generate security audits permission to an account using secpol</span></span>  
  
1.  <span data-ttu-id="7a41f-143">Windows 운영 체제의 **시작** 메뉴에서 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-143">For any Windows operating system, on the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="7a41f-144">**secpol.msc** 를 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-144">Type **secpol.msc** and then click **OK**.</span></span> <span data-ttu-id="7a41f-145">**사용자 액세스 제어** 대화 상자가 열리면 **계속**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-145">If the **User Access Control** dialog box appears, click **Continue**.</span></span>  
  
3.  <span data-ttu-id="7a41f-146">로컬 보안 정책 도구에서 **보안 설정**, **로컬 정책**을 차례로 확장한 다음 **사용자 권한 할당**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-146">In the Local Security Policy tool, expand **Security Settings**, expand **Local Policies**, and then click **User Rights Assignment**.</span></span>  
  
4.  <span data-ttu-id="7a41f-147">결과 창에서 **보안 감사 생성**을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-147">In the results pane, double-click **Generate security audits**.</span></span>  
  
5.  <span data-ttu-id="7a41f-148">**로컬 보안 설정** 탭에서 **사용자 또는 그룹 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-148">On the **Local Security Setting** tab, click **Add User or Group**.</span></span>  
  
6.  <span data-ttu-id="7a41f-149">**사용자, 컴퓨터 또는 그룹 선택** 대화 상자에서 **domain1\user1** 과 같은 사용자 계정의 이름을 입력한 다음 **확인**을 클릭하거나 **고급** 을 클릭하여 계정을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-149">In the **Select Users, Computers, or Groups** dialog box, either type the name of the user account, such as **domain1\user1** and then click **OK**, or click **Advanced** and search for the account.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="7a41f-150">보안 정책 도구를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-150">Close the Security Policy tool.</span></span>  
  
9. <span data-ttu-id="7a41f-151">이 설정을 사용하려면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-151">Restart [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to enable this setting.</span></span>  
  
##  <a name="to-configure-the-audit-object-access-setting-in-windows-using-secpol"></a><a name="secpolPermission"></a> <span data-ttu-id="7a41f-152">Windows에서 secpol을 사용하여 감사 개체 액세스 설정을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="7a41f-152">To configure the audit object access setting in Windows using secpol</span></span>  
  
1.  <span data-ttu-id="7a41f-153">운영 체제가 [!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)] 또는 Windows Server 2008 이전 버전인 경우 **시작** 메뉴에서 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-153">If the operating system is earlier than [!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)] or Windows Server 2008, on the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="7a41f-154">**secpol.msc** 를 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-154">Type **secpol.msc** and then click **OK**.</span></span> <span data-ttu-id="7a41f-155">**사용자 액세스 제어** 대화 상자가 열리면 **계속**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-155">If the **User Access Control** dialog box appears, click **Continue**.</span></span>  
  
3.  <span data-ttu-id="7a41f-156">로컬 보안 정책 도구에서 **보안 설정**, **로컬 정책**을 차례로 확장한 다음 **감사 정책**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-156">In the Local Security Policy tool, expand **Security Settings**, expand **Local Policies**, and then click **Audit Policy**.</span></span>  
  
4.  <span data-ttu-id="7a41f-157">결과 창에서 **개체 액세스 감사**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-157">In the results pane, double-click **Audit object access**.</span></span>  
  
5.  <span data-ttu-id="7a41f-158">**로컬 보안 설정** 탭의 **다음 시도 감사** 영역에서 **성공** 및 **실패**를 모두 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-158">On the **Local Security Setting** tab, in the **Audit these attempts** area, select both **Success** and **Failure**.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="7a41f-159">보안 정책 도구를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="7a41f-159">Close the Security Policy tool.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a41f-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7a41f-160">See Also</span></span>  
 [<span data-ttu-id="7a41f-161">SQL Server Audit&#40;데이터베이스 엔진&#41;</span><span class="sxs-lookup"><span data-stu-id="7a41f-161">SQL Server Audit &#40;Database Engine&#41;</span></span>](sql-server-audit-database-engine.md)  
  
  
