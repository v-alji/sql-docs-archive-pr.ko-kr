---
title: '자습서: Transact-SQL 문 작성 | Microsoft Docs'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL statements, tutorials
- Transact-SQL tutorials
- tutorials [Transact-SQL]
ms.assetid: 2addc9be-67d0-423d-a457-192fe9d7d058
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ac190d6099bca1a38ca2f286e6ce048fe5322e2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741503"
---
# <a name="tutorial-writing-transact-sql-statements"></a><span data-ttu-id="7928b-102">자습서: Transact-SQL 문 작성</span><span class="sxs-lookup"><span data-stu-id="7928b-102">Tutorial: Writing Transact-SQL Statements</span></span>
  <span data-ttu-id="7928b-103">[!INCLUDE[tsql](../includes/tsql-md.md)] 문 작성 자습서를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-103">Welcome to the Writing [!INCLUDE[tsql](../includes/tsql-md.md)] Statements tutorial.</span></span> <span data-ttu-id="7928b-104">이 자습서는 SQL 문을 처음 작성하는 사용자를 위해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-104">This tutorial is intended for users who are new to writing SQL statements.</span></span> <span data-ttu-id="7928b-105">이 자습서는 새로운 사용자가 테이블을 만들고 데이터를 삽입하는 몇 가지 기본 문을 통해 작업을 시작하는 데 도움이 될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-105">It will help new users get started by reviewing some basic statements for creating tables and inserting data.</span></span> <span data-ttu-id="7928b-106">이 자습서에서는 [!INCLUDE[tsql](../includes/tsql-md.md)]가 구현하는 SQL 표준인 [!INCLUDE[msCoName](../includes/msconame-md.md)] 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-106">This tutorial uses [!INCLUDE[tsql](../includes/tsql-md.md)], the [!INCLUDE[msCoName](../includes/msconame-md.md)] implementation of the SQL standard.</span></span> <span data-ttu-id="7928b-107">이 자습서는 [!INCLUDE[tsql](../includes/tsql-md.md)] 클래스를 대체하는 것이 아니라 [!INCLUDE[tsql](../includes/tsql-md.md)] 언어를 간략하게 소개하는 데 목적이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-107">This tutorial is intended as a brief introduction to the [!INCLUDE[tsql](../includes/tsql-md.md)] language and not as a replacement for a [!INCLUDE[tsql](../includes/tsql-md.md)] class.</span></span> <span data-ttu-id="7928b-108">의도적으로 간단한 문을 이 자습서에서 사용하고 있으므로 일반적인 프로덕션 데이터베이스에서 볼 수 있는 복잡한 문은 다루지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-108">The statements in this tutorial are intentionally simple, and are not meant to represent the complexity found in a typical production database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7928b-109">일반적으로 데이터베이스 초보 사용자는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 문을 작성하는 것보다 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 사용하여 [!INCLUDE[tsql](../includes/tsql-md.md)]에서 작업하는 것이 더 간편할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-109">Novice users of databases will usually find it easier to work with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], instead of writing [!INCLUDE[tsql](../includes/tsql-md.md)] statements.</span></span>  
  
## <a name="finding-more-information"></a><span data-ttu-id="7928b-110">추가 정보 찾기</span><span class="sxs-lookup"><span data-stu-id="7928b-110">Finding More Information</span></span>  
 <span data-ttu-id="7928b-111">특정 문에 대한 자세한 내용을 보려면 SQL Server 온라인 설명서에 이름으로 해당 문을 검색하거나 목차를 사용하여 [Transact-SQL 참조&#40;데이터베이스 엔진&#41;](/sql/t-sql/language-reference) 아래에 사전순으로 나열된 1,800개의 언어 요소를 찾아봅니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-111">To find more information about any specific statement, either search for the statement by name in SQL Server Books Online, or use the Contents to browse the 1,800 language elements listed alphabetically under [Transact-SQL Reference &#40;Database Engine&#41;](/sql/t-sql/language-reference).</span></span> <span data-ttu-id="7928b-112">또한 관심이 있는 주제와 관련된 키워드를 검색하는 것도 좋은 방법이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-112">Another good strategy for finding information is to search for key words that are related to the subject matter you are interested in.</span></span> <span data-ttu-id="7928b-113">예를 들어 월과 같은 날짜의 일부를 반환하는 방법을 보려면 **dates [SQL Server]** 의 색인을 검색한 다음 **dateparts**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-113">For example, if you want to know how to return a part of a date (such as the month), search the index for **dates [SQL Server]**, and then select **dateparts**.</span></span> <span data-ttu-id="7928b-114">이렇게 하면 [DATEPART&#40;Transact-SQL&#41;](/sql/t-sql/functions/datepart-transact-sql) 항목이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-114">This takes you to the topic [DATEPART &#40;Transact-SQL&#41;](/sql/t-sql/functions/datepart-transact-sql).</span></span> <span data-ttu-id="7928b-115">마찬가지로 문자열을 사용하는 방법을 보려면 **문자열 함수**를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-115">As another example, to find out how to work with strings, search for **string functions**.</span></span> <span data-ttu-id="7928b-116">이렇게 하면 [문자열 함수&#40;Transact-SQL&#41;](/sql/t-sql/functions/string-functions-transact-sql) 항목이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-116">This takes you to the topic [String Functions &#40;Transact-SQL&#41;](/sql/t-sql/functions/string-functions-transact-sql).</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="7928b-117">학습 내용</span><span class="sxs-lookup"><span data-stu-id="7928b-117">What You Will Learn</span></span>  
 <span data-ttu-id="7928b-118">이 자습서에서는 데이터베이스 작성, 데이터베이스에서 테이블 작성, 테이블에 데이터 삽입, 데이터 업데이트, 데이터 읽기, 데이터 삭제, 테이블 삭제 등을 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-118">This tutorial shows you how to create a database, create a table in the database, insert data into the table, update the data, read the data, delete the data, and then delete the table.</span></span> <span data-ttu-id="7928b-119">뷰와 저장 프로시저를 만들고 데이터베이스 및 데이터에 대해 사용자를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-119">You will create views and stored procedures and configure a user to the database and the data.</span></span>  
  
 <span data-ttu-id="7928b-120">이 자습서는 다음 3개의 단원으로 이루어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-120">This tutorial is divided into three lessons:</span></span>  
  
 [<span data-ttu-id="7928b-121">1단원: 데이터베이스 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="7928b-121">Lesson 1: Creating Database Objects</span></span>](lesson-1-creating-database-objects.md)  
 <span data-ttu-id="7928b-122">이 단원에서는 데이터베이스 작성, 데이터베이스에서 테이블 작성, 테이블에 데이터 삽입, 데이터 업데이트, 데이터 읽기 등을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-122">In this lesson, you create a database, create a table in the database, insert data into the table, update the data, and read the data.</span></span>  
  
 [<span data-ttu-id="7928b-123">2단원: 데이터베이스 개체에 대한 사용 권한 구성</span><span class="sxs-lookup"><span data-stu-id="7928b-123">Lesson 2: Configuring Permissions on Database Objects</span></span>](lesson-2-configuring-permissions-on-database-objects.md)  
 <span data-ttu-id="7928b-124">이 단원에서는 로그인 및 사용자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-124">In this lesson, you create a login and user.</span></span> <span data-ttu-id="7928b-125">또한 뷰와 저장 프로시저를 만든 다음 저장 프로시저에 대한 사용 권한을 사용자에게 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-125">You will also create a view and a stored procedure, and then grant the user permission to the stored procedure.</span></span>  
  
 [<span data-ttu-id="7928b-126">3단원: 데이터베이스 개체에 대한 액세스 권한 부여</span><span class="sxs-lookup"><span data-stu-id="7928b-126">Lesson 3: Deleting Database Objects</span></span>](lesson-3-1-deleting-database-objects.md)  
 <span data-ttu-id="7928b-127">이 단원에서는 데이터 액세스 권한 제거, 테이블에서 데이터 삭제, 테이블 삭제, 데이터베이스 삭제 등을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-127">In this lesson, you remove access to data, delete data from a table, delete the table, and then delete the database.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7928b-128">요구 사항</span><span class="sxs-lookup"><span data-stu-id="7928b-128">Requirements</span></span>  
 <span data-ttu-id="7928b-129">이 자습서를 완료하려면 SQL 언어를 알 필요가 없지만 테이블과 같은 기본 데이터베이스 개념을 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-129">To complete this tutorial, you do not have to know the SQL language, but you should understand basic database concepts such as tables.</span></span> <span data-ttu-id="7928b-130">이 자습서를 진행하는 동안 데이터베이스를 만들고 Windows 사용자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-130">During this tutorial, you will create a database and create a Windows user.</span></span> <span data-ttu-id="7928b-131">이러한 태스크를 수행하려면 높은 수준의 사용 권한이 필요하므로 컴퓨터에 관리자로 로그인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-131">These tasks require a high level of permissions; therefore, you should log in to the computer as an administrator.</span></span>  
  
 <span data-ttu-id="7928b-132">시스템에는 다음이 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-132">Your system must have the following installed:</span></span>  
  
-   <span data-ttu-id="7928b-133">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)](버전은 관계 없음)</span><span class="sxs-lookup"><span data-stu-id="7928b-133">Any edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="7928b-134">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 또는 Management Studio Express</span><span class="sxs-lookup"><span data-stu-id="7928b-134">Either [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or Management Studio Express.</span></span>  
  
-   <span data-ttu-id="7928b-135">Internet Explorer 6 이상</span><span class="sxs-lookup"><span data-stu-id="7928b-135">Internet Explorer 6 or later.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7928b-136">자습서를 검토할 때는 문서 뷰어 도구 모음에 **다음** 단추 및 **이전** 단추를 추가 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7928b-136">When you review the tutorials, we recommend that you add the **Next** and **Previous** buttons to the document viewer toolbar.</span></span>  
  
  
