---
title: 데이터베이스 엔진 오류 이해 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- errors [SQL Server], about errors
- errors [SQL Server], Database Engine
- errors [SQL Server]
- Database Engine [SQL Server], errors
ms.assetid: ddaca9d3-956f-46a5-8cd3-a7a15ec75878
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: aa8747066433488a8517d2931ad51f082075a66f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651688"
---
# <a name="understanding-database-engine-errors"></a><span data-ttu-id="07903-102">데이터베이스 엔진 오류 이해</span><span class="sxs-lookup"><span data-stu-id="07903-102">Understanding Database Engine Errors</span></span>
  <span data-ttu-id="07903-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]에서 발생한 오류에는 다음 테이블에 설명된 것과 같은 특성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07903-103">Errors raised by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] have the attributes described in the following table.</span></span>  
  
|<span data-ttu-id="07903-104">attribute</span><span class="sxs-lookup"><span data-stu-id="07903-104">Attribute</span></span>|<span data-ttu-id="07903-105">Description</span><span class="sxs-lookup"><span data-stu-id="07903-105">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="07903-106">오류 번호</span><span class="sxs-lookup"><span data-stu-id="07903-106">Error number</span></span>|<span data-ttu-id="07903-107">모든 오류 메시지에는 고유한 오류 번호가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07903-107">Each error message has a unique error number.</span></span>|  
|<span data-ttu-id="07903-108">오류 메시지 문자열</span><span class="sxs-lookup"><span data-stu-id="07903-108">Error message string</span></span>|<span data-ttu-id="07903-109">오류 메시지에는 오류 발생 원인에 대한 진단 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="07903-109">The error message contains diagnostic information about the cause of the error.</span></span> <span data-ttu-id="07903-110">많은 오류 메시지에는 오류를 발생시킨 개체 이름과 같은 정보가 포함된 대체 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07903-110">Many error messages have substitution variables in which information, such as the name of the object generating the error, is inserted.</span></span>|  
|<span data-ttu-id="07903-111">심각도</span><span class="sxs-lookup"><span data-stu-id="07903-111">Severity</span></span>|<span data-ttu-id="07903-112">오류의 심각도를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="07903-112">The severity indicates how serious the error is.</span></span> <span data-ttu-id="07903-113">심각도가 낮은 오류(심각도가 1 또는 2인 경우)는 정보 메시지이거나 하위 수준 경고이며</span><span class="sxs-lookup"><span data-stu-id="07903-113">Errors that have a low severity, such as 1 or 2, are information messages or low-level warnings.</span></span> <span data-ttu-id="07903-114">심각도가 높은 오류는 가능한 빨리 해결해야 할 문제를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="07903-114">Errors that have a high severity indicate problems that should be addressed as soon as possible.</span></span> <span data-ttu-id="07903-115">심각도에 대한 자세한 내용은 [데이터베이스 엔진 오류 심각도](database-engine-error-severities.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07903-115">For more information about severities, see [Database Engine Error Severities](database-engine-error-severities.md).</span></span>|  
|<span data-ttu-id="07903-116">시스템 상태</span><span class="sxs-lookup"><span data-stu-id="07903-116">State</span></span>|<span data-ttu-id="07903-117">일부 오류 메시지는 [!INCLUDE[ssDE](../../includes/ssde-md.md)]코드의 여러 곳에서 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07903-117">Some error messages can be raised at multiple points in the code for the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="07903-118">예를 들어 1105 오류는 여러 가지 다른 조건에서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="07903-118">For example, an 1105 error can be raised for several different conditions.</span></span> <span data-ttu-id="07903-119">오류를 발생시키는 각각의 특정 조건마다 고유한 상태 코드를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="07903-119">Each specific condition that raises an error assigns a unique state code.</span></span><br /><br /> <span data-ttu-id="07903-120">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 기술 자료와 같이 알려진 문제에 대한 정보를 포함하는 데이터베이스를 확인하는 경우 상태 번호를 사용하여 기록된 문제가 실제로 발생한 오류와 동일한지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07903-120">When you are viewing databases that contain information about known issues, such as the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base, you can use the state number to determine whether the recorded issue is the same as the error you have encountered.</span></span> <span data-ttu-id="07903-121">예를 들어 기술 자료 문서에서 상태가 2인 1105 오류에 대해 설명하는데 실제로 발생한 1105 오류 메시지의 상태가 3인 경우 이 오류가 기술 자료 문서에 보고된 것과 다른 원인에서 비롯되었을 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="07903-121">For example, if a Knowledge Base Article describes an 1105 error that has a state of 2 and the 1105 error message you received had a state of 3, the error probably has a different cause than the one reported in the article.</span></span><br /><br /> <span data-ttu-id="07903-122">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 엔지니어도 오류의 상태 코드를 사용하여 원본 코드에서 해당 오류 코드가 발생한 위치를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07903-122">A [!INCLUDE[msCoName](../../includes/msconame-md.md)] support engineer can also use the state code from an error to find the location in the source code where that error code is being raised.</span></span> <span data-ttu-id="07903-123">이 정보는 문제 진단에 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07903-123">This information might provide additional ideas on how to diagnose the problem.</span></span>|  
|<span data-ttu-id="07903-124">프로시저 이름</span><span class="sxs-lookup"><span data-stu-id="07903-124">Procedure name</span></span>|<span data-ttu-id="07903-125">오류가 발생한 저장 프로시저 또는 트리거의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="07903-125">Is the name of the stored procedure or trigger in which the error has occurred.</span></span>|  
|<span data-ttu-id="07903-126">줄 번호</span><span class="sxs-lookup"><span data-stu-id="07903-126">Line number</span></span>|<span data-ttu-id="07903-127">일괄 처리, 저장 프로시저, 트리거 또는 함수에서 오류를 발생시킨 문을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="07903-127">Indicates which statement in a batch, stored procedure, trigger, or function generated the error.</span></span>|  
  
 <span data-ttu-id="07903-128">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스의 모든 시스템 및 사용자 정의 오류 메시지는 **sys.messages** 카탈로그 뷰에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07903-128">All system and user-defined error messages in an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] are contained in the **sys.messages** catalog view.</span></span> <span data-ttu-id="07903-129">RAISERROR 문을 사용하여 애플리케이션에 사용자 정의 오류를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07903-129">You can use the RAISERROR statement to return user-defined errors to an application.</span></span>  
  
 <span data-ttu-id="07903-130">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] **SQLClient** 네임스페이스, ADO(ActiveX Data Objects), OLE DB 및 ODBC(Open Database Connectivity)를 비롯한 모든 데이터베이스 API는 기본 오류 특성을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="07903-130">All database APIs, such as the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] **SQLClient** namespace, ActiveX Data Objects (ADO), OLE DB, and Open Database Connectivity (ODBC), report the basic error attributes.</span></span> <span data-ttu-id="07903-131">이 정보에는 오류 번호와 메시지 문자열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="07903-131">This information includes the error number and message string.</span></span> <span data-ttu-id="07903-132">그러나 일부 API는 일부 오류 특성을 보고하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07903-132">However, not all the APIs report all the other error attributes.</span></span>  
  
 <span data-ttu-id="07903-133">TRY...CATCH 구문의 TRY 블록 범위 내에서 발생하는 오류에 대한 정보는 관련 CATCH 블록 범위 내에서 ERROR_LINE, ERROR_MESSAGE, ERROR_NUMBER, ERROR_PROCEDURE, ERROR_SEVERITY 및 ERROR_STATE와 같은 함수를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드에서 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07903-133">Information about an error that occurs in the scope of the TRY block of a TRY...CATCH construct can be obtained in [!INCLUDE[tsql](../../includes/tsql-md.md)] code by using functions such as ERROR_LINE, ERROR_MESSAGE, ERROR_NUMBER, ERROR_PROCEDURE, ERROR_SEVERITY, and ERROR_STATE in the scope of the associated CATCH block.</span></span> <span data-ttu-id="07903-134">자세한 내용은 [TRY...CATCH&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07903-134">For more information, see [TRY...CATCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="07903-135">예제</span><span class="sxs-lookup"><span data-stu-id="07903-135">Examples</span></span>  
 <span data-ttu-id="07903-136">다음 예에서는 영문( `sys.messages` ) 텍스트가 포함된 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 모든 시스템 및 사용자 정의 오류 메시지 목록을 반환하기 위해`1033`카탈로그 뷰를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="07903-136">The following example queries the `sys.messages` catalog view to return a list of all system and user-defined error messages in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that have English text (`1033`).</span></span>  
  
```  
SELECT  
    message_id,  
    language_id,  
    severity,  
    is_event_logged,  
    text  
  FROM sys.messages  
  WHERE language_id = 1033;  
```  
  
 <span data-ttu-id="07903-137">자세한 내용은 [sys.messages&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07903-137">For more information, see [sys.messages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07903-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="07903-138">See Also</span></span>  
 <span data-ttu-id="07903-139">[sys.messages&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages) </span><span class="sxs-lookup"><span data-stu-id="07903-139">[sys.messages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages) </span></span>  
 <span data-ttu-id="07903-140">[RAISERROR&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/raiserror-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="07903-140">[RAISERROR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/raiserror-transact-sql) </span></span>  
 <span data-ttu-id="07903-141">[@@ERROR&#40;Transact-SQL&#41;](/sql/t-sql/functions/error-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="07903-141">[@@ERROR &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-transact-sql) </span></span>  
 <span data-ttu-id="07903-142">[TRY...CATCH&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="07903-142">[TRY...CATCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql) </span></span>  
 <span data-ttu-id="07903-143">[ERROR_LINE&#40;Transact-SQL&#41;](/sql/t-sql/functions/error-line-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="07903-143">[ERROR_LINE &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-line-transact-sql) </span></span>  
 <span data-ttu-id="07903-144">[ERROR_MESSAGE&#40;Transact-SQL&#41;](/sql/t-sql/functions/error-message-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="07903-144">[ERROR_MESSAGE &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-message-transact-sql) </span></span>  
 <span data-ttu-id="07903-145">[ERROR_NUMBER&#40;Transact-SQL&#41;](/sql/t-sql/functions/error-number-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="07903-145">[ERROR_NUMBER &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-number-transact-sql) </span></span>  
 <span data-ttu-id="07903-146">[ERROR_PROCEDURE&#40;Transact-SQL&#41;](/sql/t-sql/functions/error-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="07903-146">[ERROR_PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-procedure-transact-sql) </span></span>  
 <span data-ttu-id="07903-147">[ERROR_SEVERITY&#40;Transact-SQL&#41;](/sql/t-sql/functions/error-severity-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="07903-147">[ERROR_SEVERITY &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-severity-transact-sql) </span></span>  
 [<span data-ttu-id="07903-148">ERROR_STATE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="07903-148">ERROR_STATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/error-state-transact-sql)  
  
  
