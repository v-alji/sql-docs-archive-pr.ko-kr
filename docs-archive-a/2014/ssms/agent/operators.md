---
title: 운영자 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- operators (users) [Database Engine]
- fail-safe operator [SQL Server]
- aliases [SQL Server], operators
- SQL Server Agent alerts, operators
- contact information [SQL Server Agent]
- net send [SQL Server]
- e-mail [SQL Server], SQL Server Agent operators
- pager notifications [SQL Server Agent]
- mail [SQL Server], SQL Server Agent operators
- operators (users) [Database Engine], defining
- jobs [SQL Server Agent], operators
- alerts [SQL Server], operators
ms.assetid: 38e8488f-2669-4cea-b9c3-5f394a663678
author: stevestein
ms.author: sstein
ms.openlocfilehash: d141a2db9a69603701200bc50dcac57ef402968a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735836"
---
# <a name="operators"></a><span data-ttu-id="e7bcd-102">연산자</span><span class="sxs-lookup"><span data-stu-id="e7bcd-102">Operators</span></span>
  <span data-ttu-id="e7bcd-103">운영자는 작업이 완료되거나 경고가 발생할 때 전자 메일 알림을 받을 수 있는 사람이나 그룹의 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-103">Operators are aliases for people or groups that can receive electronic notification when jobs have completed or alerts have been raised.</span></span> <span data-ttu-id="e7bcd-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스는 운영자를 통해 관리자 알림을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service supports the notification of administrators through operators.</span></span> <span data-ttu-id="e7bcd-105">운영자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트의 알림 및 모니터링 기능을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-105">Operators enable notification and monitoring capabilities of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
## <a name="operator-attributes-and-concepts"></a><span data-ttu-id="e7bcd-106">운영자 특성 및 개념</span><span class="sxs-lookup"><span data-stu-id="e7bcd-106">Operator Attributes and Concepts</span></span>  
 <span data-ttu-id="e7bcd-107">운영자의 기본 특성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-107">The primary attributes of an operator are:</span></span>  
  
-   <span data-ttu-id="e7bcd-108">운영자 이름</span><span class="sxs-lookup"><span data-stu-id="e7bcd-108">Operator name</span></span>  
  
-   <span data-ttu-id="e7bcd-109">연락처 정보</span><span class="sxs-lookup"><span data-stu-id="e7bcd-109">Contact information</span></span>  
  
### <a name="naming-an-operator"></a><span data-ttu-id="e7bcd-110">운영자 명명</span><span class="sxs-lookup"><span data-stu-id="e7bcd-110">Naming an Operator</span></span>  
 <span data-ttu-id="e7bcd-111">운영자는 모두 이름이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-111">Every operator must have a name.</span></span> <span data-ttu-id="e7bcd-112">운영자 이름은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 내에서 고유해야 하며 **128** 자를 초과할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-112">Operator names must be unique within the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance and can be no longer than **128** characters.</span></span>  
  
### <a name="contact-information"></a><span data-ttu-id="e7bcd-113">연락처 정보</span><span class="sxs-lookup"><span data-stu-id="e7bcd-113">Contact Information</span></span>  
 <span data-ttu-id="e7bcd-114">운영자의 연락 정보는 운영자가 알림을 받는 방법을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-114">An operator's contact information defines how the operator is notified.</span></span> <span data-ttu-id="e7bcd-115">운영자는 전자 메일, 호출기 또는 **net send** 명령으로 알림을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-115">Operators can be notified by e-mail, pager, or through the **net send** command:</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e7bcd-116">**이후 버전에서는** 에이전트에서 호출기 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] net send [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]옵션이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-116">The Pager and **net send** options will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e7bcd-117">새 개발 작업에서는 이 기능을 사용하지 말고, 현재 이 기능을 사용하는 애플리케이션은 수정하세요.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-117">Avoid using these features in new development work, and plan to modify applications that currently use these features.</span></span>  
  
-   <span data-ttu-id="e7bcd-118">**전자 메일 알림**</span><span class="sxs-lookup"><span data-stu-id="e7bcd-118">**E-mail notification**</span></span>  
  
     <span data-ttu-id="e7bcd-119">전자 메일 알림으로 운영자에게 전자 메일 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-119">E-mail notification sends an e-mail message to the operator.</span></span> <span data-ttu-id="e7bcd-120">전자 메일 알림의 경우 운영자의 전자 메일 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-120">For e-mail notification, you provide the e-mail address for the operator.</span></span>  
  
-   <span data-ttu-id="e7bcd-121">**호출기 알림**</span><span class="sxs-lookup"><span data-stu-id="e7bcd-121">**Pager notification**</span></span>  
  
     <span data-ttu-id="e7bcd-122">전자 메일을 사용하여 호출을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-122">Paging is implemented by e-mail.</span></span> <span data-ttu-id="e7bcd-123">호출기 알림의 경우 운영자가 호출기 메시지를 받는 전자 메일 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-123">For pager notification, you provide the e-mail address where the operator receives pager messages.</span></span> <span data-ttu-id="e7bcd-124">호출기 알림을 설정하려면 인바운드 메일을 처리하는 메일 서버 소프트웨어를 설치한 다음 호출기 메시지로 변환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-124">To set up pager notification, you must install software on the mail server that processes inbound mail and converts it to a pager message.</span></span> <span data-ttu-id="e7bcd-125">소프트웨어는 다음을 비롯하여 여러 가지 접근 방법 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-125">The software can take one of several approaches, including:</span></span>  
  
    -   <span data-ttu-id="e7bcd-126">호출기 공급자 사이트에서 원격 메일 서버로 메일 전달</span><span class="sxs-lookup"><span data-stu-id="e7bcd-126">Forwarding the mail to a remote mail server at the site of the pager provider.</span></span>  
  
         <span data-ttu-id="e7bcd-127">요청한 소프트웨어를 일반적으로 로컬 메일 시스템의 일부로 사용할 수 있어도 호출기 공급자는 이 서비스를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-127">The pager provider must offer this service, although the software required is generally available as part of the local mail system.</span></span> <span data-ttu-id="e7bcd-128">자세한 내용은 호출기 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-128">For more information, see your pager documentation.</span></span>  
  
    -   <span data-ttu-id="e7bcd-129">호출기 공급자 사이트에서 메일 서버로 인터넷을 통해 메일 라우팅</span><span class="sxs-lookup"><span data-stu-id="e7bcd-129">Routing the e-mail by way of the Internet to an e-mail server at the pager provider's site.</span></span>  
  
         <span data-ttu-id="e7bcd-130">첫 번째 접근 방법의 변형입니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-130">This is a variation on the first approach.</span></span>  
  
    -   <span data-ttu-id="e7bcd-131">연결된 모뎀을 사용하여 인바운드 메일을 처리하고 호출기로 전화 걸기</span><span class="sxs-lookup"><span data-stu-id="e7bcd-131">Processing the inbound e-mail and dialing the pager by using an attached modem.</span></span>  
  
         <span data-ttu-id="e7bcd-132">이 소프트웨어는 서비스 공급자를 호출하는 소유자에 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-132">This software is proprietary to pager service providers.</span></span> <span data-ttu-id="e7bcd-133">이 소프트웨어는 전자 메일 주소 정보의 일부나 전부를 호출기 번호로 해석하거나 전자 메일 이름이 변환 테이블의 호출기 번호와 일치하는지 확인하여 받은 편지함을 주기적으로 처리는 메일 클라이언트 역할을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-133">The software acts as a e-mail client that periodically processes its inbox either by interpreting all or part of the e-mail address information as a pager number, or by matching the e-mail name to a pager number in a translation table.</span></span>  
  
         <span data-ttu-id="e7bcd-134">운영자가 모두 호출기 공급자를 공유하면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 사용하여 호출기-전자 메일 시스템에서 요청하는 특수한 전자 메일의 서식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-134">If all of the operators share a pager provider, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to specify any special e-mail formatting that is required by the pager-to-e-mail system.</span></span> <span data-ttu-id="e7bcd-135">특수한 서식은 접두사 또는 접미사이며 전자 메일의 다음 항목에 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-135">The special formatting can be a prefix or a suffix and can be included in the following lines of the e-mail:</span></span>  
  
         <span data-ttu-id="e7bcd-136">**주체**:</span><span class="sxs-lookup"><span data-stu-id="e7bcd-136">**Subject:**</span></span>  
  
         <span data-ttu-id="e7bcd-137">**참조**:</span><span class="sxs-lookup"><span data-stu-id="e7bcd-137">**Cc**:</span></span>  
  
         <span data-ttu-id="e7bcd-138">**받는 사람**:</span><span class="sxs-lookup"><span data-stu-id="e7bcd-138">**To**:</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e7bcd-139">용량이 낮은 영숫자 페이징 시스템을 사용하면 호출기 알림에서 오류 텍스트를 제외하고 전송하도록 텍스트를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-139">If you use a low-capacity alphanumeric paging system, you can shorten the text that is sent by excluding the error text from the pager notification.</span></span> <span data-ttu-id="e7bcd-140">용량이 낮은 영숫자 페이징 시스템의 예로는 페이지당 64자로 제한된 시스템이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-140">An example of a low-capacity alphanumeric paging system is one that is limited to 64 characters per page.</span></span>  
  
-   <span data-ttu-id="e7bcd-141">**net sendnotification**</span><span class="sxs-lookup"><span data-stu-id="e7bcd-141">**net sendnotification**</span></span>  
  
     <span data-ttu-id="e7bcd-142">**net send** 명령을 사용하여 운영자에게 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-142">This sends a message to the operator by means of the **net send** command.</span></span> <span data-ttu-id="e7bcd-143">**net send**에서는 네트워크 메시지의 수신자(컴퓨터나 사용자)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-143">For **net send**, specify the recipient (computer or user) of a network message.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e7bcd-144">**net send** 명령은 Microsoft Windows Messenger를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-144">The **net send** command uses Microsoft Windows Messenger.</span></span> <span data-ttu-id="e7bcd-145">경고를 성공적으로 보내려면 이 서비스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 실행 중인 컴퓨터와 운영자가 사용하는 컴퓨터에서 모두 실행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-145">To successfully send alerts, this service must be running on both the computer on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running and the computer that the operator uses.</span></span>  
  
## <a name="alerting-and-fail-safe-operators"></a><span data-ttu-id="e7bcd-146">경고 알림 및 유사 시 대기 운영자</span><span class="sxs-lookup"><span data-stu-id="e7bcd-146">Alerting and Fail-Safe Operators</span></span>  
 <span data-ttu-id="e7bcd-147">경고에 응답하여 알림을 받을 운영자를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-147">You can choose which operators are to be notified in response to an alert.</span></span> <span data-ttu-id="e7bcd-148">또한 경고를 예약하여 운영자가 교대로 알림을 받도록 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-148">For example, you can assign rotating responsibilities for operator notification by scheduling alerts.</span></span> <span data-ttu-id="e7bcd-149">예를 들어 운영자 A는 월, 수, 금에 발생하는 경고에 대한 알림을 받고 운영자 B는 화, 목, 토에 발생하는 경고에 대한 알림을 받으며</span><span class="sxs-lookup"><span data-stu-id="e7bcd-149">For example, Individual A is notified of alerts that occur on Monday, Wednesday, or Friday, and Individual B is notified of alerts that occur on Tuesday, Thursday, or Saturday.</span></span>  
  
 <span data-ttu-id="e7bcd-150">유사 시 대기 운영자는 지정된 운영자에 대한 호출기 알림이 모두 실패한 다음 경고 알림을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-150">The fail-safe operator receives an alert notification after all pager notifications to the designated operators have failed.</span></span> <span data-ttu-id="e7bcd-151">예를 들어 3명의 운영자를 호출기 알림에 대해 정의했는데 지정된 운영자 중 아무도 호출을 받을 수 없으면 유사 시 대기 운영자가 알림을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-151">For example, if you have defined three operators for pager notifications and none of the designated operators can be paged, the fail-safe operator is notified.</span></span>  
  
 <span data-ttu-id="e7bcd-152">유사 시 대기 운영자는 다음 경우에 알림을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-152">The fail-safe operator is notified when:</span></span>  
  
-   <span data-ttu-id="e7bcd-153">경고에 대해 책임이 있는 운영자가 호출 받을 수 없는 경우</span><span class="sxs-lookup"><span data-stu-id="e7bcd-153">The operators responsible for the alert could not be paged.</span></span>  
  
     <span data-ttu-id="e7bcd-154">주 운영자에게 연락하지 못한 이유에는 호출기 주소가 틀리거나 운영자가 근무 중이 아닌 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-154">Reasons for failure to reach primary operators include incorrect pager addresses and off-duty operators.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e7bcd-155">에이전트가 **msdb** 데이터베이스의 시스템 테이블에 액세스할 수 없는 경우</span><span class="sxs-lookup"><span data-stu-id="e7bcd-155">Agent cannot access system tables in the **msdb** database.</span></span>  
  
     <span data-ttu-id="e7bcd-156">**sysnotifications** 시스템 테이블에서 경고에 대해 운영자 업무를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-156">The **sysnotifications** system table specifies operator responsibilities for alerts.</span></span>  
  
 <span data-ttu-id="e7bcd-157">유사 시 대기 운영자는 보안 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-157">The fail-safe operator is a security feature.</span></span> <span data-ttu-id="e7bcd-158">유사 시 대기 근무를 다른 운영자에게 다시 할당하지 않거나 유사 시 대기 근무 할당을 함께 삭제하지 않고 유사 시 대기 근무에 할당된 운영자를 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-158">You cannot delete the operator assigned to fail-safe duty without reassigning fail-safe duty to another operator, or deleting the fail-safe assignment altogether.</span></span>  
  
## <a name="notifying-an-operator"></a><span data-ttu-id="e7bcd-159">운영자에게 알림</span><span class="sxs-lookup"><span data-stu-id="e7bcd-159">Notifying an Operator</span></span>  
 <span data-ttu-id="e7bcd-160">운영자에게 알리려면 다음 중 한 가지 이상을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-160">You must set up one or more of the following in order to notify an operator:</span></span>  
  
-   <span data-ttu-id="e7bcd-161">데이터베이스 메일 기능으로 전자 메일을 보내려면 SMTP를 지원하는 전자 메일 서버에 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-161">To send e-mail with Database Mail functionality, you must have access to an e-mail server that supports SMTP.</span></span>  
  
-   <span data-ttu-id="e7bcd-162">호출할 경우에는 타사 제품 호출기-전자 메일 소프트웨어 및/또는 하드웨어가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-162">For paging, you must have third-party pager-to-e-mail software and/or hardware.</span></span>  
  
-   <span data-ttu-id="e7bcd-163">**net send**를 사용하려면 운영자가 지정된 컴퓨터에 로그온하고 지정된 컴퓨터가 Windows Messenger에서 메시지를 받도록 허용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bcd-163">To use **net send**, the operator must be logged on to the specified computer, and the specified computer must allow messages from Windows Messenger.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="e7bcd-164">관련 작업</span><span class="sxs-lookup"><span data-stu-id="e7bcd-164">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e7bcd-165">**작업**</span><span class="sxs-lookup"><span data-stu-id="e7bcd-165">**Tasks**</span></span>|<span data-ttu-id="e7bcd-166">**항목**</span><span class="sxs-lookup"><span data-stu-id="e7bcd-166">**Topic**</span></span>|  
|<span data-ttu-id="e7bcd-167">운영자 만들기 관련 태스크</span><span class="sxs-lookup"><span data-stu-id="e7bcd-167">Tasks related to creating an operator</span></span>|[<span data-ttu-id="e7bcd-168">운영자 만들기</span><span class="sxs-lookup"><span data-stu-id="e7bcd-168">Create an Operator</span></span>](create-an-operator.md)<br /><br /> [<span data-ttu-id="e7bcd-169">Designate a Fail-Safe Operator</span><span class="sxs-lookup"><span data-stu-id="e7bcd-169">Designate a Fail-Safe Operator</span></span>](designate-a-fail-safe-operator.md)|  
|<span data-ttu-id="e7bcd-170">알림 할당 관련 태스크</span><span class="sxs-lookup"><span data-stu-id="e7bcd-170">Tasks related to assigning alerts</span></span>|[<span data-ttu-id="e7bcd-171">운영자에게 경고 할당</span><span class="sxs-lookup"><span data-stu-id="e7bcd-171">Assign Alerts to an Operator</span></span>](assign-alerts-to-an-operator.md)<br /><br /> [<span data-ttu-id="e7bcd-172">경고에 대한 응답 정의&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="e7bcd-172">Define the Response to an Alert &#40;SQL Server Management Studio&#41;</span></span>](define-the-response-to-an-alert-sql-server-management-studio.md)<br /><br /> [<span data-ttu-id="e7bcd-173">Transact-sql&#41;sp_add_notification &#40;</span><span class="sxs-lookup"><span data-stu-id="e7bcd-173">sp_add_notification &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)<br /><br /> [<span data-ttu-id="e7bcd-174">운영자에게 경고 할당</span><span class="sxs-lookup"><span data-stu-id="e7bcd-174">Assign Alerts to an Operator</span></span>](assign-alerts-to-an-operator.md)|  
  
## <a name="see-also"></a><span data-ttu-id="e7bcd-175">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e7bcd-175">See Also</span></span>  
 [<span data-ttu-id="e7bcd-176">데이터베이스 메일</span><span class="sxs-lookup"><span data-stu-id="e7bcd-176">Database Mail</span></span>](../../relational-databases/database-mail/database-mail.md)  
  
  
