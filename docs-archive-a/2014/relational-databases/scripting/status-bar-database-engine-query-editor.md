---
title: 상태 표시줄(데이터베이스 엔진 쿼리 편집기)
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: e7f2d6f4-bb94-4cf5-a096-c34397e679af
author: rothja
ms.author: jroth
ms.openlocfilehash: 743ae0a4152daee19aa67f85337ae4077a3ed7f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653801"
---
# <a name="status-bar-database-engine-query-editor"></a><span data-ttu-id="fc2b2-102">상태 표시줄(데이터베이스 엔진 쿼리 편집기)</span><span class="sxs-lookup"><span data-stu-id="fc2b2-102">Status Bar (Database Engine Query Editor)</span></span>
  <span data-ttu-id="fc2b2-103">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기 창에서 각 창이 연결되는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스를 나타내도록 상태 표시줄을 색으로 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-103">The status bar of [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor windows can be color coded to indicate which instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] each window is connected to.</span></span>  
  
1.  <span data-ttu-id="fc2b2-104">**시작하기 전 주의 사항:**  [상태 표시줄 색](#StatusBarColors)</span><span class="sxs-lookup"><span data-stu-id="fc2b2-104">**Before you begin:**  [Status Bar Colors](#StatusBarColors)</span></span>  
  
2.  <span data-ttu-id="fc2b2-105">**서버 상태 색을 설정하려면:**  [개체 탐색기](#SetOEServerColor), [등록된 서버](#SetRegServerColor)</span><span class="sxs-lookup"><span data-stu-id="fc2b2-105">**To set a server status color in:**  [Object Explorer](#SetOEServerColor), [Registered Server](#SetRegServerColor)</span></span>  
  
3.  <span data-ttu-id="fc2b2-106">**상태 색을 사용하려면:**  [서버 색을 사용하여 쿼리 편집기 열기](#OpenServerColor), [상태 색을 지정하여 쿼리 편집기 열기](#OpenSpecColor)</span><span class="sxs-lookup"><span data-stu-id="fc2b2-106">**To use a status color:**  [Open Query Editor Using a Server Color](#OpenServerColor), [Open a Query Editor Specifying a Status Color](#OpenSpecColor)</span></span>  
  
##  <a name="status-bar-colors"></a><a name="StatusBarColors"></a> <span data-ttu-id="fc2b2-107">상태 표시줄 색</span><span class="sxs-lookup"><span data-stu-id="fc2b2-107">Status Bar Colors</span></span>  
 <span data-ttu-id="fc2b2-108">**개체 탐색기** 또는 **등록된 서버**에서 상태 표시줄 색을 특정 서버 노드에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-108">You can associate a status bar color with a specific server node in either **Object Explorer** or **Registered Servers**.</span></span> <span data-ttu-id="fc2b2-109">색은 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결된 서버 노드에 대해서만 지정할 수 있고 다른 SQL Server 기술에 대한 서버 노드에 대해서는 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-109">The colors can only be specified for server nodes connected to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], not server nodes for other SQL Server technologies.</span></span> <span data-ttu-id="fc2b2-110">새 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기 창을 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결할 때마다 사용자 지정 상태 표시줄 색을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-110">You can also specify a custom status bar color each time you connect a new [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="fc2b2-111">그런 다음 서버 노드에 대해 정의된 상태 색을 사용하거나 해당 편집기 창에 고유한 색을 지정하여 쿼리 편집기 창을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-111">You can then open a query editor window using either the status color defined for the server node, or specify a unique color for that editor window.</span></span>  
  
 <span data-ttu-id="fc2b2-112">개체 탐색기에서 서버 노드에 대한 사용자 지정 상태 표시줄 색을 설정하려면 연결할 때 색을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-112">Setting a custom status bar color for a server node in Object Explorer must be done when making the connection.</span></span> <span data-ttu-id="fc2b2-113">기존 서버 노드에 연결된 색을 변경하려면 연결을 끊었다가 다시 연결하여 새 색을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-113">To change the color associated with an existing server node, you must disconnect and then reconnect specifying the new color.</span></span>  
  
##  <a name="set-the-status-color-for-a-server-in-object-explorer"></a><a name="SetOEServerColor"></a> <span data-ttu-id="fc2b2-114">개체 탐색기에서 서버에 대한 상태 색 설정</span><span class="sxs-lookup"><span data-stu-id="fc2b2-114">Set the Status Color for a Server in Object Explorer</span></span>  
 <span data-ttu-id="fc2b2-115">**개체 탐색기에서 서버 상태 색을 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="fc2b2-115">**To set a server status color in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="fc2b2-116">**개체 탐색기**에서 **연결** 단추를 선택한 다음, **데이터베이스 엔진...** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-116">In **Object Explorer**, select the **Connect** button and then select **Database Engine...**.</span></span>  
  
2.  <span data-ttu-id="fc2b2-117">**서버에 연결** 대화 상자에서 **옵션 >>** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-117">On the **Connect to Server** dialog, select **Options >>**.</span></span>  
  
3.  <span data-ttu-id="fc2b2-118">**사용자 지정 색 사용** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-118">Select the **Use custom color** check box.</span></span>  
  
4.  <span data-ttu-id="fc2b2-119">색을 선택하려면 **선택...** 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-119">To select the color, select the **Select...** button.</span></span>  
  
5.  <span data-ttu-id="fc2b2-120">기본 색 또는 사용자 지정 색 중 하나를 선택하고 확인을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-120">Select either a basic or custom color, then select OK.</span></span>  
  
6.  <span data-ttu-id="fc2b2-121">나머지 연결 정보를 입력한 다음 **연결** 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-121">Fill in the rest of the connection information, and then select the **Connect** button.</span></span>  
  
##  <a name="set-the-status-color-for-a-registered-server"></a><a name="SetRegServerColor"></a> <span data-ttu-id="fc2b2-122">등록된 서버에 대한 상태 색 설정</span><span class="sxs-lookup"><span data-stu-id="fc2b2-122">Set the Status Color For a Registered Server</span></span>  
 <span data-ttu-id="fc2b2-123">**등록된 서버에 대한 서버 색을 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="fc2b2-123">**To set a server color For a Registered Server**</span></span>  
  
1.  <span data-ttu-id="fc2b2-124">**등록된 서버**에서 서버 노드를 마우스 오른쪽 단추로 클릭한 다음, **속성...** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-124">In **Registered Servers**, right click the server node and then select **Properties...**.</span></span>  
  
2.  <span data-ttu-id="fc2b2-125">**서버 등록 속성 편집** 대화 상자에서 **연결 속성** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-125">On the **Edit Server Registration Properties** dialog, select the **Connection Properties** tab.</span></span>  
  
3.  <span data-ttu-id="fc2b2-126">**사용자 지정 색 사용** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-126">Select the **Use custom color** check box.</span></span>  
  
4.  <span data-ttu-id="fc2b2-127">색을 선택하려면 **선택...** 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-127">To select the color, select the **Select...** button.</span></span>  
  
5.  <span data-ttu-id="fc2b2-128">기본 색 또는 사용자 지정 색 중 하나를 선택하고 확인을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-128">Select either a basic or custom color, then select OK.</span></span>  
  
6.  <span data-ttu-id="fc2b2-129">**서버 등록 속성 편집** 대화 상자에서 **저장** 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-129">Select the **Save** button on the **Edit Server Registration Properties** dialog.</span></span>  
  
##  <a name="open-an-editor-using-a-server-color"></a><a name="OpenServerColor"></a> <span data-ttu-id="fc2b2-130">서버 색을 사용하여 편집기 열기</span><span class="sxs-lookup"><span data-stu-id="fc2b2-130">Open An Editor Using a Server Color</span></span>  
 <span data-ttu-id="fc2b2-131">**서버 색을 사용하여 편집기 창을 열려면**</span><span class="sxs-lookup"><span data-stu-id="fc2b2-131">**To open an editor window using a server color**</span></span>  
  
-   <span data-ttu-id="fc2b2-132">**개체 탐색기** 또는 **등록된 서버**에서 서버 노드를 마우스 오른쪽 단추로 클릭하고 **새 쿼리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-132">Right-click a server node in either **Object Explorer** or **Registered Servers**, and select **New Query**.</span></span>  
  
-   <span data-ttu-id="fc2b2-133">또는 서버 노드를 강조 표시한 다음 **새 쿼리** 도구 모음 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-133">Alternatively, highlight a server node, and then select the **New Query** toolbar button.</span></span>  
  
-   <span data-ttu-id="fc2b2-134">편집기 창의 상태 표시줄에서 연결된 서버에 대해 정의된 색을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-134">The status bar in the editor window will use the color defined for the associated server.</span></span>  
  
##  <a name="open-an-editor-specifying-a-status-color"></a><a name="OpenSpecColor"></a> <span data-ttu-id="fc2b2-135">상태 색을 지정하여 편집기 열기</span><span class="sxs-lookup"><span data-stu-id="fc2b2-135">Open an Editor Specifying a Status Color</span></span>  
 <span data-ttu-id="fc2b2-136">**상태 색을 지정하여 편집기 창을 열려면**</span><span class="sxs-lookup"><span data-stu-id="fc2b2-136">**To open an editor window specifying a status color**</span></span>  
  
-   <span data-ttu-id="fc2b2-137">**파일** 메뉴를 열고 **새로 만들기**를 선택한 다음 **데이터베이스 엔진 쿼리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-137">Open the **File** menu, select **New**, and then select **Database Engine Query**.</span></span>  
  
-   <span data-ttu-id="fc2b2-138">**서버에 연결** 대화 상자에서 **옵션 >>** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-138">On the **Connect to Server** dialog, select **Options >>**.</span></span>  
  
-   <span data-ttu-id="fc2b2-139">**사용자 지정 색 사용** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-139">Select the **Use custom color** check box.</span></span>  
  
-   <span data-ttu-id="fc2b2-140">색을 선택하려면 **선택...** 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-140">To select the color, select the **Select...** button.</span></span>  
  
-   <span data-ttu-id="fc2b2-141">기본 색 또는 사용자 지정 색 중 하나를 선택하고 확인을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-141">Select either a basic or custom color, then select OK.</span></span>  
  
-   <span data-ttu-id="fc2b2-142">나머지 연결 정보를 입력한 다음 **연결** 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2b2-142">Fill in the rest of the connection information, and then select the **Connect** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc2b2-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fc2b2-143">See Also</span></span>  
 [<span data-ttu-id="fc2b2-144">쿼리 및 텍스트 편집기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="fc2b2-144">Query and Text Editors &#40;SQL Server Management Studio&#41;</span></span>](../scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  
