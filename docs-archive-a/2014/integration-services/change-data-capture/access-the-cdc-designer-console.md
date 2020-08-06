---
title: CDC Designer 콘솔 액세스 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- accMsDes
ms.assetid: b168c64e-c1b5-42d4-a92a-84de1dd0324e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7f4f6e4df0a514cb29e36bcd1270b2537dc3ba68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741200"
---
# <a name="access-the-cdc-designer-console"></a><span data-ttu-id="e6fc4-102">CDC Designer 콘솔 액세스</span><span class="sxs-lookup"><span data-stu-id="e6fc4-102">Access the CDC Designer Console</span></span>
  <span data-ttu-id="e6fc4-103">콘솔을 설치한 컴퓨터에서 CDC Designer 콘솔에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc4-103">You can access the CDC Designer Console from the computer where you installed the console.</span></span> <span data-ttu-id="e6fc4-104">설치에 대한 자세한 내용은 설치를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e6fc4-104">For more information about installation, see Installation.</span></span>  
  
 <span data-ttu-id="e6fc4-105">CDC Designer 콘솔을 열 때 SQL Server에 연결 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc4-105">When you open the CDC Designer Console, the Connect to SQL Server dialog box opens.</span></span>  
  
 <span data-ttu-id="e6fc4-106">CDC Designer에 액세스하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인은 MSXDBCDC 데이터베이스에 대한 UPDATE 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc4-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login that accesses the CDC Designer must have UPDATE permissions on the MSXDBCDC database.</span></span> <span data-ttu-id="e6fc4-107">또한 새 Oracle CDC 인스턴스를 만들려면 `dbcreator` 고정 서버 역할이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc4-107">In addition, the login must also have the `dbcreator` fixed-server role to create new Oracle CDC Instances.</span></span> <span data-ttu-id="e6fc4-108">사용 중인 CDC 데이터베이스에 대한 SELECT 권한도 로그인이 갖는 것이 좋습니다. 그렇지 않으면 사용자가 해당 데이터베이스의 상태를 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc4-108">It is recommended that the login also have SELECT access to the CDC databases being used or the user will not be able to view the state of those databases.</span></span>  
  
 <span data-ttu-id="e6fc4-109">SQL Server에 연결 대화 상자에 다음 정보를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc4-109">Enter the following information in the Connect to SQL Server dialog box.</span></span>  
  
### <a name="server-name"></a><span data-ttu-id="e6fc4-110">서버 이름</span><span class="sxs-lookup"><span data-stu-id="e6fc4-110">Server Name</span></span>  
 <span data-ttu-id="e6fc4-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 있는 서버의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc4-111">Type the name of the server where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is located.</span></span>  
  
### <a name="authentication"></a><span data-ttu-id="e6fc4-112">인증</span><span class="sxs-lookup"><span data-stu-id="e6fc4-112">Authentication</span></span>  
 <span data-ttu-id="e6fc4-113">다음 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc4-113">Select one of the following:</span></span>  
  
-   <span data-ttu-id="e6fc4-114">**Windows 인증**</span><span class="sxs-lookup"><span data-stu-id="e6fc4-114">**Windows Authentication**</span></span>  
  
-   <span data-ttu-id="e6fc4-115">**SQL Server 인증**: 이 옵션을 선택하는 경우 연결 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 사용자의 **로그인** 및 **암호**를 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc4-115">**SQL Server Authentication**: If you select this option, you must type the **Login** and **Password** for the user in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you are connecting to.</span></span>  
  
 <span data-ttu-id="e6fc4-116">MSXCDCDB 데이터베이스에 대한 액세스를 허용하는 데이터베이스 역할이 로그인에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc4-116">The login must have a database role that allows access to the MSXCDCDB database.</span></span> <span data-ttu-id="e6fc4-117">사용 중인 모든 추가 데이터베이스에 대한 액세스 권한도 있는 것이 좋습니다. 그렇지 않으면 사용자가 해당 데이터베이스의 데이터를 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc4-117">It is recommended that the login also have access to any additional databases being used or the user will not be able to view the data in those databases.</span></span>  
  
### <a name="options"></a><span data-ttu-id="e6fc4-118">옵션</span><span class="sxs-lookup"><span data-stu-id="e6fc4-118">Options</span></span>  
 <span data-ttu-id="e6fc4-119">화살표를 클릭하면 구성할 수 있는 옵션을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc4-119">Click the arrow to view available options to be configured.</span></span> <span data-ttu-id="e6fc4-120">이러한 옵션을 기본값으로 그대로 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc4-120">You can choose to leave these options with their default value.</span></span> <span data-ttu-id="e6fc4-121">사용 가능한 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc4-121">The available options are:</span></span>  
  
 <span data-ttu-id="e6fc4-122">**연결 제한 시간**</span><span class="sxs-lookup"><span data-stu-id="e6fc4-122">**Connection Timeout**</span></span>  
 <span data-ttu-id="e6fc4-123">제한 시간이 초과되기 전에 Oracle용 CDC Service가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결될 때까지 기다리는 시간(초)을 입력합니다. 기본값은 **15**입니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc4-123">Type the time (in seconds) that the CDC Service for Oracle waits for a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before timing out. The default value is **15**.</span></span>  
  
 <span data-ttu-id="e6fc4-124">**실행 제한 시간**</span><span class="sxs-lookup"><span data-stu-id="e6fc4-124">**Execution Timeout**</span></span>  
 <span data-ttu-id="e6fc4-125">제한 시간이 초과되기 전에 Oracle CDC Windows 서비스에서 명령이 실행될 때까지 기다리는 시간(초)을 입력합니다. 기본값은 **30**입니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc4-125">Type the time (in seconds) that the Oracle CDC Windows Service waits for a command to execute before timing out. The default value is **30**.</span></span>  
  
 <span data-ttu-id="e6fc4-126">**연결 암호화**</span><span class="sxs-lookup"><span data-stu-id="e6fc4-126">**Encrypt Connection**</span></span>  
 <span data-ttu-id="e6fc4-127">암호화된 연결을 사용하는 대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스와 Oracle CDC Service 사이의 통신을 위해 **연결 암호화**를 선택합니다.**고급**: **고급** 을 클릭하고 필요한 경우 고급 연결 속성 대화 상자에 추가 연결 속성을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc4-127">Select **Encrypt Connection** for communication between the Oracle CDC Service and the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance using an encrypted connection.**Advanced**: Click **Advanced** and type any additional connection properties into the Advanced Connection Properties dialog box, if necessary.</span></span>  
  
 <span data-ttu-id="e6fc4-128">**고급**</span><span class="sxs-lookup"><span data-stu-id="e6fc4-128">**Advanced**</span></span>  
 <span data-ttu-id="e6fc4-129">**고급** 을 클릭하고 필요한 경우 고급 연결 속성 대화 상자에 추가 연결 속성을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc4-129">Click **Advanced** and type any additional connection properties into the Advanced Connection Properties dialog box, if necessary.</span></span>  
  
 <span data-ttu-id="e6fc4-130">고급 연결 속성 대화 상자에 대한 자세한 내용은 [Advanced Connection Properties](advanced-connection-properties.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e6fc4-130">For information about the Advanced Connection Properties dialog box, see [Advanced Connection Properties](advanced-connection-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6fc4-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e6fc4-131">See Also</span></span>  
 [<span data-ttu-id="e6fc4-132">SQL Server 연결을 위해 CDC Designer에 대해 필요한 권한</span><span class="sxs-lookup"><span data-stu-id="e6fc4-132">SQL Server Connection Required Permissions for the CDC Designer</span></span>](sql-server-connection-required-permissions-for-the-cdc-designer.md)  
  
  
