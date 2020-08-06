---
title: 작업 전송 태스크 편집기 (일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferjobstask.general.f1
helpviewer_keywords:
- Transfer Jobs Task Editor
ms.assetid: 96531920-92d4-4a3b-a38a-6f0c8bc78ada
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d824c1904b8a3ffd0078f778a78dea898ab53577
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727276"
---
# <a name="transfer-jobs-task-editor-general-page"></a><span data-ttu-id="d707c-102">작업 전송 태스크 편집기(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="d707c-102">Transfer Jobs Task Editor (General Page)</span></span>
  <span data-ttu-id="d707c-103">**작업 전송 태스크 편집기** 대화 상자의 **일반** 페이지를 사용하여 작업 전송 태스크의 이름을 지정하고 해당 태스크를 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d707c-103">Use the **General** page of the **Transfer Jobs Task Editor** dialog box to name and describe the Transfer Jobs task.</span></span> <span data-ttu-id="d707c-104">작업 전송 태스크에 대한 자세한 내용은 [Transfer Jobs Task](control-flow/transfer-jobs-task.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d707c-104">For more information about the Transfer Jobs task, see [Transfer Jobs Task](control-flow/transfer-jobs-task.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d707c-105">대상 서버의 **sysadmin** 고정 서버 역할 또는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 고정 데이터베이스 역할 중 하나의 멤버만 대상 서버에서 작업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d707c-105">Only members of the **sysadmin** fixed server role or one of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent fixed database roles on the destination server can successfully create jobs there.</span></span> <span data-ttu-id="d707c-106">원본 서버의 작업에 액세스하려면 사용자는 최소한 원본 서버의 **SQLAgentUserRole** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d707c-106">To access jobs on the source server, users must be a member of at least the **SQLAgentUserRole** fixed database role there.</span></span> <span data-ttu-id="d707c-107">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 고정 데이터베이스 역할 및 해당 권한에 대한 자세한 내용은 [SQL Server 에이전트 고정 데이터베이스 역할](../ssms/agent/sql-server-agent-fixed-database-roles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d707c-107">For more information about [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent fixed database roles and their permissions, see [SQL Server Agent Fixed Database Roles](../ssms/agent/sql-server-agent-fixed-database-roles.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="d707c-108">옵션</span><span class="sxs-lookup"><span data-stu-id="d707c-108">Options</span></span>  
 <span data-ttu-id="d707c-109">**이름**</span><span class="sxs-lookup"><span data-stu-id="d707c-109">**Name**</span></span>  
 <span data-ttu-id="d707c-110">작업 전송 태스크에 사용할 고유 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d707c-110">Type a unique name for the Transfer Jobs task.</span></span> <span data-ttu-id="d707c-111">이 이름은 태스크 아이콘에서 레이블로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d707c-111">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d707c-112">태스크 이름은 패키지 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d707c-112">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="d707c-113">**설명**</span><span class="sxs-lookup"><span data-stu-id="d707c-113">**Description**</span></span>  
 <span data-ttu-id="d707c-114">작업 전송 태스크에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d707c-114">Type a description of the Transfer Jobs task.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d707c-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d707c-115">See Also</span></span>  
 <span data-ttu-id="d707c-116">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="d707c-116">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="d707c-117">[Integration Services 태스크](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="d707c-117">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="d707c-118">[작업 전송 태스크 편집기 &#40;작업 페이지&#41;](../../2014/integration-services/transfer-jobs-task-editor-jobs-page.md) </span><span class="sxs-lookup"><span data-stu-id="d707c-118">[Transfer Jobs Task Editor &#40;Jobs Page&#41;](../../2014/integration-services/transfer-jobs-task-editor-jobs-page.md) </span></span>  
 [<span data-ttu-id="d707c-119">식 페이지</span><span class="sxs-lookup"><span data-stu-id="d707c-119">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
