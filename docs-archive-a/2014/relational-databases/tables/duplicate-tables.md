---
title: 테이블 복제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- copying tables
- tables [SQL Server], duplicating
- duplicating tables
- table copying [SQL Server]
ms.assetid: c6b07423-d1e5-4e5e-8681-5088921f5df3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 793a38416f86a5b43a3e3bb2420127d7acf2af1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648913"
---
# <a name="duplicate-tables"></a><span data-ttu-id="03fac-102">테이블 복제</span><span class="sxs-lookup"><span data-stu-id="03fac-102">Duplicate Tables</span></span>
  <span data-ttu-id="03fac-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 사용하거나 [!INCLUDE[tsql](../../includes/tsql-md.md)] 을 사용하여 새 테이블을 만들고, 기존 테이블에서 열 정보를 복사하여 기존 테이블을 복제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03fac-103">You can duplicate an existing table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)] by creating a new table and then copying column information from an existing table.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="03fac-104">이 작업은 테이블의 구조만 복제하며 테이블 행은 복제하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="03fac-104">This operation duplicates only the structure of a table; it does not duplicate any table rows.</span></span>  
  
 <span data-ttu-id="03fac-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="03fac-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="03fac-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="03fac-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="03fac-107">보안</span><span class="sxs-lookup"><span data-stu-id="03fac-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="03fac-108">**테이블을 복제하려면**</span><span class="sxs-lookup"><span data-stu-id="03fac-108">**To duplicate a table, using:**</span></span>  
  
     [<span data-ttu-id="03fac-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="03fac-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="03fac-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="03fac-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="03fac-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="03fac-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="03fac-112">보안</span><span class="sxs-lookup"><span data-stu-id="03fac-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="03fac-113">권한</span><span class="sxs-lookup"><span data-stu-id="03fac-113">Permissions</span></span>  
 <span data-ttu-id="03fac-114">대상 데이터베이스에서 CREATE TABLE 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="03fac-114">Requires CREATE TABLE permission in the destination database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="03fac-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="03fac-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-duplicate-a-table"></a><span data-ttu-id="03fac-116">테이블을 복제하려면</span><span class="sxs-lookup"><span data-stu-id="03fac-116">To duplicate a table</span></span>  
  
1.  <span data-ttu-id="03fac-117">테이블을 만들려는 데이터베이스에 연결되어 있는지 확인한 다음 개체 탐색기에서 데이터베이스를 선택했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="03fac-117">Make sure you are connected to the database in which you want to create the table and that the database is selected in Object Explorer.</span></span>  
  
2.  <span data-ttu-id="03fac-118">개체 탐색기에서 **테이블** 을 마우스 오른쪽 단추로 클릭하고 **새 테이블**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="03fac-118">In Object Explorer, right-click **Tables** and click **New Table**.</span></span>  
  
3.  <span data-ttu-id="03fac-119">개체 탐색기에서 복사할 테이블을 마우스 오른쪽 단추로 클릭한 다음 **디자인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="03fac-119">In Object Explorer right-click the table you want to copy and click **Design**.</span></span>  
  
4.  <span data-ttu-id="03fac-120">기존 테이블에서 열을 선택하고 **편집** 메뉴에서 **복사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="03fac-120">Select the columns in the existing table and, from the **Edit** menu, click **Copy**.</span></span>  
  
5.  <span data-ttu-id="03fac-121">새 테이블로 전환하고 첫 번째 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="03fac-121">Switch back to the new table and select the first row.</span></span>  
  
6.  <span data-ttu-id="03fac-122">**편집** 메뉴에서 **붙여넣기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="03fac-122">From the **Edit** menu, click **Paste**.</span></span>  
  
7.  <span data-ttu-id="03fac-123">**파일** 메뉴에서 **저장**_table name_을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="03fac-123">From the **File** menu, click **Save**_table name_.</span></span>  
  
8.  <span data-ttu-id="03fac-124">**이름 선택** 대화 상자에서 새 테이블의 이름을 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="03fac-124">In the **Choose Name** dialog box, type a name for the new table and click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="03fac-125">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="03fac-125">Using Transact-SQL</span></span>  
  
#### <a name="to-duplicate-a-table-in-query-editor"></a><span data-ttu-id="03fac-126">쿼리 편집기에서 테이블을 복제하려면</span><span class="sxs-lookup"><span data-stu-id="03fac-126">To duplicate a table in Query Editor</span></span>  
  
1.  <span data-ttu-id="03fac-127">테이블을 만들려는 데이터베이스에 연결되어 있는지 확인한 다음 개체 탐색기에서 데이터베이스를 선택했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="03fac-127">Make sure you are connected to the database in which you want to create the table and that the database is selected in Object Explorer.</span></span>  
  
2.  <span data-ttu-id="03fac-128">복제하려는 테이블을 마우스 오른쪽 단추로 클릭하고 **테이블 스크립팅**을 가리킨 후 **CREATE**를 가리키고 **새 쿼리 편집기 창**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="03fac-128">Right-click the table you wish to duplicate, point to **Script Table as**, then point to **CREATE to**, and then select **New Query Editor Window**.</span></span>  
  
3.  <span data-ttu-id="03fac-129">테이블 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="03fac-129">Change the name of the table.</span></span>  
  
4.  <span data-ttu-id="03fac-130">새 테이블에 필요하지 않은 모든 열을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="03fac-130">Remove any columns that are not needed in the new table.</span></span>  
  
5.  <span data-ttu-id="03fac-131">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="03fac-131">Click **Execute**.</span></span>  
  
  
