---
title: SQL Server 에이전트 작업 실행 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqlserveragentjobtask.f1
helpviewer_keywords:
- Execute SQL Server Agent Job task [Integration Services]
- jobs [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 3aa3bc0e-1a1c-452e-81b8-b4e3422ea053
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d0c66eb7022312fa3ec3d161f63a9aee92b840f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651837"
---
# <a name="execute-sql-server-agent-job-task"></a><span data-ttu-id="1e74f-102">SQL Server 에이전트 작업 실행 태스크</span><span class="sxs-lookup"><span data-stu-id="1e74f-102">Execute SQL Server Agent Job Task</span></span>
  <span data-ttu-id="1e74f-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업 실행 태스크는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1e74f-103">The Execute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Job task runs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1e74f-104">에이전트는 SQL Server의 인스턴스에 정의된 작업을 실행하는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="1e74f-104">Agent is a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows service that runs jobs that have been defined in an instance of SQL Server.</span></span> <span data-ttu-id="1e74f-105">Transact-SQL 문과 ActiveX 스크립트를 실행하는 작업을 만들거나 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 및 복제 유지 관리 태스크를 수행하거나 패키지를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e74f-105">You can create jobs that execute Transact-SQL statements and ActiveX scripts, perform [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and Replication maintenance tasks, or run packages.</span></span> <span data-ttu-id="1e74f-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 모니터링하고 경고가 발생하도록 작업을 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e74f-106">You can also configure a job to monitor [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and fire alerts.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1e74f-107">에이전트 작업은 일반적으로 반복해서 수행하는 태스크를 자동화하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e74f-107">Agent jobs are typically used to automate tasks that you perform repeatedly.</span></span> <span data-ttu-id="1e74f-108">자세한 내용은 [작업 구현](../../ssms/agent/implement-jobs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1e74f-108">For more information, see [Implement Jobs](../../ssms/agent/implement-jobs.md).</span></span>  
  
 <span data-ttu-id="1e74f-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업 실행 태스크를 사용하면 패키지가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소에 관련된 관리 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e74f-109">By using the Execute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Job task, a package can perform administrative tasks related to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span> <span data-ttu-id="1e74f-110">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업은 **sp_enum_dtspackages** 와 같은 시스템 저장 프로시저를 실행하여 폴더의 패키지 목록을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e74f-110">For example, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job can run a system stored procedure such as **sp_enum_dtspackages** to obtain a list of packages in a folder.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1e74f-111">에이전트가 실행되고 있어야만 로컬 또는 다중 서버 관리 작업이 자동으로 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e74f-111">Agent must be running before local or multiserver administrative jobs can run automatically.</span></span>  
  
 <span data-ttu-id="1e74f-112">이 태스크는 **sp_start_job** 시스템 프로시저를 캡슐화하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업 이름을 프로시저에 인수로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="1e74f-112">This task encapsulates the **sp_start_job** system procedure and passes the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job to the procedure as an argument.</span></span> <span data-ttu-id="1e74f-113">자세한 내용은 [sp_start_job&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1e74f-113">For more information, see [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql).</span></span>  
  
## <a name="configuring-the-execute-sql-server-agent-job-task"></a><span data-ttu-id="1e74f-114">SQL Server 에이전트 작업 실행 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="1e74f-114">Configuring the Execute SQL Server Agent Job Task</span></span>  
 <span data-ttu-id="1e74f-115">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e74f-115">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="1e74f-116">이 태스크는 **디자이너의** 도구 상자 **에 있는** 유지 관리 계획 태스크 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 섹션에서 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e74f-116">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="1e74f-117">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="1e74f-117">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="1e74f-118">SQL Server 에이전트 작업 실행 태스크&#40;유지 관리 계획&#41;</span><span class="sxs-lookup"><span data-stu-id="1e74f-118">Execute SQL Server Agent Job Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/execute-sql-server-agent-job-task-maintenance-plan.md)  
  
 <span data-ttu-id="1e74f-119">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="1e74f-119">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="1e74f-120">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="1e74f-120">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
  
