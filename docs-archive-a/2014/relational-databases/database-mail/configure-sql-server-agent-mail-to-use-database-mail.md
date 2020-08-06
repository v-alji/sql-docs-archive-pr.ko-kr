---
title: 데이터베이스 메일을 사용하도록 SQL Server 에이전트 메일 구성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], SQL Server Agent Mail
- SQL Server Agent Mail
ms.assetid: 4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce
author: stevestein
ms.author: sstein
ms.openlocfilehash: 31d116c0bc8d7e148fc2ef6d2e344400516ad923
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728347"
---
# <a name="configure-sql-server-agent-mail-to-use-database-mail"></a><span data-ttu-id="56cb4-102">데이터베이스 메일을 사용하도록 SQL Server 에이전트 메일 구성</span><span class="sxs-lookup"><span data-stu-id="56cb4-102">Configure SQL Server Agent Mail to Use Database Mail</span></span>
  <span data-ttu-id="56cb4-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 를 사용하여 데이터베이스 메일로 알림 및 경고를 보내도록 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에이전트를 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="56cb4-103">This topic describes how to configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to use Database Mail to send notification and alerts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="56cb4-104">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="56cb4-104">**Before you begin:**</span></span>  
  
-   [<span data-ttu-id="56cb4-105">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="56cb4-105">Prerequisites</span></span>](#Prerequisites)  
  
-   [<span data-ttu-id="56cb4-106">보안</span><span class="sxs-lookup"><span data-stu-id="56cb4-106">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="56cb4-107">SQL Server Management Studio를 통해 데이터베이스 메일을 사용하도록 SQL Server 에이전트를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="56cb4-107">To Configure SQL Server Agent to use Database Mail, using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="56cb4-108">후속 작업</span><span class="sxs-lookup"><span data-stu-id="56cb4-108">Follow-up Tasks</span></span>](#Follow_Up)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="56cb4-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="56cb4-109">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="56cb4-110">필수 조건</span><span class="sxs-lookup"><span data-stu-id="56cb4-110">Prerequisites</span></span>  
  
-   <span data-ttu-id="56cb4-111">데이터베이스 메일을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="56cb4-111">Enable Database Mail.</span></span>  
  
-   <span data-ttu-id="56cb4-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스 계정이 사용할 데이터베이스 메일 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="56cb4-112">Create a Database Mail account for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account to use.</span></span>  
  
-   <span data-ttu-id="56cb4-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스 계정에서 사용할 데이터베이스 메일 프로필을 만들고 **msdb** 데이터베이스의 **DatabaseMailUserRole** 에 사용자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="56cb4-113">Create a Database Mail profile for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account to use and add the user to the **DatabaseMailUserRole** in the **msdb** database.</span></span>  
  
-   <span data-ttu-id="56cb4-114">프로필을 **msdb** 데이터베이스의 기본 프로필로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="56cb4-114">Set the profile as the default profile for the **msdb** database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="56cb4-115">보안</span><span class="sxs-lookup"><span data-stu-id="56cb4-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="56cb4-116">권한</span><span class="sxs-lookup"><span data-stu-id="56cb4-116">Permissions</span></span>  
 <span data-ttu-id="56cb4-117">프로필 계정을 만들고 저장 프로시저를 실행하는 사용자는 sysadmin 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56cb4-117">The user creating the profiles accounts and executing stored procedures should be a member of the sysadmin fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="56cb4-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="56cb4-118">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="56cb4-119">**데이터베이스 메일을 사용하도록 SQL Server 에이전트를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="56cb4-119">**To configure SQL Server Agent to use Database Mail**</span></span>  
  
-   <span data-ttu-id="56cb4-120">개체 탐색기에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="56cb4-120">In Object Explorer, expand a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="56cb4-121">**SQL Server 에이전트**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="56cb4-121">Right-click **SQL Server Agent**, and then click **Properties**.</span></span>  
  
-   <span data-ttu-id="56cb4-122">**경고 시스템**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="56cb4-122">Click **Alert System**.</span></span>  
  
-   <span data-ttu-id="56cb4-123">**메일 프로필 설정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="56cb4-123">Select **Enable Mail Profile**.</span></span>  
  
-   <span data-ttu-id="56cb4-124">**메일 시스템** 목록에서 **데이터베이스 메일**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="56cb4-124">In the **Mail system** list, select **Database Mail**.</span></span>  
  
-   <span data-ttu-id="56cb4-125">**메일 프로필**목록에서 데이터베이스 메일에 대한 메일 프로필을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="56cb4-125">In the **Mail profile list**, select a mail profile for Database Mail.</span></span>  
  
-   <span data-ttu-id="56cb4-126">SQL Server 에이전트를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="56cb4-126">Restart SQL Server Agent.</span></span>  
  
##  <a name="follow-up-tasks"></a><a name="Follow_Up"></a> <span data-ttu-id="56cb4-127">후속 작업</span><span class="sxs-lookup"><span data-stu-id="56cb4-127">Follow-up Tasks</span></span>  
 <span data-ttu-id="56cb4-128">경고 및 알림을 보내도록 에이전트를 구성하려면 다음 태스크를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56cb4-128">The following tasks are necessary to complete the configuration of Agent to send alerts and notifications.</span></span>  
  
-   [<span data-ttu-id="56cb4-129">경고</span><span class="sxs-lookup"><span data-stu-id="56cb4-129">Alerts</span></span>](../../ssms/agent/alerts.md)  
  
     <span data-ttu-id="56cb4-130">경고를 구성하여 특정 데이터베이스 이벤트 또는 운영 체제 상태를 운영자에게 알릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56cb4-130">Alerts can be configured to notify an operator of a particular database event or operating system condition.</span></span>  
  
-   [<span data-ttu-id="56cb4-131">연산자</span><span class="sxs-lookup"><span data-stu-id="56cb4-131">Operators</span></span>](../../ssms/agent/operators.md)  
  
     <span data-ttu-id="56cb4-132">운영자는 전자 알림을 받을 수 있는 사람 또는 그룹의 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="56cb4-132">Operators are aliases for people or groups that can receive electronic notification</span></span>  
  
  
