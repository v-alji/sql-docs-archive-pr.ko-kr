---
title: 중단점 위치 편집
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint location
ms.assetid: 5c28e411-0377-4210-a7ce-2a5c13dcdf74
author: rothja
ms.author: jroth
ms.openlocfilehash: 919e62d53d5c9e8898bf1d49c4b5e5aa4c0ed107
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638624"
---
# <a name="edit-a-breakpoint-location"></a><span data-ttu-id="add6e-102">중단점 위치 편집</span><span class="sxs-lookup"><span data-stu-id="add6e-102">Edit a Breakpoint Location</span></span>
  <span data-ttu-id="add6e-103">중단점 위치는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트 파일에서 중단점이 나오는 줄과 문자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="add6e-103">The breakpoint location specifies the line and character where the breakpoint resides in a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file.</span></span> <span data-ttu-id="add6e-104">중단점 위치를 편집하여 중단점을 스크립트의 다른 위치나 다른 스크립트로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="add6e-104">You can edit the breakpoint location to move the breakpoint to another location in the script, or to a different script.</span></span>  
  
## <a name="editing-a-location"></a><span data-ttu-id="add6e-105">위치 편집</span><span class="sxs-lookup"><span data-stu-id="add6e-105">Editing a Location</span></span>  
 <span data-ttu-id="add6e-106">중단점 위치를 편집하면 적중 횟수 또는 조건과 같은 모든 기존 속성과 함께 중단점이 새 위치로 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="add6e-106">When you edit a breakpoint location, the breakpoint moves to the new location, carrying with it all of the existing properties, such as a hit count or condition.</span></span>  
  
#### <a name="to-edit-a-breakpoint-location"></a><span data-ttu-id="add6e-107">중단점 위치를 편집하려면</span><span class="sxs-lookup"><span data-stu-id="add6e-107">To Edit a Breakpoint Location</span></span>  
  
1.  <span data-ttu-id="add6e-108">편집기 창에서 중단점 문자 모양을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **위치** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="add6e-108">In the editor window, right-click the breakpoint glyph, and then click **Location** on the shortcut menu.</span></span>  
  
     <span data-ttu-id="add6e-109">또는</span><span class="sxs-lookup"><span data-stu-id="add6e-109">-or-</span></span>  
  
     <span data-ttu-id="add6e-110">**중단점** 창에서 중단점 문자 모양을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **위치** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="add6e-110">In the **Breakpoints** window, right-click the breakpoint glyph, and then click **Location** on the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="add6e-111">**파일 중단점** 대화 상자에서 **파일** 을 편집하여 새 파일을 지정하거나 **줄** 을 편집하여 새 줄을 지정하거나 **문자** 를 편집하여 줄 내의 새 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="add6e-111">In the **File Breakpoint** dialog box, edit **File** to specify a new file, **Line** to specify a new line, or **Character** to specify a new location within the line.</span></span> <span data-ttu-id="add6e-112">지정한 새 파일이 쿼리 편집기 창에 이미 열려 있으면 중단점이 해당 편집기 창으로 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="add6e-112">If the new file you specify is already open in a query editor window, the breakpoint is moved to that editor window.</span></span> <span data-ttu-id="add6e-113">파일이 열려 있지 않으면 새 편집기 창이 열리고 파일이 로드된 후 중단점이 새 위치로 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="add6e-113">If the file is not opened, a new editor window is opened, the file is loaded in, and the breakpoint moved to the new location.</span></span>  
  
     <span data-ttu-id="add6e-114">**을 디버깅할 때는** 소스 코드가 원래 버전과 일치하지 않아도 됨 [!INCLUDE[tsql](../../includes/tsql-md.md)]옵션을 설정해도 아무 효과가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="add6e-114">The **Allow the source code to be different from the original version** option has no effect when debugging [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="add6e-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="add6e-115">See Also</span></span>  
 <span data-ttu-id="add6e-116">[적중 횟수 지정](specify-a-hit-count.md) </span><span class="sxs-lookup"><span data-stu-id="add6e-116">[Specify a Hit Count](specify-a-hit-count.md) </span></span>  
 <span data-ttu-id="add6e-117">[중단점 동작 지정](specify-a-breakpoint-action.md) </span><span class="sxs-lookup"><span data-stu-id="add6e-117">[Specify a Breakpoint Action](specify-a-breakpoint-action.md) </span></span>  
 <span data-ttu-id="add6e-118">[중단점 조건 지정](specify-a-breakpoint-condition.md) </span><span class="sxs-lookup"><span data-stu-id="add6e-118">[Specify a Breakpoint Condition](specify-a-breakpoint-condition.md) </span></span>  
 [<span data-ttu-id="add6e-119">중단점 필터 지정</span><span class="sxs-lookup"><span data-stu-id="add6e-119">Specify a Breakpoint Filter</span></span>](specify-a-breakpoint-filter.md)  
