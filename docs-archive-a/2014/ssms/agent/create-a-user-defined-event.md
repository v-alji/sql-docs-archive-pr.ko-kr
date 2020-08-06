---
title: 사용자 정의 이벤트 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent alerts, user-defined events
- user-defined events [SQL Server]
- multiple language support [SQL Server], alerts
- languages [SQL Server], alerts
- severity levels [SQL Server]
- global considerations [SQL Server], alerts
- events [SQL Server], user-defined
- SQL Server Agent alerts, multiple-language environments
- alerts [SQL Server], user-defined events
- alerts [SQL Server], multiple-language environments
- custom events [SQL Server Agent]
- international considerations [SQL Server], alerts
ms.assetid: 03d71a35-97fa-4bba-aa9a-23ac9c9cf879
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2323dc4da3d1a8a67dad41ea189877ade25eff0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742744"
---
# <a name="create-a-user-defined-event"></a><span data-ttu-id="457fb-102">사용자 정의 이벤트 만들기</span><span class="sxs-lookup"><span data-stu-id="457fb-102">Create a User-Defined Event</span></span>
  <span data-ttu-id="457fb-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 미리 정의된 이벤트 이외의 이벤트를 모니터링하려는 경우 사용자 정의 이벤트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="457fb-103">You can create user-defined events if you want to monitor events other than events that are predefined by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="457fb-104">각 사용자 정의 이벤트에 심각도 수준을 할당할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="457fb-104">You can also assign a severity level to each user-defined event.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="457fb-105">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용할 때 각 사용자 정의 이벤트 메시지에 대해 **Windows 애플리케이션 이벤트 로그에 쓰기** 옵션을 선택하여 메시지를 로그에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="457fb-105">When using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the **Write to Windows application event log** option for each user-defined event message, to ensure that the messages are logged.</span></span> <span data-ttu-id="457fb-106">기본적으로 심각도가 19보다 낮은 사용자 정의 메시지가 발생하면 이 메시지는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 애플리케이션 로그로 전송되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="457fb-106">By default, user-defined messages of severity lower than 19 are not sent to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application log when they occur.</span></span> <span data-ttu-id="457fb-107">심각도 수준이 19보다 낮은 사용자 정의 메시지는 SQL Server 에이전트 경고를 트리거하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="457fb-107">User-defined messages of severity lower than 19 therefore do not trigger SQL Server Agent alerts.</span></span>  
  
 <span data-ttu-id="457fb-108">사용자 정의 이벤트에는 고유한 메시지 번호가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="457fb-108">User-defined events must have a unique message number.</span></span> <span data-ttu-id="457fb-109">사용자 정의 이벤트의 메시지 번호는 50,000보다 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="457fb-109">Message numbers for a user-defined event must be greater than 50,000.</span></span> <span data-ttu-id="457fb-110">이벤트에 대한 메시지는 여러 언어로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="457fb-110">You can define messages for the event in multiple languages.</span></span> <span data-ttu-id="457fb-111">그러나 다른 언어로 된 메시지를 추가하려면 먼저 **En-US** 오류 메시지가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="457fb-111">However, an **En-US** error message must exist before messages in other languages can be added.</span></span>  
  
 <span data-ttu-id="457fb-112">여러 언어로 된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 환경을 관리하는 경우 지원되는 각 언어로 사용자 정의 메시지를 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="457fb-112">If you administer a multiple-language [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] environment, create user-defined messages in each of the languages that are supported.</span></span> <span data-ttu-id="457fb-113">예를 들어 영어 서버와 독일어 서버에서 사용할 이벤트 메시지를 새로 만들 경우에 두 서버에 같은 메시지 번호와 심각도를 사용하지만 각각 다른 언어를 할당하십시오.</span><span class="sxs-lookup"><span data-stu-id="457fb-113">For example, if you are creating a new event message to be used on both an English and a German server, use the same message number and severity for both, but assign a different language to each.</span></span>  
  
 <span data-ttu-id="457fb-114">다음 태스크는 작업에 응답하는 사용자 정의 이벤트와 경고를 만드는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="457fb-114">The following tasks provide information about how to create user-defined events and alerts that respond to them:</span></span>  
  
 <span data-ttu-id="457fb-115">**메시지 번호를 기반으로 경고를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="457fb-115">**To create an alert based on a message number**</span></span>  
  
-   [<span data-ttu-id="457fb-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="457fb-116">SQL Server Management Studio</span></span>](create-an-alert-using-an-error-number.md)  
  
-   [<span data-ttu-id="457fb-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="457fb-117">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 <span data-ttu-id="457fb-118">**심각도 수준을 기반으로 경고를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="457fb-118">**To create an alert based on severity levels**</span></span>  
  
-   [<span data-ttu-id="457fb-119">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="457fb-119">SQL Server Management Studio</span></span>](create-an-alert-using-severity-level.md)  
  
-   [<span data-ttu-id="457fb-120">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="457fb-120">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 <span data-ttu-id="457fb-121">**경고에 대한 응답을 정의하려면**</span><span class="sxs-lookup"><span data-stu-id="457fb-121">**To define the response to an alert**</span></span>  
  
-   [<span data-ttu-id="457fb-122">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="457fb-122">SQL Server Management Studio</span></span>](../sql-server-management-studio-ssms.md)  
  
-   [<span data-ttu-id="457fb-123">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="457fb-123">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)  
  
 <span data-ttu-id="457fb-124">**사용자 정의 이벤트 오류 메시지를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="457fb-124">**To create a user-defined event error message**</span></span>  
  
-   [<span data-ttu-id="457fb-125">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="457fb-125">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-addmessage-transact-sql)  
  
 <span data-ttu-id="457fb-126">**사용자 정의 이벤트 오류 메시지를 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="457fb-126">**To modify a user-defined event error message**</span></span>  
  
-   [<span data-ttu-id="457fb-127">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="457fb-127">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-altermessage-transact-sql)  
  
 <span data-ttu-id="457fb-128">**사용자 정의 이벤트 오류 메시지를 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="457fb-128">**To delete a user-defined event error message**</span></span>  
  
-   [<span data-ttu-id="457fb-129">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="457fb-129">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropmessage-transact-sql)  
  
 <span data-ttu-id="457fb-130">**경고를 비활성화하거나 다시 활성화하려면**</span><span class="sxs-lookup"><span data-stu-id="457fb-130">**To disable or reactivate an alert**</span></span>  
  
-   [<span data-ttu-id="457fb-131">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="457fb-131">SQL Server Management Studio</span></span>](disable-or-reactivate-an-alert.md)  
  
-   [<span data-ttu-id="457fb-132">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="457fb-132">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="457fb-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="457fb-133">See Also</span></span>  
 [<span data-ttu-id="457fb-134">Transact-sql&#41;sp_update_alert &#40;</span><span class="sxs-lookup"><span data-stu-id="457fb-134">sp_update_alert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)  
  
  
