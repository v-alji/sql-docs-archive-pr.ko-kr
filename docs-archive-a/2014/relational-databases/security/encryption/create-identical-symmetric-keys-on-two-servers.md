---
title: 두 서버에서 동일한 대칭 키 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- symmetric keys [SQL Server], creating
ms.assetid: a13d0b21-a43b-43c0-9c22-7ba8f3d15e80
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 38eaccffff89b0be7e59f628fcfb9b6e772a02b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741719"
---
# <a name="create-identical-symmetric-keys-on-two-servers"></a><span data-ttu-id="31ce6-102">두 서버에서 동일한 대칭 키 만들기</span><span class="sxs-lookup"><span data-stu-id="31ce6-102">Create Identical Symmetric Keys on Two Servers</span></span>
  <span data-ttu-id="31ce6-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 에서 [!INCLUDE[tsql](../../../includes/tsql-md.md)]을 사용하여 서로 다른 두 서버에서 동일한 대칭 키를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="31ce6-103">This topic describes how to create identical symmetric keys on two different servers in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="31ce6-104">ciphertext를 해독하려면 암호화하는 데 사용된 키가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="31ce6-104">In order to decrypt ciphertext, you need the key that was used to encrypt it.</span></span> <span data-ttu-id="31ce6-105">단일 데이터베이스에서 암호화와 암호 해독이 모두 수행되는 경우 키가 데이터베이스에 저장되며 사용 권한에 따라 암호화와 암호 해독에 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31ce6-105">When both encryption and decryption occur in a single database, the key is stored in the database and it is available, depending on permissions, for both encryption and decryption.</span></span> <span data-ttu-id="31ce6-106">그러나 암호화와 암호 해독이 개별 데이터베이스나 개별 서버에서 수행되는 경우 한 데이터베이스에 저장된 키를 다른 데이터베이스에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="31ce6-106">But when encryption and decryption occur in separate databases or on separate servers, the key stored in one database is not available for use on the second database</span></span>  
  
 <span data-ttu-id="31ce6-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="31ce6-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="31ce6-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="31ce6-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="31ce6-109">제한 사항</span><span class="sxs-lookup"><span data-stu-id="31ce6-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="31ce6-110">보안</span><span class="sxs-lookup"><span data-stu-id="31ce6-110">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="31ce6-111">Transact-SQL을 사용하여 서로 다른 두 서버에서 동일한 대칭 키를 만들려면</span><span class="sxs-lookup"><span data-stu-id="31ce6-111">To create identical symmetric keys on two different servers, using Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="31ce6-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="31ce6-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="31ce6-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="31ce6-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="31ce6-114">대칭 키를 만들 때 대칭 키는 인증서, 암호, 대칭 키, 비대칭 키 또는 PROVIDER 중 하나 이상을 사용하여 암호화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ce6-114">When a symmetric key is created, the symmetric key must be encrypted by using at least one of the following: certificate, password, symmetric key, asymmetric key, or PROVIDER.</span></span> <span data-ttu-id="31ce6-115">키에는 각 유형에 대해 두 개 이상의 암호화가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31ce6-115">The key can have more than one encryption of each type.</span></span> <span data-ttu-id="31ce6-116">즉, 여러 인증서, 암호, 대칭 키 및 비대칭 키를 동시에 사용하여 단일 대칭 키를 암호화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31ce6-116">In other words, a single symmetric key can be encrypted by using multiple certificates, passwords, symmetric keys, and asymmetric keys at the same time.</span></span>  
  
-   <span data-ttu-id="31ce6-117">데이터베이스 마스터 키의 공개 키 대신 암호를 사용하여 대칭 키를 암호화한 경우 TRIPLE DES 암호화 알고리즘이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="31ce6-117">When a symmetric key is encrypted with a password instead of the public key of the database master key, the TRIPLE DES encryption algorithm is used.</span></span> <span data-ttu-id="31ce6-118">따라서 AES와 같은 강력한 암호화 알고리즘을 사용하여 만든 키는 더 약한 알고리즘으로 보호됩니다.</span><span class="sxs-lookup"><span data-stu-id="31ce6-118">Because of this, keys that are created with a strong encryption algorithm, such as AES, are themselves secured by a weaker algorithm.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="31ce6-119">보안</span><span class="sxs-lookup"><span data-stu-id="31ce6-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="31ce6-120">권한</span><span class="sxs-lookup"><span data-stu-id="31ce6-120">Permissions</span></span>  
 <span data-ttu-id="31ce6-121">데이터베이스에 대한 ALTER ANY SYMMETRIC KEY 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="31ce6-121">Requires ALTER ANY SYMMETRIC KEY permission on the database.</span></span> <span data-ttu-id="31ce6-122">AUTHORIZATION이 지정된 경우 데이터베이스 사용자에 대한 IMPERSONATE 권한 또는 애플리케이션 역할에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="31ce6-122">If AUTHORIZATION is specified, requires IMPERSONATE permission on the database user or ALTER permission on the application role.</span></span> <span data-ttu-id="31ce6-123">인증서 또는 비대칭 키를 통한 암호화의 경우에는 해당 인증서 또는 비대칭 키에 대한 VIEW DEFINITION 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="31ce6-123">If encryption is by certificate or asymmetric key, requires VIEW DEFINITION permission on the certificate or asymmetric key.</span></span> <span data-ttu-id="31ce6-124">Windows 로그인, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 로그인 및 애플리케이션 역할만 대칭 키를 소유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31ce6-124">Only Windows logins, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logins, and application roles can own symmetric keys.</span></span> <span data-ttu-id="31ce6-125">그룹 및 역할은 대칭 키를 소유할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="31ce6-125">Groups and roles cannot own symmetric keys.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="31ce6-126">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="31ce6-126">Using Transact-SQL</span></span>  
  
#### <a name="to-create-identical-symmetric-keys-on-two-different-servers"></a><span data-ttu-id="31ce6-127">서로 다른 두 서버에 동일한 대칭 키를 만들려면</span><span class="sxs-lookup"><span data-stu-id="31ce6-127">To create identical symmetric keys on two different servers</span></span>  
  
1.  <span data-ttu-id="31ce6-128">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="31ce6-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="31ce6-129">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="31ce6-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="31ce6-130">다음 CREATE MASTER KEY, CREATE CERTIFICATE 및 CREATE SYMMETRIC KEY 문을 실행하여 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="31ce6-130">Create a key by running the following CREATE MASTER KEY, CREATE CERTIFICATE, and CREATE SYMMETRIC KEY statements.</span></span>  
  
    ```  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'My p@55w0Rd';  
    GO  
    CREATE CERTIFICATE [cert_keyProtection] WITH SUBJECT = 'Key Protection';  
    GO  
    CREATE SYMMETRIC KEY [key_DataShare] WITH  
        KEY_SOURCE = 'My key generation bits. This is a shared secret!',  
        ALGORITHM = AES_256,   
        IDENTITY_VALUE = 'Key Identity generation bits. Also a shared secret'  
        ENCRYPTION BY CERTIFICATE [cert_keyProtection];  
    GO  
    ```  
  
4.  <span data-ttu-id="31ce6-131">별개의 서버 인스턴스에 연결하고, 다른 쿼리 창을 열고, 위의 SQL 문을 실행하여 보조 서버에서 동일한 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="31ce6-131">Connect to a separate server instance, open a different Query Window, and run the SQL statements above to create the same key on the second server.</span></span>  
  
5.  <span data-ttu-id="31ce6-132">첫 번째 서버에서 아래의 OPEN SYMMETRIC KEY 문과 SELECT 문을 먼저 실행하여 키를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="31ce6-132">Test the keys by first running the OPEN SYMMETRIC KEY statement and the SELECT statement below on the first server.</span></span>  
  
    ```  
    OPEN SYMMETRIC KEY [key_DataShare]   
        DECRYPTION BY CERTIFICATE cert_keyProtection;  
    GO  
    SELECT encryptbykey(key_guid('key_DataShare'), 'MyData' )  
    GO  
    -- For example, the output might look like this: 0x2152F8DA8A500A9EDC2FAE26D15C302DA70D25563DAE7D5D1102E3056CE9EF95CA3E7289F7F4D0523ED0376B155FE9C3  
    ```  
  
6.  <span data-ttu-id="31ce6-133">두 번째 서버에서 이전 SELECT 문의 결과를 다음 코드에 `@blob` 값으로 붙여 넣고 다음 코드를 실행하여 중복 키가 ciphertext를 해독할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="31ce6-133">On the second server, paste the result of the previous SELECT statement into the following code as the value of `@blob` and run the following code to verify that the duplicate key can decrypt the ciphertext.</span></span>  
  
    ```  
    OPEN SYMMETRIC KEY [key_DataShare]   
        DECRYPTION BY CERTIFICATE cert_keyProtection;  
    GO  
    DECLARE @blob varbinary(8000);  
    SET @blob = SELECT CONVERT(varchar(8000), decryptbykey(@blob));  
    GO  
    ```  
  
7.  <span data-ttu-id="31ce6-134">두 서버에서 대칭 키를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="31ce6-134">Close the symmetric key on both servers.</span></span>  
  
    ```  
    CLOSE SYMMETRIC KEY [key_DataShare];  
    GO  
    ```  
  
 <span data-ttu-id="31ce6-135">자세한 내용은</span><span class="sxs-lookup"><span data-stu-id="31ce6-135">For more information, see the following:</span></span>  
  
-   [<span data-ttu-id="31ce6-136">CREATE MASTER KEY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="31ce6-136">CREATE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-master-key-transact-sql)  
  
-   [<span data-ttu-id="31ce6-137">CREATE CERTIFICATE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="31ce6-137">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-certificate-transact-sql)  
  
-   [<span data-ttu-id="31ce6-138">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="31ce6-138">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-symmetric-key-transact-sql)  
  
-   [<span data-ttu-id="31ce6-139">ENCRYPTBYKEY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="31ce6-139">ENCRYPTBYKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/encryptbykey-transact-sql)  
  
-   [<span data-ttu-id="31ce6-140">DECRYPTBYKEY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="31ce6-140">DECRYPTBYKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/decryptbykey-transact-sql)  
  
-   [<span data-ttu-id="31ce6-141">OPEN SYMMETRIC KEY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="31ce6-141">OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/open-symmetric-key-transact-sql)  
  
  
