---
title: 작업 기록 로그 크기 조정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- resizing job history log
- size [SQL Server], job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: ddee1ce8-9d1b-4017-9894-bf7256aed95d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4c25cc43295d47b2bc19d48b5b257dbbe6bcfe9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649322"
---
# <a name="resize-the-job-history-log"></a><span data-ttu-id="db339-102">Resize the Job History Log</span><span class="sxs-lookup"><span data-stu-id="db339-102">Resize the Job History Log</span></span>
  <span data-ttu-id="db339-103">이 항목 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는를 사용 하 여에서 에이전트 작업 기록 로그의 크기 제한을 설정 하는 방법에 대해 설명 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="db339-103">This topic describes how to set size limits for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job history logs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="db339-104">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="db339-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="db339-105">보안</span><span class="sxs-lookup"><span data-stu-id="db339-105">Security</span></span>](#Security)  
  
-   <span data-ttu-id="db339-106">**작업 기록 로그의 크기 제한을 설정하려면:**</span><span class="sxs-lookup"><span data-stu-id="db339-106">**To set size limits for job history logs, using:**</span></span>  
  
     [<span data-ttu-id="db339-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="db339-107">SQL Server Management Studio</span></span>](#SSMS)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="db339-108">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="db339-108">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="db339-109">보안</span><span class="sxs-lookup"><span data-stu-id="db339-109">Security</span></span>  
 <span data-ttu-id="db339-110">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="db339-110">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="db339-111">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="db339-111">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-resize-the-job-history-log-based-on-raw-size"></a><span data-ttu-id="db339-112">원시 크기에 따라 작업 기록 로그의 크기를 조정하려면</span><span class="sxs-lookup"><span data-stu-id="db339-112">To resize the job history log based on raw size</span></span>  
  
1.  <span data-ttu-id="db339-113">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="db339-113">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="db339-114">**SQL Server 에이전트**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="db339-114">Right-click **SQL Server Agent**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="db339-115">**기록** 페이지를 선택한 다음 **작업 기록 로그 크기 제한**이 선택되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="db339-115">Select the **History** page, and then confirm that **Limit size of job history log**is checked.</span></span>  
  
4.  <span data-ttu-id="db339-116">**작업 기록 로그의 최대 크기(행 수)** 입력란에 작업 기록 로그에서 허용할 최대 행 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="db339-116">In the **Maximum job history log size** box, enter the maximum number of rows the job history log should allow.</span></span>  
  
5.  <span data-ttu-id="db339-117">**작업당 작업 기록의 최대 행 수** 입력란에 작업에 대해 허용되는 작업 기록의 최대 행 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="db339-117">In the **Maximum job history rows per job** box, enter the maximum number of job history rows to allow for a job.</span></span>  
  
#### <a name="to-resize-the-job-history-log-based-on-time"></a><span data-ttu-id="db339-118">시간에 따라 작업 기록 로그의 크기를 조정하려면</span><span class="sxs-lookup"><span data-stu-id="db339-118">To resize the job history log based on time</span></span>  
  
1.  <span data-ttu-id="db339-119">**개체 탐색기**에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="db339-119">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="db339-120">**SQL Server 에이전트**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="db339-120">Right-click **SQL Server Agent**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="db339-121">**기록** 페이지를 선택한 다음 **자동으로 에이전트 기록 제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="db339-121">Select the **History** page, and then click **Automatically remove agent history**.</span></span>  
  
4.  <span data-ttu-id="db339-122">적절한 **일**, **주**또는 **월**수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="db339-122">Select the appropriate number of **Days(s)**, **Week(s)**, or **Month(s)**.</span></span>  
  
  
