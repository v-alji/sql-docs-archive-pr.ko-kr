---
title: 삭제를 위해 SQL Server에 연결 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 030b10c2-6b88-4c2c-bf67-22994be25a60
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f5f069f7686e8b6fa9176f92c9e2f47be5f2c71a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647813"
---
# <a name="connection-to-sql-server-for-delete"></a><span data-ttu-id="590e5-102">삭제를 위해 SQL Server에 연결</span><span class="sxs-lookup"><span data-stu-id="590e5-102">Connection to SQL Server for Delete</span></span>
  <span data-ttu-id="590e5-103">MSXDBCDC 데이터베이스에 대해 쓰기 권한이 포함된 데이터베이스 역할(예: **db_owner** 역할)이 없는 로그인이 Oracle CDC 인스턴스를 삭제하려고 시도하면 SQL Server에 연결 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="590e5-103">When a login without a database role that includes write permission (for example the **db_owner** role) to the MSXDBCDC database attempts to delete an Oracle CDC instance, the Connect to SQL Server dialog box is displayed.</span></span>  
  
 <span data-ttu-id="590e5-104">이 대화 상자에서 **db_owner** 데이터베이스 역할과 같이 MSXDBCDC 데이터베이스에 대해 쓰기 권한이 있는 로그인의 자격 증명을 입력하여 Oracle CDC 인스턴스를 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="590e5-104">In this dialog box you must enter the credentials for a login that has write permission to the MSXDBCDC database, such the **db_owner** database role to delete the Oracle CDC instance.</span></span>  
  
 <span data-ttu-id="590e5-105">SQL Server에 연결 대화 상자에 다음 정보를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="590e5-105">Enter the following information in the Connect to SQL Server dialog box.</span></span>  
  
 <span data-ttu-id="590e5-106">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="590e5-106">**Server Name**</span></span>  
 <span data-ttu-id="590e5-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 있는 서버의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="590e5-107">Type the name of the server where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is located.</span></span>  
  
 <span data-ttu-id="590e5-108">**인증**</span><span class="sxs-lookup"><span data-stu-id="590e5-108">**Authentication**</span></span>  
 <span data-ttu-id="590e5-109">다음 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="590e5-109">Select one of the following:</span></span>  
  
-   <span data-ttu-id="590e5-110">**Windows 인증**</span><span class="sxs-lookup"><span data-stu-id="590e5-110">**Windows Authentication**</span></span>  
  
-   <span data-ttu-id="590e5-111">**SQL Server 인증**: 이 옵션을 선택하는 경우 연결 중인 **에서 사용자의** 로그인 **및** 암호 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="590e5-111">**SQL Server Authentication**: If you select this option, you must type the **Login** and **Password** for the user in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you are connecting to.</span></span>  
  
 <span data-ttu-id="590e5-112">**옵션**</span><span class="sxs-lookup"><span data-stu-id="590e5-112">**Options**</span></span>  
 <span data-ttu-id="590e5-113">화살표를 클릭하면 구성할 수 있는 옵션을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="590e5-113">Click the arrow to view available options to be configured.</span></span> <span data-ttu-id="590e5-114">이러한 옵션을 기본값으로 그대로 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="590e5-114">You can choose to leave these options with their default value.</span></span> <span data-ttu-id="590e5-115">사용 가능한 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="590e5-115">The available options are:</span></span>  
  
-   <span data-ttu-id="590e5-116">**연결 제한 시간**: 시간 초과 오류가 발생하기 전에 프로그램이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결될 때까지 기다리는 시간(초)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="590e5-116">**Connection Timeout**: Type the time (in seconds) the program waits for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection to be established before producing a timeout error.</span></span> <span data-ttu-id="590e5-117">기본값은 **15**입니다.</span><span class="sxs-lookup"><span data-stu-id="590e5-117">The default value is **15**.</span></span>  
  
-   <span data-ttu-id="590e5-118">**실행 제한 시간**: 시간 초과 오류가 발생하기 전에 프로그램이 SQL 명령 실행을 마칠 때까지 기다리는 시간(초)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="590e5-118">**Execution Timeout**: Type the time (in seconds) that the program waits for SQL command execution to finish before producing a timeout error.</span></span> <span data-ttu-id="590e5-119">기본값은 **30**입니다.</span><span class="sxs-lookup"><span data-stu-id="590e5-119">The default value is **30**.</span></span>  
  
-   <span data-ttu-id="590e5-120">**연결 암호화**: 설정 중인 **연결을 암호화하여 개인 정보를 보호하려면** 연결 암호화 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="590e5-120">**Encrypt Connection**: Select **Encrypt Connection** to ensure that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection that being established is encrypted to guarantee privacy.</span></span>  
  
-   <span data-ttu-id="590e5-121">**고급**: **고급** 을 클릭하고 필요한 경우 고급 연결 속성 대화 상자에 추가 연결 속성을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="590e5-121">**Advanced**: Click **Advanced** and type any additional connection properties into the Advanced Connection Properties dialog box, if necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="590e5-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="590e5-122">See Also</span></span>  
 [<span data-ttu-id="590e5-123">SQL Server 연결 CDC Service에 필요한 권한</span><span class="sxs-lookup"><span data-stu-id="590e5-123">SQL Server Connection Required Permissions for the CDC Service</span></span>](sql-server-connection-required-permissions-for-the-cdc-service.md)  
  
  
