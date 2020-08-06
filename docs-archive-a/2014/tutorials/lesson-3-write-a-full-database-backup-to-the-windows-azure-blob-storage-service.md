---
title: '3 단원: Azure Blob Storage 서비스에 전체 데이터베이스 백업 작성 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 454c8296-64e9-46ed-b141-5ebfbc8a4fe2
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 17e7e6b608d248a48cde52f1107bb910f06d64ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727520"
---
# <a name="lesson-3-write-a-full-database-backup-to-the-azure-blob-storage-service"></a><span data-ttu-id="fee31-102">3단원: Azure Blob Storage Service로 전체 데이터베이스 백업 작성</span><span class="sxs-lookup"><span data-stu-id="fee31-102">Lesson 3: Write a Full Database Backup to the Azure Blob Storage Service</span></span>
  <span data-ttu-id="fee31-103">이 단원에서는 tsql 문을 사용 하 여 Azure Blob storage 서비스에 대 한 전체 데이터베이스 백업을 수행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fee31-103">This lesson demonstrates the use of tsql statement to perform a full database backup to Azure Blob storage service.</span></span>  
  
## <a name="perform-a-full-database-backup-to-the-azure-blob-storage-service"></a><span data-ttu-id="fee31-104">Azure Blob Storage 서비스에 대 한 전체 데이터베이스 백업 수행</span><span class="sxs-lookup"><span data-stu-id="fee31-104">Perform a Full Database Backup to the Azure Blob Storage Service</span></span>  
 <span data-ttu-id="fee31-105">전체 데이터베이스 백업을 만들려면 다음 절차를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="fee31-105">To create a full database backup, use the following steps:</span></span>  
  
1.  <span data-ttu-id="fee31-106">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="fee31-106">Connect to [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="fee31-107">**개체 탐색기**에서 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="fee31-107">In the **Object Explorer**, connect to the instance of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
3.  <span data-ttu-id="fee31-108">표준 메뉴 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fee31-108">On the Standard menu bar, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="fee31-109">다음 예를 복사하여 쿼리 창에 붙여 넣고 필요한 대로 수정한 다음 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fee31-109">Copy and paste the following example into the query window, modify as needed, and click **Execute**.</span></span>  
  
    ```  
    BACKUP DATABASE[AdventureWorks2012]   
    TO URL = 'https://mystorageaccount.blob.core.windows.net/privatecontainertest/AdventureWorks2012.bak'   
    /* URL includes the endpoint for the BLOB service, followed by the container name, and the name of the backup file*/   
    WITH CREDENTIAL = 'mycredential';  
    /* name of the credential you created in the previous step */   
    GO  
  
    ```  
  
5.  <span data-ttu-id="fee31-110">개체 탐색기에서 Azure Storage에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="fee31-110">In the object explorer, connect to Azure Storage.</span></span> <span data-ttu-id="fee31-111">컨테이너 및 새로 만든 백업 파일을 찾아봅니다.</span><span class="sxs-lookup"><span data-stu-id="fee31-111">Browse to find the container and the newly created backup files.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="fee31-112">다음 단원</span><span class="sxs-lookup"><span data-stu-id="fee31-112">Next Lesson</span></span>  
 <span data-ttu-id="fee31-113">[4 단원: 전체 데이터베이스 백업에서 복원 수행](../../2014/tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md)</span><span class="sxs-lookup"><span data-stu-id="fee31-113">[Lesson 4: Perform a Restore From a Full Database Backup](../../2014/tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md).</span></span>  
  
  
