---
title: 데이터베이스 메일을 통해 보낸 메일 메시지의 상태 확인 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- e-mail [SQL Server], status information
- mail [SQL Server], status information
- Database Mail [SQL Server], message status
- status information [Database Mail]
ms.assetid: eb290f24-b52f-46bc-84eb-595afee6a5f3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1642c456cd64484dede64f8127ff2f979f2242e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661138"
---
# <a name="check-the-status-of-e-mail-messages-sent-with-database-mail"></a><span data-ttu-id="22e52-102">데이터베이스 메일을 통해 보낸 전자 메일 메시지의 상태 확인</span><span class="sxs-lookup"><span data-stu-id="22e52-102">Check the Status of E-Mail Messages Sent With Database Mail</span></span>
  <span data-ttu-id="22e52-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 데이터베이스 메일로 보낸 전자 메일 메시지의 상태를 확인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="22e52-103">This topic describes how to check the status of the e-mail message sent using Database Mail  in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="22e52-104">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="22e52-104">**Before you begin:**</span></span>  
  
-   <span data-ttu-id="22e52-105">**다음을 사용하여 데이터베이스 메일을 통해 전송된 메일의 상태 보기:**  [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="22e52-105">**To view the status of the e-mail sent using Database Mail, using:**  [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="22e52-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="22e52-106">Before You Begin</span></span>  
 <span data-ttu-id="22e52-107">데이터베이스 메일은 보내는 전자 메일 메시지의 복사본을 유지하고 **msdb**데이터베이스의 **sysmail_allitems**, **sysmail_sentitems**, **sysmail_unsentitems** , **sysmail_faileditems** 뷰에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="22e52-107">Database Mail keeps copies of outgoing e-mail messages and displays them in the **sysmail_allitems**, **sysmail_sentitems**, **sysmail_unsentitems**, **sysmail_faileditems** views of the **msdb** database.</span></span> <span data-ttu-id="22e52-108">데이터베이스 메일 외부 프로그램은 작업을 기록하고 Windows 애플리케이션 이벤트 로그와 **msdb** 데이터베이스의 **sysmail_event_log** 뷰를 통해 로그를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="22e52-108">The Database Mail external program logs activity and displays the log through the Windows Application Event Log and the **sysmail_event_log** view in the **msdb** database.</span></span> <span data-ttu-id="22e52-109">전자 메일 메시지의 상태를 확인하려면 이 뷰에 대한 쿼리를 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="22e52-109">To check the status of an e-mail message, run a query against this view.</span></span> <span data-ttu-id="22e52-110">전자 메일 메시지에는 **sent**, **unsent**, **retrying**및 **failed**의 4가지 가능한 상태 중 하나가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22e52-110">E-mail messages have one of four possible statuses: **sent**, **unsent**, **retrying**, and **failed**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="22e52-111">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="22e52-111">Using Transact-SQL</span></span>  
 <span data-ttu-id="22e52-112">**데이터베이스 메일을 사용하여 보낸 전자 메일의 상태를 보려면**</span><span class="sxs-lookup"><span data-stu-id="22e52-112">**To view the status of the e-mail sent using Database Mail**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="22e52-113">이 절차에 대한 예는 이 섹션의 뒷부분에 나오는 [예제(Transact-SQL)](#TsqlExample)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="22e52-113">For an example of this procedure, see [Example (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="22e52-114">**sysmail_allitems** 테이블에서 **mailitem_id** 또는 **sent_status**로 메시지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="22e52-114">Select from the **sysmail_allitems** table, specifying the messages of interest by **mailitem_id** or **sent_status**.</span></span>  
  
2.  <span data-ttu-id="22e52-115">전자 메일 메시지에 대해 외부 프로그램에서 반환된 상태를 확인하려면 다음 섹션에 나열된 방법으로 **sysmail_allitems** 를 **mailitem_id** 열의 **sysmail_event_log** 뷰에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="22e52-115">To check the status returned from the external program for the e-mail messages, join **sysmail_allitems** to **sysmail_event_log** view on the **mailitem_id** column, as shown in the following section.</span></span>  
  
     <span data-ttu-id="22e52-116">기본적으로 외부 프로그램은 성공적으로 전송된 메시지에 대한 정보를 기록하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="22e52-116">By default, the external program does not log information about messages that were successfully sent.</span></span> <span data-ttu-id="22e52-117">모든 메시지를 기록하려면 **데이터베이스 메일 구성 마법사** 의 **시스템 매개 변수 구성**페이지를 사용하여 로깅 수준을 자세히로 설정하세요.</span><span class="sxs-lookup"><span data-stu-id="22e52-117">To log all messages, set the logging level to verbose using the **Configure System Parameters** page of the **Database Mail Configuration Wizard.**</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="22e52-118">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="22e52-118">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="22e52-119">다음 예에서는 `danw` 로 전송되었지만 외부 프로그램에서 성공적으로 보내지 못한 모든 전자 메일 메시지에 대한 정보를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="22e52-119">The following example lists information about any e-mail messages sent to `danw` that the external program could not send successfully.</span></span> <span data-ttu-id="22e52-120">이 문은 제목, 외부 프로그램에서 메시지를 보내지 못한 날짜와 시간, 데이터베이스 메일 로그의 오류 메시지를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="22e52-120">The statement lists the subject, the date and time that the external program failed to send the message, and the error message from the Database Mail log.</span></span>  
  
```  
USE msdb ;  
GO  
  
-- Show the subject, the time that the mail item row was last  
-- modified, and the log information.  
-- Join sysmail_faileditems to sysmail_event_log   
-- on the mailitem_id column.  
-- In the WHERE clause list items where danw was in the recipients,  
-- copy_recipients, or blind_copy_recipients.  
-- These are the items that would have been sent  
-- to danw.  
  
SELECT items.subject,  
    items.last_mod_date  
    ,l.description FROM dbo.sysmail_faileditems as items  
INNER JOIN dbo.sysmail_event_log AS l  
    ON items.mailitem_id = l.mailitem_id  
WHERE items.recipients LIKE '%danw%'    
    OR items.copy_recipients LIKE '%danw%'   
    OR items.blind_copy_recipients LIKE '%danw%'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="22e52-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="22e52-121">See Also</span></span>  
 [<span data-ttu-id="22e52-122">데이터베이스 메일 로그 및 감사</span><span class="sxs-lookup"><span data-stu-id="22e52-122">Database Mail Log and Audits</span></span>](database-mail-log-and-audits.md)  
  
  
