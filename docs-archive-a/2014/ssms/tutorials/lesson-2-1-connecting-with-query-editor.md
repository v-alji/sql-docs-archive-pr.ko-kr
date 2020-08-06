---
title: 쿼리 편집기와 연결 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 48725f54-a7b6-4b79-948e-965c1fe4eef1
author: stevestein
ms.author: sstein
ms.openlocfilehash: b50783450dfb9516c78a465806ee322d7a575377
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652504"
---
# <a name="connecting-with-query-editor"></a><span data-ttu-id="6bdbd-102">쿼리 편집기와 연결</span><span class="sxs-lookup"><span data-stu-id="6bdbd-102">Connecting with Query Editor</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="6bdbd-103">에서는 서버와의 연결이 끊긴 동안에도 코드를 쓰거나 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bdbd-103">permits you to write or edit code while disconnected from the server.</span></span> <span data-ttu-id="6bdbd-104">이 기능은 서버를 사용할 수 없을 때나 부족한 서버 또는 네트워크 리소스를 보존하고자 할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="6bdbd-104">This can be useful when the server is not available or when you want to conserve scarce server or network resources.</span></span> <span data-ttu-id="6bdbd-105">또한 새 쿼리 편집기 창을 열거나 코드를 다시 입력하지 않고도 쿼리 편집기의 연결을 새 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bdbd-105">You can also change the connection of Query Editor to a new instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without opening a new Query Editor window or retyping your code.</span></span>  
  
## <a name="coding-offline"></a><span data-ttu-id="6bdbd-106">오프라인으로 코드 작성</span><span class="sxs-lookup"><span data-stu-id="6bdbd-106">Coding Offline</span></span>  
  
#### <a name="to-write-code-offline-and-then-connect-to-different-servers"></a><span data-ttu-id="6bdbd-107">오프라인으로 코드를 작성한 다음 다른 서버에 연결하려면</span><span class="sxs-lookup"><span data-stu-id="6bdbd-107">To write code offline and then connect to different servers</span></span>  
  
1.  <span data-ttu-id="6bdbd-108">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 도구 모음에서 **데이터베이스 엔진 쿼리** 를 클릭하여 쿼리 편집기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6bdbd-108">On the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] toolbar, click **Database Engine Query** to open the Query Editor.</span></span>  
  
2.  <span data-ttu-id="6bdbd-109">**데이터베이스 엔진에 연결** 대화 상자에서 **취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bdbd-109">In the **Connect to Database Engine** dialog box, click **Cancel**.</span></span> <span data-ttu-id="6bdbd-110">쿼리 편집기가 열리고 쿼리 편집기의 제목 표시줄에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결되어 있지 않다는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="6bdbd-110">The Query Editor opens, and the title bar for the Query Editor indicates that you are not connected to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="6bdbd-111">코드 창에 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6bdbd-111">In the code pane, type the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    SELECT * FROM Production.Product;  
    GO  
    ```  
  
     <span data-ttu-id="6bdbd-112">이 시점에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결 **,** 실행 **,** 구문 분석 **또는**예상 실행 계획 표시 **를 클릭하여**인스턴스에 연결할 수 있습니다. 이 모든 명령은 **쿼리** 메뉴, 쿼리 편집기 도구 모음 또는 쿼리 편집기 창에서 마우스 오른쪽 단추를 클릭할 때 나타나는 바로 가기 메뉴에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bdbd-112">At this point you can connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by clicking **Connect**, **Execute**, **Parse**, or **Display Estimated Execution Plan**, all of which are available from either the **Query** menu, the Query Editor toolbar, or from the shortcut menu when you right-click in the Query Editor window.</span></span> <span data-ttu-id="6bdbd-113">이 연습에서는 도구 모음을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6bdbd-113">For this practice, we'll use the toolbar.</span></span>  
  
4.  <span data-ttu-id="6bdbd-114">도구 모음에서 **실행** 단추를 클릭하여 **데이터베이스 엔진에 연결** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6bdbd-114">On the toolbar, click the **Execute** button to open the **Connect to Database Engine** dialog box.</span></span>  
  
5.  <span data-ttu-id="6bdbd-115">**서버 이름** 입력란에 서버 이름을 입력한 다음 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bdbd-115">In the **Server name** text box, type your server name, and then click **Options**.</span></span>  
  
6.  <span data-ttu-id="6bdbd-116">**연결 속성** 탭의 **연결할 데이터베이스** 목록에서 서버를 찾아 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 를 선택한 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bdbd-116">On the **Connection Properties** tab, in the **Connect to database** list, browse the server to select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] and then click **Connect**.</span></span>  
  
7.  <span data-ttu-id="6bdbd-117">같은 연결을 사용하여 다른 쿼리 편집기 창을 열려면 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bdbd-117">To open another Query Editor window with the same connection, on the toolbar click **New Query**.</span></span>  
  
8.  <span data-ttu-id="6bdbd-118">연결을 변경하려면 쿼리 편집기 창에서 마우스 오른쪽 단추를 클릭하고 **연결**을 가리킨 다음 **연결 변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bdbd-118">To change connections, right-click in the Query Editor window, point to **Connection**, and then click **Change Connection**.</span></span>  
  
9. <span data-ttu-id="6bdbd-119">**SQL Server에 연결** 대화 상자에서 사용 가능한 다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 선택한 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bdbd-119">In the **Connect to SQL Server** dialog box, select another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if available, and then click **Connect**.</span></span>  
  
 <span data-ttu-id="6bdbd-120">이 새로운 쿼리 편집기 기능을 사용하면 여러 서버에서 같은 코드를 쉽게 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bdbd-120">This new feature of Query Editor enables you to easily run the same code on several servers.</span></span> <span data-ttu-id="6bdbd-121">이 기능은 여러 비슷한 서버와 관련된 유지 관리 동작에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="6bdbd-121">This may be useful for maintenance actions involving similar servers.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="6bdbd-122">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="6bdbd-122">Next Task in Lesson</span></span>  
 [<span data-ttu-id="6bdbd-123">들여쓰기 추가</span><span class="sxs-lookup"><span data-stu-id="6bdbd-123">Adding Indentation</span></span>](lesson-2-2-adding-indentation.md)  
  
  
