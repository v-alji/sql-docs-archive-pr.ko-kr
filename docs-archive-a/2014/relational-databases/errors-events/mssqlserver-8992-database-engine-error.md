---
title: MSSQLSERVER_8992 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8992 (Database Engine error)
ms.assetid: 68467e6a-09d8-478f-8bd9-3bb09453ada3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: adcf914accab43202cf148fe852b334c9b078287
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661662"
---
# <a name="mssqlserver_8992"></a><span data-ttu-id="9c74f-102">MSSQLSERVER_8992</span><span class="sxs-lookup"><span data-stu-id="9c74f-102">MSSQLSERVER_8992</span></span>
    
## <a name="details"></a><span data-ttu-id="9c74f-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="9c74f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9c74f-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="9c74f-104">Product Name</span></span>|<span data-ttu-id="9c74f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9c74f-105">SQL Server</span></span>|  
|<span data-ttu-id="9c74f-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="9c74f-106">Event ID</span></span>|<span data-ttu-id="9c74f-107">8992</span><span class="sxs-lookup"><span data-stu-id="9c74f-107">8992</span></span>|  
|<span data-ttu-id="9c74f-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="9c74f-108">Event Source</span></span>|<span data-ttu-id="9c74f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9c74f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9c74f-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="9c74f-110">Component</span></span>|<span data-ttu-id="9c74f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9c74f-111">SQLEngine</span></span>|  
|<span data-ttu-id="9c74f-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="9c74f-112">Symbolic Name</span></span>|<span data-ttu-id="9c74f-113">DBCC3_CHECK_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9c74f-113">DBCC3_CHECK_CATALOG</span></span>|  
|<span data-ttu-id="9c74f-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="9c74f-114">Message Text</span></span>|<span data-ttu-id="9c74f-115">카탈로그 메시지 ERROR, 수준 LEVEL, 상태 STATE: MESSAGE를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="9c74f-115">Check Catalog Msg ERROR Level LEVEL State STATE: MESSAGE.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9c74f-116">설명</span><span class="sxs-lookup"><span data-stu-id="9c74f-116">Explanation</span></span>  
 <span data-ttu-id="9c74f-117">DBCC CHECKCATALOG 또는 DBCC CHECKDB에서 지정된 개체에 대한 시스템 메타데이터 테이블 간의 불일치를 발견했습니다.</span><span class="sxs-lookup"><span data-stu-id="9c74f-117">DBCC CHECKCATALOG or DBCC CHECKDB found an inconsistency in the system metadata tables for the specified object.</span></span> <span data-ttu-id="9c74f-118">즉, 오류 메시지에 지정된 개체와 기록된 개체 ID가 일치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9c74f-118">That is, there is an inconsistency between the recorded object ID and the object specified in error message.</span></span>  
  
 <span data-ttu-id="9c74f-119">이 오류는 시스템 메타데이터의 불일치를 유발하는 방식으로 하나 이상의 시스템 테이블을 수동 업데이트한 경우에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c74f-119">This error can occur when one or more system tables has been manually updated in a way that creates an inconsistency in the system metadata.</span></span> <span data-ttu-id="9c74f-120">예를 들어 사용자가 **sysobjects** 테이블의 개체를 수동으로 삭제할 때 **sysindexes** 및 **syscolumns** 등의 다른 테이블에 있는 연관된 행을 제거하지 않았을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c74f-120">For example, a user may have manually deleted an object from the **sysobjects** table without removing associated rows in other tables such as **sysindexes** and **syscolumns**.</span></span>  
  
 <span data-ttu-id="9c74f-121">이 오류는 SQL Server 2000에서 SQL Server 2005 이상 버전으로 업그레이드된 데이터베이스에 대해 DBCC CHECKDB를 실행하는 경우에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c74f-121">This error can occur when running DBCC CHECKDB against a database that has been upgraded from SQL Server 2000 to SQL Server 2005 or later.</span></span> <span data-ttu-id="9c74f-122">SQL Server 2000의 경우 DBCC CHECKDB에 DBCC CHECKCATALOG 기능이 포함되지 않으므로 SQL Server 2000에서 데이터베이스에 대해 DBCC CHECKCATALOG를 명시적으로 실행하지 않는 한 이 오류는 업그레이드 이전에 발견되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9c74f-122">In SQL Server 2000, DBCC CHECKDB did not include DBCC CHECKCATALOG functionality, so the error would not be caught before upgrade unless DBCC CHECKCATALOG was specifically executed against the database in SQL Server 2000.</span></span>  
  
 <span data-ttu-id="9c74f-123">오류 8992와 함께 다음과 같은 오류가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c74f-123">You may see any of the following errors in conjunction with error 8992:</span></span>  
  
 <span data-ttu-id="9c74f-124">메시지 3851 - 시스템 테이블 sys.%ls%ls에서 잘못된 행(%ls)을 찾았습니다.</span><span class="sxs-lookup"><span data-stu-id="9c74f-124">Msg 3851 - An invalid row (%ls) was found in the system table sys.%ls%ls.</span></span>  
  
 <span data-ttu-id="9c74f-125">메시지 3852 - sys.%ls%ls의 행(%ls)과 대응하는 행(%ls)이 sys.%ls%ls에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9c74f-125">Msg 3852 - Row (%ls) in sys.%ls%ls does not have a matching row (%ls) in sys.%ls%ls.</span></span>  
  
 <span data-ttu-id="9c74f-126">3853 - sys.%ls%ls의 행(%ls)의 특성(%ls)과 대응하는 행(%ls)이 sys.%ls%ls에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9c74f-126">3853 - Attribute (%ls) of row (%ls) in sys.%ls%ls does not have a matching row (%ls) in sys.%ls%ls.</span></span>  
  
 <span data-ttu-id="9c74f-127">3854 - sys.%ls%ls의 행(%ls)의 특성(%ls)과 대응하는 행(%ls)이 sys.%ls%ls에 있으나 적합하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9c74f-127">3854 - Attribute (%ls) of row (%ls) in sys.%ls%ls has a matching row (%ls) in sys.%ls%ls that is invalid.</span></span>  
  
 <span data-ttu-id="9c74f-128">3855 - 특성(%ls)이 행(%ls)이 없는 상태로 sys.%ls%ls에 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="9c74f-128">3855 - Attribute (%ls) exists without a row (%ls) in sys.%ls%ls.</span></span>  
  
 <span data-ttu-id="9c74f-129">3856 - sys.%ls%ls의 행(%ls)에 있어서는 안 되는 특성(%ls)이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c74f-129">3856 - Attribute (%ls) exists but should not for row (%ls) in sys.%ls%ls.</span></span>  
  
 <span data-ttu-id="9c74f-130">3857 - sys.%ls%ls의 행(%ls)에 필요한 특성(%ls)이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9c74f-130">3857 - The attribute (%ls) is required but is missing for row (%ls) in sys.%ls%ls.</span></span>  
  
 <span data-ttu-id="9c74f-131">3858 - sys.%ls%ls의 행(%ls)의 특성(%ls)에 잘못된 값이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c74f-131">3858 - The attribute (%ls) of row (%ls) in sys.%ls%ls has an invalid value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9c74f-132">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="9c74f-132">User Action</span></span>  
  
### <a name="drop-and-re-create-the-specified-object"></a><span data-ttu-id="9c74f-133">지정된 개체 삭제 및 다시 만들기</span><span class="sxs-lookup"><span data-stu-id="9c74f-133">Drop and Re-create the Specified Object</span></span>  
 <span data-ttu-id="9c74f-134">가능한 경우 지정된 개체를 삭제하고 다시 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="9c74f-134">If possible, drop and recreate the specified object.</span></span> <span data-ttu-id="9c74f-135">예를 들어 개체가 저장 프로시저 또는 사용자 정의 형식인 경우 해당 개체를 다시 만들면 이 문제가 해결될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c74f-135">For example, if the object is a stored procedure or user-defined type, recreating the object may resolve the problem.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="9c74f-136">백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="9c74f-136">Restore from Backup</span></span>  
 <span data-ttu-id="9c74f-137">하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하세요.</span><span class="sxs-lookup"><span data-stu-id="9c74f-137">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span> <span data-ttu-id="9c74f-138">이 동작은 백업에 메타데이터 오류가 포함되지 않은 경우에만 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c74f-138">This action is only applicable if the backup does not contain the metadata error.</span></span>  
  
### <a name="export-the-data-to-a-new-database"></a><span data-ttu-id="9c74f-139">새 데이터베이스에 데이터 내보내기</span><span class="sxs-lookup"><span data-stu-id="9c74f-139">Export the Data to a New Database</span></span>  
 <span data-ttu-id="9c74f-140">백업에도 메타데이터 불일치가 있을 경우 새 데이터베이스를 만들어 기존 데이터베이스의 내용을 새 데이터베이스로 내보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c74f-140">If the backup also contains the metadata inconsistency, you need to create a new database and export the contents of the existing database to the new database.</span></span>  
  
### <a name="dbcc-checkdb-cannot-repair-this-error"></a><span data-ttu-id="9c74f-141">DBCC CHECKDB가 이 오류를 복구할 수 없음</span><span class="sxs-lookup"><span data-stu-id="9c74f-141">DBCC CHECKDB Cannot Repair This Error</span></span>  
 <span data-ttu-id="9c74f-142">이 오류를 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9c74f-142">This error cannot be repaired.</span></span>  <span data-ttu-id="9c74f-143">백업에서 데이터베이스를 복원할 수 없으면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] CSS(고객 서비스 지원 센터)에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="9c74f-143">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
### <a name="do-not-manually-update-system-tables"></a><span data-ttu-id="9c74f-144">시스템 테이블 수동 업데이트 금지</span><span class="sxs-lookup"><span data-stu-id="9c74f-144">Do Not Manually Update System Tables</span></span>  
 <span data-ttu-id="9c74f-145">시스템 테이블을 수동으로 업데이트하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="9c74f-145">Do not make manual updates to system tables.</span></span> <span data-ttu-id="9c74f-146">SQL Server는 시스템 데이터베이스에 대한 수동 변경을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9c74f-146">SQL Server does not support any manual changes to system databases.</span></span> <span data-ttu-id="9c74f-147">SQL Server 데이터베이스에서 시스템 테이블을 업데이트할 경우 두 가지 이벤트(이벤트 ID 17659와 이벤트 ID 3859)가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c74f-147">If you update a system table in a SQL Server database, two events (event ID 17659 and event ID 3859) are logged.</span></span> <span data-ttu-id="9c74f-148">자세한 내용은 기술 자료 문서 2688307, "SQL Server 데이터베이스의 시스템 테이블을 업데이트할 경우 이벤트 ID 17659와 이벤트 ID 3859가 기록됨"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9c74f-148">For more information, see KB article 2688307, "Event ID 17659 and event ID 3859 are logged when you update system tables in a SQL Server database".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c74f-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9c74f-149">See Also</span></span>  
 [<span data-ttu-id="9c74f-150">SQL Server 데이터베이스의 시스템 테이블을 업데이트할 경우 이벤트 ID 17659와 이벤트 ID 3859가 기록됨</span><span class="sxs-lookup"><span data-stu-id="9c74f-150">Event ID 17659 and event ID 3859 are logged when you update system tables in a SQL Server database</span></span>](https://support.microsoft.com/kb/2688307/EN-US)  
  
  
