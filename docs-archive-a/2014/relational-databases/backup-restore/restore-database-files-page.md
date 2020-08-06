---
title: 데이터베이스 복원(파일 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restoredb.files.f1 in the code
- sql12.swb.restoredb.files.f1
ms.assetid: 714c36ea-a9f9-43a4-99f9-a6f73d1baf8e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: edffd9454b51ea80a18311f735d29407f97f6eb6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653457"
---
# <a name="restore-database-files-page"></a><span data-ttu-id="620ad-102">데이터베이스 복원(파일 페이지)</span><span class="sxs-lookup"><span data-stu-id="620ad-102">Restore Database (Files Page)</span></span>
  <span data-ttu-id="620ad-103">**데이터베이스 복원** 대화 상자의 **파일** 페이지를 사용하여 데이터베이스 내에서 복원하려고 선택한 특정 파일을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="620ad-103">Use the **Files** page of the **Restore Database** dialog box to manage the specific files you have chosen to restore within the database.</span></span>  
  
## <a name="options"></a><span data-ttu-id="620ad-104">옵션</span><span class="sxs-lookup"><span data-stu-id="620ad-104">Options</span></span>  
  
### <a name="restore-database-files-as"></a><span data-ttu-id="620ad-105">데이터베이스 파일을 다음으로 복원</span><span class="sxs-lookup"><span data-stu-id="620ad-105">Restore database files as</span></span>  
 <span data-ttu-id="620ad-106">복원된 파일의 파일 경로를 새로 할당하고 관리하려면 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="620ad-106">Use to assign and manage the new file path to the restored files.</span></span>  
  
 <span data-ttu-id="620ad-107">**모든 폴더를 파일에 다시 배치**</span><span class="sxs-lookup"><span data-stu-id="620ad-107">**Relocate all files to folder**</span></span>  
 <span data-ttu-id="620ad-108">복원된 파일의 위치를 다시 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="620ad-108">Relocates restored files.</span></span>  
  
|<span data-ttu-id="620ad-109">옵션</span><span class="sxs-lookup"><span data-stu-id="620ad-109">Option</span></span>|<span data-ttu-id="620ad-110">Description</span><span class="sxs-lookup"><span data-stu-id="620ad-110">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="620ad-111">**데이터 파일 폴더**</span><span class="sxs-lookup"><span data-stu-id="620ad-111">**Data file folder**</span></span>|<span data-ttu-id="620ad-112">복원된 데이터 파일을 다시 배치할 데이터 파일 폴더 이름을 입력하거나 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="620ad-112">Enter or search for the data file folder name that the restored data file or files should be relocated to.</span></span>|  
|<span data-ttu-id="620ad-113">**로그 파일 폴더**</span><span class="sxs-lookup"><span data-stu-id="620ad-113">**Log file folder**</span></span>|<span data-ttu-id="620ad-114">복원된 로그 파일을 다시 배치할 로그 파일 또는 파일 폴더를 입력하거나 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="620ad-114">Enter or search for the log file or files folder that the restored log file should be relocated to.</span></span>|  
  
 <span data-ttu-id="620ad-115">**논리적 파일 이름**</span><span class="sxs-lookup"><span data-stu-id="620ad-115">**Logical File Name**</span></span>  
 <span data-ttu-id="620ad-116">복원할 각 데이터베이스 파일당 한 개의 행을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="620ad-116">Displays one row for each database file to be restored.</span></span>  
  
 <span data-ttu-id="620ad-117">**파일 유형**</span><span class="sxs-lookup"><span data-stu-id="620ad-117">**File Type**</span></span>  
 <span data-ttu-id="620ad-118">파일 형식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="620ad-118">Displays the file type.</span></span>  
  
 <span data-ttu-id="620ad-119">**원래 파일 이름**</span><span class="sxs-lookup"><span data-stu-id="620ad-119">**Original File Name**</span></span>  
 <span data-ttu-id="620ad-120">복원된 파일의 원래 파일 경로를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="620ad-120">Displays the original file path for the restored file.</span></span>  
  
 <span data-ttu-id="620ad-121">**다음으로 복원**</span><span class="sxs-lookup"><span data-stu-id="620ad-121">**Restore As**</span></span>  
 <span data-ttu-id="620ad-122">복원된 파일을 저장할 파일 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="620ad-122">Lists the file names that the restored files are to be saved as.</span></span> <span data-ttu-id="620ad-123">적절한 파일 이름을 입력하거나 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="620ad-123">Enter or search for the appropriate file name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="620ad-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="620ad-124">See Also</span></span>  
 <span data-ttu-id="620ad-125">[데이터베이스 복원&#40;일반 페이지&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="620ad-125">[Restore Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="620ad-126">[데이터베이스 복원&#40;옵션 페이지&#41;](restore-database-options-page.md) </span><span class="sxs-lookup"><span data-stu-id="620ad-126">[Restore Database &#40;Options Page&#41;](restore-database-options-page.md) </span></span>  
 <span data-ttu-id="620ad-127">[RESTORE 인수&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="620ad-127">[RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span></span>  
 <span data-ttu-id="620ad-128">[테이프 드라이브에 대한 논리적 백업 디바이스 정의&#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="620ad-128">[Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md) </span></span>  
 [<span data-ttu-id="620ad-129">RESTORE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="620ad-129">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
