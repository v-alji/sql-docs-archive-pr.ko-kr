---
title: SQL 편집기(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.sqleditor
helpviewer_keywords:
- SQL Editor
- modifying triggers
- modifying functions
- modifying stored procedures
- modifying statements
- Query Designer [SQL Server], SQL Editor
- View Designer, SQL Editor
ms.assetid: 029abf7d-6414-47ca-a3a7-b3a057efb6c2
author: stevestein
ms.author: sstein
ms.openlocfilehash: bf3d69608e8508fcc314fe67315de86da98ed53f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735803"
---
# <a name="sql-editor-visual-database-tools"></a><span data-ttu-id="913c4-102">SQL 편집기(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="913c4-102">SQL Editor (Visual Database Tools)</span></span>
  <span data-ttu-id="913c4-103">SQL 편집기를 사용하면 기존의 저장 프로시저, 함수, 트리거 및 SQL 스크립트를 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="913c4-103">Use the SQL Editor to edit existing stored procedures, functions, triggers, and SQL scripts.</span></span> <span data-ttu-id="913c4-104">이러한 개체 중 하나를 열면 이 창이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="913c4-104">This window opens when you open any of those objects.</span></span> <span data-ttu-id="913c4-105">데이터 원본에 대해 실행할 새 SQL 문을 만들려면 쿼리 디자이너의 [SQL 창](visual-database-tools.md) 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="913c4-105">If you want to create a new SQL statement to run against your data source, use the [SQL Pane](visual-database-tools.md) of Query Designer.</span></span>  
  
 <span data-ttu-id="913c4-106">SQL 편집기는 다음과 같이 다양하고 유용한 SQL 텍스트 편집 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="913c4-106">The SQL editor provides many useful SQL text-editing features, including:</span></span>  
  
-   <span data-ttu-id="913c4-107">구문 및 맞춤법 오류를 최소화하기 위해 SQL 키워드의 색을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="913c4-107">Color coding of SQL keywords to minimize syntax and spelling errors.</span></span>  
  
-   <span data-ttu-id="913c4-108">기초 저장 프로시저 및 트리거를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="913c4-108">Generating skeletal stored procedures and triggers.</span></span>  
  
-   <span data-ttu-id="913c4-109">잘라내기, 복사, 붙여넣기 및 끌기 작업을 포함한 유용한 편집 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="913c4-109">Providing useful editing functions, including cut, copy, paste, and dragging operations.</span></span>  
  
-   <span data-ttu-id="913c4-110">**도구** 메뉴에서 **옵션** 을 선택해서 편집기의 동작을 변경하여 가상 공간, 자동 줄 바꿈, 줄 번호 및 탭 크기를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="913c4-110">Changing the editor's behavior (by selecting **Options** from the **Tools** menu) to modify virtual spaces, word wrap, line numbers, and tab size.</span></span>  
  
-   <span data-ttu-id="913c4-111">디버깅 중단점에 대한 관리를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="913c4-111">Helping manage debugging breakpoints.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="913c4-112">SQL 편집기에서는 IntelliSense 기능을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="913c4-112">The SQL Editor does not have IntelliSense prompting.</span></span>  
  
 <span data-ttu-id="913c4-113">SQL 문을 편집할 때 특정 Transact-SQL 문은 얇은 선으로 둘러싸인 상자 안에 들어갑니다.</span><span class="sxs-lookup"><span data-stu-id="913c4-113">When editing SQL statements, certain Transact-SQL statements are enclosed in a box surrounded by a thin line.</span></span> <span data-ttu-id="913c4-114">이로 인해 SQL 코드를 명령 섹션으로 분할하고, 쿼리 디자이너를 사용하여 그래픽으로 디자인할 수 있는 SQL 문 블록을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="913c4-114">This helps to visually break the SQL code into command sections, and identifies blocks of SQL statements that can be graphically designed using Query Designer.</span></span> <span data-ttu-id="913c4-115">쿼리 디자이너 사용에 대한 자세한 내용은 [쿼리 및 뷰 디자인 방법 도움말 항목&#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="913c4-115">For more information on using Query Designer, see [Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="913c4-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="913c4-116">See Also</span></span>  
 [<span data-ttu-id="913c4-117">쿼리 및 뷰 디자인 방법 도움말 항목&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="913c4-117">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
