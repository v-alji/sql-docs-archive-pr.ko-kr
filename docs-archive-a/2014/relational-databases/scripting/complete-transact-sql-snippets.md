---
title: Transact-SQL 코드 조각 완성
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [SQL Server], completing snippets
- snippets [Transact-SQL], completing
- Transact-SQL snippets, completing
ms.assetid: a8316a58-bb57-485e-845f-84c23360314c
author: rothja
ms.author: jroth
ms.openlocfilehash: d90c77f72ba8ce80d26503645d9b04d795f5e503
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649443"
---
# <a name="complete-transact-sql-snippets"></a><span data-ttu-id="eccbb-102">Transact-SQL 코드 조각 완성</span><span class="sxs-lookup"><span data-stu-id="eccbb-102">Complete Transact-SQL Snippets</span></span>
  <span data-ttu-id="eccbb-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] 코드 조각을 스크립트에 삽입한 후 코드 조각의 내용을 편집하여 완전한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eccbb-103">Once a [!INCLUDE[tsql](../../includes/tsql-md.md)] code snippet has been inserted into a script, you edit the contents of the snippet to build a complete [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
## <a name="completing-snippets"></a><span data-ttu-id="eccbb-104">코드 조각 완성</span><span class="sxs-lookup"><span data-stu-id="eccbb-104">Completing Snippets</span></span>  
 <span data-ttu-id="eccbb-105">[!INCLUDE[tsql](../../includes/tsql-md.md)] 코드 조각을 스크립트에 추가하면 삽입된 코드 조각 문에서 하나 이상의 대체 지점이 강조 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="eccbb-105">When you add a [!INCLUDE[tsql](../../includes/tsql-md.md)] snippet to your script, the inserted snippet statement has one or more replacement points, which are highlighted.</span></span> <span data-ttu-id="eccbb-106">마우스 포인터를 대체 지점에 놓으면 사용자가 지정할 수 있는 구문 요소에 대한 설명이 포함된 도구 설명이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="eccbb-106">If you rest your mouse pointer on a replacement point, a tooltip appears with a description of the syntax element you can specify.</span></span> <span data-ttu-id="eccbb-107">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기는 원본 파일을 닫기 전까지는 코드 조각을 주변 스크립트와는 별개로 인식합니다.</span><span class="sxs-lookup"><span data-stu-id="eccbb-107">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor recognizes the snippet as separate from the surrounding script until you close the source file.</span></span> <span data-ttu-id="eccbb-108">대체 지점은 원본 파일을 닫을 때까지 활성 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="eccbb-108">The replacement points remain active until you close the source file.</span></span>  
  
 <span data-ttu-id="eccbb-109">코드 조각을 통해 삽입된 템플릿 코드에 다른 구문 요소를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eccbb-109">You can also add additional syntax elements to the template code inserted by a snippet.</span></span> <span data-ttu-id="eccbb-110">예를 들어 Create Table 코드 조각 템플릿은 두 개의 열 정의를 생성합니다. 열이 둘 이상인 테이블을 만들려면 여기에 다른 열 정의를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eccbb-110">For example, the Create Table snippet template generates two column definitions; you must add additional column definitions to create a table with more than two columns.</span></span>  
  
#### <a name="completing-the-snippet-statement"></a><span data-ttu-id="eccbb-111">코드 조각 문 완성</span><span class="sxs-lookup"><span data-stu-id="eccbb-111">Completing the Snippet Statement</span></span>  
  
1.  <span data-ttu-id="eccbb-112">한 대체 지점에서 다음 대체 지점으로 이동하려면 Tab 키를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="eccbb-112">Use the TAB key to move from one replacement point to the next.</span></span> <span data-ttu-id="eccbb-113">이전 대체 지점으로 이동하려면 Shift+Tab을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="eccbb-113">Use SHIFT+TAB to move to the previous replacement point.</span></span>  
  
2.  <span data-ttu-id="eccbb-114">IntelliSense를 실행하려면 Ctrl+스페이스바를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="eccbb-114">Click CTRL+SPACE to invoke IntelliSense.</span></span>  
  
3.  <span data-ttu-id="eccbb-115">목록에서 항목을 선택하거나 원하는 대체 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="eccbb-115">Select an item from the list, or type a replacement of your choice.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eccbb-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eccbb-116">See Also</span></span>  
 <span data-ttu-id="eccbb-117">[Transact-SQL 코드 조각 삽입](insert-transact-sql-snippets.md) </span><span class="sxs-lookup"><span data-stu-id="eccbb-117">[Insert Transact-SQL Snippets](insert-transact-sql-snippets.md) </span></span>  
 [<span data-ttu-id="eccbb-118">코드 감싸기 Transact-SQL 조각 삽입</span><span class="sxs-lookup"><span data-stu-id="eccbb-118">Insert Surround-with Transact-SQL snippets</span></span>](insert-surround-with-transact-sql-snippets.md)  
  
  
