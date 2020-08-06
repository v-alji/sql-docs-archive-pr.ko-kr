---
title: 데이터베이스 메일 메시지 및 이벤트 로그 보관을 처리하는 SQL Server 에이전트 작업 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- archiving mail messages and attachments [SQL Server]
- removing mail messages and attachements
- Database Mail [SQL Server], archiving
- saving mail messages and attachments
ms.assetid: 8f8f0fba-f750-4533-9b76-a9cdbcdc3b14
author: stevestein
ms.author: sstein
ms.openlocfilehash: b958b280c358a8aeb752600dee1c2aee31d14db1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649096"
---
# <a name="create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs"></a><span data-ttu-id="15d58-102">데이터베이스 메일 메시지 및 이벤트 로그 보관을 처리하는 SQL Server 에이전트 작업 만들기</span><span class="sxs-lookup"><span data-stu-id="15d58-102">Create a SQL Server Agent Job to Archive Database Mail Messages and Event Logs</span></span>
  <span data-ttu-id="15d58-103">데이터베이스 메일 및 첨부 파일의 복사본은 데이터베이스 메일 이벤트 로그와 함께 **msdb** 테이블에 보관됩니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-103">Copies of Database Mail messages and their attachments are retained in **msdb** tables along with the Database Mail event log.</span></span> <span data-ttu-id="15d58-104">정기적으로 테이블의 크기를 축소하고 더 이상 필요하지 않은 메시지와 이벤트를 보관할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-104">Periodically you might want to reduce the size of the tables and archive messages and events that are no longer needed.</span></span> <span data-ttu-id="15d58-105">다음 절차에서는 SQL Server 에이전트 작업을 만들어 이 프로세스를 자동화합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-105">The following procedures create a SQL Server Agent job to automate the process.</span></span>  
  
-   <span data-ttu-id="15d58-106">**시작하기 전에:**  , [필수 구성 요소](#Prerequisites), [권장 사항](#Recommendations), [권한](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="15d58-106">**Before you begin:**  , [Prerequisites](#Prerequisites), [Recommendations](#Recommendations), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="15d58-107">**데이터베이스 메일 메시지 및 로그를 보관하려면 다음을 사용합니다.**  [SQL Server 에이전트](#Process_Overview)</span><span class="sxs-lookup"><span data-stu-id="15d58-107">**To Archive Database Mail messages and logs using :**  [SQL Server Agent](#Process_Overview)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="15d58-108">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="15d58-108">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="15d58-109">필수 조건</span><span class="sxs-lookup"><span data-stu-id="15d58-109">Prerequisites</span></span>  
 <span data-ttu-id="15d58-110">데이터를 저장하고 보관할 새 테이블은 특수한 보관 데이터베이스에 위치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-110">The new tables to store the archive data might be located in a special archive database.</span></span> <span data-ttu-id="15d58-111">행을 텍스트 파일로 내보낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-111">Alternatively the rows could be exported to a text file.</span></span>  
 
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="15d58-112">권장 사항</span><span class="sxs-lookup"><span data-stu-id="15d58-112">Recommendations</span></span>  
 <span data-ttu-id="15d58-113">프로덕션 환경에서 오류 검사를 추가하고 작업이 실패할 경우 운영자에게 전자 메일 메시지를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-113">In your production environment, you might want to add additional error checking and send an e-mail message to operators if the job fails.</span></span>  
  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="15d58-114">권한</span><span class="sxs-lookup"><span data-stu-id="15d58-114">Permissions</span></span>  
 <span data-ttu-id="15d58-115">이 항목에서 설명하는 저장 프로시저를 실행하려면 **sysadmin** 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-115">You must be a member of the **sysadmin** fixed server role to execute the stored procedures described in this topic.</span></span>  
  
  
###  <a name="overview-of-the-process"></a><a name="Process_Overview"></a> <span data-ttu-id="15d58-116">프로세스 개요</span><span class="sxs-lookup"><span data-stu-id="15d58-116">Overview of the Process</span></span>  
  
-   <span data-ttu-id="15d58-117">첫 번째 절차에서는 다음 단계를 사용하여 Archive Database Mail이라는 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-117">The first procedure creates a job named Archive Database Mail with the following steps.</span></span>  
  
    1.  <span data-ttu-id="15d58-118">모든 메시지를 데이터베이스 메일 테이블에서 **DBMailArchive_** _<year_month>_ 형식으로 이전 달 이름에 따라 명명된 새 테이블로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-118">Copy all messages from the Database Mail tables to a new table named after the previous month in the format **DBMailArchive_**_<year_month>_.</span></span>  
  
    2.  <span data-ttu-id="15d58-119">첫 번째 단계에서 복사된 메시지와 관련된 첨부 파일을 데이터베이스 메일 테이블에서 **DBMailArchive_Attachments_** _<year_month>_ 형식으로 이전 달 이름에 따라 명명된 새 테이블로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-119">Copy the attachments related to the messages copied in the first step, from the Database Mail tables to a new table named after the previous month in the format **DBMailArchive_Attachments_**_<year_month>_.</span></span>  
  
    3.  <span data-ttu-id="15d58-120">첫 번째 단계에서 복사한 메시지와 관련된 데이터베이스 메일 이벤트 로그에서 **DBMailArchive_Log_** _<year_month>_ 형식으로 이전 달 이름을 따라 명명된 새 테이블로 이벤트를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-120">Copy the events from the Database Mail event log that are related to the messages copied in the first step, from the Database Mail tables to a new table named after the previous month in the format **DBMailArchive_Log_**_<year_month>_.</span></span>  
  
    4.  <span data-ttu-id="15d58-121">전송된 메일 항목의 레코드를 데이터베이스 메일 테이블에서 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-121">Delete the records of the transferred mail items from the Database Mail tables.</span></span>  
  
    5.  <span data-ttu-id="15d58-122">전송된 메일 항목과 관련된 이벤트를 데이터베이스 메일 이벤트 로그에서 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-122">Delete the events related to the transferred mail items from the Database Mail event log.</span></span>  
  
-   <span data-ttu-id="15d58-123">정기적으로 실행되도록 작업을 예약합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-123">Schedule the job to run periodically.</span></span>  
 
  
## <a name="to-create-a-sql-server-agent-job"></a><span data-ttu-id="15d58-124">SQL Server 에이전트 작업을 만들려면</span><span class="sxs-lookup"><span data-stu-id="15d58-124">To create a SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="15d58-125">개체 탐색기에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 확장하고 **작업**을 마우스 오른쪽 단추로 클릭한 다음 **새 작업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-125">In Object Explorer, expand [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, right-click **Jobs**, and then click **New Job**.</span></span>  
  
2.  <span data-ttu-id="15d58-126">**새 작업** 대화 상자의 **이름** 입력란에 **Archive Database Mail**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-126">In the **New Job** dialog box, in the **Name** box, type **Archive Database Mail**.</span></span>  
  
3.  <span data-ttu-id="15d58-127">**소유자** 드롭다운 목록의 해당 소유자가 **sysadmin** 고정 서버 역할의 멤버인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-127">In the **Owner** box, confirm that the owner is a member of the **sysadmin** fixed server role.</span></span>  
  
4.  <span data-ttu-id="15d58-128">**범주** 드롭다운 목록에서 **데이터베이스 유지 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-128">In the **Category** box, click the **Database Maintenance**.</span></span>  
  
5.  <span data-ttu-id="15d58-129">**설명** 입력란에 **Archive Database Mail messages**를 입력하고 **단계**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-129">In the **Description** box, type **Archive Database Mail messages**, and then click **Steps**.</span></span>  
  
  
  
## <a name="to-create-a-step-to-archive-the-database-mail-messages"></a><span data-ttu-id="15d58-130">데이터베이스 메일 메시지 보관 단계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="15d58-130">To create a step to archive the Database Mail messages</span></span>  
  
1.  <span data-ttu-id="15d58-131">**단계** 페이지에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-131">On the **Steps** page, click **New**.</span></span>  
  
2.  <span data-ttu-id="15d58-132">**단계 이름** 입력란에 **Copy Database Mail Items**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-132">In the **Step name** box, type **Copy Database Mail Items**.</span></span>  
  
3.  <span data-ttu-id="15d58-133">**유형** 드롭다운 목록에서 **Transact-SQL 스크립트(T-SQL)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-133">In the **Type** box, select **Transact-SQL script (T-SQL)**.</span></span>  
  
4.  <span data-ttu-id="15d58-134">**데이터베이스** 드롭다운 목록에서 **msdb**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-134">In the **Database** box, select **msdb**.</span></span>  
  
5.  <span data-ttu-id="15d58-135">**명령** 입력란에 다음 문을 입력하여 이전 달의 이름을 딴 테이블을 만들고 현재 달의 시작일보다 이전인 행을 포함하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-135">In the **Command** box, type the following statement to create a table named after the previous month, containing rows older than the start of the current month:</span></span>  
  
    ```  
    DECLARE @LastMonth nvarchar(12);  
    DECLARE @CopyDate nvarchar(20) ;  
    DECLARE @CreateTable nvarchar(250) ;  
    SET @LastMonth = (SELECT CAST(DATEPART(yyyy,GETDATE()) AS CHAR(4)) + '_' + CAST(DATEPART(mm,GETDATE())-1 AS varchar(2))) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime))  
    SET @CreateTable = 'SELECT * INTO msdb.dbo.[DBMailArchive_' + @LastMonth + '] FROM sysmail_allitems WHERE send_request_date < ''' + @CopyDate +'''';  
    EXEC sp_executesql @CreateTable ;  
    ```  
  
6.  <span data-ttu-id="15d58-136">**확인** 을 클릭하여 단계를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-136">Click **OK** to save the step.</span></span>  
  
  
  
## <a name="to-create-a-step-to-archive-the-database-mail-attachments"></a><span data-ttu-id="15d58-137">데이터베이스 메일 첨부 파일 보관 단계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="15d58-137">To create a step to archive the Database Mail attachments</span></span>  
  
1.  <span data-ttu-id="15d58-138">**단계** 페이지에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-138">On the **Steps** page, click **New**.</span></span>  
  
2.  <span data-ttu-id="15d58-139">**단계 이름** 입력란에 **Copy Database Mail Attachments**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-139">In the **Step name** box, type **Copy Database Mail Attachments**.</span></span>  
  
3.  <span data-ttu-id="15d58-140">**유형** 드롭다운 목록에서 **Transact-SQL 스크립트(T-SQL)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-140">In the **Type** box, select **Transact-SQL script (T-SQL)**.</span></span>  
  
4.  <span data-ttu-id="15d58-141">**데이터베이스** 드롭다운 목록에서 **msdb**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-141">In the **Database** box, select **msdb**.</span></span>  
  
5.  <span data-ttu-id="15d58-142">**명령** 입력란에 다음 문을 입력하여 이전 달의 이름을 딴 테이블을 만들고 이전 단계에서 복사한 메시지에 해당하는 첨부 파일이 포함되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-142">In the **Command** box, type the following statement to create an attachments table named after the previous month, containing the attachments that correspond to the messages transferred in the previous step:</span></span>  
  
    ```  
    DECLARE @LastMonth nvarchar(12);  
    DECLARE @CopyDate nvarchar(20) ;  
    DECLARE @CreateTable nvarchar(250) ;  
    SET @LastMonth = (SELECT CAST(DATEPART(yyyy,GETDATE()) AS CHAR(4)) + '_' + CAST(DATEPART(mm,GETDATE())-1 AS varchar(2))) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime))  
    SET @CreateTable = 'SELECT * INTO msdb.dbo.[DBMailArchive_Attachments_' + @LastMonth + '] FROM sysmail_attachments   
     WHERE mailitem_id in (SELECT DISTINCT mailitem_id FROM [DBMailArchive_' + @LastMonth + '] )';  
    EXEC sp_executesql @CreateTable ;  
    ```  
  
6.  <span data-ttu-id="15d58-143">**확인** 을 클릭하여 단계를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-143">Click **OK** to save the step.</span></span>  
  
  
  
## <a name="to-create-a-step-to-archive-the-database-mail-log"></a><span data-ttu-id="15d58-144">데이터베이스 메일 로그 보관 단계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="15d58-144">To create a step to archive the Database Mail log</span></span>  
  
1.  <span data-ttu-id="15d58-145">**단계** 페이지에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-145">On the **Steps** page, click **New**.</span></span>  
  
2.  <span data-ttu-id="15d58-146">**단계 이름** 입력란에 **Copy Database Mail Log**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-146">In the **Step name** box, type **Copy Database Mail Log**.</span></span>  
  
3.  <span data-ttu-id="15d58-147">**유형** 드롭다운 목록에서 **Transact-SQL 스크립트(T-SQL)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-147">In the **Type** box, select **Transact-SQL script (T-SQL)**.</span></span>  
  
4.  <span data-ttu-id="15d58-148">**데이터베이스** 드롭다운 목록에서 **msdb**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-148">In the **Database** box, select **msdb**.</span></span>  
  
5.  <span data-ttu-id="15d58-149">**명령** 입력란에 다음 문을 입력하여 이전 달의 이름을 딴 테이블을 만들고 이전 단계에서 복사한 메시지에 해당하는 로그 항목이 포함되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-149">In the **Command** box, type the following statement to create a log table named after the previous month, containing the log entries that correspond to the messages transferred in the earlier step:</span></span>  
  
    ```  
    DECLARE @LastMonth nvarchar(12);  
    DECLARE @CopyDate nvarchar(20) ;  
    DECLARE @CreateTable nvarchar(250) ;  
    SET @LastMonth = (SELECT CAST(DATEPART(yyyy,GETDATE()) AS CHAR(4)) + '_' + CAST(DATEPART(mm,GETDATE())-1 AS varchar(2))) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime))  
    SET @CreateTable = 'SELECT * INTO msdb.dbo.[DBMailArchive_Log_' + @LastMonth + '] FROM sysmail_Event_Log   
     WHERE mailitem_id in (SELECT DISTINCT mailitem_id FROM [DBMailArchive_' + @LastMonth + '] )';  
    EXEC sp_executesql @CreateTable ;  
    ```  
  
6.  <span data-ttu-id="15d58-150">**확인** 을 클릭하여 단계를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-150">Click **OK** to save the step.</span></span>  
  
  
  
## <a name="to-create-a-step-to-remove-the-archived-rows-from-database-mail"></a><span data-ttu-id="15d58-151">데이터베이스 메일에서 보관된 행을 제거하는 단계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="15d58-151">To create a step to remove the archived rows from Database Mail</span></span>  
  
1.  <span data-ttu-id="15d58-152">**단계** 페이지에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-152">On the **Steps** page, click **New**.</span></span>  
  
2.  <span data-ttu-id="15d58-153">**단계 이름** 입력란에 **Remove rows from Database Mail**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-153">In the **Step name** box, type **Remove rows from Database Mail**.</span></span>  
  
3.  <span data-ttu-id="15d58-154">**유형** 드롭다운 목록에서 **Transact-SQL 스크립트(T-SQL)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-154">In the **Type** box, select **Transact-SQL script (T-SQL)**.</span></span>  
  
4.  <span data-ttu-id="15d58-155">**데이터베이스** 드롭다운 목록에서 **msdb**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-155">In the **Database** box, select **msdb**.</span></span>  
  
5.  <span data-ttu-id="15d58-156">**명령** 입력란에 다음 문을 입력하여 현재 달보다 이전인 행을 데이터베이스 테이블에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-156">In the **Command** box, type the following statement to remove rows older than the current month from the Database Mail tables:</span></span>  
  
    ```  
    DECLARE @CopyDate nvarchar(20) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime)) ;  
    EXECUTE msdb.dbo.sysmail_delete_mailitems_sp @sent_before = @CopyDate ;  
    ```  
  
6.  <span data-ttu-id="15d58-157">**확인** 을 클릭하여 단계를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-157">Click **OK** to save the step.</span></span>  
  
  
  
## <a name="to-create-a-step-to-remove-the-archived-items-from-database-mail-event-log"></a><span data-ttu-id="15d58-158">데이터베이스 메일 이벤트 로그에서 보관된 항목을 제거하는 단계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="15d58-158">To create a step to remove the archived items from Database Mail event log</span></span>  
  
1.  <span data-ttu-id="15d58-159">**단계** 페이지에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-159">On the **Steps** page, click **New**.</span></span>  
  
2.  <span data-ttu-id="15d58-160">**단계 이름** 입력란에 **Remove rows from Database Mail event log**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-160">In the **Step Name** box type **Remove rows from Database Mail event log**.</span></span>  
  
3.  <span data-ttu-id="15d58-161">**유형** 드롭다운 목록에서 **Transact-SQL 스크립트(T-SQL)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-161">In the **Type** box, select **Transact-SQL script (T-SQL)**.</span></span>  
  
4.  <span data-ttu-id="15d58-162">**명령** 입력란에 다음 문을 입력하여 현재 달보다 이전인 행을 데이터베이스 메일 이벤트 로그에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-162">In the **Command** box, type the following statement to remove rows older than the current month from the Database Mail event log:</span></span>  
  
    ```  
    DECLARE @CopyDate nvarchar(20) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime)) ;  
    EXECUTE msdb.dbo.sysmail_delete_log_sp @logged_before = @CopyDate ;  
    ```  
  
5.  <span data-ttu-id="15d58-163">**확인** 을 클릭하여 단계를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-163">Click **OK** to save the step.</span></span>  
  
  
  
## <a name="to-schedule-the-job-to-run-periodically"></a><span data-ttu-id="15d58-164">정기적으로 실행되도록 작업을 예약하려면</span><span class="sxs-lookup"><span data-stu-id="15d58-164">To schedule the job to run periodically</span></span>  
  
1.  <span data-ttu-id="15d58-165">**새 작업** 대화 상자에서 **일정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-165">In the **New Job** dialog box, click **Schedules**.</span></span>  
  
2.  <span data-ttu-id="15d58-166">**일정** 페이지에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-166">On the **Schedules** page, click **New**.</span></span>  
  
3.  <span data-ttu-id="15d58-167">**이름** 입력란에 **Archive Database Mail**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-167">In the **Name** box, type **Archive Database Mail**.</span></span>  
  
4.  <span data-ttu-id="15d58-168">**일정 유형** 드롭다운 목록에서 **되풀이**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-168">In the **Schedule type** box, select **Recurring**.</span></span>  
  
5.  <span data-ttu-id="15d58-169">**빈도** 영역에서 정기적으로 작업을 실행할 옵션을 선택합니다(예: 매월 한 번).</span><span class="sxs-lookup"><span data-stu-id="15d58-169">In the **Frequency** area, select the options to run the job periodically, for example once every month.</span></span>  
  
6.  <span data-ttu-id="15d58-170">**일별 빈도** 영역에서 **한 번 수행 - \<time>** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-170">In the **Daily frequency** area, select **Occurs once at \<time>**.</span></span>  
  
7.  <span data-ttu-id="15d58-171">다른 옵션이 원하는 대로 구성되었는지 확인하고 **확인** 을 눌러 일정을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-171">Verify that the other options are configured as you wish, and then click **OK** to save the schedule.</span></span>  
  
8.  <span data-ttu-id="15d58-172">**확인** 을 클릭하여 작업을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="15d58-172">Click **OK** to save the job.</span></span>  
  
  
  
  
