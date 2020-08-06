---
title: 운영자에게 알림 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.notifyoperatortask.f1
helpviewer_keywords:
- Notify Operator task
- notifications [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 6c816c68-c6d6-44e4-bb34-c8e060a958a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ed5158a4ec5cfe8374fedbb2afbca1294b58f05e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741167"
---
# <a name="notify-operator-task"></a><span data-ttu-id="bd5d7-102">운영자에게 알림 태스크</span><span class="sxs-lookup"><span data-stu-id="bd5d7-102">Notify Operator Task</span></span>
  <span data-ttu-id="bd5d7-103">운영자에게 알림 태스크는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 운영자에게 알림 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="bd5d7-103">The Notify Operator task sends notification messages to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operators.</span></span> <span data-ttu-id="bd5d7-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 운영자는 전자 알림을 받을 수 있는 사람 또는 그룹의 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="bd5d7-104">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operator is an alias for a person or group that can receive electronic notifications.</span></span> <span data-ttu-id="bd5d7-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 운영자에 대한 자세한 내용은 [운영자](../../ssms/agent//operators.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bd5d7-105">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] operators, see [Operators](../../ssms/agent//operators.md).</span></span>  
  
 <span data-ttu-id="bd5d7-106">운영자에게 알림 태스크를 사용하면 패키지가 메일, 호출기 또는 **net send**를 통해 한 명 이상의 운영자에게 알림을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd5d7-106">By using the Notify Operator task, a package can notify one or more operators via e-mail, pager, or **net send**.</span></span> <span data-ttu-id="bd5d7-107">각 운영자는 다른 방법으로 알림을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd5d7-107">Each operator can be notified by different methods.</span></span> <span data-ttu-id="bd5d7-108">예를 들어 OperatorA는 메일과 호출기를 통해 알림을 받고 OperatorB는 호출기와 **net send**를 통해 알림을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="bd5d7-108">For example, OperatorA is notified by e-mail and pager, and OperatorB is notified by pager and **net send**.</span></span> <span data-ttu-id="bd5d7-109">태스크에서 알림을 받는 운영자는 운영자에게 알림 태스크의 **OperatorNotify** 컬렉션 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5d7-109">The operators who receive notifications from the task must be members of the **OperatorNotify** collection on the Notify Operator task.</span></span>  
  
 <span data-ttu-id="bd5d7-110">운영자에게 알림 태스크는 Transact-SQL 문이나 DBCC 명령을 캡슐화하지 않는 유일한 데이터베이스 유지 관리 태스크입니다.</span><span class="sxs-lookup"><span data-stu-id="bd5d7-110">The Notify Operator task is the only database maintenance task that does not encapsulate a Transact-SQL statement or a DBCC command.</span></span>  
  
## <a name="configuration-of-the-notify-operator-task"></a><span data-ttu-id="bd5d7-111">운영자에게 알림 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="bd5d7-111">Configuration of the Notify Operator Task</span></span>  
 <span data-ttu-id="bd5d7-112">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd5d7-112">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="bd5d7-113">이 태스크는 **디자이너의** 도구 상자 **에 있는** 유지 관리 계획 태스크 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 섹션에서 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd5d7-113">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="bd5d7-114">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="bd5d7-114">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="bd5d7-115">운영자에게 알림 태스크&#40;유지 관리 계획&#41;</span><span class="sxs-lookup"><span data-stu-id="bd5d7-115">Notify Operator Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/notify-operator-task-maintenance-plan.md)  
  
 <span data-ttu-id="bd5d7-116">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="bd5d7-116">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="bd5d7-117">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="bd5d7-117">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
  
