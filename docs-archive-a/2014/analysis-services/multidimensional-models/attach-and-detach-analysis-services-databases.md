---
title: Analysis Services 데이터베이스 연결 및 분리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.ssms.detachdatabase.f1
- sql12.asvs.ssms.attachdatabase.f1
- sql12.asvs.ssmsimbi.AttachDatabase.f1
- sql12.asvs.ssmsimbi.DetachDatabase.f1
helpviewer_keywords:
- databases [Analysis Services], attach
- databases [Analysis Services], detach
ms.assetid: 41887413-2d47-49b8-8614-553cb799fb18
author: minewiskan
ms.author: owend
ms.openlocfilehash: cd72277970605691e06f3baacf167ea135343b3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660721"
---
# <a name="attach-and-detach-analysis-services-databases"></a><span data-ttu-id="b06d5-102">Analysis Services 데이터베이스 연결 및 분리</span><span class="sxs-lookup"><span data-stu-id="b06d5-102">Attach and Detach Analysis Services Databases</span></span>
  <span data-ttu-id="b06d5-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DBA(데이터베이스 관리자)는 종종 일정 기간 동안 데이터베이스를 오프라인 상태로 유지하다가 동일한 서버 인스턴스 또는 다른 서버 인스턴스에서 해당 데이터베이스를 다시 온라인 상태로 되돌려야 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-103">There are often situations when an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database administrator (dba) wants to take a database offline for a period, and then bring that database back online on the same server instance, or on a different one.</span></span> <span data-ttu-id="b06d5-104">이러한 경우는 보다 나은 성능, 데이터베이스 확장에 따른 공간 확보, 또는 제품 업그레이드를 위해 데이터베이스를 다른 디스크로 이동하는 것과 같이 대부분 비즈니스 요구 사항에 의해 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-104">These situations are often driven by business needs, such as moving the database to a different disk for better performance, gaining room for database growth, or to upgrade a product.</span></span> <span data-ttu-id="b06d5-105">이러한 모든 상황은 물론 다른 상황에서도 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DBA는 `Attach` 및 `Detach` 명령을 사용하여 아주 간단히 데이터베이스를 오프라인 상태로 유지하다가 다시 온라인 상태로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-105">For all those cases and more, the `Attach` and `Detach` commands enable the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dba to take the database offline and bring it back online with little effort.</span></span>  
  
## <a name="attach-and-detach-commands"></a><span data-ttu-id="b06d5-106">Attach 및 Detach 명령</span><span class="sxs-lookup"><span data-stu-id="b06d5-106">Attach and Detach commands</span></span>  
 <span data-ttu-id="b06d5-107">`Attach` 명령을 사용하면 오프라인 상태였던 데이터베이스를 온라인 상태로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-107">The `Attach` command enables you to bring online a database that was taken offline.</span></span> <span data-ttu-id="b06d5-108">데이터베이스를 원래 서버 인스턴스나 다른 인스턴스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-108">You can attach the database to the original server instance, or to another instance.</span></span> <span data-ttu-id="b06d5-109">데이터베이스를 연결하면 사용자가 데이터베이스에 대해 **ReadWriteMode** 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-109">When you attach a database the user can specify the **ReadWriteMode** setting for the database.</span></span> <span data-ttu-id="b06d5-110">`Detach` 명령을 사용하면 데이터베이스를 서버로부터 오프라인 상태로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-110">The `Detach` command enables you to take offline a database from the server.</span></span>  
  
## <a name="attach-and-detach-usage"></a><span data-ttu-id="b06d5-111">Attach 및 Detach 용도</span><span class="sxs-lookup"><span data-stu-id="b06d5-111">Attach and Detach Usage</span></span>  
 <span data-ttu-id="b06d5-112">`Attach` 명령은 기존 데이터베이스 구조를 온라인 상태로 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-112">The `Attach` command is used to bring online an existing database structure.</span></span> <span data-ttu-id="b06d5-113">데이터베이스가 `ReadWrite` 모드로 연결된 경우 서버 인스턴스에 한 번만 연결할 수 있지만</span><span class="sxs-lookup"><span data-stu-id="b06d5-113">If the database is attached in `ReadWrite` mode, it can be attached only one time to a server instance.</span></span> <span data-ttu-id="b06d5-114">`ReadOnly` 모드로 연결된 경우에는 여러 서버 인스턴스에 여러 번 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-114">However, if the database is attached in `ReadOnly` mode, it can be attached multiple times to different server instances.</span></span> <span data-ttu-id="b06d5-115">하지만 동일한 데이터베이스를 동일한 서버 인스턴스에 두 번 이상 연결할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-115">However, the same database cannot be attached more than one time to the same server instance.</span></span> <span data-ttu-id="b06d5-116">동일한 데이터베이스를 두 번 이상 연결하려고 하면 데이터가 별개의 폴더에 복사되었더라도 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-116">An error is raised when an attempt is made to attach the same database more than one time, even if the data has been copied to separate folders.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b06d5-117">데이터 분리 시 암호가 필요했다면 데이터베이스 연결 시에도 동일한 암호가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-117">If a password was required to detach the database, the same password is required to attach the database.</span></span>  
  
 <span data-ttu-id="b06d5-118">`Detach` 명령은 기존 데이터베이스 구조를 오프라인 상태로 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-118">The `Detach` command is used to take offline an existing database structure.</span></span> <span data-ttu-id="b06d5-119">데이터베이스를 분리할 때는 기밀 메타데이터 보호를 위해 암호를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-119">When a database is detached, you should provide a password to protect confidential metadata.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b06d5-120">데이터 파일의 내용을 보호하려면 폴더, 하위 폴더 및 데이터 파일에 대한 액세스 제어 목록을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-120">To protect the content of the data files, you should use an access control list for the folder, subfolders, and data files.</span></span>  
  
 <span data-ttu-id="b06d5-121">데이터베이스 분리 시 서버는 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-121">When you detach a database, the server follows these steps.</span></span>  
  
|<span data-ttu-id="b06d5-122">읽기/쓰기 데이터베이스 분리</span><span class="sxs-lookup"><span data-stu-id="b06d5-122">Detaching a read/write database</span></span>|<span data-ttu-id="b06d5-123">읽기 전용 데이터베이스 분리</span><span class="sxs-lookup"><span data-stu-id="b06d5-123">Detaching a read-only database</span></span>|  
|--------------------------------------|-------------------------------------|  
|<span data-ttu-id="b06d5-124">1) 서버가 데이터베이스에 대한 CommitExclusive 잠금 요청을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-124">1) The server issues a request for a CommitExclusive Lock on the database</span></span><br /><span data-ttu-id="b06d5-125">2) 서버가 진행 중인 모든 트랜잭션이 커밋되거나 롤백될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-125">2) The server waits until all ongoing transactions are either committed or rolled back</span></span><br /><span data-ttu-id="b06d5-126">3) 서버가 데이터베이스 분리를 위해 필요한 모든 메타데이터를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-126">3) The server builds all the metadata that it must have to detach the database</span></span><br /><span data-ttu-id="b06d5-127">4) 데이터베이스가 삭제된 것으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-127">4) The database is marked as deleted</span></span><br /><span data-ttu-id="b06d5-128">5) 서버가 트랜잭션을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-128">5) The server commits the transaction</span></span>|<span data-ttu-id="b06d5-129">1) 데이터베이스가 삭제된 것으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-129">1) The database is marked as deleted</span></span><br /><span data-ttu-id="b06d5-130">2) 서버가 트랜잭션을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-130">2) The server commits the transaction</span></span><br /><br /> <br /><br /> <span data-ttu-id="b06d5-131">참고: 읽기 전용 데이터베이스에 대한 분리 암호는 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-131">Note: The detaching password cannot be changed for a read-only database.</span></span> <span data-ttu-id="b06d5-132">암호를 이미 포함하고 있는 연결된 데이터베이스에 암호 매개 변수를 제공하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-132">An error is raised if the password parameter is provided for an attached database that already contains a password.</span></span>|  
  
 <span data-ttu-id="b06d5-133">`Attach` 및 `Detach` 명령은 단일 작업으로 실행해야 하며</span><span class="sxs-lookup"><span data-stu-id="b06d5-133">The `Attach` and `Detach` commands must be executed as single operations.</span></span> <span data-ttu-id="b06d5-134">동일 트랜잭션 내 다른 작업과 결합할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-134">They cannot be combined with other operations in the same transaction.</span></span> <span data-ttu-id="b06d5-135">또한 `Attach` 및 `Detach` 명령은 원자성 트랜잭션 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-135">Also, the `Attach` and `Detach` commands are atomic transactional commands.</span></span> <span data-ttu-id="b06d5-136">작업이 성공하거나 실패하거나 둘 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-136">This means the operation will either succeed or fail.</span></span> <span data-ttu-id="b06d5-137">완료되지 않은 상태로 남는 데이터베이스는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-137">No database will be left in an uncompleted state.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b06d5-138">`Detach` 명령을 실행하려면 서버 또는 데이터베이스 관리자 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-138">Server or database administrator privileges are required to execute the `Detach` command.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b06d5-139">`Attach` 명령을 실행하려면 서버 관리자 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b06d5-139">Server administrator privileges are required to execute the `Attach` command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b06d5-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b06d5-140">See Also</span></span>  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <span data-ttu-id="b06d5-141">[Microsoft.analysisservices.sharepoint.integration.dll \*입니다.](/dotnet/api/microsoft.analysisservices.core.database.detach) </span><span class="sxs-lookup"><span data-stu-id="b06d5-141">[Microsoft.AnalysisServices.Database.Detach\*](/dotnet/api/microsoft.analysisservices.core.database.detach) </span></span>  
 <span data-ttu-id="b06d5-142">[Analysis Services 데이터베이스 이동](move-an-analysis-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="b06d5-142">[Move an Analysis Services Database](move-an-analysis-services-database.md) </span></span>  
 <span data-ttu-id="b06d5-143">[데이터베이스 ReadWriteModes](database-readwritemodes.md) </span><span class="sxs-lookup"><span data-stu-id="b06d5-143">[Database ReadWriteModes](database-readwritemodes.md) </span></span>  
 <span data-ttu-id="b06d5-144">[ReadOnly 모드와 ReadWrite 모드 간 Analysis Services 데이터베이스 전환](switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md) </span><span class="sxs-lookup"><span data-stu-id="b06d5-144">[Switch an Analysis Services database between ReadOnly and ReadWrite modes](switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md) </span></span>  
 <span data-ttu-id="b06d5-145">[Detach 요소](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element) </span><span class="sxs-lookup"><span data-stu-id="b06d5-145">[Detach Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element) </span></span>  
 [<span data-ttu-id="b06d5-146">Attach 요소</span><span class="sxs-lookup"><span data-stu-id="b06d5-146">Attach Element</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element)  
  
  
