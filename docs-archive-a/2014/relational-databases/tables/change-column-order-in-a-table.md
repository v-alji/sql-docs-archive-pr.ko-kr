---
title: 테이블에서 열 순서 변경 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], change order in a table
- column order, change
ms.assetid: cd99ef56-9085-431a-a0fc-58e7add5399f
author: stevestein
ms.author: sstein
ms.openlocfilehash: d162f9dc793ceb9ea423d94922f7358f1729712e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650878"
---
# <a name="change-column-order-in-a-table"></a><span data-ttu-id="3d680-102">테이블에서 열 순서 변경</span><span class="sxs-lookup"><span data-stu-id="3d680-102">Change Column Order in a Table</span></span>
  <span data-ttu-id="3d680-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 테이블 디자이너에서 열 순서를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d680-103">You can change the order of columns in Table Designer in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="3d680-104">테이블의 열 순서를 변경하면 특정 열 순서에 의존하는 코드나 애플리케이션에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d680-104">Changing the column order of a table may affect code and applications that depend on the specific order of columns.</span></span> <span data-ttu-id="3d680-105">여기에는 쿼리, 뷰, 저장 프로시저, 사용자 정의 함수, 클라이언트 애플리케이션 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d680-105">These include queries, views, stored procedures, user-defined functions, and client applications.</span></span> <span data-ttu-id="3d680-106">따라서 열 순서를 변경할 때는 이러한 결과를 미리 신중하게 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d680-106">Carefully consider any changes you want to make to column order before making it.</span></span> <span data-ttu-id="3d680-107">가장 좋은 방법은 애플리케이션 및 쿼리 수준에서 반환된 열에서 순서를 지정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3d680-107">Best practice is to specify the order in which the columns are returned at the application and query level.</span></span> <span data-ttu-id="3d680-108">SELECT \*를 사용해도 테이블에 정의된 순서에 따라 모든 열이 순서대로 반환된다고 가정해서는 안됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d680-108">You should not rely on the use of SELECT \* to return all columns in an expected order based on the order in which they are defined in the table.</span></span> <span data-ttu-id="3d680-109">항상 열을 표시하려는 순서에 따라 쿼리 및 애플리케이션에서 이름으로 열을 지정하세요.</span><span class="sxs-lookup"><span data-stu-id="3d680-109">Always specify the columns by name in your queries and applications in the order in which you would like them to appear.</span></span>  
  
 <span data-ttu-id="3d680-110">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="3d680-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3d680-111">**열 순서를 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="3d680-111">**To change the column order, using:**</span></span>  
  
     [<span data-ttu-id="3d680-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3d680-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="3d680-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3d680-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3d680-114">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="3d680-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-the-column-order"></a><span data-ttu-id="3d680-115">열 순서를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="3d680-115">To change the column order</span></span>  
  
1.  <span data-ttu-id="3d680-116">**개체 탐색기**에서 순서를 바꾸려는 열이 있는 테이블을 마우스 오른쪽 단추로 클릭하고 **디자인**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3d680-116">In **Object Explorer**, right-click the table with columns you want to reorder and click **Design**.</span></span>  
  
2.  <span data-ttu-id="3d680-117">순서를 바꾸려는 열 이름의 왼쪽에 있는 상자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3d680-117">Select the box to the left of the column name that you want to reorder.</span></span>  
  
3.  <span data-ttu-id="3d680-118">테이블 내에 다른 위치로 열을 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="3d680-118">Drag the column to another location within the table.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3d680-119">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="3d680-119">Using Transact-SQL</span></span>  
 <span data-ttu-id="3d680-120">**열 순서를 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="3d680-120">**To change the column order**</span></span>  
  
 <span data-ttu-id="3d680-121">이 작업은 Transact-SQL 문을 사용하여 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3d680-121">This task cannot be performed using Transact-SQL statements.</span></span>  
  
###  <a name="TsqlExample"></a>  
