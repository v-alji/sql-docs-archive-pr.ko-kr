---
title: 데이터베이스 메일 로그 및 감사 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- Database Mail [SQL Server], auditing
- logs [Database Mail]
- audits [SQL Server], Database Mail
- Database Mail [SQL Server], logging
ms.assetid: 846589ee-5fe5-4ab3-b335-0c253e569f99
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6267389f187b955982ec1c18c411f703b4562f3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742252"
---
# <a name="database-mail-log-and-audits"></a><span data-ttu-id="3cf8d-102">데이터베이스 메일 로그 및 감사</span><span class="sxs-lookup"><span data-stu-id="3cf8d-102">Database Mail Log and Audits</span></span>
  <span data-ttu-id="3cf8d-103">데이터베이스 메일 로깅 기능은 문제를 격리하여 수정하는 방법을 제공하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8d-103">The Database Mail logging functionality is designed to provide a way to isolate and correct problems.</span></span> <span data-ttu-id="3cf8d-104">데이터베이스 메일은 **msdb** 데이터베이스에 로그 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8d-104">Database Mail stores the log information in the **msdb** database.</span></span> <span data-ttu-id="3cf8d-105">데이터베이스 메일 전자 메일 콘텐츠, 전자 메일의 상태, 받은 메시지(예: 오류)에 대한 정보는 데이터베이스 메일에서 로깅되며 문제 해결 및 감사 용도에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8d-105">Information about Database Mail e-mail content, status of e-mails, and any messages received, such as errors  are logged by Database Mail and can be used for troubleshooting and auditing purposes.</span></span>  
  
## <a name="database-mail-logs"></a><span data-ttu-id="3cf8d-106">데이터베이스 메일 로그</span><span class="sxs-lookup"><span data-stu-id="3cf8d-106">Database Mail Logs</span></span>  
 <span data-ttu-id="3cf8d-107">**msdb** 데이터베이스의 테이블은 [Database Mail External Program](database-mail-external-program.md)의 정보를 기록하고</span><span class="sxs-lookup"><span data-stu-id="3cf8d-107">Tables in the **msdb** database log information from the [Database Mail External Program](database-mail-external-program.md).</span></span> <span data-ttu-id="3cf8d-108">[데이터베이스 메일 뷰&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/database-mail-views-transact-sql)는 문제 해결을 위해 이러한 테이블을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8d-108">[Database Mail Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/database-mail-views-transact-sql) expose the tables for troubleshooting purposes.</span></span> <span data-ttu-id="3cf8d-109">Service Broker에서 외부 프로그램을 활성화할 수 없거나 외부 프로그램에 네트워크 오류가 발생하거나 SMTP(Simple Mail Transport Protocol) 서버에서 메일 메시지를 거부하는 경우 [sysmail_event_log&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-event-log-transact-sql) 뷰에 오류가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8d-109">Errors appear in the [sysmail_event_log &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-event-log-transact-sql) view if Service Broker cannot activate the external program, if the external program encounters networking errors or if the Simple Mail Transport Protocol (SMTP) server refuses an e-mail message.</span></span> <span data-ttu-id="3cf8d-110">외부 프로그램에서 **msdb** 테이블에 기록할 수 없는 경우 해당 프로그램은 Windows 애플리케이션 이벤트 로그에 오류를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8d-110">In the event that the external program cannot log to the **msdb** tables, the program logs errors to the Windows application event log.</span></span>  
  
 <span data-ttu-id="3cf8d-111">**msdb** 데이터베이스의 내부 테이블에는 데이터베이스 메일에서 전송된 메일 메시지와 첨부 파일이 각 메시지의 현재 상태와 함께 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8d-111">Internal tables in the **msdb** database contain the e-mail messages and attachments sent from Database Mail, together with the current status of each message.</span></span> <span data-ttu-id="3cf8d-112">데이터베이스 메일은 각 메시지가 처리될 때마다 이러한 테이블을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8d-112">Database Mail updates these tables as each message is processed.</span></span>  
  
## <a name="database-mail-auditing-tasks"></a><span data-ttu-id="3cf8d-113">데이터베이스 메일 감사 태스크</span><span class="sxs-lookup"><span data-stu-id="3cf8d-113">Database Mail Auditing tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3cf8d-114">**데이터베이스 메일 로그 검토 및 관리**</span><span class="sxs-lookup"><span data-stu-id="3cf8d-114">**Reviewing and managing Database Mail logs**</span></span>|<span data-ttu-id="3cf8d-115">**항목에 대 한 링크**</span><span class="sxs-lookup"><span data-stu-id="3cf8d-115">**Link to Topic**</span></span>|  
|<span data-ttu-id="3cf8d-116">개별 메시지의 배달 상태 확인</span><span class="sxs-lookup"><span data-stu-id="3cf8d-116">Check the delivery status of an individual message</span></span>|[<span data-ttu-id="3cf8d-117">데이터베이스 메일을 통해 보낸 메일 메시지의 상태 확인</span><span class="sxs-lookup"><span data-stu-id="3cf8d-117">Check the Status of E-Mail Messages Sent With Database Mail</span></span>](check-the-status-of-e-mail-messages-sent-with-database-mail.md)|  
|<span data-ttu-id="3cf8d-118">데이터베이스 메일 메시지, 첨부 파일 및 로그 항목 정리</span><span class="sxs-lookup"><span data-stu-id="3cf8d-118">Clean up Database Mail messages, attachments, and log entries</span></span>|[<span data-ttu-id="3cf8d-119">sysmail_delete_mailitems_sp&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3cf8d-119">sysmail_delete_mailitems_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-mailitems-sp-transact-sql)<br /><br /> [<span data-ttu-id="3cf8d-120">sysmail_delete_log_sp&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3cf8d-120">sysmail_delete_log_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-log-sp-transact-sql)|  
|<span data-ttu-id="3cf8d-121">데이터베이스 전자 메일 메시지 및 로그 보관</span><span class="sxs-lookup"><span data-stu-id="3cf8d-121">Archive the Database Email Messages and Logs</span></span>|[<span data-ttu-id="3cf8d-122">데이터베이스 메일 메시지 및 이벤트 로그 보관을 처리하는 SQL Server 에이전트 작업 만들기</span><span class="sxs-lookup"><span data-stu-id="3cf8d-122">Create a SQL Server Agent Job to Archive Database Mail Messages and Event Logs</span></span>](create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md)|  
  
## <a name="see-also"></a><span data-ttu-id="3cf8d-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3cf8d-123">See Also</span></span>  
 [<span data-ttu-id="3cf8d-124">리소스 사용 모니터링&#40;시스템 모니터&#41;</span><span class="sxs-lookup"><span data-stu-id="3cf8d-124">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](../performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
