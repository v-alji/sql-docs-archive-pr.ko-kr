---
title: 통계 이름 바꾸기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- renaming statistics
- statistics [SQL Server], renaming
ms.assetid: a3bed7b7-3dc5-4b33-b1c6-67c27f573764
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1528dcec50a662524531065d597b004fe7f59e5f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659879"
---
# <a name="rename-statistics"></a><span data-ttu-id="9f969-102">통계 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="9f969-102">Rename Statistics</span></span>
  <span data-ttu-id="9f969-103">다음을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 통계 개체의 이름을 바꾸려면 사용합니다. [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f969-103">You can rename a statistics object in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
  
 <span data-ttu-id="9f969-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="9f969-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9f969-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="9f969-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9f969-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="9f969-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="9f969-107">보안</span><span class="sxs-lookup"><span data-stu-id="9f969-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9f969-108">**다음을 사용하여 통계 개체의 이름을 바꾸려면**</span><span class="sxs-lookup"><span data-stu-id="9f969-108">**To rename a statistics object, using:**</span></span>  
  
     [<span data-ttu-id="9f969-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9f969-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9f969-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="9f969-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="9f969-111">제한 사항</span><span class="sxs-lookup"><span data-stu-id="9f969-111">Limitations and Restrictions</span></span>  
 <span data-ttu-id="9f969-112">기본적으로 인덱스를 만들면 해당 인덱스의 키 열에 통계가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="9f969-112">By default, creating an index creates a statistic on the key columns of that index.</span></span> <span data-ttu-id="9f969-113">따라서 색인의 이름을 바꿀 경우 통계 개체의 이름이 자동으로 바뀌고 그 반대의 경우에도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="9f969-113">Therefore, renaming the index automatically renames the statistics object, and vice versa.</span></span>  
  
 <span data-ttu-id="9f969-114">개체 이름의 일부를 변경하면 스크립트나 저장 프로시저가 작동되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f969-114">Changing any part of an object name can break scripts and stored procedures.</span></span> <span data-ttu-id="9f969-115">이름을 바꾸는 것보다 통계 개체를 삭제하고 새로운 이름으로 다시 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9f969-115">Instead of renaming, we recommend that you drop the statistics object and re-create it with the new name.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9f969-116">보안</span><span class="sxs-lookup"><span data-stu-id="9f969-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9f969-117">권한</span><span class="sxs-lookup"><span data-stu-id="9f969-117">Permissions</span></span>  
 <span data-ttu-id="9f969-118">테이블이나 뷰에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9f969-118">Requires ALTER permission on the table or view.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9f969-119">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="9f969-119">Using Transact-SQL</span></span>  
  
#### <a name="to-rename-a-statistics-object"></a><span data-ttu-id="9f969-120">통계 개체의 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="9f969-120">To rename a statistics object</span></span>  
  
1.  <span data-ttu-id="9f969-121">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9f969-121">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9f969-122">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9f969-122">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9f969-123">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9f969-123">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_rename N'AK_Employee_LoginID', N'AK_Emp_Login', N'STATISTICS';   
    GO  
    ```  
  
 <span data-ttu-id="9f969-124">자세한 내용은 [sp_rename&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9f969-124">For more information, see [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql).</span></span>  
  
  
