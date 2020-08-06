---
title: 서비스 마스터 키 복원 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- service master key [SQL Server], importing
- service master key [SQL Server], restoring
ms.assetid: 14bdbbbe-d384-4692-b670-4243d2466fe1
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 2ad99fc9baa518d50678ddd6e6db1ec554658823
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743167"
---
# <a name="restore-the-service-master-key"></a><span data-ttu-id="ce8b1-102">서비스 마스터 키 복원</span><span class="sxs-lookup"><span data-stu-id="ce8b1-102">Restore the Service Master Key</span></span>
  <span data-ttu-id="ce8b1-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 서비스 마스터 키를 복원하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8b1-103">This topic describes how to restore the service master key in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="ce8b1-104">이 키는 복원할 필요가 거의 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ce8b1-104">It is unlikely that you will ever need to restore the service master key.</span></span> <span data-ttu-id="ce8b1-105">만약 키를 복원할 경우 각별히 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8b1-105">If you do, you should proceed with extreme caution.</span></span> <span data-ttu-id="ce8b1-106">자세한 내용은 [Back Up the Service Master Key](service-master-key.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce8b1-106">For more information, see [Back Up the Service Master Key](service-master-key.md).</span></span>  
  
 <span data-ttu-id="ce8b1-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="ce8b1-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ce8b1-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="ce8b1-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ce8b1-109">제한 사항</span><span class="sxs-lookup"><span data-stu-id="ce8b1-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ce8b1-110">보안</span><span class="sxs-lookup"><span data-stu-id="ce8b1-110">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="ce8b1-111">Transact-SQL을 사용하여 서비스 마스터 키를 복원하려면</span><span class="sxs-lookup"><span data-stu-id="ce8b1-111">To restore the service master key using Transact-SQL</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ce8b1-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="ce8b1-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ce8b1-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="ce8b1-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="ce8b1-114">서비스 마스터 키가 복원되면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 는 현재 서비스 마스터 키로 암호화된 모든 키 및 암호를 해독한 다음 백업 파일에서 로드된 서비스 마스터 키로 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8b1-114">When the service master key is restored, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] decrypts all the keys and secrets that have been encrypted with the current service master key, and then encrypts them with the service master key loaded from the backup file.</span></span>  
  
-   <span data-ttu-id="ce8b1-115">암호 해독 중 하나가 실패하면 복원이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8b1-115">If any one of the decryptions fails, the restore will fail.</span></span> <span data-ttu-id="ce8b1-116">오류를 무시하기 위해 FORCE 옵션을 사용할 수 있지만 이 옵션을 사용하면 암호를 해독할 수 없는 데이터를 손실할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce8b1-116">You can use the FORCE option to ignore errors, but this option will cause the loss of any data that cannot be decrypted.</span></span>  
  
-   <span data-ttu-id="ce8b1-117">암호화 계층을 다시 생성하는 작업에는 리소스가 많이 소비됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce8b1-117">Regenerating the encryption hierarchy is a resource-intensive operation.</span></span> <span data-ttu-id="ce8b1-118">이 작업은 사용량이 적은 기간 동안에 실행하도록 예약해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8b1-118">You should schedule this during a period of low demand.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="ce8b1-119">서비스 마스터 키는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 암호화 계층의 루트입니다.</span><span class="sxs-lookup"><span data-stu-id="ce8b1-119">The service master key is the root of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption hierarchy.</span></span> <span data-ttu-id="ce8b1-120">서비스 마스터 키는 트리에 있는 모든 다른 키를 직접 또는 간접적으로 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8b1-120">The service master key directly or indirectly secures all other keys in the tree.</span></span> <span data-ttu-id="ce8b1-121">강제 복원 중에 종속 키의 암호를 해독할 수 없으면 해당 키로 보호되는 데이터가 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce8b1-121">If a dependent key cannot be decrypted during a forced restore, data that is secured by that key will be lost.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ce8b1-122">보안</span><span class="sxs-lookup"><span data-stu-id="ce8b1-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ce8b1-123">권한</span><span class="sxs-lookup"><span data-stu-id="ce8b1-123">Permissions</span></span>  
 <span data-ttu-id="ce8b1-124">서버에 대한 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8b1-124">Requires CONTROL SERVER permission on the server.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ce8b1-125">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="ce8b1-125">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-the-service-master-key"></a><span data-ttu-id="ce8b1-126">서비스 마스터 키를 복원하려면</span><span class="sxs-lookup"><span data-stu-id="ce8b1-126">To restore the service master key</span></span>  
  
1.  <span data-ttu-id="ce8b1-127">물리적 백업 미디어 또는 로컬 파일 시스템의 디렉터리에서 백업한 서비스 마스터 키의 복사본을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8b1-127">Retrieve a copy of the backed-up service master key, either from a physical backup medium or a directory on the local file system.</span></span>  
  
2.  <span data-ttu-id="ce8b1-128">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8b1-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
3.  <span data-ttu-id="ce8b1-129">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8b1-129">On the Standard bar, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="ce8b1-130">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8b1-130">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Restores the service master key from a backup file.  
    RESTORE SERVICE MASTER KEY   
        FROM FILE = 'c:\temp_backups\keys\service_master_key'   
        DECRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';  
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="ce8b1-131">키의 경로와 암호(있는 경우)는 위에 나타난 것과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="ce8b1-131">The file path to the key and the key's password (if it exists) will be different than what is indicated above.</span></span> <span data-ttu-id="ce8b1-132">둘 다 서버 및 키 설정에 대해 고유한지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="ce8b1-132">Please make sure that both are specific to your server and key set-up.</span></span>  
  
  
