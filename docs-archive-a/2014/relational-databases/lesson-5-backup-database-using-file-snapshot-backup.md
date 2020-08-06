---
title: '6 단원: 온-프레미스의 원본 컴퓨터에서 Azure의 대상 컴퓨터로 데이터베이스 마이그레이션 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: d9134ade-7b03-4c5c-8ed3-3bc369a61691
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b9af8a260493561f9728d1677b7667bd3f36cb46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653366"
---
# <a name="lesson-6-migrate-a-database-from-a-source-machine-on-premises-to-a-destination-machine-in-azure"></a><span data-ttu-id="44000-102">6단원: 온-프레미스의 원본 머신에서 Azure의 대상 머신으로 데이터베이스 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="44000-102">Lesson 6: Migrate a database from a source machine on-premises to a destination machine in Azure</span></span>
  <span data-ttu-id="44000-103">이 단원에서는 다른 온-프레미스 컴퓨터 또는 Azure의 가상 컴퓨터에 있을 수 있는 다른 SQL Server 이미 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-103">This lesson assumes that you already have another SQL Server, which might reside in another on-premises computer or in a virtual machine in Azure.</span></span> <span data-ttu-id="44000-104">Azure에서 SQL Server 가상 머신을 만드는 방법에 대 한 자세한 내용은 [azure에서 SQL Server 가상 머신 프로 비전](https://www.windowsazure.com/manage/windows/common-tasks/install-sql-server/)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="44000-104">For information on how to create a SQL Server virtual machine in Azure, see [Provisioning a SQL Server Virtual Machine on Azure](https://www.windowsazure.com/manage/windows/common-tasks/install-sql-server/).</span></span> <span data-ttu-id="44000-105">Azure에서 SQL Server 가상 컴퓨터를 프로 비전 한 후 다른 컴퓨터의 SQL Server Management Studio을 통해이 가상 컴퓨터의 SQL Server 인스턴스에 연결할 수 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-105">After provisioning a SQL Server virtual machine in Azure, make sure that you can connect to an instance of SQL Server in this virtual machine via SQL Server Management Studio in another computer.</span></span>  
  
 <span data-ttu-id="44000-106">이 단원에서는 다음 단계를 이미 완료했다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-106">This lesson also assumes that you already completed the following steps:</span></span>  
  
-   <span data-ttu-id="44000-107">Azure Storage 계정이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44000-107">You have an Azure Storage account.</span></span>  
  
-   <span data-ttu-id="44000-108">Azure Storage 계정으로 컨테이너를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="44000-108">You have created a container under your Azure Storage account.</span></span>  
  
-   <span data-ttu-id="44000-109">읽기, 쓰기 및 나열 권한이 있는 컨테이너에 정책을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="44000-109">You have created a policy on a container with read, write, and list rights.</span></span> <span data-ttu-id="44000-110">SAS 키도 생성했습니다.</span><span class="sxs-lookup"><span data-stu-id="44000-110">You also generated a SAS key.</span></span>  
  
-   <span data-ttu-id="44000-111">원본 컴퓨터에서 SQL Server 자격 증명을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="44000-111">You have created a SQL Server credential on the source machine.</span></span>  
  
-   <span data-ttu-id="44000-112">Azure에서 대상 SQL Server 가상 머신을 이미 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="44000-112">You already have created a destination SQL Server virtual machine in Azure.</span></span> <span data-ttu-id="44000-113">SQL Server 2014를 포함하는 플랫폼 이미지를 선택하여 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="44000-113">We recommend that you create it by selecting a platform image that includes SQL Server 2014.</span></span>  
  
 <span data-ttu-id="44000-114">SQL Server 온-프레미스에서 Azure의 다른 가상 머신으로 데이터베이스를 마이그레이션하려면 다음 단계를 수행 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="44000-114">To migrate a database from SQL Server on-premises to another virtual machine in Azure, you can follow these steps:</span></span>  
  
1.  <span data-ttu-id="44000-115">원본 컴퓨터(이 자습서의 경우 온-프레미스 컴퓨터)의 SQL Server Management Studio에서 쿼리 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="44000-115">In the source machine (which is an on-premises computer in this tutorial), open a query window in SQL Server Management Studio.</span></span> <span data-ttu-id="44000-116">다음 문을 실행하여 데이터베이스를 분리하고 다른 컴퓨터로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-116">Detach your database to move it to another machine by executing these statements:</span></span>  
  
    ```  
    -- Detach the database in the source machine   
    USE master  
    EXEC sp_detach_db 'TestDB1', 'true';  
    ```  
  
2.  <span data-ttu-id="44000-117">대상 컴퓨터로 데이터베이스를 전송해야 하는 경우 먼저 대상 컴퓨터를 준비해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-117">If you need to transfer a database to a destination machine, first you must prepare it.</span></span> <span data-ttu-id="44000-118">대상 컴퓨터를 준비하려면 먼저 대상 컴퓨터에서 SQL Server 자격 증명을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-118">To prepare your destination machine, first you need to create a SQL Server credential in the destination machine.</span></span> <span data-ttu-id="44000-119">암호화된 데이터베이스인 경우 원본 컴퓨터에서 대상 컴퓨터로 인증서도 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-119">If it is an encrypted database, you need to import the certificate from the source machine to the destination machine as well.</span></span>  
  
    1.  <span data-ttu-id="44000-120">대상 컴퓨터에서 SQL Server 자격 증명을 만들려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-120">To create a SQL Server Credential in the destination machine, follow these steps:</span></span>  
  
        1.  <span data-ttu-id="44000-121">원본 컴퓨터에서 SQL Server Management Studio를 통해 대상 컴퓨터에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-121">Connect to the destination machine via SQL Server Management Studio in your source computer.</span></span>  <span data-ttu-id="44000-122">또는 대상 컴퓨터에서 SQL Server Management Studio를 직접 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-122">Or, start SQL Server Management Studio in your destination computer directly.</span></span>  
  
        2.  <span data-ttu-id="44000-123">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-123">On the Standard tool bar, click **New Query**.</span></span>  
  
        3.  <span data-ttu-id="44000-124">다음 예를 복사하여 쿼리 창에 붙여 넣고 필요한 대로 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-124">Copy and paste the following example into the query window, modify as needed.</span></span> <span data-ttu-id="44000-125">다음 문은 저장소 컨테이너의 공유 액세스 인증서를 저장 하는 SQL Server 자격 증명을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="44000-125">The following statement creates a SQL Server Credential to store your storage container's Shared Access Certificate.</span></span>  
  
            ```sql  
  
            USE master   
            GO   
            CREATE CREDENTIAL [http://teststorageaccnt.blob.core.windows.net/testcontainer]   
            WITH IDENTITY='SHARED ACCESS SIGNATURE',   
            SECRET = 'your SAS key'   
            GO  
  
            ```  
  
        4.  <span data-ttu-id="44000-126">사용할 수 있는 모든 자격 증명을 보려면 쿼리 창에서 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-126">To see all available credentials, you can run the following statement in the query window:</span></span>  
  
            ```sql  
            SELECT * from sys.credentials   
            ```  
  
        5.  <span data-ttu-id="44000-127">대상 서버에 연결되었으면 쿼리 창을 열고 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-127">When connected to the destination server, open query window, and run:</span></span>  
  
            ```sql  
  
            -- Create a master key and a server certificate   
            USE master   
            GO   
            CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'MySQLKey01'; -- You may use a different password.   
            GO   
            CREATE CERTIFICATE MySQLCert   
            FROM FILE = 'C:\certs\MySQLCert.CER'   
            WITH PRIVATE KEY   
            (   
            FILE = 'C:\certs\MySQLPrivateKeyFile.PVK',   
            DECRYPTION BY PASSWORD = 'MySQLKey01'   
            );   
            GO  
  
            ```  
  
             <span data-ttu-id="44000-128">이 단계의 끝에서 대상 컴퓨터는 원본 컴퓨터에서 백업된 암호화 인증서를 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="44000-128">At the end of this step, the destination machine has imported the encryption certificate that was backed up from the source machine.</span></span> <span data-ttu-id="44000-129">다음 작업으로, 대상 컴퓨터에서 데이터 파일을 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44000-129">Next, you can attach the data files in the destination machine.</span></span>  
  
    2.  <span data-ttu-id="44000-130">그런 다음 FOR ATTACH 옵션을 사용 하 여 Azure Storage에 있는 기존 파일을 가리키는 데이터 및 로그 파일이 포함 된 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="44000-130">Then, create a database with data and log files pointing to the existing files in Azure Storage by using FOR ATTACH option.</span></span> <span data-ttu-id="44000-131">쿼리 창에서 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-131">In the query window, run the following statement:</span></span>  
  
        ```sql  
  
        --Create a database on the destination server   
        CREATE DATABASE TestDB1onDest   
        ON   
        (NAME = TestDB1_data,   
            FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Data.mdf' )   
        LOG ON   
         (NAME = TestDB1_log,   
            FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Log.ldf')   
        FOR ATTACH   
        GO  
  
        ```  
  
    3.  <span data-ttu-id="44000-132">개체 탐색기에서 데이터베이스를 클릭하고 새로 고침을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-132">On the Object Explorer, click Databases, right-click Refresh.</span></span> <span data-ttu-id="44000-133">새로 만든 데이터베이스인 TestDB1onDest가 표시된 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44000-133">You should be able to see the newly created database TestDB1onDest listed.</span></span>  
  
    4.  <span data-ttu-id="44000-134">쿼리 창에서 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-134">Next, run the following statement in the query window:</span></span>  
  
        ```sql  
  
        USE TestDB1onDest   
        SELECT * FROM Table1;   
        GO  
  
        ```  
  
         <span data-ttu-id="44000-135">4단원에서 입력한 데이터가 모두 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="44000-135">This should list all the data you entered in Lesson 4.</span></span>  
  
 <span data-ttu-id="44000-136">암호화된 데이터베이스가 데이터 이동 없이 다른 컴퓨팅 인스턴스로 전송되었습니다.</span><span class="sxs-lookup"><span data-stu-id="44000-136">Note that the encrypted database was transferred to another compute instance with no data movement.</span></span>  
  
 <span data-ttu-id="44000-137">SQL Server Management Studio 사용자 인터페이스를 사용 하 여 Azure Storage에 있는 기존 파일을 가리키는 데이터 및 로그 파일이 포함 된 데이터베이스를 만들려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-137">To create a database with data and log files pointing to the existing files in Azure Storage using SQL Server Management Studio user interface, perform these steps:</span></span>  
  
1.  <span data-ttu-id="44000-138">**개체 탐색기**에서 SQL Server 데이터베이스 엔진의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-138">In **Object Explorer**, connect to an instance of the SQL Server Database Engine and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="44000-139">**데이터베이스**를 마우스 오른쪽 단추로 클릭한 다음 **새 데이터베이스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-139">Right-click **Databases**, and then click **New Database**.</span></span> <span data-ttu-id="44000-140">TestDB1을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-140">Then, right-click TestDB1.</span></span> <span data-ttu-id="44000-141">태스크를 클릭한 다음 분리를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-141">Click Tasks, and then click Detach.</span></span> <span data-ttu-id="44000-142">분리 대화 상자에서 연결 삭제를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-142">In the Detach dialog window, check Drop Connections.</span></span> <span data-ttu-id="44000-143">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-143">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="44000-144">SQL Server 2014 CTP2 이상이 설치된 대상 컴퓨터에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-144">Connect to the destination machine, which has SQL Server 2014 CTP2 or later.</span></span> <span data-ttu-id="44000-145">대상 컴퓨터를 준비하려면 TestDB1을 배치한 동일한 컨테이너를 가리키도록 대상 컴퓨터에서 SQL Server 자격 증명을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-145">To prepare your destination machine, you need to create a SQL Server credential in the destination machine to point to the same container that you put TestDB1 in.</span></span> <span data-ttu-id="44000-146">동일한 컴퓨터에서 다시 연결할 경우 다른 자격 증명을 만들 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="44000-146">If you are going to re-attach in the same computer, you do not need to create another credential.</span></span>  
  
4.  <span data-ttu-id="44000-147">**개체 탐색기**에서 **데이터베이스** 를 마우스 오른쪽 단추로 클릭하고 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-147">In **Object Explorer**, right-click **Databases** and click **Attach**.</span></span>  
  
5.  <span data-ttu-id="44000-148">**데이터베이스 연결** 대화 상자에서 연결할 데이터베이스를 지정하려면 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-148">In the **Attach Databases** dialog box, to specify the database to be attached, click **Add**.</span></span> <span data-ttu-id="44000-149">**데이터베이스 파일 찾기** 대화 상자에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-149">In the **Locate Database Files** dialog window:</span></span>  
  
     <span data-ttu-id="44000-150">데이터베이스 데이터 파일 위치에 대해를 입력 `https://teststorageaccnt.blob.core.windows.net/testcontainer/` 합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-150">For Database Data File Location, type: `https://teststorageaccnt.blob.core.windows.net/testcontainer/`.</span></span>  
  
     <span data-ttu-id="44000-151">파일 이름에을 입력 `TestDB1Data.mdf` 합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-151">For File name, type: `TestDB1Data.mdf`.</span></span>  
  
6.  <span data-ttu-id="44000-152">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44000-152">Click **OK**.</span></span>  
  
     <span data-ttu-id="44000-153">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-6-7.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="44000-153">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-6-7.gif "SQL 14 CTP2")</span></span>  
  
 <span data-ttu-id="44000-154">**다음 단원:**</span><span class="sxs-lookup"><span data-stu-id="44000-154">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="44000-155">7단원: Azure Storage에 데이터 파일 이동</span><span class="sxs-lookup"><span data-stu-id="44000-155">Lesson 7: Move your data files to Azure Storage</span></span>](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)  
  
