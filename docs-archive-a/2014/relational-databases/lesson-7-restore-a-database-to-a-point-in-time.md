---
title: '8단원: 데이터베이스를 Azure Storage로 복원 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a9f99670-e1de-441e-972c-69faffcac17a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: adec725d1b519fb67560dc572823ba0a116aaa54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660548"
---
# <a name="lesson-8-restore-a-database-to-azure-storage"></a><span data-ttu-id="a6c39-103">8단원:</span><span class="sxs-lookup"><span data-stu-id="a6c39-103">Lesson 8.</span></span> <span data-ttu-id="a6c39-104">Azure Storage에 데이터베이스 복원</span><span class="sxs-lookup"><span data-stu-id="a6c39-104">Restore a database to Azure Storage</span></span>
  <span data-ttu-id="a6c39-105">이 단원에서는 로컬로 백업 파일을 만들고 Azure Storage 복원 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-105">In this lesson, you will learn how to create a backup file locally and then restore it to Azure Storage.</span></span> <span data-ttu-id="a6c39-106">온-프레미스 또는 Azure의 가상 머신에서 데이터베이스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-106">Note that you can have your database either on either on-premises or in a virtual machine in Azure.</span></span> <span data-ttu-id="a6c39-107">이 단원을 수행하기 위해 4, 5, 6, 7단원을 완료할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-107">To follow this lesson, you do not need to complete Lesson 4, 5, 6, and 7.</span></span>  
  
 <span data-ttu-id="a6c39-108">이 단원에서는 다음 단계를 이미 완료했다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-108">This lesson assumes that you already completed the following steps:</span></span>  
  
-   <span data-ttu-id="a6c39-109">Azure Storage 계정이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-109">You have an Azure Storage account.</span></span>  
  
-   <span data-ttu-id="a6c39-110">Azure Storage 계정으로 컨테이너를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-110">You have created a container under your Azure Storage account.</span></span>  
  
-   <span data-ttu-id="a6c39-111">읽기, 쓰기 및 나열 권한이 있는 컨테이너에 정책을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-111">You have created a policy on a container with read, write, and list rights.</span></span> <span data-ttu-id="a6c39-112">SAS 키도 생성했습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-112">You also generated a SAS key.</span></span>  
  
-   <span data-ttu-id="a6c39-113">원본 컴퓨터에서 공유 액세스 서명 기반의 SQL Server 자격 증명을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-113">You have created a SQL Server credential on the source machine based on Shared Access Signature.</span></span>  
  
-   <span data-ttu-id="a6c39-114">원본 컴퓨터에서 데이터베이스를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-114">You have created a database in the source machine.</span></span>  
  
 <span data-ttu-id="a6c39-115">Azure Storage로 데이터베이스를 복원 하려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-115">To restore a database to Azure Storage, you can follow these steps:</span></span>  
  
1.  <span data-ttu-id="a6c39-116">원본 컴퓨터에서 SQL Server Management Studio를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-116">In the source machine, start SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="a6c39-117">새로 만든 데이터베이스에 연결된 경우 쿼리 창을 열고</span><span class="sxs-lookup"><span data-stu-id="a6c39-117">When connected to the newly created database, open the query window.</span></span> <span data-ttu-id="a6c39-118">다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-118">Run the following statement:</span></span>  
  
    ```sql  
  
    USE TestDB3Restore;   
    GO   
    BACKUP DATABASE TestDB3Restore   
    TO DISK = 'C:\BACKUP\TestDB3Restore.Bak'   
       WITH FORMAT,   
       NAME = 'Full Backup of TestDB3Restore'   
    GO  
  
    ```  
  
3.  <span data-ttu-id="a6c39-119">다음 문을 복사하여 쿼리 창에서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-119">Next, copy and run the following statements in the Query window.</span></span>  
  
    ```sql  
  
    USE master;   
    GO   
    RESTORE DATABASE TestDB3Restore    
    FROM DISK = 'C:\BACKUP\TestDB3Restore.bak'    
    WITH REPLACE,   
    MOVE 'TestDB3Restore' TO 'https://teststorageaccnt.blob.core.windows.net/testcontainrestore/TestDB3Restore.mdf',     
    MOVE 'TestDB3Restore_log' TO 'https://teststorageaccnt.blob.core.windows.net/testcontainrestore/TestDB3Restore_log.ldf';   
    GO  
  
    ```  
  
     <span data-ttu-id="a6c39-120">이 단계가 끝나면 컨테이너에 관리 포털의 데이터 파일(.mdf 및 .ldf)이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-120">At the end of this step, your container should list data (.mdf) and (.ldf) files on the Management Portal.</span></span>  
  
 <span data-ttu-id="a6c39-121">SQL Server Management Studio 사용자 인터페이스를 사용 하 여 Azure Storage을 가리키는 데이터 및 로그 파일이 포함 된 데이터베이스를 복원 하려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-121">To restore a database with data and log files pointing to Azure Storage using SQL Server Management Studio user interface, perform these steps:</span></span>  
  
1.  <span data-ttu-id="a6c39-122">**개체 탐색기**에서 서버 이름을 클릭 하 여 서버 트리를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-122">In **Object Explorer**, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="a6c39-123">**데이터베이스**를 확장 하 고 데이터베이스를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-123">Expand **Databases**, and, select your database.</span></span>  
  
3.  <span data-ttu-id="a6c39-124">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 가리킨 다음 **복원**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-124">Right-click the database, point to **Tasks**, and then click **Restore**.</span></span>  
  
4.  <span data-ttu-id="a6c39-125">**일반** 페이지의 **복원** 원본 섹션에서 **원본** 장치를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-125">On the **General** page, in the **Restore** source section, click **Source** device.</span></span>  
  
5.  <span data-ttu-id="a6c39-126">**원본** 디바이스 입력란에 대한 찾아보기 단추를 클릭합니다. **백업 디바이스 선택** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-126">Click the browse button for the **Source** device text box, which opens the **Select Backup Devices** dialog box.</span></span>  
  
6.  <span data-ttu-id="a6c39-127">백업 미디어 입력란에서 **파일**을 선택하고 **추가** 단추를 클릭하여 백업 파일(.bak)을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-127">In the Backup media text box, select **File**, and click the **Add** button to locate the backup (.bak) file.</span></span> <span data-ttu-id="a6c39-128">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-128">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="a6c39-129">첫 번째 페이지에서 **파일** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-129">Click **Files** on the first page.</span></span>  
  
8.  <span data-ttu-id="a6c39-130">**데이터베이스 파일** 을 다음으로 복원 섹션의 다음 **으로 복원** 필드에 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-130">In the **Restore Database Files** as section, under **Restore As** field, type the followings:</span></span>  
  
     <span data-ttu-id="a6c39-131">데이터 파일에 대해을 입력 `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS.mdf` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-131">For data file, type: `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS.mdf`.</span></span> <span data-ttu-id="a6c39-132">로그 파일에 대해을 입력 `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS_log.ldf` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-132">For log file, type: `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS_log.ldf`.</span></span>  
  
     <span data-ttu-id="a6c39-133">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-8.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="a6c39-133">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-8.gif "SQL 14 CTP2")</span></span>  
  
9. <span data-ttu-id="a6c39-134">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-134">Click **OK**.</span></span>  
  
 <span data-ttu-id="a6c39-135">복원이 완료되면 관리 포털에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-135">When the restore is done, log in to the Management Portal.</span></span> <span data-ttu-id="a6c39-136">다음과 같이 컨테이너에서 .mdf 및 .ldf 파일을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c39-136">You should be able to see the .mdf and .ldf files in the container as follows:</span></span>  
  
 <span data-ttu-id="a6c39-137">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-9.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="a6c39-137">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-9.gif "SQL 14 CTP2")</span></span>  
  
 <span data-ttu-id="a6c39-138">**다음 단원:**</span><span class="sxs-lookup"><span data-stu-id="a6c39-138">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="a6c39-139">단원 9. Azure Storage에서 데이터베이스 복원</span><span class="sxs-lookup"><span data-stu-id="a6c39-139">Lesson 9. Restore a database from Azure Storage</span></span>](../relational-databases/lesson-8-restore-as-new-database-from-log-backup.md)  
  
  
