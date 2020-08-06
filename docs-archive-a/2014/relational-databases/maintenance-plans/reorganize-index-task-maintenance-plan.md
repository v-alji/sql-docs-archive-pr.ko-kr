---
title: 인덱스 다시 구성 태스크(유지 관리 계획) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.defrag.f1
helpviewer_keywords:
- Reorganize Index Task dialog box
ms.assetid: e9cbebbd-f36f-4176-9832-382a46ac946c
author: rothja
ms.author: jroth
ms.openlocfilehash: 0bbb154045b781f8a92dfce9c9d2f6ee2d819c17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649513"
---
# <a name="reorganize-index-task-maintenance-plan"></a><span data-ttu-id="72084-102">인덱스 다시 구성 태스크(유지 관리 계획)</span><span class="sxs-lookup"><span data-stu-id="72084-102">Reorganize Index Task (Maintenance Plan)</span></span>
  <span data-ttu-id="72084-103">**인덱스 다시 구성 태스크** 대화 상자를 사용하여 인덱스 페이지를 보다 효율적인 검색 순서로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72084-103">Use the **ReorganizeIndex Task** dialog to move index pages into a more efficient search order.</span></span> <span data-ttu-id="72084-104">`ALTER INDEX REORGANIZE` 데이터베이스의 경우 이 태스크를 수행하면 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 문이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="72084-104">This task uses the `ALTER INDEX REORGANIZE` statement with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] databases.</span></span>  
  
## <a name="options"></a><span data-ttu-id="72084-105">옵션</span><span class="sxs-lookup"><span data-stu-id="72084-105">Options</span></span>  
 <span data-ttu-id="72084-106">**연결**</span><span class="sxs-lookup"><span data-stu-id="72084-106">**Connection**</span></span>  
 <span data-ttu-id="72084-107">이 태스크를 수행할 때 사용할 서버 연결을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="72084-107">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="72084-108">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="72084-108">**New**</span></span>  
 <span data-ttu-id="72084-109">이 태스크를 수행할 때 사용할 새 서버 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="72084-109">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="72084-110">아래에서는 **새 연결** 대화 상자에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="72084-110">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="72084-111">**데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="72084-111">**Databases**</span></span>  
 <span data-ttu-id="72084-112">이 태스크의 영향을 받는 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="72084-112">Specify the databases affected by this task.</span></span>  
  
-   <span data-ttu-id="72084-113">**모든 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="72084-113">**All databases**</span></span>  
  
     <span data-ttu-id="72084-114">tempdb를 제외한 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 대해 유지 관리 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="72084-114">Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases except tempdb.</span></span>  
  
-   <span data-ttu-id="72084-115">**모든 시스템 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="72084-115">**All system databases**</span></span>  
  
     <span data-ttu-id="72084-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tempdb **를 제외한 각**시스템 데이터베이스에 대해 유지 관리 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="72084-116">Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases except **tempdb**.</span></span> <span data-ttu-id="72084-117">사용자가 만든 데이터베이스에 대해서는 유지 관리 태스크가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72084-117">No maintenance tasks are run against user-created databases.</span></span>  
  
-   <span data-ttu-id="72084-118">**모든 사용자 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="72084-118">**All user databases**</span></span>  
  
     <span data-ttu-id="72084-119">사용자가 만든 모든 데이터베이스에 대해 유지 관리 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="72084-119">Generate a maintenance plan that runs maintenance tasks against all user-created databases.</span></span> <span data-ttu-id="72084-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 데이터베이스에 대해서는 유지 관리 태스크가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72084-120">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
-   <span data-ttu-id="72084-121">**다음 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="72084-121">**These specific databases**</span></span>  
  
     <span data-ttu-id="72084-122">선택한 데이터베이스에 대해서만 유지 관리 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="72084-122">Generate a maintenance plan that runs maintenance tasks against only those databases that are selected.</span></span> <span data-ttu-id="72084-123">이 옵션을 선택한 경우에는 목록에서 하나 이상의 데이터베이스를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72084-123">At least one database in the list must be selected if this option is chosen.</span></span>  
  
 <span data-ttu-id="72084-124">**Object**</span><span class="sxs-lookup"><span data-stu-id="72084-124">**Object**</span></span>  
 <span data-ttu-id="72084-125">테이블, 뷰 또는 둘 다를 표시하도록 **선택** 표를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="72084-125">Limit the **Selection** grid to display tables, views, or both.</span></span>  
  
 <span data-ttu-id="72084-126">**선택**</span><span class="sxs-lookup"><span data-stu-id="72084-126">**Selection**</span></span>  
 <span data-ttu-id="72084-127">이 태스크의 영향을 받는 테이블 또는 인덱스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="72084-127">Specify the tables or indexes affected by this task.</span></span> <span data-ttu-id="72084-128">**개체** 상자에서 **테이블 및 뷰** 를 선택한 경우에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="72084-128">Not available when **Tables and Views** is selected in the **Object** box.</span></span>  
  
 <span data-ttu-id="72084-129">**큰 개체 압축**</span><span class="sxs-lookup"><span data-stu-id="72084-129">**Compact large objects**</span></span>  
 <span data-ttu-id="72084-130">가능한 경우에 테이블 및 뷰에 대한 공간 할당을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="72084-130">Deallocate space for tables and views when possible.</span></span> <span data-ttu-id="72084-131">이 옵션에서는 `ALTER INDEX LOB_COMPACTION = ON`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="72084-131">This option uses `ALTER INDEX LOB_COMPACTION = ON`.</span></span>  
  
 <span data-ttu-id="72084-132">**T-SQL 보기**</span><span class="sxs-lookup"><span data-stu-id="72084-132">**View T-SQL**</span></span>  
 <span data-ttu-id="72084-133">선택한 옵션을 기반으로 서버에 대해 수행한 이 태스크의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="72084-133">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="72084-134">영향을 받은 개체 수가 많은 경우에는 표시하는 데 시간이 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72084-134">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="72084-135">새 연결 대화 상자</span><span class="sxs-lookup"><span data-stu-id="72084-135">New Connection Dialog Box</span></span>  
 <span data-ttu-id="72084-136">**연결 이름**</span><span class="sxs-lookup"><span data-stu-id="72084-136">**Connection name**</span></span>  
 <span data-ttu-id="72084-137">새 연결의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="72084-137">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="72084-138">**서버 이름 선택 또는 입력**</span><span class="sxs-lookup"><span data-stu-id="72084-138">**Select or enter a server name**</span></span>  
 <span data-ttu-id="72084-139">이 태스크를 수행할 때 연결할 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="72084-139">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="72084-140">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="72084-140">**Refresh**</span></span>  
 <span data-ttu-id="72084-141">사용할 수 있는 서버 목록을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="72084-141">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="72084-142">**서버 로그온 정보 입력**</span><span class="sxs-lookup"><span data-stu-id="72084-142">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="72084-143">서버에 대한 인증 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="72084-143">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="72084-144">**Windows NT 통합 보안 사용**</span><span class="sxs-lookup"><span data-stu-id="72084-144">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="72084-145">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows 인증을 사용하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="72084-145">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="72084-146">**특정 사용자 이름 및 암호 사용**</span><span class="sxs-lookup"><span data-stu-id="72084-146">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="72084-147">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="72084-147">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="72084-148">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="72084-148">This option is not available.</span></span>  
  
 <span data-ttu-id="72084-149">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="72084-149">**User name**</span></span>  
 <span data-ttu-id="72084-150">인증 시 사용할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="72084-150">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="72084-151">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="72084-151">This option is not available.</span></span>  
  
 <span data-ttu-id="72084-152">**암호**</span><span class="sxs-lookup"><span data-stu-id="72084-152">**Password**</span></span>  
 <span data-ttu-id="72084-153">인증 시 사용할 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="72084-153">Provide a password to use when authenticating.</span></span> <span data-ttu-id="72084-154">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="72084-154">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72084-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="72084-155">See Also</span></span>  
 <span data-ttu-id="72084-156">[ALTER INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="72084-156">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 [<span data-ttu-id="72084-157">DBCC INDEXDEFRAG&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="72084-157">DBCC INDEXDEFRAG &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-indexdefrag-transact-sql)  
  
  
