---
title: 쿼리 변경 내용 취소(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- reverting queries
- queries [SQL Server], discarding changes
- discarding query changes
ms.assetid: 7bb17ece-1222-4622-b476-5789d7641c64
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9ec712f0a8a708db79d054833180776d604e58dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660270"
---
# <a name="discard-changes-made-to-queries-visual-database-tools"></a><span data-ttu-id="818fe-102">쿼리 변경 내용 취소(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="818fe-102">Discard Changes Made to Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="818fe-103">쿼리 정의에 대한 변경 내용을 저장하기 전에 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="818fe-103">You can discard changes made to a query definition prior to saving them.</span></span> <span data-ttu-id="818fe-104">이러한 변경 내용을 저장한 후에는 이전 상태로 되돌릴 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="818fe-104">Once they have been saved, they cannot be returned to a previous state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="818fe-105">결과 창에서 값에 대해 변경한 내용을 실행 취소하려면 레코드에서 포커스를 옮기기 전에 Esc 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="818fe-105">To undo a change you've made to values in the Results pane, press the ESC key before you move off of the record.</span></span> <span data-ttu-id="818fe-106">레코드에서 포커스를 옮길 때 변경 내용이 데이터베이스에 커밋되지 않는다는 메시지가 표시되는 경우에도 Esc 키를 눌러 이전 값을 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="818fe-106">If you move off of a record and receive a notice that the changes will not be committed to the database you can also press the ESC key to revert to the previous value.</span></span>  
  
### <a name="to-discard-changes-made-to-a-query-definition"></a><span data-ttu-id="818fe-107">쿼리 정의의 변경 내용을 취소하려면</span><span class="sxs-lookup"><span data-stu-id="818fe-107">To discard changes made to a query definition</span></span>  
  
1.  <span data-ttu-id="818fe-108">쿼리 및 뷰 디자이너에 쿼리가 열려 있는 상태로 **파일** 메뉴에서 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="818fe-108">With the query open in Query and View Designer, from the **File** menu, click **Close**.</span></span>  
  
2.  <span data-ttu-id="818fe-109">**Microsoft SQL Server Management Studio** 대화 상자에서 **아니요**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="818fe-109">In the **Microsoft SQL Server Management Studio** dialog box, click **No**.</span></span>  
  
     <span data-ttu-id="818fe-110">마지막 저장 상태로 쿼리 정의가 되돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="818fe-110">The query definition will return to the state it was in at the last save.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="818fe-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="818fe-111">See Also</span></span>  
 <span data-ttu-id="818fe-112">[Visual Database Tools를 &#40;쿼리 저장&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="818fe-112">[Save Queries &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="818fe-113">[쿼리 및 뷰 디자인 방법 도움말 항목 &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="818fe-113">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 <span data-ttu-id="818fe-114">[Visual Database Tools를 &#40;쿼리를 사용 하 여 기본 작업을 수행&#41;](perform-basic-operations-with-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="818fe-114">[Perform Basic Operations with Queries &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="818fe-115">결과 창에서 데이터 작업&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="818fe-115">Work with Data in the Results Pane &#40;Visual Database Tools&#41;</span></span>](results-pane-visual-database-tools.md)  
  
  
