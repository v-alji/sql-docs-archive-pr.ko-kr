---
title: 코드 감싸기 Transact-SQL 조각 삽입
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- snippets [Transact-SQL], surround with
- IntelliSense [SQL Server], surround with snippets
- Transact-SQL snippets, surround with
ms.assetid: 5b5a8c6c-968e-4361-a7f5-9e2ac186d927
author: rothja
ms.author: jroth
ms.openlocfilehash: 773019ad338664de3092138758e07ee3730833bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660484"
---
# <a name="insert-surround-with-transact-sql-snippets"></a><span data-ttu-id="37cdb-102">코드 감싸기 Transact-SQL 조각 삽입</span><span class="sxs-lookup"><span data-stu-id="37cdb-102">Insert Surround-with Transact-SQL snippets</span></span>
  <span data-ttu-id="37cdb-103">코드 감싸기 조각은 일련의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 BEGIN, IF 또는 WHILE 블록으로 묶을 때 시작 지점으로 사용할 수 있는 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="37cdb-103">A surround-with snippet is a template you can use as a starting point when enclosing a set of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in a BEGIN, IF, or WHILE block.</span></span>  
  
## <a name="inserting-surround-with-snippets"></a><span data-ttu-id="37cdb-104">코드 감싸기 조각 삽입</span><span class="sxs-lookup"><span data-stu-id="37cdb-104">Inserting Surround-with Snippets</span></span>  
 <span data-ttu-id="37cdb-105">코드 감싸기 조각은 바로 가기 키, **편집** 메뉴 및 상황에 맞는 메뉴의 세 가지 방법 중 하나로 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37cdb-105">Surround-with snippets can be launched by one of three ways: through a keyboard shortcut, through the **Edit** menu, and through the context menu.</span></span>  
  
 <span data-ttu-id="37cdb-106">코드 조각을 삽입한 후에는 올바른 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문이 되도록 대체 텍스트를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37cdb-106">After inserting the snippet, you must change the replacement text to form a valid [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="37cdb-107">자세한 내용은 [Transact-SQL 코드 조각 완성](complete-transact-sql-snippets.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="37cdb-107">For more information, see [Complete Transact-SQL Snippets](complete-transact-sql-snippets.md).</span></span>  
  
#### <a name="to-insert-a-surround-with-snippet"></a><span data-ttu-id="37cdb-108">코드 감싸기 조각을 삽입하려면</span><span class="sxs-lookup"><span data-stu-id="37cdb-108">To insert a surround-with snippet</span></span>  
  
1.  <span data-ttu-id="37cdb-109">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기 창에서 블록에 포함할 일련의 문을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="37cdb-109">In the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window, select the set of statements to be included in the block.</span></span>  
  
2.  <span data-ttu-id="37cdb-110">다음 세 가지 방법 중 하나를 사용하여 코드 감싸기 조각 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="37cdb-110">Use one of these three methods to display the list of surround-with snippets:</span></span>  
  
    -   <span data-ttu-id="37cdb-111">Ctrl+K, Ctrl+S를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="37cdb-111">Type CTRL+K, CTRL+S.</span></span>  
  
    -   <span data-ttu-id="37cdb-112">**편집** 메뉴에서 **IntelliSense**를 가리킨 다음 **코드 감싸기** 명령을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="37cdb-112">From the **Edit** menu, point to **IntelliSense**, and then select the **Surround With** command.</span></span>  
  
    -   <span data-ttu-id="37cdb-113">선택한 텍스트를 마우스 오른쪽 단추로 클릭한 다음 상황에 맞는 메뉴에서 **코드 감싸기** 명령을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="37cdb-113">Right-click the selected text, and then select the **Surround With** command from the context menu.</span></span>  
  
3.  <span data-ttu-id="37cdb-114">마우스를 사용하거나 코드 조각 이름을 입력하고 Tab 키 또는 Enter 키를 눌러 목록에서 코드 조각(BEGIN, IF 또는 WHILE)의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="37cdb-114">Select the name of the snippet (BEGIN, IF, or WHILE) from the list either by using the mouse, or by typing the name of the snippet and pressing TAB or ENTER.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37cdb-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="37cdb-115">See Also</span></span>  
 [<span data-ttu-id="37cdb-116">Transact-SQL 코드 조각 삽입</span><span class="sxs-lookup"><span data-stu-id="37cdb-116">Insert Transact-SQL Snippets</span></span>](insert-transact-sql-snippets.md)  
  
  
