---
title: Transact-SQL 코드 조각 삽입
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [SQL Server], snippets
- Transact-SQL snippets, code
- snippets [Transact-SQL], how to insert
ms.assetid: d66c96f4-2e84-4d79-9bfd-3635fdd98425
author: rothja
ms.author: jroth
ms.openlocfilehash: 26a7a224e700c726ee3d4437321843d45ddb6e44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660483"
---
# <a name="insert-transact-sql-snippets"></a><span data-ttu-id="dcc11-102">Transact-SQL 코드 조각 삽입</span><span class="sxs-lookup"><span data-stu-id="dcc11-102">Insert Transact-SQL Snippets</span></span>
  <span data-ttu-id="dcc11-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] 코드 조각은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리 편집기에서 새 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 문을 작성할 때 시작 지점으로 사용할 수 있는 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="dcc11-103">A [!INCLUDE[tsql](../../includes/tsql-md.md)] code snippet is a template you can use as a starting point when writing new [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span>  
  
## <a name="inserting-snippets"></a><span data-ttu-id="dcc11-104">조각 삽입</span><span class="sxs-lookup"><span data-stu-id="dcc11-104">Inserting Snippets</span></span>  
 <span data-ttu-id="dcc11-105">**조각 삽입** 메뉴를 사용하여 범주별로 분류된 조각 목록을 열고 이 목록에서 조각을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcc11-105">You can use the **Insert Snippet** menu to open a categorized list of snippets to choose from.</span></span>  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="dcc11-106">조각에는 해당 지점과 관련된 구문을 제안하는 텍스트인 대체 지점이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcc11-106">snippets contain replacement points: text that suggests the syntax relevant to that point.</span></span> <span data-ttu-id="dcc11-107">예를 들어 CREATE TABLE 조각에는 테이블 이름, 열 이름, 열 데이터 형식 등의 요소에 대한 대체 지점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcc11-107">For example, the CREATE TABLE snippet has replacement points for elements such as the table name, column names, and column data types.</span></span> <span data-ttu-id="dcc11-108">코드 조각을 삽입한 후에는 올바른 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문이 되도록 대체 텍스트를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcc11-108">After inserting the snippet, you must change the replacement text to form a valid [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="dcc11-109">자세한 내용은 [Transact-SQL 코드 조각 완성](complete-transact-sql-snippets.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dcc11-109">For more information, see [Complete Transact-SQL Snippets](complete-transact-sql-snippets.md).</span></span>  
  
#### <a name="inserting-a-snippet-by-using-the-insert-snippet-menu"></a><span data-ttu-id="dcc11-110">조각 삽입 메뉴를 사용하여 조각 삽입</span><span class="sxs-lookup"><span data-stu-id="dcc11-110">Inserting a Snippet by Using the Insert Snippet Menu</span></span>  
  
1.  <span data-ttu-id="dcc11-111">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기 창에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 조각을 삽입할 위치에 커서를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="dcc11-111">In the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window, put the cursor where you want to insert the [!INCLUDE[tsql](../../includes/tsql-md.md)] snippet.</span></span>  
  
2.  <span data-ttu-id="dcc11-112">다음 세 가지 방법 중 하나로 조각 선택 도구 설명을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="dcc11-112">Launch the snippet picker tooltip in one of three ways:</span></span>  
  
    -   <span data-ttu-id="dcc11-113">Ctrl+K, Ctrl+X를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="dcc11-113">Press CTRL+K, CTRL+X.</span></span>  
  
    -   <span data-ttu-id="dcc11-114">**편집** 메뉴에서 **IntelliSense**를 가리킨 다음 **조각 삽입**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dcc11-114">On the **Edit** menu, point to **IntelliSense**, then click **Insert Snippet**.</span></span>  
  
    -   <span data-ttu-id="dcc11-115">마우스 오른쪽 단추를 클릭한 다음 바로 가기 메뉴에서 **조각 삽입** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dcc11-115">Right-click the mouse and then select the **Insert Snippet** command from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="dcc11-116">조각을 두 번 클릭하거나 조각 선택에서 조각을 선택하고 Tab 키 또는 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="dcc11-116">Double-click the snippet, or select the snippet from the snippet picker and then press TAB or ENTER.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcc11-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dcc11-117">See Also</span></span>  
 [<span data-ttu-id="dcc11-118">코드 감싸기 Transact-SQL 조각 삽입</span><span class="sxs-lookup"><span data-stu-id="dcc11-118">Insert Surround-with Transact-SQL snippets</span></span>](insert-surround-with-transact-sql-snippets.md)  
  
  
