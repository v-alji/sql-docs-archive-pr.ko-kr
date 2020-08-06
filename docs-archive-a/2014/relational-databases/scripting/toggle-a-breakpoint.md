---
title: 중단점 설정/해제
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c477ab89-a1cd-4f2c-aa7c-40525041100f
author: rothja
ms.author: jroth
ms.openlocfilehash: 72e26e9b1d04bc2eced6bcb6d93d3c86a016d308
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653794"
---
# <a name="toggle-a-breakpoint"></a><span data-ttu-id="f65a7-102">중단점 설정/해제</span><span class="sxs-lookup"><span data-stu-id="f65a7-102">Toggle a Breakpoint</span></span>
  <span data-ttu-id="f65a7-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] 문에 중단점을 설정하는 작업을 중단점 설정/해제라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f65a7-103">The act of setting a breakpoint on a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is called toggling a breakpoint.</span></span>  
  
## <a name="breakpoints"></a><span data-ttu-id="f65a7-104">중단점</span><span class="sxs-lookup"><span data-stu-id="f65a7-104">Breakpoints</span></span>  
 <span data-ttu-id="f65a7-105">중단점이 설정되면 문 왼쪽에 있는 회색 막대에서 아이콘으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f65a7-105">Once the breakpoint has been set, it is represented by an icon in the grey bar to the left of the statement.</span></span> <span data-ttu-id="f65a7-106">이 아이콘을 중단점 문자 모양이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f65a7-106">The icon is called a breakpoint glyph.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="f65a7-107">중단점은 완전한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f65a7-107">breakpoints are applied to a complete [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="f65a7-108">중단점을 설정/해제하면 디버거는 관련 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f65a7-108">When a breakpoint is toggled on, the debugger highlights the associated [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
 <span data-ttu-id="f65a7-109">한 줄에 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문이 여러 개 있는 경우 각 문에 대해 중단점을 설정/해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f65a7-109">If there are multiple [!INCLUDE[tsql](../../includes/tsql-md.md)] statements on a line, you can toggle a breakpoint for each statement.</span></span> <span data-ttu-id="f65a7-110">창 왼쪽에 있는 회색 막대를 클릭하면 줄의 첫 번째 문에서 중단점이 설정/해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="f65a7-110">Clicking in the grey bar on the left of the window toggles a breakpoint on the first statement on the line.</span></span> <span data-ttu-id="f65a7-111">다음 문의 아무 부분이나 강조 표시하거나 커서를 다음 문으로 이동한 후 F9 키를 누르거나 **디버그** 메뉴에서 **중단점 설정/해제** 를 클릭하여 다음 문에서 중단점을 설정/해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f65a7-111">You can toggle a breakpoint in a subsequent statement by highlighting any part of the statement, or moving the cursor into the statement, and then either pressing F9 or clicking **Toggle Breakpoint** on the **Debug** menu.</span></span> <span data-ttu-id="f65a7-112">한 줄에 중단점이 여러 개 있더라도 왼쪽의 회색 막대에는 중단점 문자 모양이 하나만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f65a7-112">If you have multiple breakpoints on a line, there is only one breakpoint glyph in the grey bar on the left.</span></span>  
  
 <span data-ttu-id="f65a7-113">중단점을 설정/해제한 후 중단점에 대한 다양한 동작(예: 중단점 속성 편집, 중단점 일시 해제)을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f65a7-113">After a breakpoint has been toggled, you can perform various actions on the breakpoint, such as editing its properties or temporarily disabling it.</span></span> <span data-ttu-id="f65a7-114">자세한 내용은 [Transact-SQL 중단점](transact-sql-breakpoints.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f65a7-114">For more information, see [Transact-SQL Breakpoints](transact-sql-breakpoints.md).</span></span>  
  
## <a name="toggle-a-breakpoint"></a><span data-ttu-id="f65a7-115">중단점 설정/해제</span><span class="sxs-lookup"><span data-stu-id="f65a7-115">Toggle a Breakpoint</span></span>  
 <span data-ttu-id="f65a7-116">**Transact-SQL 문에서 중단점을 설정/해제하려면**</span><span class="sxs-lookup"><span data-stu-id="f65a7-116">**To toggle a breakpoint on a Transact-SQL statement**</span></span>  
  
1.  <span data-ttu-id="f65a7-117">[!INCLUDE[tsql](../../includes/tsql-md.md)] 문 왼쪽에 있는 회색 막대를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f65a7-117">Click the gray bar to the left side of the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
2.  <span data-ttu-id="f65a7-118">또는 문의 일부를 강조 표시하거나 커서를 문으로 이동한 후 다음 중 하나의 동작을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f65a7-118">Alternatively, either highlight any part of the statement or move the cursor to the statement, and then perform either action:</span></span>  
  
    -   <span data-ttu-id="f65a7-119">F9 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="f65a7-119">Press F9.</span></span>  
  
    -   <span data-ttu-id="f65a7-120">**디버그** 메뉴에서 **중단점 설정/해제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f65a7-120">On the **Debug** menu, click **Toggle Breakpoint**.</span></span>  
  
  
