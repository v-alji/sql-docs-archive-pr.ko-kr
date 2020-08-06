---
title: 명령 창
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Command Window [Transact-SQL]
ms.assetid: e567ebf9-0793-451b-92c7-26193a02d9da
author: rothja
ms.author: jroth
ms.openlocfilehash: c766ed5408de96b6a2305ce377f9031947618a7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659919"
---
# <a name="command-window"></a><span data-ttu-id="b91ff-102">명령 창</span><span class="sxs-lookup"><span data-stu-id="b91ff-102">Command Window</span></span>
  <span data-ttu-id="b91ff-103">**명령 창** 을 사용하여 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 쿼리 편집기 창에서 현재 디버깅 중인 코드에 디버그 및 편집 명령과 같은 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b91ff-103">Use the **CommandWindow** to run commands, such as debug and edit commands, against the code in the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] Query Editor window that is currently being debugged.</span></span> <span data-ttu-id="b91ff-104">**명령 창**을 사용하려면 디버그 모드여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b91ff-104">You must be in debug mode to use the **Command Window**.</span></span> <span data-ttu-id="b91ff-105">[!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **명령** 창에서도 지원되는 많은 명령을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b91ff-105">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger supports many of the commands that are also supported in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Command** window.</span></span> <span data-ttu-id="b91ff-106">자세한 내용은 [Visual Studio 명령 창](https://go.microsoft.com/fwlink/?LinkId=112007)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b91ff-106">For more information, see [Visual Studio Command Window](https://go.microsoft.com/fwlink/?LinkId=112007).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="b91ff-107">작업 목록</span><span class="sxs-lookup"><span data-stu-id="b91ff-107">Task List</span></span>  
 <span data-ttu-id="b91ff-108">**명령 창에 액세스하려면**</span><span class="sxs-lookup"><span data-stu-id="b91ff-108">**To access the Command Window**</span></span>  
  
-   <span data-ttu-id="b91ff-109">**디버그** 메뉴에서 **디버깅 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b91ff-109">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
 <span data-ttu-id="b91ff-110">**변수 값을 인쇄하려면**</span><span class="sxs-lookup"><span data-stu-id="b91ff-110">**To print the value of a variable**</span></span>  
  
-   <span data-ttu-id="b91ff-111">**Commandwindow**에서 \*\*Debug. Print \<VariableName> \*\*를 입력 한 다음 enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b91ff-111">In the **CommandWindow**, type **Debug.Print \<VariableName>**, and then press ENTER.</span></span>  
  
 <span data-ttu-id="b91ff-112">**현재 스레드에 대한 정보를 표시하려면**</span><span class="sxs-lookup"><span data-stu-id="b91ff-112">**To list information about the current thread**</span></span>  
  
-   <span data-ttu-id="b91ff-113">**Commandwindow**에서를 입력 한 `Debug.ListThread` 다음 enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b91ff-113">In the **CommandWindow**, type `Debug.ListThread`, and then press ENTER.</span></span>  
  
 <span data-ttu-id="b91ff-114">**간략한 조사식 창에 변수를 추가하려면**</span><span class="sxs-lookup"><span data-stu-id="b91ff-114">**To add a variable to the QuickWatch window**</span></span>  
  
-   <span data-ttu-id="b91ff-115">**Commandwindow**에서 \*\*Debug. 간략 한 조사식 \<VariableName> \*\*을 입력 한 다음 enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b91ff-115">In the **CommandWindow**, type **Debug.QuickWatch \<VariableName>**, and then press ENTER.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b91ff-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b91ff-116">See Also</span></span>  
 [<span data-ttu-id="b91ff-117">Transact-SQL 디버거</span><span class="sxs-lookup"><span data-stu-id="b91ff-117">Transact-SQL Debugger</span></span>](transact-sql-debugger.md)  
