---
title: 운영자에게 알림 태스크(유지 관리 계획) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.notifyoperator.f1
helpviewer_keywords:
- Notify Operator Task dialog box
ms.assetid: 39c0797c-ad2b-4591-85c9-a23a7f902895
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4feb59622c2a42de67193c75d545a6b8a2a08863
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652112"
---
# <a name="notify-operator-task-maintenance-plan"></a><span data-ttu-id="82c24-102">운영자에게 알림 태스크(유지 관리 계획)</span><span class="sxs-lookup"><span data-stu-id="82c24-102">Notify Operator Task (Maintenance Plan)</span></span>
  <span data-ttu-id="82c24-103">**운영자에게 알림 태스크** 대화 상자를 사용하여 이 유지 관리 계획에 자동 알림을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82c24-103">Use the **Notify Operators Task** dialog to add an automatic notification to this maintenance plan.</span></span> <span data-ttu-id="82c24-104">이 태스크를 사용하려면 MSDB를 사용하여 데이터베이스 메일을 활성화하고 메일 호스트 데이터베이스로 구성해야 합니다. 또한 유효한 메일 주소를 가지고 있는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 운영자가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82c24-104">To use this task you must have Database Mail enabled and properly configured with MSDB as a Mail Host Database, and have a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operator with a valid e-mail address.</span></span>  
  
 <span data-ttu-id="82c24-105">이 태스크에서는 sp_notify_operator 저장 프로시저를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="82c24-105">This task uses the sp_notify_operator stored procedure.</span></span>  
  
## <a name="options"></a><span data-ttu-id="82c24-106">옵션</span><span class="sxs-lookup"><span data-stu-id="82c24-106">Options</span></span>  
 <span data-ttu-id="82c24-107">**연결**</span><span class="sxs-lookup"><span data-stu-id="82c24-107">**Connection**</span></span>  
 <span data-ttu-id="82c24-108">이 태스크를 수행할 때 사용할 서버 연결을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82c24-108">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="82c24-109">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="82c24-109">**New**</span></span>  
 <span data-ttu-id="82c24-110">이 태스크를 수행할 때 사용할 새 서버 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="82c24-110">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="82c24-111">아래에서는 **새 연결** 대화 상자에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="82c24-111">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="82c24-112">**알릴 운영자**</span><span class="sxs-lookup"><span data-stu-id="82c24-112">**Operators to notify**</span></span>  
 <span data-ttu-id="82c24-113">전자 메일의 받는 사람을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="82c24-113">Specify the recipient of the e-mail.</span></span>  
  
 <span data-ttu-id="82c24-114">**알림 메시지 제목**</span><span class="sxs-lookup"><span data-stu-id="82c24-114">**Notification message subject**</span></span>  
 <span data-ttu-id="82c24-115">알림 메시지 제목 줄에 포함할 텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="82c24-115">Specify the text to include in the notification message subject line.</span></span>  
  
 <span data-ttu-id="82c24-116">**알림 메시지 본문**</span><span class="sxs-lookup"><span data-stu-id="82c24-116">**Notification message body**</span></span>  
 <span data-ttu-id="82c24-117">알림 메시지 본문에 포함할 텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="82c24-117">Specify the text to include in the notification message body.</span></span>  
  
 <span data-ttu-id="82c24-118">**T-SQL 보기**</span><span class="sxs-lookup"><span data-stu-id="82c24-118">**View T-SQL**</span></span>  
 <span data-ttu-id="82c24-119">선택한 옵션을 기반으로 서버에 대해 수행한 이 태스크의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="82c24-119">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="82c24-120">영향을 받은 개체 수가 많은 경우에는 표시하는 데 시간이 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82c24-120">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="82c24-121">새 연결 대화 상자</span><span class="sxs-lookup"><span data-stu-id="82c24-121">New Connection Dialog Box</span></span>  
 <span data-ttu-id="82c24-122">**연결 이름**</span><span class="sxs-lookup"><span data-stu-id="82c24-122">**Connection name**</span></span>  
 <span data-ttu-id="82c24-123">새 연결의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="82c24-123">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="82c24-124">**서버 이름 선택 또는 입력**</span><span class="sxs-lookup"><span data-stu-id="82c24-124">**Select or enter a server name**</span></span>  
 <span data-ttu-id="82c24-125">이 태스크를 수행할 때 연결할 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82c24-125">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="82c24-126">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="82c24-126">**Refresh**</span></span>  
 <span data-ttu-id="82c24-127">사용할 수 있는 서버 목록을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="82c24-127">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="82c24-128">**서버 로그온 정보 입력**</span><span class="sxs-lookup"><span data-stu-id="82c24-128">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="82c24-129">서버에 대한 인증 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="82c24-129">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="82c24-130">**Windows NT 통합 보안 사용**</span><span class="sxs-lookup"><span data-stu-id="82c24-130">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="82c24-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows 인증을 사용하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="82c24-131">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="82c24-132">**특정 사용자 이름 및 암호 사용**</span><span class="sxs-lookup"><span data-stu-id="82c24-132">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="82c24-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="82c24-133">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="82c24-134">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82c24-134">This option is not available.</span></span>  
  
 <span data-ttu-id="82c24-135">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="82c24-135">**User name**</span></span>  
 <span data-ttu-id="82c24-136">인증 시 사용할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="82c24-136">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="82c24-137">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82c24-137">This option is not available.</span></span>  
  
 <span data-ttu-id="82c24-138">**암호**</span><span class="sxs-lookup"><span data-stu-id="82c24-138">**Password**</span></span>  
 <span data-ttu-id="82c24-139">인증 시 사용할 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="82c24-139">Provide a password to use when authenticating.</span></span> <span data-ttu-id="82c24-140">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82c24-140">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82c24-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="82c24-141">See Also</span></span>  
 <span data-ttu-id="82c24-142">[데이터베이스 메일](../database-mail/database-mail.md) </span><span class="sxs-lookup"><span data-stu-id="82c24-142">[Database Mail](../database-mail/database-mail.md) </span></span>  
 [<span data-ttu-id="82c24-143">sp_notify_operator&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="82c24-143">sp_notify_operator &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-notify-operator-transact-sql)  
  
  
