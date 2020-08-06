---
title: CDC Service에서 작업하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: db5c718a-6e7f-48ec-82a3-9d5b131716e5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7cfb5a0ed0e9ded8e0be118deb3c819626448896
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649634"
---
# <a name="how-to-work-with-cdc-services"></a><span data-ttu-id="ac5d8-102">CDC Service에서 작업하는 방법</span><span class="sxs-lookup"><span data-stu-id="ac5d8-102">How to Work with CDC Services</span></span>
  <span data-ttu-id="ac5d8-103">이 절차에서는 CDC Service 구성 콘솔을 사용하여 Oracle CDC Service에서 작업하기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 준비하고 새 CDC Service를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-103">This procedure describes how to use the CDC Service Configuration Console to prepare a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to work with Oracle CDC Services and to create a new CDC service.</span></span>  
  
### <a name="to-work-with-cdc-services"></a><span data-ttu-id="ac5d8-104">CDC Service에서 작업하려면</span><span class="sxs-lookup"><span data-stu-id="ac5d8-104">To work with CDC services</span></span>  
  
1.  <span data-ttu-id="ac5d8-105">**시작** 메뉴에서 **Oracle CDC Service 구성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-105">From the **Start** menu, select the **CDC Service Configuration for Oracle**.</span></span>  
  
2.  <span data-ttu-id="ac5d8-106">왼쪽 창에서 **로컬 CDC Service** (루트 수준)를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-106">From the left pane, select **Local CDC Services** (the root level).</span></span>  
  
3.  <span data-ttu-id="ac5d8-107">다음 태스크 중 하나 또는 모두 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-107">You carry out the one or both of the following tasks:</span></span>  
  
    -   <span data-ttu-id="ac5d8-108">**SQL Server 준비**</span><span class="sxs-lookup"><span data-stu-id="ac5d8-108">**Prepare SQL Server**</span></span>  
  
         <span data-ttu-id="ac5d8-109">CDC Service 구성 콘솔 오른쪽의 **작업** 창에서 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-109">Select this option from the **Actions** pane on the right side of the CDC Service Configuration Console.</span></span>  
  
         <span data-ttu-id="ac5d8-110">**로컬 CDC Service** 를 마우스 오른쪽 단추로 클릭하고 **SQL Server 준비**를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-110">You can also right-click **Local CDC Services** and select **Prepare SQL Server**.</span></span>  
  
         <span data-ttu-id="ac5d8-111">Oracle CDC를 위한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 준비 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-111">The Preparing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instance for Oracle CDC dialog box opens.</span></span>  
  
         <span data-ttu-id="ac5d8-112">Oracle CDC Service를 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 준비하려면 로그인은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 고정 서버 역할이 있는 `dbcreator` 로그인이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-112">To prepare the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance for Oracle CDC services, the login must have a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login with the `dbcreator` fixed server role.</span></span> <span data-ttu-id="ac5d8-113">이 로그인은 Oracle CDC Service 및 이후 Oracle CDC 인스턴스 추가에 필요한 MSXDBCDC 데이터베이스를 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-113">This login is used to create the MSXDBCDC database that is required for adding Oracle CDC Services and, later on, Oracle CDC Instances.</span></span>  
  
         <span data-ttu-id="ac5d8-114">이 대화 상자를 사용하는 방법은 [Prepare SQL Server for CDC](prepare-sql-server-for-cdc.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-114">For information on how to use this dialog box, see [Prepare SQL Server for CDC](prepare-sql-server-for-cdc.md).</span></span> <span data-ttu-id="ac5d8-115">CDC를 위한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 설정 방법에 대한 자세한 내용은 [CDC를 위해 SQL Server를 준비하는 방법](how-to-prepare-sql-server-for-cdc.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-115">For information on how to enable a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance for CDC, see [How to Prepare SQL Server for CDC](how-to-prepare-sql-server-for-cdc.md).</span></span>  
  
    -   <span data-ttu-id="ac5d8-116">**새 CDC Service 만들기**</span><span class="sxs-lookup"><span data-stu-id="ac5d8-116">**Create a new CDC service**</span></span>  
  
         <span data-ttu-id="ac5d8-117">CDC Service 구성 콘솔 오른쪽의 **작업** 창에서 **새 서비스** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-117">Click **New Service** from the **Actions** pane on the right side of the CDC Service Configuration Console.</span></span>  
  
         <span data-ttu-id="ac5d8-118">**로컬 CDC Service** 를 마우스 오른쪽 단추로 클릭하고 **새 서비스**를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-118">You can also right-Click **Local CDC Services** and select **New Service**.</span></span>  
  
         <span data-ttu-id="ac5d8-119">새 Oracle CDC Service 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-119">The New Oracle CDC Service dialog box opens.</span></span>  
  
         <span data-ttu-id="ac5d8-120">이 대화 상자를 사용하는 방법은 [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-120">For information on how to use this dialog box, see [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md).</span></span> <span data-ttu-id="ac5d8-121">CDC Service를 만들거나 편집하는 방법은 [CDC Service를 만들고 편집하는 방법](how-to-create-and-edit-a-cdc-service.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-121">For information on how to create or edit a CDC service, see [How to Create and Edit a CDC Service](how-to-create-and-edit-a-cdc-service.md).</span></span>  
  
         <span data-ttu-id="ac5d8-122">Oracle CDC Service에서 사용되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인은 `public` 고정 서버 역할의 구성원이면 가능하며 다른 권한은 필요 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-122">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login used by the Oracle CDC Service only needs to be a member of the `public` fixed-server role, no other privileges are needed.</span></span> <span data-ttu-id="ac5d8-123">하지만 Oracle CDC Service를 만들려면 로그인은 MSXDBCDC 데이터베이스에 대해 쓰기 권한이 있어야 합니다. 예를 들어 **db_owner** 데이터베이스 역할을 로그인에 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-123">However, to create the Oracle CDC Service, the login must have write permission to the MSXDBCDC database, for example the **db_owner** database role must be assigned to the login.</span></span> <span data-ttu-id="ac5d8-124">MSXDBCDC 데이터베이스에 대해 쓰기 권한이 없는 로그인이 새 Oracle CDC 인스턴스를 만들려고 시도하면 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-124">When a login without write permission to the MSXDBDCDC database attempts to create a new Oracle CDC instance an error message is displayed.</span></span> <span data-ttu-id="ac5d8-125">해당 대화 상자에서 **확인** 을 클릭하여 SQL Server에 연결 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-125">Click **OK** in that dialog box to display the Connect to SQL Server dialog box.</span></span>  
  
         <span data-ttu-id="ac5d8-126">**db_owner** 데이터베이스 역할과 같이 MSXDBCDC 데이터베이스에 대해 쓰기 권한이 있는 로그인의 자격 증명을 입력하는 방법은 [Oracle CDC Service 만들기 및 편집](create-and-edit-an-oracle-cdc-service.md) 및 [SQL Server에 연결](connection-to-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-126">For information on how to enter the credentials for a login that has write permission to the MSXDBCDC database, such the **db_owner** database role, see [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md) and [Connection to SQL Server](connection-to-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac5d8-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ac5d8-127">See Also</span></span>  
 [<span data-ttu-id="ac5d8-128">CDC Service 작업</span><span class="sxs-lookup"><span data-stu-id="ac5d8-128">Work with CDC Services</span></span>](work-with-cdc-services.md)  
  
  
