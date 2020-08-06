---
title: 정책 관리자에 정책 실패를 알리도록 경고 구성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, configure alerts
ms.assetid: e8e60159-d5b0-49d5-91f3-af8e9cb994c1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9eb84ced3bb6313dd5920deaf479925556f08fc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728216"
---
# <a name="configure-alerts-to-notify-policy-administrators-of-policy-failures"></a><span data-ttu-id="c927a-102">정책 관리자에서 정책 실패를 알리도록 경고 구성</span><span class="sxs-lookup"><span data-stu-id="c927a-102">Configure Alerts to Notify Policy Administrators of Policy Failures</span></span>
  <span data-ttu-id="c927a-103">정책 기반 관리 정책이 세 가지 자동 평가 모드 중 하나로 실행된 경우 정책 위반이 발생하면 이벤트 로그에 메시지가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="c927a-103">When Policy-Based Management policies are executed in one of the three automated evaluation modes, if a policy violation occurs, a message is written to the event log.</span></span> <span data-ttu-id="c927a-104">이 메시지가 이벤트 로그에 기록되는 경우 알림을 받으려면 메시지를 검색하고 동작을 수행하도록 경고를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c927a-104">To be notified when this message is written to the event log, you can create an alert to detect the message and perform an action.</span></span> <span data-ttu-id="c927a-105">경고는 다음 표에서와 같이 메시지를 검색해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c927a-105">The alert should detect the messages as shown in the following table.</span></span>  
  
|<span data-ttu-id="c927a-106">실행 모드</span><span class="sxs-lookup"><span data-stu-id="c927a-106">Execution mode</span></span>|<span data-ttu-id="c927a-107">메시지 번호</span><span class="sxs-lookup"><span data-stu-id="c927a-107">Message number</span></span>|  
|--------------------|--------------------|  
|<span data-ttu-id="c927a-108">변경 시: 방지</span><span class="sxs-lookup"><span data-stu-id="c927a-108">On change: prevent</span></span><br /><br /> <span data-ttu-id="c927a-109">(자동인 경우)</span><span class="sxs-lookup"><span data-stu-id="c927a-109">(if automatic)</span></span>|<span data-ttu-id="c927a-110">34050</span><span class="sxs-lookup"><span data-stu-id="c927a-110">34050</span></span>|  
|<span data-ttu-id="c927a-111">변경 시: 방지</span><span class="sxs-lookup"><span data-stu-id="c927a-111">On change: prevent</span></span><br /><br /> <span data-ttu-id="c927a-112">(요청 시)</span><span class="sxs-lookup"><span data-stu-id="c927a-112">(if On demand)</span></span>|<span data-ttu-id="c927a-113">34051</span><span class="sxs-lookup"><span data-stu-id="c927a-113">34051</span></span>|  
|<span data-ttu-id="c927a-114">예약 시</span><span class="sxs-lookup"><span data-stu-id="c927a-114">On schedule</span></span>|<span data-ttu-id="c927a-115">34052</span><span class="sxs-lookup"><span data-stu-id="c927a-115">34052</span></span>|  
|<span data-ttu-id="c927a-116">변경 시</span><span class="sxs-lookup"><span data-stu-id="c927a-116">On change</span></span>|<span data-ttu-id="c927a-117">34053</span><span class="sxs-lookup"><span data-stu-id="c927a-117">34053</span></span>|  
  
 <span data-ttu-id="c927a-118">정책 기반 관리 오류 메시지에 응답하도록 경고를 설정하려면 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c927a-118">To set up an alert to respond to the Policy-Based Management error messages, see the following topics:</span></span>  
  
-   [<span data-ttu-id="c927a-119">운영자 만들기</span><span class="sxs-lookup"><span data-stu-id="c927a-119">Create an Operator</span></span>](../../ssms/agent/create-an-operator.md)  
  
-   [<span data-ttu-id="c927a-120">오류 번호를 사용하여 경고 만들기</span><span class="sxs-lookup"><span data-stu-id="c927a-120">Create an Alert Using an Error Number</span></span>](../../ssms/agent/create-an-alert-using-an-error-number.md)  
  
-   [<span data-ttu-id="c927a-121">운영자에게 경고 할당</span><span class="sxs-lookup"><span data-stu-id="c927a-121">Assign Alerts to an Operator</span></span>](../../ssms/agent/assign-alerts-to-an-operator.md)  
  
## <a name="permissions"></a><span data-ttu-id="c927a-122">사용 권한</span><span class="sxs-lookup"><span data-stu-id="c927a-122">Permissions</span></span>  
 <span data-ttu-id="c927a-123">정책이 요청 시 평가되면 사용자의 보안 컨텍스트에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c927a-123">When policies are evaluated on demand, they execute in the security context of the user.</span></span> <span data-ttu-id="c927a-124">오류 로그에 작성하려면 사용자가 ALTER TRACE 권한을 가지고 있거나 sysadmin 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c927a-124">To write to the error log, the user must have ALTER TRACE permissions or be a member of the sysadmin fixed server role.</span></span> <span data-ttu-id="c927a-125">적은 권한의 사용자가 평가하는 정책은 이벤트 로그에 작성되지 않고 경고를 발생시키지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c927a-125">Policies that are evaluated by a user that has less privileges will not write to the event log, and will not fire an alert.</span></span>  
  
 <span data-ttu-id="c927a-126">자동화된 실행 모드는 sysadmin 역할의 멤버로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c927a-126">The automated execution modes execute as a member of the sysadmin role.</span></span> <span data-ttu-id="c927a-127">그러면 정책에서 오류 로그 기록 및 경고 발생을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c927a-127">This allows the policy to write to the error log and raise an alert.</span></span>  
  
## <a name="additional-considerations-about-alerts"></a><span data-ttu-id="c927a-128">경고에 대한 추가 고려 사항</span><span class="sxs-lookup"><span data-stu-id="c927a-128">Additional Considerations About Alerts</span></span>  
 <span data-ttu-id="c927a-129">경고에 대한 다음 추가 고려 사항에 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="c927a-129">Be aware of the following additional considerations about alerts:</span></span>  
  
-   <span data-ttu-id="c927a-130">경고는 설정된 정책에 대해서만 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="c927a-130">Alerts are raised only for policies that are enabled.</span></span> <span data-ttu-id="c927a-131">**요청 시** 정책을 설정할 수 없으므로 요청 시 실행되는 정책에 대해서는 경고가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c927a-131">Because **On demand** policies cannot be enabled, alerts are not raised for policies that are executed on demand.</span></span>  
  
-   <span data-ttu-id="c927a-132">전자 메일 메시지 보내기와 같은 동작을 수행하려는 경우 메일 계정을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c927a-132">If the action you want to take includes sending an e-mail message, you must configure a mail account.</span></span> <span data-ttu-id="c927a-133">데이터베이스 메일을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c927a-133">We recommend that you use Database Mail.</span></span> <span data-ttu-id="c927a-134">데이터베이스 메일을 설정하는 방법에 대한 자세한 내용은 [데이터베이스 메일 계정 만들기](../database-mail/create-a-database-mail-account.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c927a-134">For more information about how to set up Database Mail, see [Create a Database Mail Account](../database-mail/create-a-database-mail-account.md).</span></span>  
  
  
