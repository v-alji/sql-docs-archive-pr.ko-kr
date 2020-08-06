---
title: 데이터베이스 마스터 키 복원 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], importing
ms.assetid: 16897cc5-db8f-43bb-a38e-6855c82647cf
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 614ba8bdc494ae7e7e5b3ed7b62390721ef642a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743164"
---
# <a name="restore-a-database-master-key"></a><span data-ttu-id="7cb69-102">데이터베이스 마스터 키 복원</span><span class="sxs-lookup"><span data-stu-id="7cb69-102">Restore a Database Master Key</span></span>
  <span data-ttu-id="7cb69-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 데이터베이스 마스터 키를 복원하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7cb69-103">This topic describes how to restore the database master key in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="7cb69-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="7cb69-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7cb69-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="7cb69-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7cb69-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="7cb69-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="7cb69-107">보안</span><span class="sxs-lookup"><span data-stu-id="7cb69-107">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="7cb69-108">Transact-SQL을 사용하여 데이터베이스 마스터 키를 복원하려면</span><span class="sxs-lookup"><span data-stu-id="7cb69-108">To restore the database master key using Transact-SQL</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7cb69-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="7cb69-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="7cb69-110">제한 사항</span><span class="sxs-lookup"><span data-stu-id="7cb69-110">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="7cb69-111">마스터 키가 복원되면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 는 현재 사용 중인 마스터 키로 암호화된 모든 키의 암호를 해독한 다음 복원된 마스터 키를 사용하여 이러한 키를 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="7cb69-111">When the master key is restored, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] decrypts all the keys that are encrypted with the currently active master key, and then encrypts these keys with the restored master key.</span></span> <span data-ttu-id="7cb69-112">이 리소스를 많이 사용하는 작업은 사용량이 낮은 기간 동안에만 수행하도록 예약해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cb69-112">This resource-intensive operation should be scheduled during a period of low demand.</span></span> <span data-ttu-id="7cb69-113">현재 데이터베이스 마스터 키가 열려 있지 않거나 열 수 없는 경우 또는 이 키를 사용하여 암호화된 일부 키의 암호를 해독할 수 없는 경우 복원 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="7cb69-113">If the current database master key is not open or cannot be opened, or if any of the keys that are encrypted by it cannot be decrypted, the restore operation fails.</span></span>  
  
-   <span data-ttu-id="7cb69-114">암호 해독 중 하나가 실패하면 복원이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="7cb69-114">If any one of the decryptions fails, the restore will fail.</span></span> <span data-ttu-id="7cb69-115">오류를 무시하기 위해 FORCE 옵션을 사용할 수 있지만 이 옵션을 사용하면 암호를 해독할 수 없는 데이터를 손실할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cb69-115">You can use the FORCE option to ignore errors, but this option will cause the loss of any data that cannot be decrypted.</span></span>  
  
-   <span data-ttu-id="7cb69-116">서비스 마스터 키로 마스터 키가 암호화된 경우 복원된 마스터 키는 서비스 마스터 키로도 암호화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cb69-116">If the master key was encrypted by the service master key, the restored master key will also be encrypted by the service master key.</span></span>  
  
-   <span data-ttu-id="7cb69-117">현재 데이터베이스에 마스터 키가 없는 경우 RESTORE MASTER KEY가 마스터 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7cb69-117">If there is no master key in the current database, RESTORE MASTER KEY creates a master key.</span></span> <span data-ttu-id="7cb69-118">새 마스터 키는 서비스 마스터 키로 자동으로 암호화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7cb69-118">The new master key will not be automatically encrypted with the service master key.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7cb69-119">보안</span><span class="sxs-lookup"><span data-stu-id="7cb69-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7cb69-120">권한</span><span class="sxs-lookup"><span data-stu-id="7cb69-120">Permissions</span></span>  
 <span data-ttu-id="7cb69-121">데이터베이스에 대한 CONTROL 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7cb69-121">Requires CONTROL permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio-with-transact-sql"></a><a name="SSMSProcedure"></a><span data-ttu-id="7cb69-122">Transact-sql과 함께 SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="7cb69-122">Using SQL Server Management Studio with Transact-SQL</span></span>  
  
#### <a name="to-restore-the-database-master-key"></a><span data-ttu-id="7cb69-123">데이터베이스 마스터 키를 복원하려면</span><span class="sxs-lookup"><span data-stu-id="7cb69-123">To restore the database master key</span></span>  
  
1.  <span data-ttu-id="7cb69-124">물리적 백업 미디어 또는 로컬 파일 시스템의 디렉터리에서 백업한 데이터베이스 마스터 키의 복사본을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="7cb69-124">Retrieve a copy of the backed-up database master key, either from a physical backup medium or a directory on the local file system.</span></span>  
  
2.  <span data-ttu-id="7cb69-125">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="7cb69-125">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
3.  <span data-ttu-id="7cb69-126">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7cb69-126">On the Standard bar, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="7cb69-127">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7cb69-127">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Restores the database master key of the AdventureWorks2012 database.  
    USE AdventureWorks2012;  
    GO  
    RESTORE MASTER KEY   
        FROM FILE = 'c:\backups\keys\AdventureWorks2012_master_key'   
        DECRYPTION BY PASSWORD = '3dH85Hhk003#GHkf02597gheij04'   
        ENCRYPTION BY PASSWORD = '259087M#MyjkFkjhywiyedfgGDFD';  
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="7cb69-128">키의 경로와 암호(있는 경우)는 위에 나타난 것과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="7cb69-128">The file path to the key and the key's password (if it exists) will be different than what is indicated above.</span></span> <span data-ttu-id="7cb69-129">둘 다 서버 및 키 설정에 대해 고유한지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="7cb69-129">Please make sure that both are specific to your server and key set-up.</span></span>  
  
 <span data-ttu-id="7cb69-130">자세한 내용은 [RESTORE MASTER KEY&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-master-key-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7cb69-130">For more information, see [RESTORE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-master-key-transact-sql)</span></span>  
  
  
