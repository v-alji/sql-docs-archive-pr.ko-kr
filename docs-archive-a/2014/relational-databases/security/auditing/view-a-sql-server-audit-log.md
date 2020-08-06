---
title: SQL Server 감사 로그 보기 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- audits [SQL Server], viewing logs
- viewing audit logs
- logs [SQL Server], audit
ms.assetid: e8feaca0-7852-422b-895a-319b965d8d9b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 8f9902a4fc92ef0b35bae62eb80170762c52fdec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647570"
---
# <a name="view-a-sql-server-audit-log"></a><span data-ttu-id="176f0-102">SQL Server 감사 로그 보기</span><span class="sxs-lookup"><span data-stu-id="176f0-102">View a SQL Server Audit Log</span></span>
  <span data-ttu-id="176f0-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 을 사용하여 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 SQL Server 감사 로그를 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="176f0-103">This topic describes how to view a SQL Server audit log in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="176f0-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="176f0-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="176f0-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="176f0-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="176f0-106">보안</span><span class="sxs-lookup"><span data-stu-id="176f0-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="176f0-107">**다음을 사용하여 SQL Server 감사 로그를 봅니다.**</span><span class="sxs-lookup"><span data-stu-id="176f0-107">**To view a SQL Server audit log, using:**</span></span>  
  
     [<span data-ttu-id="176f0-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="176f0-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="176f0-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="176f0-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="176f0-110">보안</span><span class="sxs-lookup"><span data-stu-id="176f0-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="176f0-111">권한</span><span class="sxs-lookup"><span data-stu-id="176f0-111">Permissions</span></span>  
 <span data-ttu-id="176f0-112">`CONTROL SERVER` 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="176f0-112">Requires the `CONTROL SERVER` permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="176f0-113">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="176f0-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-a-sql-server-audit-log"></a><span data-ttu-id="176f0-114">SQL Server 감사 로그를 보려면</span><span class="sxs-lookup"><span data-stu-id="176f0-114">To view a SQL Server audit log</span></span>  
  
1.  <span data-ttu-id="176f0-115">개체 탐색기에서 **보안** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="176f0-115">In Object Explorer, expand the **Security** folder.</span></span>  
  
2.  <span data-ttu-id="176f0-116">**감사** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="176f0-116">Expand the **Audits** folder.</span></span>  
  
3.  <span data-ttu-id="176f0-117">보려는 감사 로그를 마우스 오른쪽 단추로 클릭하고 **감사 로그 보기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="176f0-117">Right-click the audit log that you want to view and select **View Audit Logs**.</span></span> <span data-ttu-id="176f0-118">그러면 **로그 파일 뷰어-**_server_name_ 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="176f0-118">This opens the **Log File Viewer -**_server_name_ dialog box.</span></span> <span data-ttu-id="176f0-119">자세한 내용은 [Log File Viewer F1 Help](../../logs/log-file-viewer-f1-help.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="176f0-119">For more information, see [Log File Viewer F1 Help](../../logs/log-file-viewer-f1-help.md).</span></span>  
  
4.  <span data-ttu-id="176f0-120">완료되면 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="176f0-120">When finished, click **Close**.</span></span>  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="176f0-121">은 로그 파일 뷰어를 사용하여 감사 로그를 보는 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="176f0-121">recommends viewing the audit log by using the Log File Viewer.</span></span> <span data-ttu-id="176f0-122">그러나 자동화된 모니터링 시스템을 만들면 [sys.fn_get_audit_file&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql) 함수를 사용하여 감사 파일에서 정보를 직접 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="176f0-122">However, if you are creating an automated monitoring system, the information in the audit file can be read directly by using the [sys.fn_get_audit_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql) function.</span></span> <span data-ttu-id="176f0-123">파일을 직접 읽으면 약간 다른 (처리되지 않은) 형식으로 데이터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="176f0-123">Reading the file directly returns data in a slightly different (unprocessed) format.</span></span> <span data-ttu-id="176f0-124">자세한 내용은 fn_get_audit_file를 참조 하세요 **.**</span><span class="sxs-lookup"><span data-stu-id="176f0-124">See **sys.fn_get_audit_file** for more information</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="176f0-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="176f0-125">See Also</span></span>  
 <span data-ttu-id="176f0-126">[SQL Server Audit&#40;데이터베이스 엔진&#41;](sql-server-audit-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="176f0-126">[SQL Server Audit &#40;Database Engine&#41;](sql-server-audit-database-engine.md) </span></span>  
 [<span data-ttu-id="176f0-127">보안 로그에 SQL Server 감사 이벤트 쓰기</span><span class="sxs-lookup"><span data-stu-id="176f0-127">Write SQL Server Audit Events to the Security Log</span></span>](write-sql-server-audit-events-to-the-security-log.md)  
  
  
