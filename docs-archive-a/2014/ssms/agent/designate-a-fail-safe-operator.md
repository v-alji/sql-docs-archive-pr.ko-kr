---
title: 유사 시 대기 운영자 지정 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- fail-safe operator [SQL Server]
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: 0f4eb513-5c0a-4523-974e-e85c1deeb57f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 714ed78875bd289f2fe2d64a5699c59bce58ced0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737461"
---
# <a name="designate-a-fail-safe-operator"></a><span data-ttu-id="9e087-102">유사 시 대기 운영자 지정</span><span class="sxs-lookup"><span data-stu-id="9e087-102">Designate a Fail-Safe Operator</span></span>
  <span data-ttu-id="9e087-103">유사 시 대기 운영자는 지정된 운영자에게 알릴 수 없을 경우 경고를 받는 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="9e087-103">A fail-safe operator is a user who receives the alert if the designated operator cannot be reached.</span></span> <span data-ttu-id="9e087-104">이 항목 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는를 사용 하 여에서 에이전트 경고 알림을 받을 유사 시 대기 운영자를 설정 하는 방법에 대해 설명 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9e087-104">This topic describes how to set a fail-safe operator to receive [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert notifications in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="9e087-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="9e087-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9e087-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="9e087-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9e087-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="9e087-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="9e087-108">보안</span><span class="sxs-lookup"><span data-stu-id="9e087-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9e087-109">**유사 시 대기 운영자를 지정하려면:**</span><span class="sxs-lookup"><span data-stu-id="9e087-109">**To designate a fail-safe operator, using:**</span></span>  
  
     [<span data-ttu-id="9e087-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9e087-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9e087-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="9e087-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="9e087-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="9e087-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="9e087-113">**이후 버전에서는** 에이전트에서 호출기 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] net send [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]옵션이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e087-113">The Pager and **net send** options will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9e087-114">새 개발 작업에서는 이 기능을 사용하지 말고, 현재 이 기능을 사용하는 애플리케이션은 수정하세요.</span><span class="sxs-lookup"><span data-stu-id="9e087-114">Avoid using these features in new development work, and plan to modify applications that currently use these features.</span></span>  
  
-   <span data-ttu-id="9e087-115">SQL Server 에이전트는 데이터베이스 메일을 사용하여 운영자에게 전자 메일 및 호출기 알림을 보내도록 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e087-115">Note that SQL Server Agent must be configured to use Database Mail to send e-mail and pager notifications to operators.</span></span> <span data-ttu-id="9e087-116">자세한 내용은 [경고를 운영자에게 할당](assign-alerts-to-an-operator.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e087-116">For more information, see [Assign Alerts to an Operator](assign-alerts-to-an-operator.md).</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="9e087-117">는 작업 구조를 만들고 관리할 수 있는 바람직한 방법을 제공하는데 이는 그래픽을 사용하여 쉽게 작업을 관리할 수 있는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="9e087-117">provides an easy, graphical way to manage jobs, and is the recommended way to create and manage the job infrastructure.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9e087-118">보안</span><span class="sxs-lookup"><span data-stu-id="9e087-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9e087-119">권한</span><span class="sxs-lookup"><span data-stu-id="9e087-119">Permissions</span></span>  
 <span data-ttu-id="9e087-120">**sysadmin** 고정 서버 역할의 멤버만 유사 시 대기 운영자를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e087-120">Only members of the **sysadmin** fixed server role can designate fail-safe operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9e087-121">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="9e087-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-designate-a-fail-safe-operator"></a><span data-ttu-id="9e087-122">유사 시 대기 운영자를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="9e087-122">To designate a fail-safe operator</span></span>  
  
1.  <span data-ttu-id="9e087-123">**개체 탐색기** 에서 더하기 기호를 클릭하여 유사 시 대기로 지정할 SQL Server 에이전트 운영자가 포함된 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="9e087-123">In **Object Explorer,** click the plus sign to expand the server that contains the SQL Server Agent operator that you want to designate as a fail-safe.</span></span>  
  
2.  <span data-ttu-id="9e087-124">**SQL Server 에이전트** 를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e087-124">Right-click **SQL Server Agent** and select **Properties**.</span></span>  

3.  <span data-ttu-id="9e087-125">**SQL Server 에이전트 속성-**_server_name_ 대화 상자의 **페이지 선택**아래에서 **경고 시스템**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e087-125">In the **SQL Server Agent Properties -**_server_name_ dialog box, under **Select a page**, select **Alert System**.</span></span>  
 
4.  <span data-ttu-id="9e087-126">**유사 시 대기 운영자**에서 **유사 시 대기 운영자 설정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9e087-126">Under **Fail-safe operator**, select **Enable fail-safe operator**.</span></span>  
  
5.  <span data-ttu-id="9e087-127">**운영자** 목록에서 유사 시 대기 운영자로 설정할 운영자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9e087-127">In the **Operator** list, select the operator that you want to make a fail-safe.</span></span>  
  
6.  <span data-ttu-id="9e087-128">**전자 메일**, **호출기**또는 **Net send**확인란 중 하나 이상을 선택하여 운영자에게 알림을 보낼 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9e087-128">Select either any or all of the following check boxes to specify how the operator will be notified: **E-mail**, **Pager**, or **Net send**.</span></span>  
  
7.  <span data-ttu-id="9e087-129">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9e087-129">When finished, click **OK**.</span></span>  
  
  
