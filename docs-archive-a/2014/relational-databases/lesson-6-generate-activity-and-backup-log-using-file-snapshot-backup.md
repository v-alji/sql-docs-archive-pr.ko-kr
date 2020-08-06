---
title: '7 단원: 데이터 파일을 Azure Storage로 이동 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 26aa534a-afe7-4a14-b99f-a9184fc699bd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 753863d7b8b8d8fa554f1579bee6837c525efd9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653365"
---
# <a name="lesson-7-move-your-data-files-to-azure-storage"></a><span data-ttu-id="8422a-102">7단원: Azure Storage에 데이터 파일 이동</span><span class="sxs-lookup"><span data-stu-id="8422a-102">Lesson 7: Move your data files to Azure Storage</span></span>
  <span data-ttu-id="8422a-103">이 단원에서는 데이터 파일을 Azure Storage로 이동 하는 방법에 대해 설명 합니다 (SQL Server 인스턴스는 아님).</span><span class="sxs-lookup"><span data-stu-id="8422a-103">In this lesson, you will learn how to move your data files to Azure Storage (but not your SQL Server instance).</span></span> <span data-ttu-id="8422a-104">이 단원을 수행하기 위해 4, 5, 6단원을 완료할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8422a-104">To follow this lesson, you do not need to complete Lesson 4, 5, and 6.</span></span>  
  
 <span data-ttu-id="8422a-105">데이터 파일을 Azure Storage로 이동 하려면 문을 사용 하 여 `ALTER DATABASE` 데이터 파일의 위치를 변경 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8422a-105">To move your data files to Azure Storage, you can use the `ALTER DATABASE` statement as it helps to change the location of the data files.</span></span>  
  
 <span data-ttu-id="8422a-106">이 단원에서는 다음 단계를 이미 완료했다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="8422a-106">This lesson assumes that you already completed the following steps:</span></span>  
  
-   <span data-ttu-id="8422a-107">Azure Storage 계정이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8422a-107">You have an Azure Storage account.</span></span>  
  
-   <span data-ttu-id="8422a-108">Azure Storage 계정으로 컨테이너를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="8422a-108">You have created a container under your Azure Storage account.</span></span>  
  
-   <span data-ttu-id="8422a-109">읽기, 쓰기 및 나열 권한이 있는 컨테이너에 정책을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="8422a-109">You have created a policy on a container with read, write, and list rights.</span></span> <span data-ttu-id="8422a-110">SAS 키도 생성했습니다.</span><span class="sxs-lookup"><span data-stu-id="8422a-110">You also generated a SAS key.</span></span>  
  
-   <span data-ttu-id="8422a-111">원본 컴퓨터에서 SQL Server 자격 증명을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="8422a-111">You have created a SQL Server credential on the source machine.</span></span>  
  
 <span data-ttu-id="8422a-112">다음 단계를 사용 하 여 데이터 파일을 Azure Storage로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8422a-112">Next, use the following steps to move your data files to Azure Storage:</span></span>  
  
1.  <span data-ttu-id="8422a-113">먼저 원본 컴퓨터에서 테스트 데이터베이스를 만들고 일부 데이터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8422a-113">First, create a test database in the source machine and add some data to it.</span></span>  
  
    ```sql  
  
    USE master;   
    CREATE DATABASE TestDB1Alter;   
    GO   
    USE TestDB1Alter;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO  
  
    ```  
  
2.  <span data-ttu-id="8422a-114">다음 코드를 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="8422a-114">Run the following code:</span></span>  
  
    ```sql  
  
    -- In the following statement, modify the path specified in FILENAME to   
    -- the new location of the file in Azure Storage container.   
    ALTER DATABASE TestDB1Alter    
        MODIFY FILE ( NAME = TestDB1Alter,    
                    FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontaineralter/TestDB1AlterData.mdf');   
    GO  
  
    ```  
  
3.  <span data-ttu-id="8422a-115">이를 실행 하면 "" TestDB1Alter "파일이 시스템 카탈로그에서 수정 되었습니다. 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8422a-115">When you run this, you will see this message: "The file "TestDB1Alter" has been modified in the system catalog.</span></span> <span data-ttu-id="8422a-116">새 경로는 다음에 데이터베이스가 시작 될 때 사용 됩니다. "</span><span class="sxs-lookup"><span data-stu-id="8422a-116">The new path will be used the next time the database is started."</span></span>  
  
4.  <span data-ttu-id="8422a-117">데이터베이스를 오프라인으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8422a-117">Then, set the database offline.</span></span>  
  
    ```sql  
  
    ALTER DATABASE TestDB1Alter SET OFFLINE;   
    GO  
  
    ```  
  
5.  <span data-ttu-id="8422a-118">이제 [AzCopy Tool](https://docs.microsoft.com/archive/blogs/windowsazurestorage/azcopy-uploadingdownloading-files-for-windows-azure-blobs), [Put Page](https://msdn.microsoft.com/library/azure/ee691975.aspx), [Storage Client Library Reference](https://msdn.microsoft.com/library/azure/dn261237.aspx)또는 타사 저장소 탐색기 도구 중 하나를 사용 하 여 데이터 파일을 Azure Storage에 복사 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8422a-118">Now, you need to copy the data files to Azure Storage by using one of the following methods: [AzCopy Tool](https://docs.microsoft.com/archive/blogs/windowsazurestorage/azcopy-uploadingdownloading-files-for-windows-azure-blobs), [Put Page](https://msdn.microsoft.com/library/azure/ee691975.aspx), [Storage Client Library Reference](https://msdn.microsoft.com/library/azure/dn261237.aspx), or a third-party storage explorer tool.</span></span>  
  
     <span data-ttu-id="8422a-119">**중요** : 이 새로운 향상된 기능을 사용할 때는 항상 블록 Blob이 아니라 페이지 Blob을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8422a-119">**Important:** When using this new enhancement, always make sure that you create a page blob not a block blob.</span></span>  
  
6.  <span data-ttu-id="8422a-120">데이터베이스를 온라인으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8422a-120">Then, set the database online.</span></span>  
  
    ```sql  
  
    ALTER DATABASE TestDB1Alter SET ONLINE;   
    GO  
  
    ```  
  
 <span data-ttu-id="8422a-121">**다음 단원:**</span><span class="sxs-lookup"><span data-stu-id="8422a-121">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="8422a-122">단원 8. Azure Storage로 데이터베이스 복원</span><span class="sxs-lookup"><span data-stu-id="8422a-122">Lesson 8. Restore a database to Azure Storage</span></span>](lesson-7-restore-a-database-to-a-point-in-time.md)  
  
  
