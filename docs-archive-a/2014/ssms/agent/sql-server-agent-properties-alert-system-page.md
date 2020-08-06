---
title: SQL Server 에이전트 속성(경고 시스템 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.alert.f1
ms.assetid: 3e6d3bfd-20ee-4593-86cc-f65b1c08c69d
author: stevestein
ms.author: sstein
ms.openlocfilehash: ff203be21efbd99b90f02261cfe94dd49bd0d849
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659777"
---
# <a name="sql-server-agent-properties-alert-system-page"></a><span data-ttu-id="07404-102">SQL Server 에이전트 속성(경고 시스템 페이지)</span><span class="sxs-lookup"><span data-stu-id="07404-102">SQL Server Agent Properties (Alert System Page)</span></span>
  <span data-ttu-id="07404-103">이 페이지를 사용하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 경고가 보낸 메시지의 설정을 확인하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07404-103">Use this page to view and modify the settings for messages sent by [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts.</span></span>  
  
## <a name="options"></a><span data-ttu-id="07404-104">옵션</span><span class="sxs-lookup"><span data-stu-id="07404-104">Options</span></span>  
 <span data-ttu-id="07404-105">**메일 세션**</span><span class="sxs-lookup"><span data-stu-id="07404-105">**Mail session**</span></span>  
 <span data-ttu-id="07404-106">이 섹션의 옵션을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 메일을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="07404-106">The options in this section configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Mail.</span></span>  
  
 <span data-ttu-id="07404-107">**메일 프로필 설정**</span><span class="sxs-lookup"><span data-stu-id="07404-107">**Enable mail profile**</span></span>  
 <span data-ttu-id="07404-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 메일을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="07404-108">Enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Mail.</span></span> <span data-ttu-id="07404-109">기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 메일은 설정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07404-109">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Mail is not enabled.</span></span>  
  
 <span data-ttu-id="07404-110">**메일 시스템**</span><span class="sxs-lookup"><span data-stu-id="07404-110">**Mail System**</span></span>  
 <span data-ttu-id="07404-111">사용할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 메일 시스템을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="07404-111">Sets the mail system for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to use.</span></span> <span data-ttu-id="07404-112">데이터베이스 메일</span><span class="sxs-lookup"><span data-stu-id="07404-112">Database Mail</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07404-113">전자 메일 시스템을 변경한 후 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스를 다시 시작해야만 변경 내용이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="07404-113">After changing the e-mail system, you must restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service for the change to take effect.</span></span>  
  
 <span data-ttu-id="07404-114">**메일 프로필**</span><span class="sxs-lookup"><span data-stu-id="07404-114">**Mail Profile**</span></span>  
 <span data-ttu-id="07404-115">사용할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 프로필을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="07404-115">Sets the profile for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to use.</span></span> <span data-ttu-id="07404-116">**\<new Database Mail profile...>** 을 선택하여 새 프로필을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07404-116">You may also select **\<new Database Mail profile...>** to create a new profile.</span></span>  
  
 <span data-ttu-id="07404-117">**호출기 전자 메일**</span><span class="sxs-lookup"><span data-stu-id="07404-117">**Pager e-mails**</span></span>  
 <span data-ttu-id="07404-118">이 섹션의 옵션을 사용하여 호출 시스템에서 사용하는 호출기 주소로 보낼 전자 메일 메시지를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07404-118">The options in this section allow you to configure e-mail messages sent to pager addresses to work with your paging system.</span></span>  
  
 <span data-ttu-id="07404-119">**호출기 전자 메일 주소 형식**</span><span class="sxs-lookup"><span data-stu-id="07404-119">**Address formatting for pager e-mails**</span></span>  
 <span data-ttu-id="07404-120">이 섹션에서는 호출기 전자 메일의 주소 형식과 전자 메일에 포함되는 제목 줄을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07404-120">This section allows you to specify the format of the addresses and the subject line included in pager e-mails.</span></span>  
  
 <span data-ttu-id="07404-121">**받는 사람 줄**</span><span class="sxs-lookup"><span data-stu-id="07404-121">**To line**</span></span>  
 <span data-ttu-id="07404-122">메시지의 **받는 사람** 줄에 대한 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="07404-122">Specifies the options for the **To** line of the message</span></span>  
  
 <span data-ttu-id="07404-123">**Prefix**</span><span class="sxs-lookup"><span data-stu-id="07404-123">**Prefix**</span></span>  
 <span data-ttu-id="07404-124">호출기로 전송되는 메시지의 **받는 사람** 줄 시작 부분에 표시되어야 할 고정 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="07404-124">Type any fixed text that your system requires at the beginning of the **To** line of messages sent to a pager.</span></span>  
  
 <span data-ttu-id="07404-125">**호출기**</span><span class="sxs-lookup"><span data-stu-id="07404-125">**Pager**</span></span>  
 <span data-ttu-id="07404-126">접두사와 접미사 사이에 메시지의 전자 메일 주소를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="07404-126">Includes the e-mail address for the message between the prefix and the suffix.</span></span>  
  
 <span data-ttu-id="07404-127">**접미사**</span><span class="sxs-lookup"><span data-stu-id="07404-127">**Suffix**</span></span>  
 <span data-ttu-id="07404-128">호출기로 전송되는 메시지의 **받는 사람** 줄 끝 부분에 표시되어야 할 고정 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="07404-128">Type any fixed text that your paging system requires at the end of the **To** line of messages sent to a pager.</span></span>  
  
 <span data-ttu-id="07404-129">**참조 줄**</span><span class="sxs-lookup"><span data-stu-id="07404-129">**Cc line**</span></span>  
 <span data-ttu-id="07404-130">메시지의 **참조** 줄에 대한 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="07404-130">Specifies options for the **Cc** line of the message.</span></span>  
  
 <span data-ttu-id="07404-131">**Prefix**</span><span class="sxs-lookup"><span data-stu-id="07404-131">**Prefix**</span></span>  
 <span data-ttu-id="07404-132">호출기로 전송되는 메시지의 **참조** 줄 시작 부분에 표시되어야 할 고정 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="07404-132">Type any fixed text that your system requires at the beginning of the **Cc** line of messages sent to a pager.</span></span>  
  
 <span data-ttu-id="07404-133">**호출기**</span><span class="sxs-lookup"><span data-stu-id="07404-133">**Pager**</span></span>  
 <span data-ttu-id="07404-134">접두사와 접미사 사이에 메시지의 전자 메일 주소를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="07404-134">Includes the e-mail address for the message between the prefix and the suffix.</span></span>  
  
 <span data-ttu-id="07404-135">**접미사**</span><span class="sxs-lookup"><span data-stu-id="07404-135">**Suffix**</span></span>  
 <span data-ttu-id="07404-136">호출기로 전송되는 메시지의 **참조** 줄 끝 부분에 표시되어야 할 고정 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="07404-136">Type any fixed text that your paging system requires at the end of the **Cc** line of messages sent to a pager.</span></span>  
  
 <span data-ttu-id="07404-137">**Subject**</span><span class="sxs-lookup"><span data-stu-id="07404-137">**Subject**</span></span>  
 <span data-ttu-id="07404-138">메시지의 제목에 대한 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="07404-138">Specifies the options for the subject of the message.</span></span>  
  
 <span data-ttu-id="07404-139">**Prefix**</span><span class="sxs-lookup"><span data-stu-id="07404-139">**Prefix**</span></span>  
 <span data-ttu-id="07404-140">호출기로 전송되는 메시지의 **제목** 줄 시작 부분에 표시되어야 할 고정 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="07404-140">Type any fixed text that your paging system requires at the beginning of the **Subject** line of messages sent to a pager.</span></span>  
  
 <span data-ttu-id="07404-141">**접미사**</span><span class="sxs-lookup"><span data-stu-id="07404-141">**Suffix**</span></span>  
 <span data-ttu-id="07404-142">호출기로 전송되는 메시지의 **제목** 줄 끝 부분에 표시되어야 할 고정 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="07404-142">Type any fixed text that your paging system requires at the end of the **Subject** line of messages sent to a pager.</span></span>  
  
 <span data-ttu-id="07404-143">**알림 메시지에 전자 메일 본문 포함**</span><span class="sxs-lookup"><span data-stu-id="07404-143">**Include body of e-mail in notification message**</span></span>  
 <span data-ttu-id="07404-144">호출기로 전송되는 메시지에 전자 메일 메시지 본문을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="07404-144">Includes the body of the e-mail message in the message sent to the pager.</span></span>  
  
 <span data-ttu-id="07404-145">**유사 시 대기 운영자**</span><span class="sxs-lookup"><span data-stu-id="07404-145">**Fail-safe operator**</span></span>  
 <span data-ttu-id="07404-146">이 섹션에서는 유사 시 대기 운영자에 대한 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07404-146">This section allows you to specify the options for the fail-safe operator.</span></span>  
  
 <span data-ttu-id="07404-147">**유사 시 대기 운영자 설정**</span><span class="sxs-lookup"><span data-stu-id="07404-147">**Enable fail-safe operator**</span></span>  
 <span data-ttu-id="07404-148">유사 시 대기 운영자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="07404-148">Specifies a fail safe operator.</span></span>  
  
 <span data-ttu-id="07404-149">**연산자**</span><span class="sxs-lookup"><span data-stu-id="07404-149">**Operator**</span></span>  
 <span data-ttu-id="07404-150">유사 시 대기 알림을 받을 운영자의 이름을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="07404-150">Sets the name of the operator to receive fail-safe notifications.</span></span>  
  
 <span data-ttu-id="07404-151">**알림 방법**</span><span class="sxs-lookup"><span data-stu-id="07404-151">**Notify using**</span></span>  
 <span data-ttu-id="07404-152">유사 시 대기 운영자에게 알릴 때 사용할 방법을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="07404-152">Sets the method to use for notifying the fail-safe operator.</span></span>  
  
 <span data-ttu-id="07404-153">**토큰 바꾸기**</span><span class="sxs-lookup"><span data-stu-id="07404-153">**Token Replacement**</span></span>  
 <span data-ttu-id="07404-154">이 섹션을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 경고로 실행되는 작업에 사용할 수 있는 작업 단계 토큰을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07404-154">This section allows you to enable job step tokens that can be used in jobs run by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts.</span></span> <span data-ttu-id="07404-155">작업 단계 토큰에 대한 자세한 내용은 [작업 단계에서 토큰 사용](use-tokens-in-job-steps.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07404-155">For more information about job step tokens, see [Use Tokens in Job Steps](use-tokens-in-job-steps.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="07404-156">Windows 이벤트 로그에 대한 쓰기 권한이 있는 모든 Windows 사용자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 경고로 활성화되는 작업 단계에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07404-156">Any Windows user with write permissions on the Windows Event Log may be able to access job steps that are activated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts.</span></span> <span data-ttu-id="07404-157">이러한 보안상 위험을 방지하기 위해 경고로 활성화되는 작업에 사용할 수 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 토큰은 기본적으로 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="07404-157">To avoid this security risk, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent tokens that can be used in jobs activated by alerts are disabled by default.</span></span> <span data-ttu-id="07404-158">이러한 토큰은 **$(A-DBN)** , **$(A-SVR)** , **$(A-ERR)** , **$(A-SEV)** 및 **$(A-MSG)** 입니다.</span><span class="sxs-lookup"><span data-stu-id="07404-158">These tokens are: **$(A-DBN)**, **$(A-SVR)**, **$(A-ERR)**, **$(A-SEV)**, and **$(A-MSG)**.</span></span>  
>   
>  <span data-ttu-id="07404-159">이러한 토큰을 사용해야 하는 경우 토큰을 설정하기 전에 Administrators 그룹과 같은 트러스트된 Windows 보안 그룹의 멤버만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 설치된 컴퓨터의 이벤트 로그에 대한 쓰기 권한을 가지도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="07404-159">If you need to use these tokens, ensure that only members of trusted Windows security groups, such as the Administrators group, have write permissions on the Event Log of the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resides before enabling them.</span></span>  
  
 <span data-ttu-id="07404-160">**경고에 대한 모든 응답 작업에 대해 토큰 바꾸기**</span><span class="sxs-lookup"><span data-stu-id="07404-160">**Replace tokens for all job responses to alerts**</span></span>  
 <span data-ttu-id="07404-161">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 경고로 활성화되는 작업에 대해 토큰 바꾸기를 설정하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07404-161">Select this check box to enable token replacement for jobs that are activated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alerts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07404-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="07404-162">See Also</span></span>  
 <span data-ttu-id="07404-163">[작업자](operators.md) </span><span class="sxs-lookup"><span data-stu-id="07404-163">[Operators](operators.md) </span></span>  
 <span data-ttu-id="07404-164">[데이터베이스 메일 사용 하도록 SQL Server 에이전트 메일 구성](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md) </span><span class="sxs-lookup"><span data-stu-id="07404-164">[Configure SQL Server Agent Mail to Use Database Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md) </span></span>  
 [<span data-ttu-id="07404-165">데이터베이스 메일</span><span class="sxs-lookup"><span data-stu-id="07404-165">Database Mail</span></span>](../../relational-databases/database-mail/database-mail.md)  
  
  
