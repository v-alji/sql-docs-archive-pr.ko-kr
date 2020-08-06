---
title: SQL Server 변경 데이터베이스 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- oraIns
ms.assetid: 4f79c24a-e99a-4a06-8637-51eeec406259
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0eaeb26d5bea4c9e50db29aaa45297ba763dbbfa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740216"
---
# <a name="create-the-sql-server-change-database"></a><span data-ttu-id="bf054-102">SQL Server 변경 데이터베이스 만들기</span><span class="sxs-lookup"><span data-stu-id="bf054-102">Create the SQL Server Change Database</span></span>
  <span data-ttu-id="bf054-103">새 인스턴스 마법사를 시작하면 CDC 데이터베이스 만들기 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="bf054-103">When you start the New Instance wizard, the Create CDC Database page opens.</span></span> <span data-ttu-id="bf054-104">CDC 데이터베이스 만들기 페이지를 사용하여 새 CDC 인스턴스에 대한 정보를 제공하고 변경 데이터베이스를 새로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf054-104">Use the Create CDC Database page to provide information about the new CDC instance and create a new Change database.</span></span>  
  
 <span data-ttu-id="bf054-105">새로 만든 CDC 데이터베이스는 SQL Server CDC에 사용할 수 있도록 설정되며 이를 위해서는 `sysadmin` 고정 서버 역할의 멤버인 로그인이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="bf054-105">When you create a new CDC database it is enabled for SQL Server CDC and this enablement requires a login that is a member of the `sysadmin` fixed-server role.</span></span>  
  
 <span data-ttu-id="bf054-106">Oracle CDC 인스턴스 만들기 마법사를 시작하는 사용자가 `sysadmin` 고정 서버 역할의 멤버가 아닌 경우 SQL Server에 연결 대화 상자가 열리고 SQL Server CDC에 데이터베이스 사용 태스크를 수행하기 위한 sysadmin 역할의 멤버 자격 증명을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="bf054-106">When a user that starts the Create an Oracle CDC Instance wizard is not a member of the `sysadmin` fixed-server role, the Connect to SQL Server dialog box opens and requests the credentials for a member of the sysadmin role to carry out the Enable the database for SQL Server CDC task.</span></span> <span data-ttu-id="bf054-107">CDC 데이터베이스가 만들어지면 `sysadmin` 로그인은 삭제되고 Oracle Designer 콘솔 시작 시 사용된 원래 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인으로 작업이 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf054-107">When the CDC database is created, the `sysadmin` login is discarded and work resumes with the original [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login used when the Oracle Designer Console was entered.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bf054-108">SQL Server CDC에 데이터베이스 사용 이외의 태스크의 경우 새 인스턴스 마법사를 실행하는 데 사용된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인에 MSXDBCDC 데이터베이스에 대한 `dbcreator` 고정 서버 역할과 UPDATE 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf054-108">For tasks other than Enable the database for SQL Server CDC of, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login used for running the New Instance Wizard must have the `dbcreator` fixed-server role and UPDATE permissions on the MSXDBCDC database.</span></span>  
  
 <span data-ttu-id="bf054-109">SQL 서버에 연결 대화 상자에서 데이터를 입력하는 방법은 [SQL Server Connection for Instance Creation](sql-server-connection-for-instance-creation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bf054-109">For information on entering the data in the Connect to SQL Server dialog box, see [SQL Server Connection for Instance Creation](sql-server-connection-for-instance-creation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="bf054-110">옵션</span><span class="sxs-lookup"><span data-stu-id="bf054-110">Options</span></span>  
 <span data-ttu-id="bf054-111">**Oracle CDC 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="bf054-111">**Oracle CDC Instance**</span></span>  
 <span data-ttu-id="bf054-112">만들려는 CDC 인스턴스에 대한 다음 정보를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bf054-112">Type the following information about the CDC instance you are creating.</span></span>  
  
-   <span data-ttu-id="bf054-113">**이름**: 새 서비스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bf054-113">**Name**: Type a name for the new service.</span></span> <span data-ttu-id="bf054-114">이 이름은 새 변경 데이터베이스의 이름이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf054-114">This will also be the name of the new Change database.</span></span>  
  
-   <span data-ttu-id="bf054-115">**설명**: 새 인스턴스를 식별하는 데 도움이 되는 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bf054-115">**Description**: Type a description for the new instance to help you identify it.</span></span> <span data-ttu-id="bf054-116">이 구성 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="bf054-116">This is optional.</span></span>  
  
 <span data-ttu-id="bf054-117">**SQL Server 변경 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="bf054-117">**SQL Server Change Database**</span></span>  
 <span data-ttu-id="bf054-118">이 섹션은 데이터베이스를 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf054-118">This section is used to create the database.</span></span>  
  
1.  <span data-ttu-id="bf054-119">**변경 데이터베이스**: 이 이름은 새 변경 데이터베이스의 이름이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf054-119">**Change Database**: The name of the new Change database.</span></span> <span data-ttu-id="bf054-120">데이터베이스의 이름은 인스턴스에 대해 지정한 이름과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="bf054-120">The name of the database is the same as the name that you gave to the instance.</span></span> <span data-ttu-id="bf054-121">이 읽기 전용 필드에는 데이터베이스의 전체 경로가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf054-121">This read-only field displays the full path to the database.</span></span>  
  
2.  <span data-ttu-id="bf054-122">**데이터베이스 만들기**: **데이터베이스 만들기** 를 클릭하여 데이터베이스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf054-122">**Create Database**: Click **Create Database** to create the database.</span></span>  
  
     <span data-ttu-id="bf054-123">데이터베이스를 만들려면 로그인에 `sysasmin` 서버 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf054-123">To create the database, the login must have the `sysasmin` server role.</span></span> <span data-ttu-id="bf054-124">자세한 내용은 위의 보안 참고 사항을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bf054-124">See the security note above for more information.</span></span>  
  
     <span data-ttu-id="bf054-125">데이터베이스를 만든 후 **다음** 을 클릭하여 [Connect to an Oracle Source Database](connect-to-an-oracle-source-database.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="bf054-125">After you create the database, you can click **Next** to [Connect to an Oracle Source Database](connect-to-an-oracle-source-database.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf054-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bf054-126">See Also</span></span>  
 <span data-ttu-id="bf054-127">[SQL Server 변경 데이터베이스 인스턴스를 만드는 방법](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="bf054-127">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 [<span data-ttu-id="bf054-128">Oracle CDC Service</span><span class="sxs-lookup"><span data-stu-id="bf054-128">The Oracle CDC Service</span></span>](the-oracle-cdc-service.md)  
  
  
