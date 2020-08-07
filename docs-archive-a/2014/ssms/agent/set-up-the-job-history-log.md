---
title: 작업 기록 로그 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 018e5c49-d3a0-4504-851a-f70996a34bb7
author: stevestein
ms.author: sstein
ms.openlocfilehash: cb42e1daaee8a3a9e5ae9cc3c09a8cc42dcbff56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727891"
---
# <a name="set-up-the-job-history-log"></a><span data-ttu-id="76b38-102">Set Up the Job History Log</span><span class="sxs-lookup"><span data-stu-id="76b38-102">Set Up the Job History Log</span></span>
  <span data-ttu-id="76b38-103">이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업 기록 로그를 설정 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="76b38-103">This topic describes how to set up the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job history log.</span></span>  
  
-   <span data-ttu-id="76b38-104">**시작하기 전 주의 사항:**  [보안](#Security)</span><span class="sxs-lookup"><span data-stu-id="76b38-104">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="76b38-105">**다음을 사용하여 작업 기록 로그 설정**  [SQL Server Management Studio](#SSMS)</span><span class="sxs-lookup"><span data-stu-id="76b38-105">**To setup the job history log, using:**  [SQL Server Management Studio](#SSMS)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="76b38-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="76b38-106">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="76b38-107">보안</span><span class="sxs-lookup"><span data-stu-id="76b38-107">Security</span></span>  
 <span data-ttu-id="76b38-108">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="76b38-108">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="76b38-109">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="76b38-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="76b38-110">**작업 기록 로그를 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="76b38-110">**To set up the job history log**</span></span>  
  
1.  <span data-ttu-id="76b38-111">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="76b38-111">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="76b38-112">**SQL Server 에이전트**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76b38-112">Right-click **SQL Server Agent**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="76b38-113">**SQL Server 에이전트 속성** 대화 상자에서 **기록** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76b38-113">In the **SQL Server Agent Properties** dialog box, select the **History** page.</span></span>  
  
4.  <span data-ttu-id="76b38-114">다음 옵션 중에서 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="76b38-114">Choose from the following options:</span></span>  
  
    1.  <span data-ttu-id="76b38-115">**작업 기록 로그 크기 제한**을 선택한 다음 작업 기록 로그의 최대 행 수와 작업당 최대 행 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="76b38-115">Check **Limit size of job history log**, and then type the maximum number of rows for the job history log, and the maximum number of rows per job.</span></span>  
  
    2.  <span data-ttu-id="76b38-116">**자동으로 에이전트 기록 제거**를 선택한 다음 해당 기간보다 오래된 기록은 로그에서 삭제되도록 기간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="76b38-116">Check **Automatically remove agent history**, and specify a time period, such that history older than this period will be purged from the log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76b38-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="76b38-117">See Also</span></span>  
 <span data-ttu-id="76b38-118">[작업 구현](implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="76b38-118">[Implement Jobs](implement-jobs.md) </span></span>  
 <span data-ttu-id="76b38-119">[작업 활동 모니터링](monitor-job-activity.md) </span><span class="sxs-lookup"><span data-stu-id="76b38-119">[Monitor Job Activity](monitor-job-activity.md) </span></span>  
 [<span data-ttu-id="76b38-120">작업 만들기</span><span class="sxs-lookup"><span data-stu-id="76b38-120">Create Jobs</span></span>](create-jobs.md)  
  
  
