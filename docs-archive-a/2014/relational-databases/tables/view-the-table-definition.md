---
title: 테이블 정의 보기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- showing table properties
- displaying table properties
- tables [SQL Server], properties
- viewing table properties
ms.assetid: 1865fb7c-f480-4100-9007-df5364cd002a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 53170a78a104bfce4b4e4177015461f2eb9093e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661589"
---
# <a name="view-the-table-definition"></a><span data-ttu-id="dba62-102">테이블 정의 보기</span><span class="sxs-lookup"><span data-stu-id="dba62-102">View the Table Definition</span></span>
  <span data-ttu-id="dba62-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 테이블의 속성을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dba62-103">You can display properties for a table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="dba62-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="dba62-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="dba62-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="dba62-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="dba62-106">보안</span><span class="sxs-lookup"><span data-stu-id="dba62-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="dba62-107">**테이블 속성을 표시하려면**</span><span class="sxs-lookup"><span data-stu-id="dba62-107">**To display table properties, using:**</span></span>  
  
     [<span data-ttu-id="dba62-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="dba62-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="dba62-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="dba62-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="dba62-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="dba62-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="dba62-111">보안</span><span class="sxs-lookup"><span data-stu-id="dba62-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="dba62-112">권한</span><span class="sxs-lookup"><span data-stu-id="dba62-112">Permissions</span></span>  
 <span data-ttu-id="dba62-113">테이블을 소유하고 있거나 해당 테이블에 대한 권한을 부여 받은 경우에만 테이블의 속성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dba62-113">You can only see properties in a table if you either own the table or have been granted permissions to that table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="dba62-114">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="dba62-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-show-table-properties-in-the-properties-window"></a><span data-ttu-id="dba62-115">속성 창에 테이블 속성을 표시하려면</span><span class="sxs-lookup"><span data-stu-id="dba62-115">To show table properties in the Properties window</span></span>  
  
1.  <span data-ttu-id="dba62-116">개체 탐색기에서 속성을 표시하려는 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dba62-116">In Object Explorer, select the table for which you want to show properties.</span></span>  
  
2.  <span data-ttu-id="dba62-117">테이블을 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **속성** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dba62-117">Right-click the table and choose **Properties** from the shortcut menu.</span></span> <span data-ttu-id="dba62-118">자세한 내용은 [Table Properties](table-properties-ssms.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dba62-118">For more information, see [Table Properties](table-properties-ssms.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="dba62-119">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="dba62-119">Using Transact-SQL</span></span>  
  
#### <a name="to-show-table-properties"></a><span data-ttu-id="dba62-120">테이블 속성을 표시하려면</span><span class="sxs-lookup"><span data-stu-id="dba62-120">To show table properties</span></span>  
  
1.  <span data-ttu-id="dba62-121">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="dba62-121">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="dba62-122">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dba62-122">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="dba62-123">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dba62-123">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="dba62-124">다음 예에서는 지정된 개체에 대한 `sys.tables` 카탈로그 뷰의 모든 열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="dba62-124">The example returns all columns from the `sys.tables` catalog view for the specified object.</span></span>  
  
    ```  
    SELECT * FROM sys.tables  
    WHERE object_id = 1973582069;  
  
    ```  
  
 <span data-ttu-id="dba62-125">자세한 내용은 [sys.tables&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dba62-125">For more information, see [sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
