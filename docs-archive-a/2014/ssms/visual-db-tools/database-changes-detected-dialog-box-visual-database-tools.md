---
title: 데이터베이스 변경 감지 대화 상자(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.schema.databasechangesdetected
- vdtsql.chm:65543
- vdtsql.chm:65554
ms.assetid: 91f13086-371f-46a2-9f46-804c1415f3ed
author: stevestein
ms.author: sstein
ms.openlocfilehash: 91d58e812b93f207d592d245d094b0fbeddcce72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731252"
---
# <a name="database-changes-detected-dialog-box-visual-database-tools"></a><span data-ttu-id="6e2f0-102">데이터베이스 변경 감지 대화 상자(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6e2f0-102">Database Changes Detected Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="6e2f0-103">이 대화 상자는 데이터베이스 다이어그램이나 선택된 테이블을 저장하려 하지만 저장 동작이 적용되는 일부 데이터베이스 개체가 최신 상태가 아닌 경우에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="6e2f0-103">This dialog appears if you attempt to save a database diagram or selected tables but some of the database objects that will be affected by the save action are out of date with the database.</span></span> <span data-ttu-id="6e2f0-104">이 대화 상자에 표시되는 변경 내용을 적용하면 데이터베이스가 다이어그램과 일치하도록 업데이트되고 다른 사용자의 변경 내용을 덮어쓰게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e2f0-104">Accepting the changes shown in this dialog box updates the database to match your diagram and overwrites other users' changes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6e2f0-105">테이블이나 데이터베이스 다이어그램에 적용된 변경 내용을 실행 취소할 수는 없지만 테이블이나 다이어그램을 저장하기 전까지는 변경 내용이 데이터베이스에 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e2f0-105">Although you cannot undo changes made to a table or database diagram, the changes are not saved to the database until you save the table or diagram.</span></span> <span data-ttu-id="6e2f0-106">**아니요** 를 선택하고 모든 열려 있는 다이어그램을 저장하지 않은 채 닫으면 저장되지 않은 변경 내용을 모두 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e2f0-106">You can discard any unsaved changes by choosing **No** and closing all open diagrams without saving them.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6e2f0-107">옵션</span><span class="sxs-lookup"><span data-stu-id="6e2f0-107">Options</span></span>  
 <span data-ttu-id="6e2f0-108">**차이점 발견 경고**</span><span class="sxs-lookup"><span data-stu-id="6e2f0-108">**Warn about difference detection**</span></span>  
 <span data-ttu-id="6e2f0-109">이후에 데이터베이스 다이어그램이나 선택된 테이블을 저장하려 할 때 이 대화 상자를 표시할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6e2f0-109">Specify whether this dialog box appears the next time you attempt to save a database diagram or selected tables.</span></span> <span data-ttu-id="6e2f0-110">이 옵션을 선택하면 오래된 다이어그램이나 테이블을 데이터베이스와 함께 저장하려 할 때마다 이 대화 상자가 계속하여 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="6e2f0-110">Checked means that the dialog box continues to appear each time you save a diagram or table that is out of date with the database.</span></span> <span data-ttu-id="6e2f0-111">이 옵션을 해제하면 대화 상자가 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e2f0-111">Unchecked means that the dialog box does not appear.</span></span> <span data-ttu-id="6e2f0-112">이 확인란은 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e2f0-112">By default, this box is checked.</span></span> <span data-ttu-id="6e2f0-113">이 옵션이 해제되어 있는 경우 **옵션** 대화 상자에서 다시 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e2f0-113">If you uncheck this option, you can recheck it in the **Options** dialog box.</span></span>  
  
 <span data-ttu-id="6e2f0-114">**예**</span><span class="sxs-lookup"><span data-stu-id="6e2f0-114">**Yes**</span></span>  
 <span data-ttu-id="6e2f0-115">목록에 표시된 모든 변경 내용으로 데이터베이스를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="6e2f0-115">Update the database with all the changes shown in the list.</span></span>  
  
 <span data-ttu-id="6e2f0-116">**아니요**</span><span class="sxs-lookup"><span data-stu-id="6e2f0-116">**No**</span></span>  
 <span data-ttu-id="6e2f0-117">저장 동작을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="6e2f0-117">Cancel the save action.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6e2f0-118">데이터베이스에 일치하도록 다이어그램을 새로 고치려면 변경 내용을 저장하지 않은 상태로 다이어그램을 닫고 서버 탐색기에서 다이어그램을 마우스 오른쪽 단추로 클릭한 다음 새로 고침을 클릭하고 다이어그램을 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6e2f0-118">To refresh your diagram to match the database, close it without saving changes, right-click the diagram in Server Explorer and click Refresh, and then reopen the diagram.</span></span>  
  
 <span data-ttu-id="6e2f0-119">**텍스트 파일 저장**</span><span class="sxs-lookup"><span data-stu-id="6e2f0-119">**Save Text File**</span></span>  
 <span data-ttu-id="6e2f0-120">**다른 이름으로 저장** 대화 상자가 나타납니다. 이 대화 상자를 사용하면 데이터베이스 변경 내용 목록이 포함된 텍스트 파일의 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e2f0-120">Display the **Save As** dialog box, letting you specify a location for a text file containing a list of the database changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e2f0-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6e2f0-121">See Also</span></span>  
 <span data-ttu-id="6e2f0-122">[Visual Database Tools를 사용 하 &#40;수정 된 데이터베이스를 사용 하 여 데이터베이스 다이어그램 조정&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6e2f0-122">[Reconcile a Database Diagram with a Modified Database &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="6e2f0-123">다중 사용자 환경&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="6e2f0-123">Multiuser Environments &#40;Visual Database Tools&#41;</span></span>](multiuser-environments-visual-database-tools.md)  
  
  
