---
title: 데이터베이스 만들기(자습서) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- tutorial creating a database
ms.assetid: e1e2c83f-dfad-4bb8-aa7a-09d3f69517ae
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 99d5439c289b5d4e71786d4c6734f158f6bba371
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652479"
---
# <a name="creating-a-database-tutorial"></a><span data-ttu-id="51eff-102">데이터베이스 만들기(자습서)</span><span class="sxs-lookup"><span data-stu-id="51eff-102">Creating a Database (Tutorial)</span></span>
  <span data-ttu-id="51eff-103">많은 [!INCLUDE[tsql](../includes/tsql-md.md)] 문과 마찬가지로 CREATE DATABASE 문에는 필수 매개 변수로 데이터베이스 이름이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51eff-103">Like many [!INCLUDE[tsql](../includes/tsql-md.md)] statements, the CREATE DATABASE statement has a required parameter: the name of the database.</span></span> <span data-ttu-id="51eff-104">또한 CREATE DATABASE에는 데이터베이스 파일을 저장할 디스크 위치와 같은 많은 선택적 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51eff-104">CREATE DATABASE also has many optional parameters, such as the disk location where you want to put the database files.</span></span> <span data-ttu-id="51eff-105">선택적 매개 변수 없이 CREATE DATABASE를 실행할 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 는 이러한 여러 매개 변수에 기본값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="51eff-105">When you execute CREATE DATABASE without the optional parameters, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] uses default values for many of these parameters.</span></span> <span data-ttu-id="51eff-106">이 자습서에서는 아주 약간의 선택적 구문 매개 변수만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="51eff-106">This tutorial uses very few of the optional syntax parameters.</span></span>  
  
### <a name="to-create-a-database"></a><span data-ttu-id="51eff-107">데이터베이스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="51eff-107">To create a database</span></span>  
  
1.  <span data-ttu-id="51eff-108">쿼리 편집기 창에서 다음 코드를 입력하되 실행하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51eff-108">In a Query Editor window, type but do not execute the following code:</span></span>  
  
    ```  
    CREATE DATABASE TestData  
    GO  
    ```  
  
2.  <span data-ttu-id="51eff-109">포인터를 사용하여 `CREATE DATABASE`단어를 선택한 다음 **F1**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="51eff-109">Use the pointer to select the words `CREATE DATABASE`, and then press **F1**.</span></span> <span data-ttu-id="51eff-110">SQL Server 온라인 설명서의 CREATE DATABASE 항목이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="51eff-110">The CREATE DATABASE topic in SQL Server Books Online should open.</span></span> <span data-ttu-id="51eff-111">이 기술을 사용하여 CREATE DATABASE 및 이 자습서에 사용되는 다른 문의 전체 구문을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51eff-111">You can use this technique to find the complete syntax for CREATE DATABASE and for the other statements that are used in this tutorial.</span></span>  
  
3.  <span data-ttu-id="51eff-112">쿼리 편집기에서 **F5** 키를 눌러 문을 실행하고 `TestData`라는 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51eff-112">In Query Editor, press **F5** to execute the statement and create a database named `TestData`.</span></span>  
  
 <span data-ttu-id="51eff-113">데이터베이스를 만들 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 는 **model** 데이터베이스의 복사본을 만들고 복사본의 이름을 데이터베이스 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="51eff-113">When you create a database, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] makes a copy of the **model** database, and renames the copy to the database name.</span></span> <span data-ttu-id="51eff-114">선택적 매개 변수로 데이터베이스의 처음 크기를 큰 값으로 지정하지 않은 경우 이 작업은 몇 초 내에 수행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eff-114">This operation should only take several seconds, unless you specify a large initial size of the database as an optional parameter.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="51eff-115">단일 일괄 처리에서 둘 이상의 문을 전송할 경우 GO 키워드는 문을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="51eff-115">The keyword GO separates statements when more than one statement is submitted in a single batch.</span></span> <span data-ttu-id="51eff-116">일괄 처리에 문이 하나만 포함된 경우 GO는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="51eff-116">GO is optional when the batch contains only one statement.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="51eff-117">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="51eff-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="51eff-118">테이블 만들기&#40;자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="51eff-118">Creating a Table &#40;Tutorial&#41;</span></span>](lesson-1-2-creating-a-table.md)  
  
## <a name="see-also"></a><span data-ttu-id="51eff-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="51eff-119">See Also</span></span>  
 [<span data-ttu-id="51eff-120">CREATE DATABASE&#40;SQL Server Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="51eff-120">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
  
