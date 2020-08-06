---
title: '4 단원: Azure Storage에서 데이터베이스 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a9ae1501-b614-49d3-b975-6569da8350b2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 50fca85111d5897b738e577e7735049e0b055a03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660551"
---
# <a name="lesson-4-create-a-database-in-azure-storage"></a><span data-ttu-id="fa0e8-102">4단원: Azure Storage에서 데이터베이스 만들기</span><span class="sxs-lookup"><span data-stu-id="fa0e8-102">Lesson 4: Create a database in Azure Storage</span></span>
  <span data-ttu-id="fa0e8-103">이 단원에서는 Azure의 SQL Server 데이터 파일 기능을 사용 하 여 데이터베이스를 만드는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-103">In this lesson, you will learn how to create a database using the SQL Server Data Files in Azure feature.</span></span> <span data-ttu-id="fa0e8-104">이 단원 전에 1, 2, 3단원을 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-104">Note that before this lesson, you must complete the Lesson 1, 2, and 3.</span></span> <span data-ttu-id="fa0e8-105">3 단원에서는 Azure storage 컨테이너에 대 한 정보와 관련 정책 이름 및 SAS 키를 4 단원 이전 SQL Server 자격 증명 저장소에 저장 해야 하기 때문에 매우 중요 한 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-105">Lesson 3 is a very important step because you need to store the information about your Azure storage container and its associated policy name and SAS key in the SQL Server credential store before Lesson 4.</span></span>  
  
 <span data-ttu-id="fa0e8-106">데이터 또는 로그 파일에서 사용하는 각 스토리지 컨테이너에 대해 컨테이너 경로와 일치하는 이름의 SQL Server 자격 증명을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-106">For each storage container used by a data or log file, you must create a SQL Server Credential whose name matches the container path.</span></span> <span data-ttu-id="fa0e8-107">그런 다음에서 새 데이터베이스를 만들 수 있습니다 Azure Storage</span><span class="sxs-lookup"><span data-stu-id="fa0e8-107">Then, you can create a new database in Azure Storage</span></span>  
  
 <span data-ttu-id="fa0e8-108">이 단원에서는 다음 단계를 이미 완료했다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-108">This lesson assumes that you already completed the following steps:</span></span>  
  
-   <span data-ttu-id="fa0e8-109">Azure Storage 계정이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-109">You have an Azure Storage account.</span></span>  
  
-   <span data-ttu-id="fa0e8-110">Azure Storage 계정으로 컨테이너를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-110">You have created a container under your Azure Storage account.</span></span>  
  
-   <span data-ttu-id="fa0e8-111">읽기, 쓰기 및 나열 권한이 있는 컨테이너에 정책을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-111">You have created a policy on a container with read, write, and list rights.</span></span> <span data-ttu-id="fa0e8-112">SAS 키도 생성했습니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-112">You also generated a SAS key.</span></span>  
  
-   <span data-ttu-id="fa0e8-113">원본 컴퓨터에서 SQL Server 자격 증명을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-113">You have created a SQL Server credential on the source machine.</span></span>  
  
 <span data-ttu-id="fa0e8-114">Azure Storage의 데이터 파일 SQL Server 기능을 사용 하 여 Azure에서 데이터베이스를 만들려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-114">To create a database in Azure using the SQL Server Data Files in Azure Storage feature, follow these steps:</span></span>  
  
1.  <span data-ttu-id="fa0e8-115">SQL Server Management Studio에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-115">Connect to SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="fa0e8-116">개체 탐색기에서 설치된 데이터베이스 엔진의 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-116">In Object Explorer, connect to the instance of Database Engine installed.</span></span>  
  
3.  <span data-ttu-id="fa0e8-117">표준 도구 모음에서 새 쿼리를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-117">On the Standard tool bar, click New Query.</span></span>  
  
4.  <span data-ttu-id="fa0e8-118">다음 예를 복사하여 쿼리 창에 붙여 넣고 필요한 대로 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-118">Copy and paste the following example into the query window, modify as needed.</span></span> <span data-ttu-id="fa0e8-119">FILENAME 필드는 스토리지 컨테이너에 있는 데이터베이스 파일의 URI 경로를 가리키며 https로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-119">Note that the FILENAME field refers to the URI path of the database file in storage container and it must start with https.</span></span>  
  
    ```  
  
    --Create a database that uses a SQL Server credential    
    CREATE DATABASE TestDB1    
    ON   
    (NAME = TestDB1_data,   
       FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Data.mdf')   
     LOG ON   
    (NAME = TestDB1_log,   
        FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Log.ldf')   
    GO  
  
    ```  
  
     <span data-ttu-id="fa0e8-120">데이터베이스에 일부 데이터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-120">Add some data to your database.</span></span>  
  
    ```  
  
    USE TestDB1;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO  
  
    ```  
  
5.  <span data-ttu-id="fa0e8-121">온-프레미스 SQL Server에서 새로운 TestDB1을 보려면 개체 탐색기에서 데이터베이스를 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-121">To see the new TestDB1 in your on-premises SQL Server, refresh databases in the Object Explorer.</span></span>  
  
6.  <span data-ttu-id="fa0e8-122">이와 마찬가지로 스토리지 계정에서 새로 만든 데이터베이스를 보려면 SSMS(SQL Server Management Studio)를 통해 스토리지 계정에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-122">Similarly, to see the newly created database in your storage account, connect to your storage account via SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="fa0e8-123">SQL Server Management Studio를 사용 하 여 Azure storage에 연결 하는 방법에 대 한 자세한 내용은 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-123">For information on how to connect to an Azure storage using SQL Server Management Studio, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="fa0e8-124">먼저 스토리지 계정 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-124">First, get the storage account information.</span></span> <span data-ttu-id="fa0e8-125">관리 포털에 로그인한 다음</span><span class="sxs-lookup"><span data-stu-id="fa0e8-125">Log in to the Management Portal.</span></span> <span data-ttu-id="fa0e8-126">**스토리지**를 클릭하고 스토리지 계정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-126">Then, click **Storage** and choose your storage account.</span></span> <span data-ttu-id="fa0e8-127">스토리지 계정이 선택되면 페이지 아래쪽에서 **액세스 키 관리** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-127">When a storage account is selected, click **Manage Access Keys** at the bottom of the page.</span></span> <span data-ttu-id="fa0e8-128">다음과 유사한 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-128">This opens a similar dialog window:</span></span>  
  
         <span data-ttu-id="fa0e8-129">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-1.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="fa0e8-129">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-1.gif "SQL 14 CTP2")</span></span>  
  
    2.  <span data-ttu-id="fa0e8-130">**저장소 계정 이름** 및 **기본 액세스 키** 값을 SSMS의 **Azure Storage에 연결** 대화 상자 창에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-130">Copy the **Storage Account Name** and **Primary Access Key** values to the **Connect to Azure Storage** dialog window in SSMS.</span></span> <span data-ttu-id="fa0e8-131">그런 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-131">Then, click **Connect**.</span></span> <span data-ttu-id="fa0e8-132">다음 스크린 샷에서와 같이 스토리지 계정 컨테이너에 대한 정보가 SSMS에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-132">This brings the information about storage account containers to SSMS as shown in the following screenshot:</span></span>  
  
         <span data-ttu-id="fa0e8-133">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="fa0e8-133">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2.gif "SQL 14 CTP2")</span></span>  
  
 <span data-ttu-id="fa0e8-134">다음 스크린 샷에서는 온-프레미스 및 Azure Storage 환경 모두에서 새로 만든 데이터베이스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-134">The following screenshot demonstrates the new created database both in on-premises and Azure Storage environment.</span></span>  
  
 <span data-ttu-id="fa0e8-135">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2b.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="fa0e8-135">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2b.gif "SQL 14 CTP2")</span></span>  
  
 <span data-ttu-id="fa0e8-136">**참고:** 컨테이너의 데이터 파일에 대한 활성 참조가 있는 경우 연결된 SQL Server 자격 증명을 삭제하려고 하면 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-136">**Note:** If there are any active references to data files in a container, any attempts to delete the associated SQL Server credential fails.</span></span> <span data-ttu-id="fa0e8-137">이와 마찬가지로 BLOB의 특정 데이터베이스 파일에 대한 임대가 이미 있는 경우 SQL Server 자격 증명을 삭제하려면 먼저 BLOB에서 임대를 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-137">Similarly, if there is already a lease on a specific database file in a blob and you want to delete it, first you need to break the lease on the blob.</span></span> <span data-ttu-id="fa0e8-138">임대를 중단하려면 [Blob 임대](https://msdn.microsoft.com/library/azure/ee691972.aspx)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-138">To break the lease, you can use [Lease Blob](https://msdn.microsoft.com/library/azure/ee691972.aspx).</span></span>  
  
 <span data-ttu-id="fa0e8-139">이 새로운 기능을 사용하면 CREATE DATABASE 문이 기본적으로 클라우드 사용 데이터베이스로 설정되도록 SQL Server를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-139">Using this new feature, you can configure SQL Server so that any CREATE DATABASE statement will default to a cloud enabled database.</span></span> <span data-ttu-id="fa0e8-140">즉, SQL Server Management Studio 서버 인스턴스 속성에서 기본 데이터 및 로그 위치를 설정 하 여 데이터베이스를 만들 때마다 모든 데이터베이스 파일 (.mdf, .ldf)이 Azure Storage에서 페이지 blob으로 만들어지도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-140">In other words, you can set default data and log locations in SQL Server Management Studio Server instance properties so anytime you create a database, all database files (.mdf, .ldf) are created as page blobs in Azure Storage.</span></span>  
  
 <span data-ttu-id="fa0e8-141">SQL Server Management Studio 사용자 인터페이스를 사용 하 여 Azure Storage에서 데이터베이스를 만들려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-141">To create a database in Azure Storage by using SQL Server Management Studio user interface, perform these steps:</span></span>  
  
1.  <span data-ttu-id="fa0e8-142">개체 탐색기에서 SQL Server 데이터베이스 엔진의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-142">In Object Explorer, connect to an instance of the SQL Server Database Engine and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="fa0e8-143">데이터베이스를 마우스 오른쪽 단추로 클릭한 다음 새 데이터베이스를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-143">Right-click Databases, and then click New Database.</span></span>  
  
3.  <span data-ttu-id="fa0e8-144">새 데이터베이스 대화 상자에서 데이터베이스 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-144">In the New Database dialog window, type a database name.</span></span>  
  
4.  <span data-ttu-id="fa0e8-145">주 데이터 및 트랜잭션 로그 파일의 기본값을 변경하려면 데이터베이스 파일 표에서 해당 셀을 클릭한 다음 새 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-145">Change the default values of the primary data and transaction log files, in the Database files grid, click the appropriate cell and enter the new value.</span></span> <span data-ttu-id="fa0e8-146">또한 파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-146">Also, specify the path for the file location.</span></span> <span data-ttu-id="fa0e8-147">Path의 경우 스토리지 컨테이너의 URL 경로를 입력합니다(예: `https://teststorageaccnt.blob.core.windows.net/testcontainer/`).</span><span class="sxs-lookup"><span data-stu-id="fa0e8-147">For Path, type the URL path of the storage container, such as `https://teststorageaccnt.blob.core.windows.net/testcontainer/`.</span></span> <span data-ttu-id="fa0e8-148">FileName의 경우 데이터베이스 파일(.mdf, .ldf)의 물리적 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-148">For FileName, type the physical file names of the database files (.mdf, .ldf).</span></span>  
  
     <span data-ttu-id="fa0e8-149">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-4.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="fa0e8-149">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-4.gif "SQL 14 CTP2")</span></span>  
  
     <span data-ttu-id="fa0e8-150">자세한 내용은 [데이터베이스에 데이터 또는 로그 파일 추가](databases/add-data-or-log-files-to-a-database.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-150">For more information, see [Add Data or Log Files to a Database](databases/add-data-or-log-files-to-a-database.md).</span></span>  
  
5.  <span data-ttu-id="fa0e8-151">다른 모든 기본값을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-151">Keep all other default values.</span></span>  
  
6.  <span data-ttu-id="fa0e8-152">확인을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-152">Click OK.</span></span>  
  
 <span data-ttu-id="fa0e8-153">온-프레미스 SQL Server에서 새로운 TestDB1을 보려면 개체 탐색기에서 데이터베이스를 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-153">To see the new TestDB1 in your on-premises SQL Server, refresh databases in the Object Explorer.</span></span> <span data-ttu-id="fa0e8-154">이 단원의 앞에서 설명한 대로 스토리지 계정에서 새로 만든 데이터베이스를 보려면 SSMS(SQL Server Management Studio)를 통해 스토리지 계정에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="fa0e8-154">Similarly, to see the newly created database in your storage account, connect to your storage account via SQL Server Management Studio (SSMS) as explained earlier in this lesson.</span></span>  
  
 <span data-ttu-id="fa0e8-155">**다음 단원:**</span><span class="sxs-lookup"><span data-stu-id="fa0e8-155">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="fa0e8-156">5 단원. TDE를 사용 하 여 데이터베이스를 암호화 &#40;선택&#41;</span><span class="sxs-lookup"><span data-stu-id="fa0e8-156">Lesson 5. &#40;Optional&#41; Encrypt your database using TDE</span></span>](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)  
  
  
