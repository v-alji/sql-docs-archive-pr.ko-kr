---
title: 서버에 연결(연결 속성 페이지) 데이터베이스 엔진 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttosqlserver.connectionproperties.f1
ms.assetid: edc1143c-6a47-4b02-92ab-441bdea8ea8a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 41f2aa3fd5004a371515ee5d8905c7bb73699829
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739033"
---
# <a name="connect-to-server-connection-properties-page-database-engine"></a><span data-ttu-id="6a0f8-102">서버에 연결(연결 속성 페이지) 데이터베이스 엔진</span><span class="sxs-lookup"><span data-stu-id="6a0f8-102">Connect to Server (Connection Properties Page) Database Engine</span></span>
  <span data-ttu-id="6a0f8-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스에 연결하거나 [!INCLUDE[ssDE](../../includes/ssde-md.md)]을 **등록된 서버**에 등록할 때 이 탭을 사용하여 옵션을 확인하거나 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-103">Use this tab to view or specify options when connecting to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] or registering [!INCLUDE[ssDE](../../includes/ssde-md.md)] in **Registered Servers**.</span></span> <span data-ttu-id="6a0f8-104">**연결** 및 **옵션** 은 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결 중인 경우에만 이 대화 상자에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-104">**Connect** and **Options** only appear in this dialog box when connecting to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="6a0f8-105">**테스트** 및 **저장** 은 [!INCLUDE[ssDE](../../includes/ssde-md.md)]등록 시에만 이 대화 상자에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-105">**Test** and **Save** only appear in this dialog box when registering [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="6a0f8-106">옵션</span><span class="sxs-lookup"><span data-stu-id="6a0f8-106">Options</span></span>  
 <span data-ttu-id="6a0f8-107">**데이터베이스에 연결**</span><span class="sxs-lookup"><span data-stu-id="6a0f8-107">**Connect to database**</span></span>  
 <span data-ttu-id="6a0f8-108">목록에서 연결할 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-108">Select a database to connect to from the list.</span></span> <span data-ttu-id="6a0f8-109">를 선택 하면 **\<default>** 서버의 기본 데이터베이스에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-109">If you select **\<default>**, you will be connected to the default database for the server.</span></span> <span data-ttu-id="6a0f8-110">를 선택 하면 **\<Browse server>** 연결할 데이터베이스의 서버를 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-110">If you select **\<Browse server>**, you can browse the server for the database to which to connect.</span></span>  
  
 <span data-ttu-id="6a0f8-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 통해 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]데이터베이스 엔진 인스턴스에 연결할 때는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용해야 하며 **서버에 연결** 대화 상자의 **연결 속성** 탭에서 데이터베이스를 지정해야 합니다. **연결 암호화** 확인란을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-111">When connecting to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine through [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], you must use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication and specify a database in the **Connect to Server** dialog box, on the **Connection Properties** tab. Ensure that you select the **Encrypt connection** checkbox.</span></span>  
  
 <span data-ttu-id="6a0f8-112">기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 **master**에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-112">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connects to **master**.</span></span> <span data-ttu-id="6a0f8-113">사용자 데이터베이스를 지정하면 개체 탐색기에서 해당 데이터베이스와 해당 개체만 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-113">If you specify a user database, you will only see that database and its objects in Object Explorer.</span></span> <span data-ttu-id="6a0f8-114">**master**에 연결하면 모든 데이터베이스를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-114">If you connect to **master**, you will be able to see all databases.</span></span> <span data-ttu-id="6a0f8-115">자세한 내용은 [Azure SQL Database 개요](/azure/sql-database/sql-database-technical-overview)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-115">For more information, see the [Azure SQL Database Overview](/azure/sql-database/sql-database-technical-overview).</span></span>  
  
 <span data-ttu-id="6a0f8-116">**네트워크 프로토콜**</span><span class="sxs-lookup"><span data-stu-id="6a0f8-116">**Network protocol**</span></span>  
 <span data-ttu-id="6a0f8-117">목록에서 프로토콜을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-117">Select a protocol from the list.</span></span> <span data-ttu-id="6a0f8-118">컴퓨터 관리에서 클라이언트 네트워크 구성을 사용하여 구성한 클라이언트 프로토콜을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-118">The available client protocols are those that you configured using the Client Network Configuration in Computer Management.</span></span>  
  
 <span data-ttu-id="6a0f8-119">**네트워크 패킷 크기**</span><span class="sxs-lookup"><span data-stu-id="6a0f8-119">**Network packet size**</span></span>  
 <span data-ttu-id="6a0f8-120">전송할 네트워크 패킷의 크기를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-120">Enter the size of the network packets to be sent.</span></span> <span data-ttu-id="6a0f8-121">기본값은 4096바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-121">The default is 4096 bytes.</span></span>  
  
 <span data-ttu-id="6a0f8-122">**연결 시간 제한**</span><span class="sxs-lookup"><span data-stu-id="6a0f8-122">**Connection timeout**</span></span>  
 <span data-ttu-id="6a0f8-123">제한 시간이 초과 되기 전까지 연결이 설정 될 때까지 대기 하는 시간 (초)을 입력 합니다. 기본값은 15 초입니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-123">Enter the number of seconds to wait for a connection to be established before timing out. The default value is 15 seconds.</span></span>  
  
 <span data-ttu-id="6a0f8-124">**실행 제한 시간**</span><span class="sxs-lookup"><span data-stu-id="6a0f8-124">**Execution timeout**</span></span>  
 <span data-ttu-id="6a0f8-125">서버에서 태스크가 실행 완료되기까지 대기하는 시간(초)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-125">Enter the amount of time in seconds to wait before execution of a task is completed on the server.</span></span> <span data-ttu-id="6a0f8-126">기본값은 0초이며 시간 제한 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-126">The default value is zero seconds, which indicates there is no time-out.</span></span>  
  
 <span data-ttu-id="6a0f8-127">**연결 암호화**</span><span class="sxs-lookup"><span data-stu-id="6a0f8-127">**Encrypt connection**</span></span>  
 <span data-ttu-id="6a0f8-128">연결 암호화를 강제 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-128">Forces encryption of the connection.</span></span>  
  
 <span data-ttu-id="6a0f8-129">**사용자 지정 색 사용**</span><span class="sxs-lookup"><span data-stu-id="6a0f8-129">**Use custom color**</span></span>  
 <span data-ttu-id="6a0f8-130">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기 창의 상태 표시줄 배경색을 지정하려는 경우 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-130">Select to specify the background color for the status bar in a [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window.</span></span> <span data-ttu-id="6a0f8-131">색을 지정하려면 **선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-131">To specify the color, click **Select**.</span></span> <span data-ttu-id="6a0f8-132">**색** 대화 상자의 **기본 색** 표에서 미리 정의된 색을 선택하거나 **사용자 지정 색 만들기** 를 클릭하여 사용자 지정 색을 정의하고 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-132">In the **Color** dialog box, select a predefined color from the **Basic Colors** grid or click **Define Custom Colors** to define and use a custom color.</span></span>  
  
-   <span data-ttu-id="6a0f8-133">**개체 탐색기** 창에서 서버 항목에 대한 색을 지정하면 쿼리 편집기 창을 열 때 해당 색이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-133">When you specify a color for a server entry in the **Object Explorer** pane, that color is used when you open a Query Editor window.</span></span> <span data-ttu-id="6a0f8-134">쿼리 편집기 창을 열려면 서버 항목을 마우스 오른쪽 단추로 클릭하고 **새 쿼리**를 선택하거나 **개체 탐색기** 창이 활성 상태이고 이 서버에 포커스가 있으면 도구 모음에서 **새 쿼리** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-134">To open a Query Editor window, either right-click the server entry and select **New Query**; or, when the **Object Explorer** pane is active and focused on this server, click **New Query** on the toolbar.</span></span>  
  
-   <span data-ttu-id="6a0f8-135">**등록된 서버** 창에서 서버 항목에 대한 색을 지정하면 쿼리 편집기 창을 열 때 해당 색이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-135">When you specify a color for a server entry in the **Registered Servers** pane, that color is used when you open a Query Editor window.</span></span> <span data-ttu-id="6a0f8-136">쿼리 편집기 창을 열려면 서버 항목을 마우스 오른쪽 단추로 클릭하고 **새 쿼리**를 선택하거나 **등록된 서버** 창이 활성 상태이고 이 서버에 포커스가 있으면 도구 모음에서 **새 쿼리** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-136">To open a Query Editor window, either right-click the server entry and select **New Query**; or, when the **Registered Server** pane is active and focused on this server, click **New Query** on the toolbar.</span></span>  
  
-   <span data-ttu-id="6a0f8-137">**파일** 메뉴에서 **새로 만들기** 를 클릭하고 **데이터베이스 엔진 쿼리**를 클릭하면 **서버에 연결** 대화 상자에서 지정한 색이 쿼리 편집기 창에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-137">On the **File** menu, when you click **New** and then **Database Engine Query**, the color you that you specify in the **Connect to Server** dialog box applies to that Query Editor window.</span></span>  
  
 <span data-ttu-id="6a0f8-138">**모두 다시 설정**</span><span class="sxs-lookup"><span data-stu-id="6a0f8-138">**Reset All**</span></span>  
 <span data-ttu-id="6a0f8-139">수동으로 입력한 모든 연결 속성 값을 기본값으로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-139">Replace all manually entered connection property values with their defaults.</span></span>  
  
 <span data-ttu-id="6a0f8-140">**연결**</span><span class="sxs-lookup"><span data-stu-id="6a0f8-140">**Connect**</span></span>  
 <span data-ttu-id="6a0f8-141">목록에 있는 값을 사용하여 연결을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-141">Attempt a connection using the listed values.</span></span>  
  
 <span data-ttu-id="6a0f8-142">**Options**</span><span class="sxs-lookup"><span data-stu-id="6a0f8-142">**Options**</span></span>  
 <span data-ttu-id="6a0f8-143">대화 상자를 변경하여 암호 저장과 같은 추가 서버 연결 옵션을 숨기려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-143">Click to change the dialog box and hide the additional server connection options, such as remembering the password.</span></span>  
  
 <span data-ttu-id="6a0f8-144">**Test**</span><span class="sxs-lookup"><span data-stu-id="6a0f8-144">**Test**</span></span>  
 <span data-ttu-id="6a0f8-145">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 을 **등록된 서버**에 등록하는 경우 연결을 테스트하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-145">When registering [!INCLUDE[ssDE](../../includes/ssde-md.md)] in **Registered Servers**, click to test the connection.</span></span>  
  
 <span data-ttu-id="6a0f8-146">**저장**</span><span class="sxs-lookup"><span data-stu-id="6a0f8-146">**Save**</span></span>  
 <span data-ttu-id="6a0f8-147">**등록된 서버**에 설정을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6a0f8-147">Saves the settings in **Registered Servers**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a0f8-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6a0f8-148">See Also</span></span>  
 [<span data-ttu-id="6a0f8-149">연결 속성 대화 상자</span><span class="sxs-lookup"><span data-stu-id="6a0f8-149">Connection Properties Dialog Box</span></span>](../../database-engine/connection-properties-dialog-box.md)  
  
  
