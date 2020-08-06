---
title: CDC를 위한 SQL Server 준비 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- prepSqlSrv
ms.assetid: 20b51dbf-a545-4234-87ae-4228268a0fb2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dafa29d9bdb0c27decb605398a6d1cfe383427e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647811"
---
# <a name="prepare-sql-server-for-cdc"></a><span data-ttu-id="1c02b-102">CDC를 위한 SQL Server 준비</span><span class="sxs-lookup"><span data-stu-id="1c02b-102">Prepare SQL Server for CDC</span></span>
  <span data-ttu-id="1c02b-103">Oracle CDC Service에서는 모든 대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 MSXDBCDC 데이터베이스가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c02b-103">The Oracle CDC service requires all target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances to contain the MSXDBCDC database.</span></span> <span data-ttu-id="1c02b-104">CDC Service 구성 콘솔에서 SQL Server 준비 작업을 사용하여 이 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1c02b-104">You create this database using the Prepare SQL Server action in the CDC Service Configuration Console.</span></span> <span data-ttu-id="1c02b-105">이 작업은 이 데이터베이스의 필수 테이블, 저장 프로시저 및 기타 필수 아티팩트를 만들기 위해 실행되는 특수 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1c02b-105">This creates a special script that is run to create the required tables, stored procedures, and other required artifacts for this database.</span></span> <span data-ttu-id="1c02b-106">이 작업은 각 대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대해 한 번만 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c02b-106">This task is done one time only for each target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="1c02b-107">MSXDBCDC 데이터베이스에 대한 자세한 내용은 MSXDBCDC 데이터베이스를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1c02b-107">For more information about the MSXDBCDC database, see The MSXDBCDC Database.</span></span>  
  
 <span data-ttu-id="1c02b-108">CDC Service 구성 콘솔에서 **SQL Server 준비**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1c02b-108">In the CDC Service Configuration Console, click **Prepare SQL Server**.</span></span> <span data-ttu-id="1c02b-109">이 옵션을 사용할 수 없는 경우 콘솔의 왼쪽 창에서 **로컬 CDC Service** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1c02b-109">If this option is not available, make sure that **Local CDC Services** is selected in the left pane of the console.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1c02b-110">옵션</span><span class="sxs-lookup"><span data-stu-id="1c02b-110">Options</span></span>  
  
### <a name="server-name"></a><span data-ttu-id="1c02b-111">서버 이름</span><span class="sxs-lookup"><span data-stu-id="1c02b-111">Server Name</span></span>  
 <span data-ttu-id="1c02b-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 있는 서버의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1c02b-112">Type the name of the server where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is located.</span></span>  
  
### <a name="authentication"></a><span data-ttu-id="1c02b-113">인증</span><span class="sxs-lookup"><span data-stu-id="1c02b-113">Authentication</span></span>  
 <span data-ttu-id="1c02b-114">다음 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1c02b-114">Select one of the following:</span></span>  
  
-   <span data-ttu-id="1c02b-115">**Windows 인증**</span><span class="sxs-lookup"><span data-stu-id="1c02b-115">**Windows Authentication**</span></span>  
  
-   <span data-ttu-id="1c02b-116">**SQL Server 인증**: 이 옵션을 선택하는 경우 연결 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 사용자의 **사용자 이름**과 **암호**를 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c02b-116">**SQL Server Authentication**: If you select this option, you must type the **User Name** and **Password** for the user in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you are connecting to.</span></span>  
  
 <span data-ttu-id="1c02b-117">Oracle CDC에 대해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 준비하려면 로그인은 MSXDBCDC 데이터베이스에 대해 쓰기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c02b-117">To prepare the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance for Oracle CDC, the login must have write permission to the MSXDBCDC database.</span></span> <span data-ttu-id="1c02b-118">MSXDBCDC 데이터베이스에 대해 쓰기 권한이 있는 로그인(예: `sysasmin` 역할의 멤버)의 자격 증명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1c02b-118">Enter the credentials for a login that has write permission to the MSXDBCDC database, such as a member of the `sysasmin` role.</span></span>  
  
### <a name="options"></a><span data-ttu-id="1c02b-119">옵션</span><span class="sxs-lookup"><span data-stu-id="1c02b-119">Options</span></span>  
 <span data-ttu-id="1c02b-120">화살표를 클릭하면 구성할 수 있는 옵션을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c02b-120">Click the arrow to view available options to be configured.</span></span> <span data-ttu-id="1c02b-121">이러한 옵션을 기본값으로 그대로 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c02b-121">You can choose to leave these options with their default value.</span></span> <span data-ttu-id="1c02b-122">사용 가능한 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1c02b-122">The available options are:</span></span>  
  
-   <span data-ttu-id="1c02b-123">**연결 제한 시간**: 제한 시간이 초과되기 전에 Oracle용 CDC Service가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결될 때까지 기다리는 시간(초)을 입력합니다. 기본값은 **15**입니다.</span><span class="sxs-lookup"><span data-stu-id="1c02b-123">**Connection Timeout**: Type the time (in seconds) that the CDC Service for Oracle waits for a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before timing out. The default value is **15**.</span></span>  
  
-   <span data-ttu-id="1c02b-124">**실행 제한 시간**: 제한 시간이 초과되기 전에 Oracle CDC Windows 서비스에서 명령이 실행될 때까지 기다리는 시간(초)을 입력합니다. 기본값은 **30**입니다.</span><span class="sxs-lookup"><span data-stu-id="1c02b-124">**Execution Timeout**: Type the time (in seconds) that the Oracle CDC Windows Service waits for a command to execute before timing out. The default value is **30**.</span></span>  
  
-   <span data-ttu-id="1c02b-125">**연결 암호화**: 암호화된 연결을 사용하는 대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스와 Oracle CDC Service 사이의 통신을 위해 **연결 암호화**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1c02b-125">**Encrypt Connection**: Select **Encrypt Connection** for communication between the Oracle CDC Service and the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance using an encrypted connection.</span></span>  
  
-   <span data-ttu-id="1c02b-126">**고급**: 필요한 경우 모든 추가 연결 속성을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1c02b-126">**Advanced**: Type any additional connection properties, if necessary.</span></span>  
  
### <a name="view-script"></a><span data-ttu-id="1c02b-127">스크립트 보기</span><span class="sxs-lookup"><span data-stu-id="1c02b-127">View Script</span></span>  
 <span data-ttu-id="1c02b-128">설치 스크립트의 읽기 전용 버전을 보려면 **스크립트 보기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1c02b-128">Click **View Script** to view a read-only version of the setup script.</span></span> <span data-ttu-id="1c02b-129">필요한 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 관리자는 이 스크립트를 SQL Server 관리 콘솔에 복사하여 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c02b-129">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator can copy this script into the SQL Server Management Console to edit it, if necessary.</span></span> <span data-ttu-id="1c02b-130">SQL Server 스크립트 준비에 대한 자세한 내용은 [Oracle CDC를 위한 SQL Server 준비-스크립트 보기](prepare-sql-server-for-oracle-cdc-view-script.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1c02b-130">For more information about the Prepare SQL Server Script, see [Prepare SQL Server for Oracle CDC-View Script](prepare-sql-server-for-oracle-cdc-view-script.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c02b-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1c02b-131">See Also</span></span>  
 <span data-ttu-id="1c02b-132">[CDC Service에서 작업하는 방법](work-with-cdc-services.md) </span><span class="sxs-lookup"><span data-stu-id="1c02b-132">[How to Work with CDC Services](work-with-cdc-services.md) </span></span>  
 [<span data-ttu-id="1c02b-133">CDC를 위해 SQL Server를 준비하는 방법</span><span class="sxs-lookup"><span data-stu-id="1c02b-133">How to Prepare SQL Server for CDC</span></span>](prepare-sql-server-for-cdc.md)  
  
  
