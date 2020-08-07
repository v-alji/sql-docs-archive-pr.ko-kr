---
title: 등록된 서버 및 개체 탐색기와 연결 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: d6b3911f-68b4-4483-831b-df89d6400add
author: stevestein
ms.author: sstein
ms.openlocfilehash: b4bc75ad7f3682765dc102064a5621cd541ccd12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727823"
---
# <a name="connect-with-registered-servers-and-object-explorer"></a><span data-ttu-id="8ef3a-102">등록된 서버 및 개체 탐색기와 연결</span><span class="sxs-lookup"><span data-stu-id="8ef3a-102">Connect with Registered Servers and Object Explorer</span></span>
  <span data-ttu-id="8ef3a-103">이 자습서에서는 등록된 서버와 개체 탐색기를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-103">This tutorial demonstrates the use of Registered Servers and Object Explorer.</span></span>  
  
 <span data-ttu-id="8ef3a-104">이 자습서에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-104">This tutorial uses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="8ef3a-105">보안을 위해 예제 데이터베이스는 기본적으로 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-105">To help enhance security, by default, the sample databases are not installed.</span></span> <span data-ttu-id="8ef3a-106">자세한 정보는 [SQL Server 예제 및 예제 데이터베이스 설치](http://sqlserversamples.codeplex.com)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-106">For more information, see [Installing SQL Server Samples and Sample Databases](http://sqlserversamples.codeplex.com).</span></span>  
  
## <a name="connecting-to-servers"></a><span data-ttu-id="8ef3a-107">서버에 연결</span><span class="sxs-lookup"><span data-stu-id="8ef3a-107">Connecting to Servers</span></span>  
 <span data-ttu-id="8ef3a-108">등록된 서버 구성 요소의 도구 모음에는 [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]및 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에 대한 단추가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-108">The toolbar of the Registered Servers component has buttons for the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="8ef3a-109">이들 중 하나 이상의 서버 유형을 등록하여 쉽게 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-109">You can register one or more of these server types for convenient management.</span></span> <span data-ttu-id="8ef3a-110">이 연습에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-110">Try the following exercise to register the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
#### <a name="to-register-the-database"></a><span data-ttu-id="8ef3a-111">데이터베이스를 등록하려면</span><span class="sxs-lookup"><span data-stu-id="8ef3a-111">To register the database</span></span>  
  
1.  <span data-ttu-id="8ef3a-112">필요한 경우 등록된 서버 도구 모음에서 **데이터베이스 엔진** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-112">On the Registered Servers toolbar, click **Database Engine** if you have to.</span></span> <span data-ttu-id="8ef3a-113">이미 선택되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-113">(It may already be selected.)</span></span>  
  
2.  <span data-ttu-id="8ef3a-114">**데이터베이스 엔진**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-114">Expand **Database Engine**.</span></span>  
  
3.  <span data-ttu-id="8ef3a-115">**로컬 서버 그룹**을 마우스 오른쪽 단추로 클릭한 다음 **새 서버 등록**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-115">Right-click **Local Server Groups**, and then click **New Server Registration**.</span></span>  
  
4.  <span data-ttu-id="8ef3a-116">**새 서버 등록** 대화 상자의 **서버 이름** 입력란에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-116">In the **New Server Registration** dialog box, in the **Server name** text box, type the name of your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
5.  <span data-ttu-id="8ef3a-117">**등록된 서버 이름** 입력란에 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-117">In the **Registered server name** box, type [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span>  
  
6.  <span data-ttu-id="8ef3a-118">**연결 속성** 탭의 **데이터베이스에 연결** 목록에서을 선택 **\<Browse server...>** 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-118">On the **Connection Properties** tab, in the **Connect to database** list, select **\<Browse server...>**.</span></span>  
  
7.  <span data-ttu-id="8ef3a-119">**데이터베이스 찾아보기** 대화 상자에서 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-119">In the **Browse for Databases** dialog box, click **Yes**.</span></span>  
  
8.  <span data-ttu-id="8ef3a-120">**서버에서 데이터베이스 찾아보기** 대화 상자에서 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-120">In the **Browse Server for Database** dialog box, select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], and then click **OK**.</span></span>  
  
9. <span data-ttu-id="8ef3a-121">서버가 제대로 등록되었는지 확인하려면 **테스트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-121">To verify that the server has been registered correctly, click **Test**.</span></span>  
  
10. <span data-ttu-id="8ef3a-122">**새 서버 등록** 대화 상자에서 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-122">In the **New Server Registration** dialog box, click **Save**.</span></span>  
  
## <a name="connecting-with-object-explorer"></a><span data-ttu-id="8ef3a-123">개체 탐색기와 연결</span><span class="sxs-lookup"><span data-stu-id="8ef3a-123">Connecting with Object Explorer</span></span>  
 <span data-ttu-id="8ef3a-124">등록된 서버와 마찬가지로 개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]및 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-124">Like Registered Servers, Object Explorer can connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
#### <a name="to-connect-with-object-explorer"></a><span data-ttu-id="8ef3a-125">개체 탐색기와 연결하려면</span><span class="sxs-lookup"><span data-stu-id="8ef3a-125">To connect with Object Explorer</span></span>  
  
1.  <span data-ttu-id="8ef3a-126">개체 탐색기의 도구 모음에서 **연결** 을 클릭하여 가능한 연결 유형 목록을 표시한 다음 **데이터베이스 엔진**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-126">On the toolbar of Object Explorer, click **Connect** for a list of possible connection types, and then select **Database Engine**.</span></span>  
  
2.  <span data-ttu-id="8ef3a-127">**서버에 연결** 대화 상자의 **서버 이름** 입력란에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-127">In the **Connect to Server** dialog box, in the **Server name** text box, type the name of your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="8ef3a-128">**옵션** 을 클릭하고 원하는 옵션을 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-128">Click **Options** and explore the choices.</span></span>  
  
4.  <span data-ttu-id="8ef3a-129">서버에 연결하려면 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-129">To connect to the server, click **Connect**.</span></span> <span data-ttu-id="8ef3a-130">이미 연결된 경우 개체 탐색기로 돌아가고 해당 서버에 포커스가 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-130">If you are already connected, this action just returns you to Object Explorer and sets the focus on that server.</span></span>  
  
     <span data-ttu-id="8ef3a-131">개체 탐색기를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 보안, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트, 복제 및 데이터베이스 메일을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-131">With Object Explorer you can administer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Security, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, Replication, and Database Mail.</span></span> <span data-ttu-id="8ef3a-132">개체 탐색기에서는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]및 [!INCLUDE[ssIS](../../includes/ssis-md.md)]의 일부 기능만 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-132">Object Explorer can only manage some of the features of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssIS](../../includes/ssis-md.md)].</span></span> <span data-ttu-id="8ef3a-133">이러한 각 구성 요소에는 특별한 도구가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-133">Each of those components has additional specialized tools.</span></span>  
  
5.  <span data-ttu-id="8ef3a-134">개체 탐색기에서 **데이터베이스** 폴더를 확장하고 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-134">In Object Explorer, expand the **Databases** folder and select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span>  
  
     <span data-ttu-id="8ef3a-135">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서는 시스템 데이터베이스를 별개의 폴더에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef3a-135">Notice that [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] presents the system databases in a separate folder.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="8ef3a-136">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="8ef3a-136">Next Task in Lesson</span></span>  
 [<span data-ttu-id="8ef3a-137">환경 레이아웃 변경</span><span class="sxs-lookup"><span data-stu-id="8ef3a-137">Change the Environment Layout</span></span>](lesson-1-3-change-the-environment-layout.md)  
  
  
