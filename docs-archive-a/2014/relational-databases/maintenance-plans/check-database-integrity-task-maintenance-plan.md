---
title: 데이터베이스 무결성 검사 태스크(유지 관리 계획) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.maintplanproperties.integrity.f1
- sql12.swb.maint.integrity.f1
helpviewer_keywords:
- Check Database Integrity Task dialog box
ms.assetid: 3534494a-5dfe-4738-b49a-e7fabd731c47
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f786755a3b7ed5d991b4cf0e32c067e355c111ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653358"
---
# <a name="check-database-integrity-task-maintenance-plan"></a><span data-ttu-id="70304-102">데이터베이스 무결성 검사 태스크(유지 관리 계획)</span><span class="sxs-lookup"><span data-stu-id="70304-102">Check Database Integrity Task (Maintenance Plan)</span></span>
  <span data-ttu-id="70304-103">**데이터베이스 무결성 검사 태스크** 대화 상자를 사용하면 `DBCC CHECKDB`[!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행하여 사용자 및 시스템 테이블, 데이터베이스 인덱스의 할당 및 구조적 무결성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70304-103">Use the **Check Database Integrity Task** dialog to check the allocation and structural integrity of user and system tables, and indexes in the database, by running the `DBCC CHECKDB`[!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="70304-104">`DBCC` 를 실행하면 데이터베이스의 모든 무결성 문제가 보고되므로 시스템 관리자나 데이터베이스 소유자가 나중에 이 문제들을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70304-104">Running `DBCC` ensures that any integrity problems with the database are reported, thereby allowing them to be addressed later by a system administrator or database owner.</span></span>  
  
## <a name="options"></a><span data-ttu-id="70304-105">옵션</span><span class="sxs-lookup"><span data-stu-id="70304-105">Options</span></span>  
 <span data-ttu-id="70304-106">**연결**</span><span class="sxs-lookup"><span data-stu-id="70304-106">**Connection**</span></span>  
 <span data-ttu-id="70304-107">이 태스크를 수행할 때 사용할 서버 연결을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="70304-107">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="70304-108">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="70304-108">**New**</span></span>  
 <span data-ttu-id="70304-109">이 태스크를 수행할 때 사용할 새 서버 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="70304-109">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="70304-110">아래에서는 **새 연결** 대화 상자에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="70304-110">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="70304-111">**데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="70304-111">**Databases**</span></span>  
 <span data-ttu-id="70304-112">이 태스크의 영향을 받는 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="70304-112">Specify the databases affected by this task.</span></span>  
  
-   <span data-ttu-id="70304-113">**모든 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="70304-113">**All databases**</span></span>  
  
     <span data-ttu-id="70304-114">**tempdb**를 제외한 모든 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 대해 유지 관리 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="70304-114">Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases except **tempdb**.</span></span>  
  
-   <span data-ttu-id="70304-115">**모든 시스템 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="70304-115">**All system databases**</span></span>  
  
     <span data-ttu-id="70304-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tempdb **를 제외한 각**시스템 데이터베이스에 대해 유지 관리 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="70304-116">Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases except **tempdb**.</span></span> <span data-ttu-id="70304-117">사용자가 만든 데이터베이스에 대해서는 유지 관리 태스크가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70304-117">No maintenance tasks are run against user-created databases.</span></span>  
  
-   <span data-ttu-id="70304-118">**모든 사용자 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="70304-118">**All user databases**</span></span>  
  
     <span data-ttu-id="70304-119">사용자가 만든 모든 데이터베이스에 대해 유지 관리 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="70304-119">Generate a maintenance plan that runs maintenance tasks against all user-created databases.</span></span> <span data-ttu-id="70304-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 데이터베이스에 대해서는 유지 관리 태스크가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70304-120">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
-   <span data-ttu-id="70304-121">**다음 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="70304-121">**These specific databases**</span></span>  
  
     <span data-ttu-id="70304-122">선택한 데이터베이스에 대해서만 유지 관리 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="70304-122">Generate a maintenance plan that runs maintenance tasks against only those databases that are selected.</span></span> <span data-ttu-id="70304-123">이 옵션을 선택한 경우에는 목록에서 하나 이상의 데이터베이스를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70304-123">At least one database in the list must be selected if this option is chosen.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="70304-124">유지 관리 계획은 호환성 수준 80 이상으로 설정된 데이터베이스에 대해서만 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="70304-124">Maintenance plans only run against databases set to compatibility level 80 or higher.</span></span> <span data-ttu-id="70304-125">호환성 수준 70 이하로 설정된 데이터베이스는 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70304-125">Databases set to compatibility level 70 or lower are not displayed.</span></span>  
  
 <span data-ttu-id="70304-126">**인덱스 포함**</span><span class="sxs-lookup"><span data-stu-id="70304-126">**Include indexes**</span></span>  
 <span data-ttu-id="70304-127">모든 인덱스 페이지와 테이블 데이터 페이지가 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="70304-127">Check the integrity of all the index pages as well as the table data pages.</span></span>  
  
 <span data-ttu-id="70304-128">**T-SQL 보기**</span><span class="sxs-lookup"><span data-stu-id="70304-128">**View T-SQL**</span></span>  
 <span data-ttu-id="70304-129">선택한 옵션을 기반으로 서버에 대해 수행한 이 태스크의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="70304-129">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70304-130">영향을 받은 개체 수가 많은 경우에는 표시하는 데 시간이 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70304-130">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="70304-131">새 연결 대화 상자</span><span class="sxs-lookup"><span data-stu-id="70304-131">New Connection Dialog Box</span></span>  
 <span data-ttu-id="70304-132">**연결 이름**</span><span class="sxs-lookup"><span data-stu-id="70304-132">**Connection name**</span></span>  
 <span data-ttu-id="70304-133">새 연결의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="70304-133">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="70304-134">**서버 이름 선택 또는 입력**</span><span class="sxs-lookup"><span data-stu-id="70304-134">**Select or enter a server name**</span></span>  
 <span data-ttu-id="70304-135">이 태스크를 수행할 때 연결할 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="70304-135">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="70304-136">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="70304-136">**Refresh**</span></span>  
 <span data-ttu-id="70304-137">사용할 수 있는 서버 목록을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="70304-137">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="70304-138">**서버 로그온 정보 입력**</span><span class="sxs-lookup"><span data-stu-id="70304-138">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="70304-139">서버에 대한 인증 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="70304-139">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="70304-140">**Windows NT 통합 보안 사용**</span><span class="sxs-lookup"><span data-stu-id="70304-140">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="70304-141">Windows 인증을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="70304-141">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with Windows Authentication.</span></span>  
  
 <span data-ttu-id="70304-142">**특정 사용자 이름 및 암호 사용**</span><span class="sxs-lookup"><span data-stu-id="70304-142">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="70304-143">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="70304-143">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="70304-144">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70304-144">This option is not available.</span></span>  
  
 <span data-ttu-id="70304-145">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="70304-145">**User name**</span></span>  
 <span data-ttu-id="70304-146">인증 시 사용할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="70304-146">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="70304-147">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70304-147">This option is not available.</span></span>  
  
 <span data-ttu-id="70304-148">**암호**</span><span class="sxs-lookup"><span data-stu-id="70304-148">**Password**</span></span>  
 <span data-ttu-id="70304-149">인증 시 사용할 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="70304-149">Provide a password to use when authenticating.</span></span> <span data-ttu-id="70304-150">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70304-150">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70304-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="70304-151">See Also</span></span>  
 [<span data-ttu-id="70304-152">DBCC CHECKDB&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="70304-152">DBCC CHECKDB &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  
