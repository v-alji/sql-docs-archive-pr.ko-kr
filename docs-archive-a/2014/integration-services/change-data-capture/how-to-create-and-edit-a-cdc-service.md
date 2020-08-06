---
title: CDC Service를 만들고 편집하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1b3d47a5-dc89-482d-bbc7-fff04f194c43
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d90534b475901b08fcd2e09acdc0f7976f0fb6e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728619"
---
# <a name="how-to-create-and-edit-a-cdc-service"></a><span data-ttu-id="28f05-102">CDC Service를 만들고 편집하는 방법</span><span class="sxs-lookup"><span data-stu-id="28f05-102">How to Create and Edit a CDC Service</span></span>
  <span data-ttu-id="28f05-103">이 프로시저에서는 CDC Service 구성 콘솔에서 새 Oracle CDC Service를 만들고 편집하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="28f05-103">These procedures describe how to create and edit a new Oracle CDC Service from the CDC Service Configuration Console.</span></span>  
  
 <span data-ttu-id="28f05-104">이 프로시저는 Oracle CDC Service가 구성된 컴퓨터에서 관리자 권한이 있는 Windows 사용자가 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28f05-104">This procedure requires a Windows user with administrator privileges on the computer where the Oracle CDC service is configured.</span></span>  
  
### <a name="to-create-a-new-cdc-service"></a><span data-ttu-id="28f05-105">새 CDC Service를 만들려면</span><span class="sxs-lookup"><span data-stu-id="28f05-105">To create a new CDC service</span></span>  
  
1.  <span data-ttu-id="28f05-106">**시작** 메뉴에서 **Oracle용 CDC Service 구성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="28f05-106">From the **Start** menu, select **CDC Service Configuration for Oracle**.</span></span>  
  
2.  <span data-ttu-id="28f05-107">왼쪽 창에서 로컬 CDC Service를 마우스 오른쪽 단추로 클릭하고 새 서비스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="28f05-107">From the left pane, right click Local CDC Services and select New Service</span></span>  
  
     <span data-ttu-id="28f05-108">**동작** 창에서 **새 서비스** 를 클릭할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28f05-108">You can also click **New Service** from the **Actions** pane.</span></span>  
  
3.  <span data-ttu-id="28f05-109">새 Oracle CDC Service 대화 상자에서 필요한 정보를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="28f05-109">Type or enter the required information in the New Oracle CDC Service dialog box.</span></span> <span data-ttu-id="28f05-110">새 Oracle CDC Service 대화 상자에서 정보를 입력하는 방법은 [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md) 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="28f05-110">See [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md) for information on how to enter information in the New Oracle CDC Service dialog box.</span></span>  
  
     <span data-ttu-id="28f05-111">새 Oracle CDC Service 대화 상자에서 제공하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인은 서비스를 실행할 때 Oracle CDC Service에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="28f05-111">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login provided in the New Oracle CDC Service dialog box is used by the Oracle CDC Service when the service runs.</span></span> <span data-ttu-id="28f05-112">이 로그인은 공용 고정 서버 역할의 구성원이면 가능하며 다른 권한은 필요 없습니다.</span><span class="sxs-lookup"><span data-stu-id="28f05-112">This login only needs to be a member of the public fixed-server role, no other privileges are needed.</span></span> <span data-ttu-id="28f05-113">새 Oracle CDC 인스턴스를 추가하면 해당 로그인은 연결된 **CDC 데이터베이스에 대한** db_owner [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 액세스 권한을 받게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28f05-113">Once new Oracle CDC Instances are added, that login receives **db_owner** access to the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC databases.</span></span>  
  
4.  <span data-ttu-id="28f05-114">필요한 정보를 다 입력한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="28f05-114">When you finish entering the required information, click **OK**.</span></span>  
  
     <span data-ttu-id="28f05-115">Oracle CDC Windows 서비스 정의를 만들려면 프로그램은 연결된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 MSXDBCDC 데이터베이스에 대한 액세스 권한을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28f05-115">To create the Oracle CDC Windows Service definition, the program needs update access to the MSXDBCDC database in the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="28f05-116">**확인**을 클릭하면 사용자가 MSXDBCDC 데이터베이스의 업데이트 권한이 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 입력할 수 있는 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="28f05-116">When you click **OK**, a dialog box prompts the user to enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login with an update access to the MSXDBCDC database.</span></span>  
  
     <span data-ttu-id="28f05-117">SQL Server에 연결 대화 상자에 입력해야 하는 데이터에 대한 자세한 내용은 [Connection to SQL Server](connection-to-sql-server.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="28f05-117">For information about the data you must type into the Connect to SQL Server dialog box, see [Connection to SQL Server](connection-to-sql-server.md).</span></span>  
  
5.  <span data-ttu-id="28f05-118">**확인** 을 클릭하여 새 Oracle CDC Service 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="28f05-118">Click **OK** to close the New Oracle CDC Service dialog box.</span></span>  
  
### <a name="to-edit-a-cdc-service"></a><span data-ttu-id="28f05-119">CDC Service를 편집하려면</span><span class="sxs-lookup"><span data-stu-id="28f05-119">To edit a CDC service</span></span>  
  
1.  <span data-ttu-id="28f05-120">**시작** 메뉴에서 **Oracle용 CDC Service 구성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="28f05-120">From the **Start** menu, select **CDC Service Configuration for Oracle**.</span></span>  
  
2.  <span data-ttu-id="28f05-121">왼쪽 창에서 **로컬 CDC Service** 를 선택한 다음 편집하려는 로컬 서비스를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="28f05-121">From the left pane, select **Local CDC Services** then right-click the local service you want to edit and select **Properties**.</span></span>  
  
     <span data-ttu-id="28f05-122">중간에서 작업할 서비스를 선택하고 **동작** 창에서 **속성**을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28f05-122">You can also select the service you are working with in the middle and then from the **Actions** pane, click **Properties**.</span></span>  
  
3.  <span data-ttu-id="28f05-123">CDC Service 속성 대화 상자에서 필요한 정보를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="28f05-123">Type or enter the required information in the CDC Service Properties dialog box.</span></span> <span data-ttu-id="28f05-124">CDC Service 속성 대화 상자에서 정보를 입력하는 방법은 [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md) 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="28f05-124">See [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md) for information on how to enter information in the CDC Service Properties dialog box.</span></span>  
  
4.  <span data-ttu-id="28f05-125">필요한 정보를 다 입력한 후 **확인**을 클릭하면 SQL Server에 연결 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="28f05-125">When you finish entering the required information, Click **OK**, the Connect to SQL Server dialog box opens.</span></span>  
  
     <span data-ttu-id="28f05-126">MSXDBCDC 데이터베이스에 대해 쓰기 권한이 없는 로그인이 새 Oracle CDC 인스턴스를 만들려고 시도하면 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="28f05-126">When a login without write permission to the MSXDBDCDC database attempts to create a new Oracle CDC instance an error message is displayed.</span></span> <span data-ttu-id="28f05-127">해당 대화 상자에서 **확인** 을 클릭하여 SQL Server에 연결 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="28f05-127">Click **OK** in that dialog box to display the Connect to SQL Server dialog box.</span></span> <span data-ttu-id="28f05-128">이 대화 상자에서 **db_owner** 데이터베이스 역할과 같은 MSXDBCDC 데이터베이스에 대해 쓰기 권한이 있는 로그인의 자격 증명을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28f05-128">In this dialog box you must enter the credentials for a login that has write permission to the MSXDBCDC database, such the **db_owner** database role.</span></span>  
  
     <span data-ttu-id="28f05-129">SQL Server에 연결 대화 상자에 입력해야 하는 데이터에 대한 자세한 내용은 [Connection to SQL Server](connection-to-sql-server.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="28f05-129">For information about the data you must type into the Connect to SQL Server dialog box, see [Connection to SQL Server](connection-to-sql-server.md).</span></span>  
  
5.  <span data-ttu-id="28f05-130">Oracle에 연결 대화 상자에서 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="28f05-130">Click **OK** in the Connect to Oracle dialog box.</span></span> <span data-ttu-id="28f05-131">두 대화 상자가 모두 닫히며 서비스가 업데이트되고 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="28f05-131">Both dialog boxes close and the service is updated and registered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28f05-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="28f05-132">See Also</span></span>  
 <span data-ttu-id="28f05-133">[Change Data Capture Designer for Oracle by Attunity](change-data-capture-designer-for-oracle-by-attunity.md) </span><span class="sxs-lookup"><span data-stu-id="28f05-133">[Change Data Capture Designer for Oracle by Attunity](change-data-capture-designer-for-oracle-by-attunity.md) </span></span>  
 [<span data-ttu-id="28f05-134">Oracle CDC Service 만들기 및 편집</span><span class="sxs-lookup"><span data-stu-id="28f05-134">Create and Edit an Oracle CDC Service</span></span>](create-and-edit-an-oracle-cdc-service.md)  
  
  
