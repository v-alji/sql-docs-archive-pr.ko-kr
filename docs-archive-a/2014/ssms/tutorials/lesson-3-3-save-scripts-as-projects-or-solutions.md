---
title: 스크립트를 프로젝트 또는 솔루션으로 저장 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 72dfd37f-dbe7-4d1d-bda6-7eb54c7922d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9fade3900c8859f211bb0c66820dc97792262481
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733396"
---
# <a name="save-scripts-as-projects-or-solutions"></a><span data-ttu-id="7f599-102">스크립트를 프로젝트 또는 솔루션으로 저장</span><span class="sxs-lookup"><span data-stu-id="7f599-102">Save Scripts as Projects or Solutions</span></span>
  <span data-ttu-id="7f599-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio에 익숙한 개발자라면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 솔루션 탐색기를 쉽게 활용할 수 있을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-103">Developers familiar with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio will welcome Solution Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="7f599-104">업무 지원 스크립트를 스크립트 프로젝트로 그룹화하고 스크립트 프로젝트를 하나의 솔루션으로 함께 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-104">The scripts that support your business can be grouped into script projects, and the script projects can be managed together as a solution.</span></span> <span data-ttu-id="7f599-105">스크립트 프로젝트와 솔루션에 배치된 스크립트는 하나의 그룹으로 함께 열거나 Visual SourceSafe와 같은 원본 제어 제품에 함께 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-105">When scripts are placed in script projects and solutions they can be opened together as a group, or saved together to a source control product such as Visual SourceSafe.</span></span> <span data-ttu-id="7f599-106">스크립트 프로젝트에는 스크립트를 제대로 실행하기 위한 연결 정보가 포함되며 지원 텍스트 파일 같이 스크립트가 아닌 파일이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-106">Script projects include the connection information for the scripts to execute properly, and can include non-script files such as a supporting text file.</span></span>  
  
 <span data-ttu-id="7f599-107">다음 연습에서는 스크립트 프로젝트와 솔루션에 배치되어 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스를 쿼리하는 간단한 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-107">The following practice creates a short script that queries the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, placed in a script project and solution.</span></span>  
  
## <a name="using-script-projects-and-solutions"></a><span data-ttu-id="7f599-108">스크립트 프로젝트 및 솔루션 사용</span><span class="sxs-lookup"><span data-stu-id="7f599-108">Using Script Projects and Solutions</span></span>  
  
#### <a name="to-create-a-script-project-and-solution"></a><span data-ttu-id="7f599-109">스크립트 프로젝트와 솔루션을 만들려면</span><span class="sxs-lookup"><span data-stu-id="7f599-109">To create a script project and solution</span></span>  
  
1.  <span data-ttu-id="7f599-110">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]를 열고 개체 탐색기로 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-110">Open [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and connect to a server with Object Explorer.</span></span>  
  
2.  <span data-ttu-id="7f599-111">**파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-111">On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="7f599-112">**새 프로젝트** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-112">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="7f599-113">**이름** 입력란에 **StatusCheck**를 입력하고 **템플릿** 에서 **SQL Server 스크립트**를 클릭한 다음 **확인** 을 클릭하여 새 솔루션과 스크립트 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-113">In the **Name** text box, type **StatusCheck**, click **SQL Server Scripts** in **Templates**, and then click **OK** to open a new solution and script project.</span></span>  
  
4.  <span data-ttu-id="7f599-114">솔루션 탐색기에서 **연결**을 마우스 오른쪽 단추로 클릭한 다음 **새 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-114">In Solution Explorer, right-click **Connections**, and then click **New Connection**.</span></span> <span data-ttu-id="7f599-115">**서버에 연결** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-115">The **Connect to Server** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="7f599-116">**서버 이름** 목록 상자에 서버 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-116">In the **Server name** list box, type the name of your server.</span></span>  
  
6.  <span data-ttu-id="7f599-117">**옵션**을 클릭한 다음 **연결 속성** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-117">Click **Options**, and then click the **Connection Properties** tab.</span></span>  
  
7.  <span data-ttu-id="7f599-118">**연결할 데이터베이스** 상자에서 서버를 찾아보고 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스를 선택한 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-118">In the **Connect to database** box, browse the server, select the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, and then click **Connect**.</span></span> <span data-ttu-id="7f599-119">데이터베이스를 포함한 연결 정보가 프로젝트에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-119">The connection information including the database is added to the project.</span></span>  
  
8.  <span data-ttu-id="7f599-120">속성 창이 표시되지 않으면 솔루션 탐색기에서 새 연결을 클릭한 다음 F4 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-120">If the Properties window is not displayed, click the new connection in Solution Explorer, and then press F4.</span></span> <span data-ttu-id="7f599-121">연결 속성이 나타나고 **로** 초기 데이터베이스 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]를 포함하는 연결 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-121">The properties for the connection appear, and show information about the connection including the **Initial Database** as [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span>  
  
9. <span data-ttu-id="7f599-122">솔루션 탐색기에서 연결을 마우스 오른쪽 단추로 클릭한 다음 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-122">In Solution Explorer, right-click the connection, and then click **New Query**.</span></span> <span data-ttu-id="7f599-123">서버의 **데이터베이스에 연결된** SQLQuery1.sql [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 이라는 새 쿼리가 생성되어 스크립트 프로젝트에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-123">A new query called **SQLQuery1.sql** is created, connected to the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database on your server, and added to your script project.</span></span>  
  
10. <span data-ttu-id="7f599-124">쿼리 편집기에 다음 쿼리를 입력하여 작업 주문 시작 날짜 전 기한이 있는 작업 주문 수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-124">In Query Editor, type the following query to determine how many work orders have due dates, before the work order starting dates.</span></span> <span data-ttu-id="7f599-125">자습서 창에서 코드를 복사하여 붙여 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-125">(You can copy and paste the code from the Tutorial window.)</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT COUNT(WorkOrderID)  
    FROM Production.WorkOrder  
    WHERE DueDate < StartDate;  
  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="7f599-126">쿼리를 입력할 공간이 더 필요하면 Shift+Alt+Enter를 눌러 전체 화면 모드로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-126">If you need more room to type your query, press SHIFT+ALT+ENTER, to switch to full-screen mode.</span></span>  
  
11. <span data-ttu-id="7f599-127">솔루션 탐색기에서 **SQLQuery1**을 마우스 오른쪽 단추로 클릭한 다음 **이름 바꾸기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-127">In Solution Explorer, right-click **SQLQuery1**, and then click **Rename**.</span></span> <span data-ttu-id="7f599-128">쿼리의 새 이름으로 **Check workorders.sql** 을 입력 하 고 enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-128">Type **Check Workorders.sql** as the new name for the query and press ENTER.</span></span>  
  
12. <span data-ttu-id="7f599-129">솔루션과 스크립트 프로젝트를 저장하려면 **파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7f599-129">To save your solution and script project, on the **File** menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="7f599-130">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="7f599-130">Next Task in Lesson</span></span>  
 [<span data-ttu-id="7f599-131">요약: 솔루션 및 스크립트 프로젝트</span><span class="sxs-lookup"><span data-stu-id="7f599-131">Summary: Solutions and Script Projects</span></span>](lesson-3-4-summary-solutions-and-script-projects.md)  
  
  
