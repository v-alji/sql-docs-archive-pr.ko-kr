---
title: SQL Server Management Studio 시작 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 25ffaea6-0eee-4169-8dd0-1da417c28fc6
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8fc9de4884da9a4c372eecdeb6fde12cf3c507e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727836"
---
# <a name="start-sql-server-management-studio"></a><span data-ttu-id="0e42e-102">SQL Server Management Studio 시작</span><span class="sxs-lookup"><span data-stu-id="0e42e-102">Start SQL Server Management Studio</span></span>
  <span data-ttu-id="0e42e-103">이 자습서를 시작하기 전에 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 간단히 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="0e42e-103">To begin this tutorial, let's take a look at [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="opening-sql-server-management-studio"></a><span data-ttu-id="0e42e-104">SQL Server Management Studio 열기</span><span class="sxs-lookup"><span data-stu-id="0e42e-104">Opening SQL Server Management Studio</span></span>  
  
#### <a name="to-open-sql-server-management-studio"></a><span data-ttu-id="0e42e-105">SQL Server Management Studio를 열려면</span><span class="sxs-lookup"><span data-stu-id="0e42e-105">To open SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="0e42e-106">**시작** 메뉴에서 **모든 프로그램**,을 차례로 가리킨 [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] 다음 **SQL Server Management Studio**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e42e-106">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], and then click **SQL Server Management Studio**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0e42e-107">기본적으로 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]는 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0e42e-107">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is not installed by default.</span></span> <span data-ttu-id="0e42e-108">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]를 사용할 수 없으면 설치 프로그램을 실행하여 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="0e42e-108">If [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] is unavailable, install it by running Setup.</span></span> [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]<span data-ttu-id="0e42e-109">는 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0e42e-109">is not available with [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span> [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]<span data-ttu-id="0e42e-110">Express는 [Microsoft 다운로드 센터](https://www.microsoft.com/download/details.aspx?id=14630)에서 무료로 다운로드할 수 있지만이 자습서에 설명 된 것과 다른 사용자 인터페이스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e42e-110">Express is available as a free download from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=14630), but has a different user interface than is described in this tutorial.</span></span>  
  
2.  <span data-ttu-id="0e42e-111">**서버에 연결** 대화 상자에서 기본 설정을 확인한 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0e42e-111">In the **Connect to Server** dialog box, verify the default settings, and then click **Connect**.</span></span> <span data-ttu-id="0e42e-112">연결 하려면 **서버 이름** 상자에가 설치 된 컴퓨터의 이름을 포함 해야 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0e42e-112">To connect, the **Server name** box must contain the name of the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span> <span data-ttu-id="0e42e-113">[!INCLUDE[ssDE](../../includes/ssde-md.md)]이 명명 된 인스턴스인 경우 **서버 이름** 상자에는 \<*computer_name*> \\ <> *instance_name* 형식으로 인스턴스 이름도 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e42e-113">If the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is a named instance, the **Server name** box should also contain the instance name in the format \<*computer_name*>\\<*instance_name*>.</span></span>  
  
## <a name="management-studio-components"></a><span data-ttu-id="0e42e-114">Management Studio 구성 요소</span><span class="sxs-lookup"><span data-stu-id="0e42e-114">Management Studio Components</span></span>  
 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="0e42e-115">는 유형에 따른 전용 창에 정보를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0e42e-115">presents information in windows dedicated to specific types of information.</span></span> <span data-ttu-id="0e42e-116">데이터베이스 정보는 개체 탐색기 및 문서 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e42e-116">Database information is shown in Object Explorer and document windows.</span></span>  
  
-   <span data-ttu-id="0e42e-117">개체 탐색기는 서버에 있는 모든 데이터베이스 개체의 트리 뷰로,</span><span class="sxs-lookup"><span data-stu-id="0e42e-117">Object Explorer is a tree view of all the database objects in a server.</span></span> <span data-ttu-id="0e42e-118">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]및 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]데이터베이스를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e42e-118">This can include the databases of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="0e42e-119">개체 탐색기에는 연결된 모든 서버에 대한 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e42e-119">Object Explorer includes information for all servers to which it is connected.</span></span> <span data-ttu-id="0e42e-120">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]를 열면 마지막으로 사용된 설정에 개체 탐색기를 연결하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e42e-120">When you open [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you are prompted to connect Object Explorer to the settings that were last used.</span></span> <span data-ttu-id="0e42e-121">등록된 서버 구성 요소에서 서버를 두 번 클릭하여 연결할 수 있지만 연결할 서버를 등록하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e42e-121">You can double-click any server in the Registered Servers component to connect to it, but you do not have to register a server to connect.</span></span>  
  
-   <span data-ttu-id="0e42e-122">문서 창은 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]의 가장 큰 부분으로,</span><span class="sxs-lookup"><span data-stu-id="0e42e-122">The document window is the largest portion of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="0e42e-123">쿼리 편집기와 브라우저 창을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e42e-123">The document windows can contain query editors and browser windows.</span></span> <span data-ttu-id="0e42e-124">기본적으로 현재 컴퓨터의 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결된 요약 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e42e-124">By default, the Summary page is displayed, connected to the instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] on the current computer.</span></span>  
  
## <a name="showing-additional-windows"></a><span data-ttu-id="0e42e-125">추가 창 표시</span><span class="sxs-lookup"><span data-stu-id="0e42e-125">Showing Additional Windows</span></span>  
  
#### <a name="to-show-the-registered-servers-window"></a><span data-ttu-id="0e42e-126">등록된 서버 창을 표시하려면</span><span class="sxs-lookup"><span data-stu-id="0e42e-126">To show the Registered Servers window</span></span>  
  
1.  <span data-ttu-id="0e42e-127">**보기** 메뉴에서 **등록된 서버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0e42e-127">On the **View** menu, click **Registered Servers**.</span></span>  
  
     <span data-ttu-id="0e42e-128">등록된 서버 창은 개체 탐색기 위에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0e42e-128">The Registered Servers window appears above Object Explorer.</span></span> <span data-ttu-id="0e42e-129">예약된 서버에는 사용자가 자주 관리하는 서버가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e42e-129">Registered Servers lists servers which you manage frequently.</span></span> <span data-ttu-id="0e42e-130">이 목록에서 서버를 추가하거나 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e42e-130">You can add and remove servers from this list.</span></span> <span data-ttu-id="0e42e-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 실행 중인 컴퓨터의 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]인스턴스만 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e42e-131">The only servers listed are the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances on the computer where you are running [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="0e42e-132">서버가 나타나지 않으면 등록 된 서버에서 **데이터베이스 엔진**를 마우스 오른쪽 단추로 클릭 한 다음 **로컬 서버 등록 업데이트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e42e-132">If your server does not appear, in Registered Servers, right-click **Database Engine**, and then click **Update Local Server Registration**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="0e42e-133">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="0e42e-133">Next Task in Lesson</span></span>  
 [<span data-ttu-id="0e42e-134">등록된 서버 및 개체 탐색기와 연결</span><span class="sxs-lookup"><span data-stu-id="0e42e-134">Connect with Registered Servers and Object Explorer</span></span>](../object/object-explorer.md)  
  
  
