---
title: 작업 실행 종료 설정(SQL Server Management Studio) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
- SQL Server Agent jobs, execution shutdowns
ms.assetid: ac23e88f-53fc-41de-bb16-0c27c002d5a5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0e60807676c3c54faf1d44de318ff0a31c2e20b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659782"
---
# <a name="set-job-execution-shutdown-sql-server-management-studio"></a><span data-ttu-id="4fd6f-102">Set Job Execution Shutdown (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="4fd6f-102">Set Job Execution Shutdown (SQL Server Management Studio)</span></span>
  <span data-ttu-id="4fd6f-103">이 항목에서는를 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용 하 여 에이전트가에서 완료 될 때까지 에이전트가 완료 될 때까지 대기 하는 시간을 설정 하는 방법에 대해 설명 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4fd6f-103">This topic describes how to set the time that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent will wait for executing jobs to finish before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent itself finishes in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="4fd6f-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="4fd6f-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4fd6f-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="4fd6f-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4fd6f-106">보안</span><span class="sxs-lookup"><span data-stu-id="4fd6f-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4fd6f-107">**다음을 사용하여 SQL Server 에이전트 작업의 종료 시간을 설정합니다.**</span><span class="sxs-lookup"><span data-stu-id="4fd6f-107">**To set a shutdown time for a SQL Server Agent job, using:**</span></span>  
  
     [<span data-ttu-id="4fd6f-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4fd6f-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4fd6f-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="4fd6f-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4fd6f-110">보안</span><span class="sxs-lookup"><span data-stu-id="4fd6f-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4fd6f-111">권한</span><span class="sxs-lookup"><span data-stu-id="4fd6f-111">Permissions</span></span>  
 <span data-ttu-id="4fd6f-112">기본적으로 **sysadmin** 고정 서버 역할의 멤버는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 기다리는 시간을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fd6f-112">By default, members of the **sysadmin** fixed server role can set the time that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent will wait for executing jobs to finish before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent itself finishes.</span></span> <span data-ttu-id="4fd6f-113">다른 사용자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **데이터베이스의 다음** 에이전트 고정 데이터베이스 역할 중 하나를 부여 받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fd6f-113">Other users must be granted one of the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles in the **msdb** database:</span></span>  
  
-   <span data-ttu-id="4fd6f-114">**SQLAgentUserRole**</span><span class="sxs-lookup"><span data-stu-id="4fd6f-114">**SQLAgentUserRole**</span></span>  
  
-   <span data-ttu-id="4fd6f-115">**SQLAgentReaderRole**</span><span class="sxs-lookup"><span data-stu-id="4fd6f-115">**SQLAgentReaderRole**</span></span>  
  
-   <span data-ttu-id="4fd6f-116">**SQLAgentOperatorRole**</span><span class="sxs-lookup"><span data-stu-id="4fd6f-116">**SQLAgentOperatorRole**</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4fd6f-117">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="4fd6f-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-job-execution-shutdown"></a><span data-ttu-id="4fd6f-118">작업 실행 종료를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="4fd6f-118">To set job execution shutdown</span></span>  
  
1.  <span data-ttu-id="4fd6f-119">**개체 탐색기** 에서 더하기 기호를 클릭하여 작업 실행 종료 간격을 설정하려는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="4fd6f-119">In **Object Explorer,** , click the plus sign to expand the server where you want to set a job execution shutdown interval.</span></span>  
  
2.  <span data-ttu-id="4fd6f-120">**SQL Server 에이전트** 를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fd6f-120">Right-click **SQL Server Agent** and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="4fd6f-121">**페이지 선택**아래에서 **작업 시스템**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4fd6f-121">Under **Select a page**, select **Job System**.</span></span>  
  
4.  <span data-ttu-id="4fd6f-122">**시스템 종료 제한 시간 간격** 을 설정하여 시스템 종료 제한 시간 간격을 늘리거나 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="4fd6f-122">Set the **Shutdown time-out interval** in seconds to increase or decrease the shutdown time-out interval.</span></span> <span data-ttu-id="4fd6f-123">이 값에 따라 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 자체적으로 종료하기 전에 실행 중인 작업을 종료하기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 대기하는 시간이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fd6f-123">This determines how long [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent will wait for executing jobs to finish before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent itself finishes.</span></span>  
  
  
