---
title: 데이터 열 암호화 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], columns
- cryptography [SQL Server], columns
ms.assetid: 38e9bf58-10c6-46ed-83cb-e2d76cda0adc
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 00f8b06296b3407ac070cd40378f3ff1039a0b93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741704"
---
# <a name="encrypt-a-column-of-data"></a><span data-ttu-id="d68e0-102">데이터 열 암호화</span><span class="sxs-lookup"><span data-stu-id="d68e0-102">Encrypt a Column of Data</span></span>
  <span data-ttu-id="d68e0-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 을 통해 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 대칭 암호화를 사용하여 데이터 열을 암호화하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d68e0-103">This topic describes how to encrypt a column of data by using symmetric encryption in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="d68e0-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="d68e0-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d68e0-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="d68e0-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d68e0-106">보안</span><span class="sxs-lookup"><span data-stu-id="d68e0-106">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="d68e0-107">Transact-SQL을 사용하여 데이터 열을 암호화하려면</span><span class="sxs-lookup"><span data-stu-id="d68e0-107">To encrypt a column of data, using Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d68e0-108">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="d68e0-108">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d68e0-109">보안</span><span class="sxs-lookup"><span data-stu-id="d68e0-109">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d68e0-110">권한</span><span class="sxs-lookup"><span data-stu-id="d68e0-110">Permissions</span></span>  
 <span data-ttu-id="d68e0-111">다음 권한은 아래 단계를 수행하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d68e0-111">The following permissions are necessary to perform the steps below:</span></span>  
  
-   <span data-ttu-id="d68e0-112">데이터베이스에 대한 CONTROL 권한.</span><span class="sxs-lookup"><span data-stu-id="d68e0-112">CONTROL permission on the database.</span></span>  
  
-   <span data-ttu-id="d68e0-113">데이터베이스에 대한 CREATE CERTIFICATE 권한.</span><span class="sxs-lookup"><span data-stu-id="d68e0-113">CREATE CERTIFICATE permission on the database.</span></span> <span data-ttu-id="d68e0-114">Windows 로그인, SQL Server 로그인 및 애플리케이션 역할만 인증서를 소유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d68e0-114">Only Windows logins, SQL Server logins, and application roles can own certificates.</span></span> <span data-ttu-id="d68e0-115">그룹 및 역할은 인증서를 소유할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d68e0-115">Groups and roles cannot own certificates.</span></span>  
  
-   <span data-ttu-id="d68e0-116">테이블에 대한 ALTER 권한.</span><span class="sxs-lookup"><span data-stu-id="d68e0-116">ALTER permission on the table.</span></span>  
  
-   <span data-ttu-id="d68e0-117">키에 대한 일부 사용 권한이며 VIEW DEFINITION 권한이 거부되지 않은 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d68e0-117">Some permission on the key and must not have been denied VIEW DEFINITION permission.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d68e0-118">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="d68e0-118">Using Transact-SQL</span></span>  
  
#### <a name="to-encrypt-a-column-of-data-using-a-simple-symmetric-encryption"></a><span data-ttu-id="d68e0-119">간단한 대칭 암호화를 사용하여 데이터 열을 암호화하려면</span><span class="sxs-lookup"><span data-stu-id="d68e0-119">To encrypt a column of data using a simple symmetric encryption</span></span>  
  
1.  <span data-ttu-id="d68e0-120">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d68e0-120">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d68e0-121">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d68e0-121">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d68e0-122">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d68e0-122">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    --If there is no master key, create one now.   
    IF NOT EXISTS   
        (SELECT * FROM sys.symmetric_keys WHERE symmetric_key_id = 101)  
        CREATE MASTER KEY ENCRYPTION BY   
        PASSWORD = '23987hxJKL95QYV4369#ghf0%lekjg5k3fd117r$$#1946kcj$n44ncjhdlj'  
    GO  
  
    CREATE CERTIFICATE Sales09  
       WITH SUBJECT = 'Customer Credit Card Numbers';  
    GO  
  
    CREATE SYMMETRIC KEY CreditCards_Key11  
        WITH ALGORITHM = AES_256  
        ENCRYPTION BY CERTIFICATE Sales09;  
    GO  
  
    -- Create a column in which to store the encrypted data.  
    ALTER TABLE Sales.CreditCard   
        ADD CardNumber_Encrypted varbinary(128);   
    GO  
  
    -- Open the symmetric key with which to encrypt the data.  
    OPEN SYMMETRIC KEY CreditCards_Key11  
       DECRYPTION BY CERTIFICATE Sales09;  
  
    -- Encrypt the value in column CardNumber using the  
    -- symmetric key CreditCards_Key11.  
    -- Save the result in column CardNumber_Encrypted.    
    UPDATE Sales.CreditCard  
    SET CardNumber_Encrypted = EncryptByKey(Key_GUID('CreditCards_Key11')  
        , CardNumber, 1, HashBytes('SHA1', CONVERT( varbinary  
        , CreditCardID)));  
    GO  
  
    -- Verify the encryption.  
    -- First, open the symmetric key with which to decrypt the data.  
  
    OPEN SYMMETRIC KEY CreditCards_Key11  
       DECRYPTION BY CERTIFICATE Sales09;  
    GO  
  
    -- Now list the original card number, the encrypted card number,  
    -- and the decrypted ciphertext. If the decryption worked,  
    -- the original number will match the decrypted number.  
  
    SELECT CardNumber, CardNumber_Encrypted   
        AS 'Encrypted card number', CONVERT(nvarchar,  
        DecryptByKey(CardNumber_Encrypted, 1 ,   
        HashBytes('SHA1', CONVERT(varbinary, CreditCardID))))  
        AS 'Decrypted card number' FROM Sales.CreditCard;  
    GO  
    ```  
  
#### <a name="to-encrypt-a-column-of-data-using-symmetric-encryption-that-includes-an-authenticator"></a><span data-ttu-id="d68e0-123">인증자를 포함하는 대칭 암호화를 사용하여 데이터 열을 암호화하려면</span><span class="sxs-lookup"><span data-stu-id="d68e0-123">To encrypt a column of data using symmetric encryption that includes an authenticator</span></span>  
  
1.  <span data-ttu-id="d68e0-124">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d68e0-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d68e0-125">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d68e0-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d68e0-126">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d68e0-126">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
  
    --If there is no master key, create one now.   
    IF NOT EXISTS   
        (SELECT * FROM sys.symmetric_keys WHERE symmetric_key_id = 101)  
        CREATE MASTER KEY ENCRYPTION BY   
        PASSWORD = '23987hxJKL969#ghf0%94467GRkjg5k3fd117r$$#1946kcj$n44nhdlj'  
    GO  
  
    CREATE CERTIFICATE HumanResources037  
       WITH SUBJECT = 'Employee Social Security Numbers';  
    GO  
  
    CREATE SYMMETRIC KEY SSN_Key_01  
        WITH ALGORITHM = AES_256  
        ENCRYPTION BY CERTIFICATE HumanResources037;  
    GO  
  
    USE [AdventureWorks2012];  
    GO  
  
    -- Create a column in which to store the encrypted data.  
    ALTER TABLE HumanResources.Employee  
        ADD EncryptedNationalIDNumber varbinary(128);   
    GO  
  
    -- Open the symmetric key with which to encrypt the data.  
    OPEN SYMMETRIC KEY SSN_Key_01  
       DECRYPTION BY CERTIFICATE HumanResources037;  
  
    -- Encrypt the value in column NationalIDNumber with symmetric   
    -- key SSN_Key_01. Save the result in column EncryptedNationalIDNumber.  
    UPDATE HumanResources.Employee  
    SET EncryptedNationalIDNumber = EncryptByKey(Key_GUID('SSN_Key_01'), NationalIDNumber);  
    GO  
  
    -- Verify the encryption.  
    -- First, open the symmetric key with which to decrypt the data.  
    OPEN SYMMETRIC KEY SSN_Key_01  
       DECRYPTION BY CERTIFICATE HumanResources037;  
    GO  
  
    -- Now list the original ID, the encrypted ID, and the   
    -- decrypted ciphertext. If the decryption worked, the original  
    -- and the decrypted ID will match.  
    SELECT NationalIDNumber, EncryptedNationalIDNumber   
        AS 'Encrypted ID Number',  
        CONVERT(nvarchar, DecryptByKey(EncryptedNationalIDNumber))   
        AS 'Decrypted ID Number'  
        FROM HumanResources.Employee;  
    GO  
    ```  
  
 <span data-ttu-id="d68e0-127">자세한 내용은</span><span class="sxs-lookup"><span data-stu-id="d68e0-127">For more information, see the following:</span></span>  
  
-   [<span data-ttu-id="d68e0-128">CREATE CERTIFICATE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d68e0-128">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-certificate-transact-sql)  
  
-   [<span data-ttu-id="d68e0-129">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d68e0-129">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-symmetric-key-transact-sql)  
  
-   [<span data-ttu-id="d68e0-130">ALTER TABLE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d68e0-130">ALTER TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-table-transact-sql)  
  
-   [<span data-ttu-id="d68e0-131">OPEN SYMMETRIC KEY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d68e0-131">OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/open-symmetric-key-transact-sql)  
  
  
