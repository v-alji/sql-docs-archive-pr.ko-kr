---
title: 인스턴스를 만들기 위한 SQL Server 연결 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 81d0e7e2-d8f0-4bd9-9565-218ce996f28e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cdff17b763257c2a3280981c1f5c16040cc61413
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647809"
---
# <a name="sql-server-connection-for-instance-creation"></a><span data-ttu-id="ff2bf-102">인스턴스를 만들기 위한 SQL Server 연결</span><span class="sxs-lookup"><span data-stu-id="ff2bf-102">SQL Server Connection for Instance Creation</span></span>
  <span data-ttu-id="ff2bf-103">Oracle CDC 인스턴스를 만드는 첫 번째 단계 중 하나는 대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 CDC 데이터베이스를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ff2bf-103">One of the first steps when creating an Oracle CDC Instance is the creation of a CDC database on the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="ff2bf-104">이 CDC 데이터베이스가 SQL Server CDC에 사용되며 이를 위해서는 `sysadmin` 고정 서버 역할의 멤버인 로그인이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ff2bf-104">This CDC database is enabled for SQL Server CDC and this enablement requires a login that is a member of the `sysadmin` fixed-server role.</span></span>  
  
 <span data-ttu-id="ff2bf-105">**Oracle CDC 인스턴스 만들기** 마법사를 시작하는 사용자가 `sysadmin` 고정 서버 역할의 멤버가 아닌 경우 **SQL Server에 연결** 대화 상자가 열리고 SQL Server CDC에 데이터베이스 사용 태스크를 수행하기 위한 `sysadmin` 역할의 멤버에 대해 자격 증명을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="ff2bf-105">When a user that starts the **Create an Oracle CDC Instance** wizard is not a member of the `sysadmin` fixed-server role, the **Connect to SQL Server** dialog box opens and requests the credentials for a member of the `sysadmin` role to carry out the Enable the database for SQL Server CDC task.</span></span> <span data-ttu-id="ff2bf-106">CDC 데이터베이스가 만들어지면 `sysadmin` 로그인은 삭제되고 Oracle Designer 콘솔 시작 시 사용된 원래 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인으로 작업이 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff2bf-106">When the CDC database is created, the `sysadmin` login is discarded and work resumes with the original [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login used when the Oracle Designer Console was entered.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="ff2bf-107">작업 목록</span><span class="sxs-lookup"><span data-stu-id="ff2bf-107">Task List</span></span>  
 <span data-ttu-id="ff2bf-108">**SQL Server에 연결** 대화 상자에 다음 정보를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ff2bf-108">Enter the following information in the **Connect to SQL Server** dialog box.</span></span>  
  
 <span data-ttu-id="ff2bf-109">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="ff2bf-109">**Server Name**</span></span>  
 <span data-ttu-id="ff2bf-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 있는 서버의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ff2bf-110">Type the name of the server where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is located.</span></span>  
  
 <span data-ttu-id="ff2bf-111">**인증**</span><span class="sxs-lookup"><span data-stu-id="ff2bf-111">**Authentication**</span></span>  
 <span data-ttu-id="ff2bf-112">다음 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ff2bf-112">Select one of the following:</span></span>  
  
-   <span data-ttu-id="ff2bf-113">**Windows 인증**</span><span class="sxs-lookup"><span data-stu-id="ff2bf-113">**Windows Authentication**</span></span>  
  
-   <span data-ttu-id="ff2bf-114">**SQL Server 인증**: 이 옵션을 선택하는 경우 연결 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 사용자의 **로그인** 및 **암호**를 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff2bf-114">**SQL Server Authentication**: If you select this option, you must type the **Login** and **Password** for the user in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you are connecting to.</span></span>  
  
 <span data-ttu-id="ff2bf-115">MSXCDCDB 데이터베이스에 대한 액세스를 허용하는 데이터베이스 역할이 로그인에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff2bf-115">The login must have a database role that allows access to the MSXCDCDB database.</span></span> <span data-ttu-id="ff2bf-116">사용 중인 모든 추가 데이터베이스에 대한 액세스 권한도 있는 것이 좋습니다. 그렇지 않으면 사용자가 해당 데이터베이스의 데이터를 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ff2bf-116">It is recommended that the login also have access to any additional databases being used or the user will not be able to view the data in those databases.</span></span>  
  
 <span data-ttu-id="ff2bf-117">**옵션**</span><span class="sxs-lookup"><span data-stu-id="ff2bf-117">**Options**</span></span>  
 <span data-ttu-id="ff2bf-118">화살표를 클릭하면 구성할 수 있는 옵션을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff2bf-118">Click the arrow to view available options to be configured.</span></span> <span data-ttu-id="ff2bf-119">이러한 옵션을 기본값으로 그대로 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff2bf-119">You can choose to leave these options with their default value.</span></span> <span data-ttu-id="ff2bf-120">사용 가능한 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ff2bf-120">The available options are:</span></span>  
  
-   <span data-ttu-id="ff2bf-121">**연결 제한 시간**: 제한 시간이 초과되기 전에 Oracle용 CDC Service가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결될 때까지 기다리는 시간(초)을 입력합니다. 기본값은 **15**입니다.</span><span class="sxs-lookup"><span data-stu-id="ff2bf-121">**Connection Timeout**: Type the time (in seconds) that the CDC Service for Oracle waits for a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before timing out. The default value is **15**.</span></span>  
  
-   <span data-ttu-id="ff2bf-122">**실행 제한 시간**: 제한 시간이 초과되기 전에 Oracle CDC Windows 서비스에서 명령이 실행될 때까지 기다리는 시간(초)을 입력합니다. 기본값은 **30**입니다.</span><span class="sxs-lookup"><span data-stu-id="ff2bf-122">**Execution Timeout**: Type the time (in seconds) that the Oracle CDC Windows Service waits for a command to execute before timing out. The default value is **30**.</span></span>  
  
-   <span data-ttu-id="ff2bf-123">**연결 암호화**: 암호화된 연결을 사용하는 대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스와 Oracle CDC Service 사이의 통신을 위해 **연결 암호화**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ff2bf-123">**Encrypt Connection**: Select **Encrypt Connection** for communication between the Oracle CDC Service and the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance using an encrypted connection.</span></span>  
  
-   <span data-ttu-id="ff2bf-124">**고급**: **고급** 을 클릭하고 필요한 경우 고급 연결 속성 대화 상자에 추가 연결 속성을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ff2bf-124">**Advanced**: Click **Advanced** and type any additional connection properties into the Advanced Connection Properties dialog box, if necessary.</span></span>  
  
     <span data-ttu-id="ff2bf-125">고급 연결 속성 대화 상자에 대한 자세한 내용은 [Advanced Connection Properties](advanced-connection-properties.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ff2bf-125">For information about the Advanced Connection Properties dialog box, see [Advanced Connection Properties](advanced-connection-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff2bf-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ff2bf-126">See Also</span></span>  
 <span data-ttu-id="ff2bf-127">[SQL Server 변경 데이터베이스 만들기](create-the-sql-server-change-database.md) </span><span class="sxs-lookup"><span data-stu-id="ff2bf-127">[Create the SQL Server Change Database](create-the-sql-server-change-database.md) </span></span>  
 [<span data-ttu-id="ff2bf-128">SQL Server 연결을 위해 CDC Designer에 대해 필요한 권한</span><span class="sxs-lookup"><span data-stu-id="ff2bf-128">SQL Server Connection Required Permissions for the CDC Designer</span></span>](sql-server-connection-required-permissions-for-the-cdc-designer.md)  
  
  
