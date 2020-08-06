---
title: 데이터베이스 마스터 키 백업 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], exporting
ms.assetid: 7ad9a0a0-6e4f-4f7b-8801-8c1b9d49c4d8
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 9a66d28fea8289719d3efb2351409e0f14379ec9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741727"
---
# <a name="back-up-a-database-master-key"></a><span data-ttu-id="fc796-102">데이터베이스 마스터 키 백업</span><span class="sxs-lookup"><span data-stu-id="fc796-102">Back Up a Database Master Key</span></span>
  <span data-ttu-id="fc796-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 데이터베이스 마스터 키를 백업하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fc796-103">This topic describes how to back up a database master key in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="fc796-104">데이터베이스 마스터 키는 데이터베이스 내의 다른 키와 인증서를 암호화하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc796-104">The database master key is used to encrypt other keys and certificates inside a database.</span></span> <span data-ttu-id="fc796-105">데이터베이스 마스터 키가 삭제되거나 손상된 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에서 해당 마스터 키를 해독하지 못할 수 있으며 해당 마스터 키를 사용하여 암호화한 데이터는 사실상 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc796-105">If it is deleted or corrupted, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] may be unable to decrypt those keys, and the data encrypted using them will be effectively lost.</span></span> <span data-ttu-id="fc796-106">그러므로 데이터베이스 마스터 키를 백업하고 이 백업을 안전한 오프 사이트 위치에 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc796-106">For this reason, you should back up the database master key and store the backup in a secure off-site location.</span></span>  
  
 <span data-ttu-id="fc796-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="fc796-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="fc796-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="fc796-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fc796-109">제한 사항</span><span class="sxs-lookup"><span data-stu-id="fc796-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="fc796-110">보안</span><span class="sxs-lookup"><span data-stu-id="fc796-110">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="fc796-111">Transact-SQL을 사용하여 데이터베이스 마스터 키를 백업하려면</span><span class="sxs-lookup"><span data-stu-id="fc796-111">To back up a database master key using Transact-SQL</span></span>](#Procedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fc796-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="fc796-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="fc796-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="fc796-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="fc796-114">마스터 키를 열어야 하기 때문에 백업하기 전에 암호를 해독해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc796-114">The master key must be open and, therefore, decrypted before it is backed up.</span></span> <span data-ttu-id="fc796-115">서비스 마스터 키를 사용하여 암호화된 경우 마스터 키를 명시적으로 열 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fc796-115">If it is encrypted with the service master key, the master key does not have to be explicitly opened.</span></span> <span data-ttu-id="fc796-116">하지만 마스터 키가 암호로만 암호화된 경우 명시적으로 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc796-116">But if the master key is encrypted only with a password, it must be explicitly opened.</span></span>  
  
-   <span data-ttu-id="fc796-117">마스터 키는 만들자 마자 백업하고 외부의 안전한 위치에 보관하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fc796-117">We recommend that you back up the master key as soon as it is created, and store the backup in a secure, off-site location.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fc796-118">보안</span><span class="sxs-lookup"><span data-stu-id="fc796-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fc796-119">권한</span><span class="sxs-lookup"><span data-stu-id="fc796-119">Permissions</span></span>  
 <span data-ttu-id="fc796-120">데이터베이스에 대한 CONTROL 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fc796-120">Requires CONTROL permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio-with-transact-sql"></a><a name="Procedure"></a><span data-ttu-id="fc796-121">Transact-sql과 함께 SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="fc796-121">Using SQL Server Management Studio with Transact-SQL</span></span>  
  
#### <a name="to-back-up-the-database-master-key"></a><span data-ttu-id="fc796-122">데이터베이스 마스터 키를 백업하려면</span><span class="sxs-lookup"><span data-stu-id="fc796-122">To back-up the database master key</span></span>  
  
1.  <span data-ttu-id="fc796-123">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 백업할 데이터베이스 마스터 키가 들어 있는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="fc796-123">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance containing the database master key you wish to back up.</span></span>  
  
2.  <span data-ttu-id="fc796-124">백업 미디어에 데이터베이스 마스터 키를 암호화하는 데 사용할 암호를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc796-124">Choose a password that will be used to encrypt the database master key on the backup medium.</span></span> <span data-ttu-id="fc796-125">이 암호의 복잡성을 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc796-125">This password is subject to complexity checks.</span></span>  
  
3.  <span data-ttu-id="fc796-126">백업 키의 복사본을 저장하기 위해 이동식 백업 미디어를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="fc796-126">Obtain a removable backup medium for storing a copy of the backed-up key.</span></span>  
  
4.  <span data-ttu-id="fc796-127">키의 백업을 만들 NTFS 디렉터리를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="fc796-127">Identify an NTFS directory in which to create the backup of the key.</span></span> <span data-ttu-id="fc796-128">다음 단계에서 지정하는 파일을 만들 위치인</span><span class="sxs-lookup"><span data-stu-id="fc796-128">This is where you will create the file specified in the next step.</span></span> <span data-ttu-id="fc796-129">이 디렉터리는 매우 제한적인 ACL(액세스 제한 목록)로 보호되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc796-129">The directory should be protected with highly restrictive access control lists (ACLs).</span></span>  
  
5.  <span data-ttu-id="fc796-130">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="fc796-130">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
6.  <span data-ttu-id="fc796-131">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fc796-131">On the Standard bar, click **New Query**.</span></span>  
  
7.  <span data-ttu-id="fc796-132">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fc796-132">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates a backup of the "AdventureWorks2012" master key. Because this master key is not encrypted by the service master key, a password must be specified when it is opened.  
    USE AdventureWorks2012;   
    GO  
    OPEN MASTER KEY DECRYPTION BY PASSWORD = 'sfj5300osdVdgwdfkli7';   
  
    BACKUP MASTER KEY TO FILE = 'c:\temp\exportedmasterkey'   
        ENCRYPTION BY PASSWORD = 'sd092735kjn$&adsg';   
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="fc796-133">키의 경로와 암호(있는 경우)는 위에 나타난 것과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="fc796-133">The file path to the key and the key's password (if it exists) will be different than what is indicated above.</span></span> <span data-ttu-id="fc796-134">둘 다 서버 및 키 설정에 대해 고유한지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="fc796-134">Please make sure that both are specific to your server and key set-up.</span></span>  
  
8.  <span data-ttu-id="fc796-135">파일을 백업 미디어에 복사하고 복사본을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="fc796-135">Copy the file to the backup medium and verify the copy.</span></span>  
  
9. <span data-ttu-id="fc796-136">백업을 안전한 오프 사이트 위치에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="fc796-136">Store the backup in a secure, off-site location.</span></span>  
  
 <span data-ttu-id="fc796-137">자세한 내용은 [OPEN MASTER KEY&#40;Transact-SQL&#41;](/sql/t-sql/statements/open-master-key-transact-sql) 및 [BACKUP MASTER KEY&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fc796-137">For more information, see [OPEN MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/open-master-key-transact-sql) and [BACKUP MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql).</span></span>  
  
  
