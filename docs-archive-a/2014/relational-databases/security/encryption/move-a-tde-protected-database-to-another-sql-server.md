---
title: 다른 SQL Server로 TDE 보호 데이터베이스 이동 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Transparent Data Encryption, moving
- TDE, moving a database
ms.assetid: fb420903-df54-4016-bab6-49e6dfbdedc7
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 3b03b4d9ecf31e9953fd3e22cec5c51bbacc0c25
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743168"
---
# <a name="move-a-tde-protected-database-to-another-sql-server"></a><span data-ttu-id="26c8f-102">다른 SQL Server로 TDE 보호 데이터베이스 이동</span><span class="sxs-lookup"><span data-stu-id="26c8f-102">Move a TDE Protected Database to Another SQL Server</span></span>
  <span data-ttu-id="26c8f-103">이 항목에서는 TDE(투명한 데이터 암호화)를 사용하여 데이터베이스를 보호하고 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../../includes/tsql-md.md)]을 사용하여 이 데이터베이스를 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 다른 인스턴스로 이동하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-103">This topic describes how to protect a database by using transparent data encryption (TDE), and then move the database to another instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="26c8f-104">TDE는 데이터 및 로그 파일에 대한 실시간 I/O 암호화 및 암호 해독을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-104">TDE performs real-time I/O encryption and decryption of the data and log files.</span></span> <span data-ttu-id="26c8f-105">암호화에는 복구 중에 사용 가능하도록 데이터베이스 부트 레코드에 저장된 DEK(데이터베이스 암호화 키)가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-105">The encryption uses a database encryption key (DEK), which is stored in the database boot record for availability during recovery.</span></span> <span data-ttu-id="26c8f-106">DEK는 서버의 `master` 데이터베이스에 저장된 인증서 또는 EKM 모듈로 보호되는 비대칭 키를 사용하여 보호되는 대칭 키입니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-106">The DEK is a symmetric key secured by using a certificate stored in the `master` database of the server or an asymmetric key protected by an EKM module.</span></span>  
  
 <span data-ttu-id="26c8f-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="26c8f-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="26c8f-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="26c8f-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="26c8f-109">제한 사항</span><span class="sxs-lookup"><span data-stu-id="26c8f-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="26c8f-110">보안</span><span class="sxs-lookup"><span data-stu-id="26c8f-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="26c8f-111">**다음을 사용하여 투명한 데이터 암호화로 보호되는 데이터베이스를 만듭니다.**</span><span class="sxs-lookup"><span data-stu-id="26c8f-111">**To create a database protected by transparent data encryption, using:**</span></span>  
  
     [<span data-ttu-id="26c8f-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="26c8f-112">SQL Server Management Studio</span></span>](#SSMSCreate)  
  
     [<span data-ttu-id="26c8f-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="26c8f-113">Transact-SQL</span></span>](#TsqlCreate)  
  
-   <span data-ttu-id="26c8f-114">**다음을 사용하여 데이터베이스를 이동합니다.**</span><span class="sxs-lookup"><span data-stu-id="26c8f-114">**To move a database, using:**</span></span>  
  
     [<span data-ttu-id="26c8f-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="26c8f-115">SQL Server Management Studio</span></span>](#SSMSMove)  
  
     [<span data-ttu-id="26c8f-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="26c8f-116">Transact-SQL</span></span>](#TsqlMove)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="26c8f-117">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="26c8f-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="26c8f-118">제한 사항</span><span class="sxs-lookup"><span data-stu-id="26c8f-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="26c8f-119">TDE로 보호되는 데이터베이스를 이동하려면 DEK를 여는 데 사용되는 인증서 또는 비대칭 키도 이동해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-119">When moving a TDE protected database, you must also move the certificate or asymmetric key that is used to open the DEK.</span></span> <span data-ttu-id="26c8f-120">에서 `master` 데이터베이스 파일에 액세스할 수 있도록 대상 서버의 데이터베이스에 인증서 또는 비대칭 키가 설치 되어 있어야 합니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="26c8f-120">The certificate or asymmetric key must be installed in the `master` database of the destination server, so that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can access the database files.</span></span> <span data-ttu-id="26c8f-121">자세한 내용은 [TDE&#40;투명한 데이터 암호화&#41;](transparent-data-encryption.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26c8f-121">For more information, see [Transparent Data Encryption &#40;TDE&#41;](transparent-data-encryption.md).</span></span>  
  
-   <span data-ttu-id="26c8f-122">인증서를 복구하려면 인증서 파일 및 프라이빗 키 파일의 사본을 보관해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-122">You must retain copies of both the certificate file and the private key file in order to recover the certificate.</span></span> <span data-ttu-id="26c8f-123">프라이빗 키의 암호는 데이터베이스 마스터 키 암호와 동일할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-123">The password for the private key does not have to be the same as the database master key password.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="26c8f-124">여기에 생성 된 파일을 \*\*C:\Program FILES\MICROSOFT SQL Server\MSSQL12.에 저장 합니다. \*\*기본적으로 MSSQLSERVER\MSSQL\DATA입니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-124">stores the files created here in **C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA** by default.</span></span> <span data-ttu-id="26c8f-125">파일 이름 및 위치는 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-125">Your file names and locations might be different.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="26c8f-126">보안</span><span class="sxs-lookup"><span data-stu-id="26c8f-126">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="26c8f-127">권한</span><span class="sxs-lookup"><span data-stu-id="26c8f-127">Permissions</span></span>  
  
-   <span data-ttu-id="26c8f-128">데이터베이스 `CONTROL DATABASE` 마스터 키를 만들려면 데이터베이스에 대 한 권한이 필요 `master` 합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-128">Requires `CONTROL DATABASE` permission on the `master` database to create the database master key.</span></span>  
  
-   <span data-ttu-id="26c8f-129">`CREATE CERTIFICATE` `master` Dek를 보호 하는 인증서를 만들려면 데이터베이스에 대 한 권한이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-129">Requires `CREATE CERTIFICATE` permission on the `master` database to create the certificate that protects the DEK.</span></span>  
  
-   <span data-ttu-id="26c8f-130">암호화된 데이터베이스에 대한 `CONTROL DATABASE` 권한과 데이터베이스 암호화 키를 암호화하는 데 사용되는 인증서 또는 비대칭 키에 대한 `VIEW DEFINITION` 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-130">Requires `CONTROL DATABASE` permission on the encrypted database and `VIEW DEFINITION` permission on the certificate or asymmetric key that is used to encrypt the database encryption key.</span></span>  
  
##  <a name="to-create-a-database-protected-by-transparent-data-encryption"></a><a name="SSMSProcedure"></a> <span data-ttu-id="26c8f-131">투명한 데이터 암호화로 보호되는 데이터베이스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="26c8f-131">To create a database protected by transparent data encryption</span></span>  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSCreate"></a> <span data-ttu-id="26c8f-132">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="26c8f-132">Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="26c8f-133">데이터베이스에 데이터베이스 마스터 키 및 인증서를 만듭니다 `master` .</span><span class="sxs-lookup"><span data-stu-id="26c8f-133">Create a database master key and certificate in the `master` database.</span></span> <span data-ttu-id="26c8f-134">자세한 내용은 아래에서 **Transact-SQL 사용** 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26c8f-134">For more information, see **Using Transact-SQL** below.</span></span>  
  
2.  <span data-ttu-id="26c8f-135">데이터베이스에서 서버 인증서의 백업을 만듭니다 `master` .</span><span class="sxs-lookup"><span data-stu-id="26c8f-135">Create a backup of the server certificate in the `master` database.</span></span> <span data-ttu-id="26c8f-136">자세한 내용은 아래에서 **Transact-SQL 사용** 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26c8f-136">For more information, see **Using Transact-SQL** below.</span></span>  
  
3.  <span data-ttu-id="26c8f-137">개체 탐색기에서 **데이터베이스** 폴더를 마우스 오른쪽 단추로 클릭한 다음 **새 데이터베이스**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-137">In Object Explorer, right-click the **Databases** folder and select **New Database**.</span></span>  
  
4.  <span data-ttu-id="26c8f-138">**새 데이터베이스** 대화 상자의 **데이터베이스 이름** 상자에 새 데이터베이스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-138">In the **New Database** dialog box, in the **Database name** box, enter the name of the new database.</span></span>  
  
5.  <span data-ttu-id="26c8f-139">**소유자** 상자에 새 데이터베이스의 소유자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-139">In the **Owner** box, enter the name of the new database's owner.</span></span> <span data-ttu-id="26c8f-140">또는 줄임표 **(...)** 를 클릭하여 **데이터베이스 소유자 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-140">Alternately, click the ellipsis **(...)** to open the **Select Database Owner** dialog box.</span></span> <span data-ttu-id="26c8f-141">새 데이터베이스를 만드는 방법은 [Create a Database](../../databases/create-a-database.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26c8f-141">For more information on creating a new database, see [Create a Database](../../databases/create-a-database.md).</span></span>  
  
6.  <span data-ttu-id="26c8f-142">개체 탐색기에서 더하기 기호를 클릭하여 **데이터베이스** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-142">In Object Explorer, click the plus sign to expand the **Databases** folder.</span></span>  
  
7.  <span data-ttu-id="26c8f-143">만든 데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 가리킨 다음 **데이터베이스 암호화 관리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-143">Right-click the database you created, point to **Tasks**, and select **Manage Database Encryption**.</span></span>  
  
     <span data-ttu-id="26c8f-144">**데이터베이스 암호화 관리** 대화 상자에는 다음과 같은 옵션이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-144">The following options are available on the **Manage Database Encryption** dialog box.</span></span>  
  
     <span data-ttu-id="26c8f-145">**암호화 알고리즘**</span><span class="sxs-lookup"><span data-stu-id="26c8f-145">**Encryption Algorithm**</span></span>  
     <span data-ttu-id="26c8f-146">데이터베이스 암호화에 사용할 알고리즘을 표시하거나 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-146">Displays or sets the algorithm to use for database encryption.</span></span> <span data-ttu-id="26c8f-147">기본 알고리즘은 `AES128`입니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-147">`AES128` is the default algorithm.</span></span> <span data-ttu-id="26c8f-148">이 필드는 비워 둘 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-148">This field cannot be blank.</span></span> <span data-ttu-id="26c8f-149">암호화 알고리즘에 대한 자세한 내용은 [Choose an Encryption Algorithm](choose-an-encryption-algorithm.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26c8f-149">For more information on encryption algorithms, see [Choose an Encryption Algorithm](choose-an-encryption-algorithm.md).</span></span>  
  
     <span data-ttu-id="26c8f-150">**서버 인증서 사용**</span><span class="sxs-lookup"><span data-stu-id="26c8f-150">**Use server certificate**</span></span>  
     <span data-ttu-id="26c8f-151">인증서로 암호화의 보안을 유지하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-151">Sets the encryption to be secured by a certificate.</span></span> <span data-ttu-id="26c8f-152">목록에서 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-152">Select one from the list.</span></span> <span data-ttu-id="26c8f-153">서버 인증서에 대한 `VIEW DEFINITION` 권한이 없으면 이 목록은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-153">If you do not have the `VIEW DEFINITION` permission on server certificates, this list will be empty.</span></span> <span data-ttu-id="26c8f-154">암호화의 인증서 방법을 선택한 경우에는 이 값을 비워 둘 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-154">If a certificate method of encryption is selected, this value cannot be empty.</span></span> <span data-ttu-id="26c8f-155">인증서에 대한 자세한 내용은 [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="26c8f-155">For more information about certificates, see [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
     <span data-ttu-id="26c8f-156">**서버 비대칭 키 사용**</span><span class="sxs-lookup"><span data-stu-id="26c8f-156">**Use server asymmetric key**</span></span>  
     <span data-ttu-id="26c8f-157">비대칭 키로 암호화의 보안을 유지하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-157">Sets the encryption to be secured by an asymmetric key.</span></span> <span data-ttu-id="26c8f-158">사용 가능한 비대칭 키만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-158">Only available asymmetric keys are displayed.</span></span> <span data-ttu-id="26c8f-159">EKM 모듈에서 보호하는 비대칭 키만 TDE를 사용하여 데이터베이스를 암호화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-159">Only an asymmetric key protected by an EKM module can encrypt a database using TDE.</span></span>  
  
     <span data-ttu-id="26c8f-160">**데이터베이스 암호화 설정**</span><span class="sxs-lookup"><span data-stu-id="26c8f-160">**Set Database Encryption On**</span></span>  
     <span data-ttu-id="26c8f-161">데이터베이스의 TDE를 설정(선택) 또는 해제(선택 취소)로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-161">Alters the database to turn on (checked) or turn off (unchecked) TDE.</span></span>  
  
8.  <span data-ttu-id="26c8f-162">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-162">When finished, click **OK**.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlCreate"></a> <span data-ttu-id="26c8f-163">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="26c8f-163">Using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="26c8f-164">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-164">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="26c8f-165">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-165">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="26c8f-166">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-166">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Create a database master key and a certificate in the master database.  
    USE master ;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '*rt@40(FL&dasl1';  
    GO  
    CREATE CERTIFICATE TestSQLServerCert   
    WITH SUBJECT = 'Certificate to protect TDE key'  
    GO  
    -- Create a backup of the server certificate in the master database.  
    -- The following code stores the backup of the certificate and the private key file in the default data location for this instance of SQL Server   
    -- (C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA).  
  
    BACKUP CERTIFICATE TestSQLServerCert   
    TO FILE = 'TestSQLServerCert'  
    WITH PRIVATE KEY   
    (  
        FILE = 'SQLPrivateKeyFile',  
        ENCRYPTION BY PASSWORD = '*rt@40(FL&dasl1'  
    );  
    GO  
    -- Create a database to be protected by TDE.  
    CREATE DATABASE CustRecords ;  
    GO  
    -- Switch to the new database.  
    -- Create a database encryption key, that is protected by the server certificate in the master database.   
    -- Alter the new database to encrypt the database using TDE.  
    USE CustRecords;  
    GO  
    CREATE DATABASE ENCRYPTION KEY  
    WITH ALGORITHM = AES_128  
    ENCRYPTION BY SERVER CERTIFICATE TestSQLServerCert;  
    GO  
    ALTER DATABASE CustRecords  
    SET ENCRYPTION ON;  
    GO  
    ```  
  
 <span data-ttu-id="26c8f-167">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26c8f-167">For more information, see:</span></span>  
  
-   [<span data-ttu-id="26c8f-168">CREATE MASTER KEY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26c8f-168">CREATE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-master-key-transact-sql)  
  
-   [<span data-ttu-id="26c8f-169">CREATE CERTIFICATE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26c8f-169">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-certificate-transact-sql)  
  
-   [<span data-ttu-id="26c8f-170">BACKUP CERTIFICATE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26c8f-170">BACKUP CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/backup-certificate-transact-sql)  
  
-   [<span data-ttu-id="26c8f-171">CREATE DATABASE&#40;SQL Server Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26c8f-171">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
-   [<span data-ttu-id="26c8f-172">CREATE DATABASE ENCRYPTION KEY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26c8f-172">CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-encryption-key-transact-sql)  
  
-   [<span data-ttu-id="26c8f-173">ALTER DATABASE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26c8f-173">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
##  <a name="to-move-a-database"></a><a name="TsqlProcedure"></a><span data-ttu-id="26c8f-174">데이터베이스를 이동 하려면</span><span class="sxs-lookup"><span data-stu-id="26c8f-174">To move a database</span></span>  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSMove"></a> <span data-ttu-id="26c8f-175">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="26c8f-175">Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="26c8f-176">개체 탐색기에서 위에서 암호화한 데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크** 를 가리킨 후, **분리...** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-176">In Object Explorer, right-click the database you encrypted above, point to **Tasks** and select **Detach...**.</span></span>  
  
     <span data-ttu-id="26c8f-177">**데이터베이스 분리** 대화 상자에는 다음과 같은 옵션이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-177">The following options are available in the **Detach Database** dialog box.</span></span>  
  
     <span data-ttu-id="26c8f-178">**분리할 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="26c8f-178">**Databases to detach**</span></span>  
     <span data-ttu-id="26c8f-179">분리할 데이터베이스를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-179">Lists the databases to detach.</span></span>  
  
     <span data-ttu-id="26c8f-180">**데이터베이스 이름**</span><span class="sxs-lookup"><span data-stu-id="26c8f-180">**Database Name**</span></span>  
     <span data-ttu-id="26c8f-181">분리할 데이터베이스 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-181">Displays the name of the database to be detached.</span></span>  
  
     <span data-ttu-id="26c8f-182">**연결 삭제**</span><span class="sxs-lookup"><span data-stu-id="26c8f-182">**Drop Connections**</span></span>  
     <span data-ttu-id="26c8f-183">지정한 데이터베이스에 대한 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-183">Disconnect connections to the specified database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="26c8f-184">활성 연결이 있는 데이터베이스는 분리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-184">You cannot detach a database with active connections.</span></span>  
  
     <span data-ttu-id="26c8f-185">**통계 업데이트**</span><span class="sxs-lookup"><span data-stu-id="26c8f-185">**Update Statistics**</span></span>  
     <span data-ttu-id="26c8f-186">기본적으로 분리 작업은 데이터베이스를 분리할 때 오래된 최적화 통계를 유지합니다. 기존의 최적화 통계를 업데이트하려면 이 확인란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-186">By default, the detach operation retains any out-of-date optimization statistics when detaching the database; to update the existing optimization statistics, click this check box.</span></span>  
  
     <span data-ttu-id="26c8f-187">**전체 텍스트 카탈로그 유지**</span><span class="sxs-lookup"><span data-stu-id="26c8f-187">**Keep Full-Text Catalogs**</span></span>  
     <span data-ttu-id="26c8f-188">기본적으로 분리 작업은 데이터베이스와 연결된 모든 전체 텍스트 카탈로그를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-188">By default, the detach operation keeps any full-text catalogs that are associated with the database.</span></span> <span data-ttu-id="26c8f-189">전체 텍스트 카탈로그를 제거하려면 **전체 텍스트 카탈로그 유지** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-189">To remove them, clear the **Keep Full-Text Catalogs** check box.</span></span> <span data-ttu-id="26c8f-190">이 옵션은 데이터베이스를 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]에서 업그레이드하는 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-190">This option appears only when you are upgrading a database from [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span>  
  
     <span data-ttu-id="26c8f-191">**상태**</span><span class="sxs-lookup"><span data-stu-id="26c8f-191">**Status**</span></span>  
     <span data-ttu-id="26c8f-192">다음 상태 중 하나를 표시합니다. **준비** 또는 **준비 안 됨**을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-192">Displays one of the following states: **Ready** or **Not ready**.</span></span>  
  
     <span data-ttu-id="26c8f-193">**메시지**</span><span class="sxs-lookup"><span data-stu-id="26c8f-193">**Message**</span></span>  
     <span data-ttu-id="26c8f-194">다음과 같이 **메시지** 열에 데이터베이스에 대한 정보가 표시될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-194">The **Message** column may display information about the database, as follows:</span></span>  
  
    -   <span data-ttu-id="26c8f-195">데이터베이스가 복제와 관련된 경우 **상태** 는 **준비 안 됨** 이고 **메시지** 열에는 **데이터베이스 복제 완료**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-195">When a database is involved with replication, the **Status** is **Not ready** and the **Message** column displays **Database replicated**.</span></span>  
  
    -   <span data-ttu-id="26c8f-196">데이터베이스에 하나 이상의 활성 연결이 있는 경우 **상태**는 **준비 안 됨**이고 **메시지** 열에는 _<number_of_active_connections>_ **활성 연결**이 표시됩니다. 예를 들어 **1 활성 연결**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-196">When a database has one or more active connections, the **Status** is **Not ready** and the **Message** column displays _<number_of_active_connections>_**Active connection(s)** - for example: **1 Active connection(s)**.</span></span> <span data-ttu-id="26c8f-197">데이터베이스를 분리하려면 먼저 **연결 삭제**를 선택하여 모든 활성 연결을 끊어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-197">Before you can detach the database, you need to disconnect any active connections by selecting **Drop Connections**.</span></span>  
  
     <span data-ttu-id="26c8f-198">메시지에 대한 자세한 내용을 보려면 하이퍼링크로 연결된 텍스트를 클릭하여 작업 모니터를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-198">To obtain more information about a message, click the hyperlinked text to open Activity Monitor.</span></span>  
  
2.  <span data-ttu-id="26c8f-199">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-199">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="26c8f-200">Windows 탐색기를 사용하여 데이터베이스 파일을 원본 서버에서 대상 서버의 동일한 위치로 이동 또는 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-200">Using Windows Explorer, move or copy the database files from the source server to the same location on the destination server.</span></span>  
  
4.  <span data-ttu-id="26c8f-201">Window 탐색기를 사용하여 서버 인증서 및 프라이빗 키 파일의 백업을 원본 서버에서 대상 서버의 동일한 위치로 이동 또는 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-201">Using Windows Explorer, move or copy the backup of the server certificate and the private key file from the source server to the same location on the destination server.</span></span>  
  
5.  <span data-ttu-id="26c8f-202">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 대상 인스턴스에서 데이터베이스 마스터 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-202">Create a database master key on the destination instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="26c8f-203">자세한 내용은 아래에서 **Transact-SQL 사용** 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26c8f-203">For more information, see **Using Transact-SQL** below.</span></span>  
  
6.  <span data-ttu-id="26c8f-204">원본 서버 인증서 백업 파일을 사용하여 서버 인증서를 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-204">Recreate the server certificate by using the original server certificate backup file.</span></span> <span data-ttu-id="26c8f-205">자세한 내용은 아래에서 **Transact-SQL 사용** 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26c8f-205">For more information, see **Using Transact-SQL** below.</span></span>  
  
7.  <span data-ttu-id="26c8f-206">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]의 개체 탐색기에서 **데이터베이스** 폴더를 마우스 오른쪽 단추로 클릭하고 **연결...** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-206">In Object Explorer in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], right-click the **Databases** folder and select **Attach...**.</span></span>  
  
8.  <span data-ttu-id="26c8f-207">**데이터베이스 연결** 대화 상자의 **연결할 데이터베이스**아래에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-207">In the **Attach Databases** dialog box, under **Databases to attach**, click **Add**.</span></span>  
  
9. <span data-ttu-id="26c8f-208">**데이터베이스 파일 찾기-**_server_name_ 대화 상자에서 새 서버에 연결할 데이터베이스 파일을 선택 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-208">In the **Locate Database Files -**_server_name_ dialog box, select the database file to attach to the new server and click **OK**.</span></span>  
  
     <span data-ttu-id="26c8f-209">**데이터베이스 연결** 대화 상자에는 다음과 같은 옵션이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-209">The following options are available in the **Attach Databases** dialog box.</span></span>  
  
     <span data-ttu-id="26c8f-210">**연결할 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="26c8f-210">**Databases to attach**</span></span>  
     <span data-ttu-id="26c8f-211">선택한 데이터베이스에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-211">Displays information about the selected databases.</span></span>  
  
     \<no column header>  
     <span data-ttu-id="26c8f-212">연결 작업의 상태를 나타내는 아이콘을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-212">Displays an icon indicating the status of the attach operation.</span></span> <span data-ttu-id="26c8f-213">가능한 아이콘은 아래의 **상태** 에 대한 설명에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-213">The possible icons are described in the **Status** description, below).</span></span>  
  
     <span data-ttu-id="26c8f-214">**MDF 파일 위치**</span><span class="sxs-lookup"><span data-stu-id="26c8f-214">**MDF File Location**</span></span>  
     <span data-ttu-id="26c8f-215">선택한 MDF 파일의 경로와 파일 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-215">Displays the path and file name of the selected MDF file.</span></span>  
  
     <span data-ttu-id="26c8f-216">**데이터베이스 이름**</span><span class="sxs-lookup"><span data-stu-id="26c8f-216">**Database Name**</span></span>  
     <span data-ttu-id="26c8f-217">데이터베이스 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-217">Displays the name of the database.</span></span>  
  
     <span data-ttu-id="26c8f-218">**다른 이름으로 연결**</span><span class="sxs-lookup"><span data-stu-id="26c8f-218">**Attach As**</span></span>  
     <span data-ttu-id="26c8f-219">필요에 따라 연결할 데이터베이스의 이름을 다른 이름으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-219">Optionally, specifies a different name for the database to attach as.</span></span>  
  
     <span data-ttu-id="26c8f-220">**소유자**</span><span class="sxs-lookup"><span data-stu-id="26c8f-220">**Owner**</span></span>  
     <span data-ttu-id="26c8f-221">필요에 따라 다른 소유자를 선택할 수 있도록 가능한 데이터베이스 소유자의 드롭다운 목록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-221">Provides a drop-down list of possible database owners from which you can optionally select a different owner.</span></span>  
  
     <span data-ttu-id="26c8f-222">**상태**</span><span class="sxs-lookup"><span data-stu-id="26c8f-222">**Status**</span></span>  
     <span data-ttu-id="26c8f-223">다음 표에 설명된 내용과 같이 데이터베이스의 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-223">Displays the status of the database according to the following table.</span></span>  
  
    |<span data-ttu-id="26c8f-224">아이콘</span><span class="sxs-lookup"><span data-stu-id="26c8f-224">Icon</span></span>|<span data-ttu-id="26c8f-225">상태 텍스트</span><span class="sxs-lookup"><span data-stu-id="26c8f-225">Status text</span></span>|<span data-ttu-id="26c8f-226">Description</span><span class="sxs-lookup"><span data-stu-id="26c8f-226">Description</span></span>|  
    |----------|-----------------|-----------------|  
    |<span data-ttu-id="26c8f-227">(아이콘 없음)</span><span class="sxs-lookup"><span data-stu-id="26c8f-227">(No icon)</span></span>|<span data-ttu-id="26c8f-228">(텍스트 없음)</span><span class="sxs-lookup"><span data-stu-id="26c8f-228">(No text)</span></span>|<span data-ttu-id="26c8f-229">연결 작업이 시작되지 않았거나 이 개체에 대해 보류 중입니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-229">Attach operation has not been started or may be pending for this object.</span></span> <span data-ttu-id="26c8f-230">대화 상자가 열려 있는 경우에 표시되는 기본 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-230">This is the default when the dialog is opened.</span></span>|  
    |<span data-ttu-id="26c8f-231">녹색, 오른쪽 방향 삼각형</span><span class="sxs-lookup"><span data-stu-id="26c8f-231">Green, right-pointing triangle</span></span>|<span data-ttu-id="26c8f-232">진행 중</span><span class="sxs-lookup"><span data-stu-id="26c8f-232">In progress</span></span>|<span data-ttu-id="26c8f-233">연결 작업이 시작되었지만 아직 완료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-233">Attach operation has been started but it is not complete.</span></span>|  
    |<span data-ttu-id="26c8f-234">녹색 확인 표시</span><span class="sxs-lookup"><span data-stu-id="26c8f-234">Green check mark</span></span>|<span data-ttu-id="26c8f-235">Success</span><span class="sxs-lookup"><span data-stu-id="26c8f-235">Success</span></span>|<span data-ttu-id="26c8f-236">개체가 성공적으로 연결되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-236">The object has been attached successfully.</span></span>|  
    |<span data-ttu-id="26c8f-237">흰색 십자 표시가 있는 빨강 원</span><span class="sxs-lookup"><span data-stu-id="26c8f-237">Red circle containing a white cross</span></span>|<span data-ttu-id="26c8f-238">Error</span><span class="sxs-lookup"><span data-stu-id="26c8f-238">Error</span></span>|<span data-ttu-id="26c8f-239">연결 작업을 수행하는 동안 오류가 발생하여 완료하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-239">Attach operation encountered an error and did not complete successfully.</span></span>|  
    |<span data-ttu-id="26c8f-240">오른쪽과 왼쪽에 두 개의 검정 사분면이 있고 위쪽과 아래쪽에 두 개의 흰색 사분면이 있는 원</span><span class="sxs-lookup"><span data-stu-id="26c8f-240">Circle containing two black quadrants (on left and right) and two white quadrants (on top and bottom)</span></span>|<span data-ttu-id="26c8f-241">중지됨</span><span class="sxs-lookup"><span data-stu-id="26c8f-241">Stopped</span></span>|<span data-ttu-id="26c8f-242">사용자가 작업을 중지하여 연결 작업이 완료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-242">Attach operation was not completed successfully because the user stopped the operation.</span></span>|  
    |<span data-ttu-id="26c8f-243">시계 반대 방향을 가리키는 곡선 모양의 화살표가 있는 원</span><span class="sxs-lookup"><span data-stu-id="26c8f-243">Circle containing a curved arrow pointing counter-clockwise</span></span>|<span data-ttu-id="26c8f-244">롤백됨</span><span class="sxs-lookup"><span data-stu-id="26c8f-244">Rolled Back</span></span>|<span data-ttu-id="26c8f-245">연결 작업이 성공적으로 완료되었지만 다른 개체를 연결하는 동안 발생한 오류로 인해 롤백되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-245">Attach operation was successful but it has been rolled back due to an error during attachment of another object.</span></span>|  
  
     <span data-ttu-id="26c8f-246">**메시지**</span><span class="sxs-lookup"><span data-stu-id="26c8f-246">**Message**</span></span>  
     <span data-ttu-id="26c8f-247">빈 메시지 또는 "파일을 찾을 수 없습니다"라는 하이퍼링크를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-247">Displays either a blank message or a "File not found" hyperlink.</span></span>  
  
     <span data-ttu-id="26c8f-248">**추가**</span><span class="sxs-lookup"><span data-stu-id="26c8f-248">**Add**</span></span>  
     <span data-ttu-id="26c8f-249">필요한 기본 데이터베이스 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-249">Find the necessary main database files.</span></span> <span data-ttu-id="26c8f-250">사용자가 .mdf 파일을 선택하면 **연결할 데이터베이스** 표의 각 필드에 적절한 정보가 자동으로 입력됩니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-250">When the user selects an .mdf file, applicable information is automatically filled in the respective fields of the **Databases to attach** grid.</span></span>  
  
     <span data-ttu-id="26c8f-251">**제거**</span><span class="sxs-lookup"><span data-stu-id="26c8f-251">**Remove**</span></span>  
     <span data-ttu-id="26c8f-252">선택한 파일을 **연결할 데이터베이스** 표에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-252">Removes the selected file from the **Databases to attach** grid.</span></span>  
  
     <span data-ttu-id="26c8f-253">**“** _<database_name>_ **” 데이터베이스 정보**</span><span class="sxs-lookup"><span data-stu-id="26c8f-253">**"** _<database_name>_ **" database details**</span></span>  
     <span data-ttu-id="26c8f-254">연결할 파일의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-254">Displays the names of the files to be attached.</span></span> <span data-ttu-id="26c8f-255">파일의 경로 이름을 확인하거나 변경하려면 **찾아보기** 단추( **...** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-255">To verify or change the pathname of a file, click the **Browse** button (**...**).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="26c8f-256">파일이 없으면 **메시지** 열에 "찾을 수 없음"이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-256">If a file does not exist, the **Message** column displays "Not found."</span></span> <span data-ttu-id="26c8f-257">로그 파일을 찾을 수 없는 경우 다른 디렉터리에 있거나 삭제된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-257">If a log file is not found, it exists in another directory or has been deleted.</span></span> <span data-ttu-id="26c8f-258">올바른 위치를 가리키도록 **데이터베이스 정보** 표의 파일 경로를 업데이트하거나 표에서 로그 파일을 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-258">You need to either update the file path in the **database details** grid to point to the correct location or remove the log file from the grid.</span></span> <span data-ttu-id="26c8f-259">.ndf 데이터 파일을 찾을 수 없는 경우 올바른 위치를 가리키도록 표에서 해당 파일의 경로를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-259">If an .ndf data file is not found, you need to update its path in the grid to point to the correct location.</span></span>  
  
     <span data-ttu-id="26c8f-260">**원래 파일 이름**</span><span class="sxs-lookup"><span data-stu-id="26c8f-260">**Original File Name**</span></span>  
     <span data-ttu-id="26c8f-261">데이터베이스에 속한 연결된 파일의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-261">Displays the name of the attached file belonging to the database.</span></span>  
  
     <span data-ttu-id="26c8f-262">**파일 유형**</span><span class="sxs-lookup"><span data-stu-id="26c8f-262">**File Type**</span></span>  
     <span data-ttu-id="26c8f-263">파일의 형식( **데이터** 또는 **로그**)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-263">Indicates the type of file, **Data** or **Log**.</span></span>  
  
     <span data-ttu-id="26c8f-264">**현재 파일 경로**</span><span class="sxs-lookup"><span data-stu-id="26c8f-264">**Current File Path**</span></span>  
     <span data-ttu-id="26c8f-265">선택한 데이터베이스 파일의 경로를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-265">Displays the path to the selected database file.</span></span> <span data-ttu-id="26c8f-266">이 경로는 직접 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-266">The path can be edited manually.</span></span>  
  
     <span data-ttu-id="26c8f-267">**메시지**</span><span class="sxs-lookup"><span data-stu-id="26c8f-267">**Message**</span></span>  
     <span data-ttu-id="26c8f-268">빈 메시지 또는 "**파일을 찾을 수 없습니다**"라는 하이퍼링크를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-268">Displays either a blank message or a "**File not found**" hyperlink.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlMove"></a> <span data-ttu-id="26c8f-269">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="26c8f-269">Using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="26c8f-270">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-270">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="26c8f-271">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-271">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="26c8f-272">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="26c8f-272">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Detach the TDE protected database from the source server.   
    USE master ;  
    GO  
    EXEC master.dbo.sp_detach_db @dbname = N'CustRecords';  
    GO  
    -- Move or copy the database files from the source server to the same location on the destination server.   
    -- Move or copy the backup of the server certificate and the private key file from the source server to the same location on the destination server.   
    -- Create a database master key on the destination instance of SQL Server.   
    USE master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '*rt@40(FL&dasl1';  
    GO  
    -- Recreate the server certificate by using the original server certificate backup file.   
    -- The password must be the same as the password that was used when the backup was created.  
  
    CREATE CERTIFICATE TestSQLServerCert   
    FROM FILE = 'TestSQLServerCert'  
    WITH PRIVATE KEY   
    (  
        FILE = 'SQLPrivateKeyFile',  
        DECRYPTION BY PASSWORD = '*rt@40(FL&dasl1'  
    );  
    GO  
    -- Attach the database that is being moved.   
    -- The path of the database files must be the location where you have stored the database files.  
    CREATE DATABASE [CustRecords] ON   
    ( FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\CustRecords.mdf' ),  
    ( FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\CustRecords_log.LDF' )  
    FOR ATTACH ;  
    GO  
    ```  
  
 <span data-ttu-id="26c8f-273">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26c8f-273">For more information, see:</span></span>  
  
-   [<span data-ttu-id="26c8f-274">sp_detach_db&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26c8f-274">sp_detach_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql)  
  
-   [<span data-ttu-id="26c8f-275">CREATE MASTER KEY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26c8f-275">CREATE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-master-key-transact-sql)  
  
-   [<span data-ttu-id="26c8f-276">CREATE CERTIFICATE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26c8f-276">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-certificate-transact-sql)  
  
-   [<span data-ttu-id="26c8f-277">CREATE DATABASE&#40;SQL Server Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26c8f-277">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="26c8f-278">참고 항목</span><span class="sxs-lookup"><span data-stu-id="26c8f-278">See Also</span></span>  
 [<span data-ttu-id="26c8f-279">데이터베이스 분리 및 연결&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="26c8f-279">Database Detach and Attach &#40;SQL Server&#41;</span></span>](../../databases/database-detach-and-attach-sql-server.md)  
  
  
