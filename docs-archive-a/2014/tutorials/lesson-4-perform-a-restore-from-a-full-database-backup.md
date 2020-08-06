---
title: '4 단원: 전체 데이터베이스 백업에서 복원 수행 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 580f76e6-9802-4abc-9043-db6de592c733
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 9906ea14c2f76a49644a8f76fbd894adf8b9d500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649868"
---
# <a name="lesson-4-perform-a-restore-from-a-full-database-backup"></a><span data-ttu-id="3b6fa-102">4단원: 전체 데이터베이스 백업에서 복원 수행</span><span class="sxs-lookup"><span data-stu-id="3b6fa-102">Lesson 4: Perform a Restore From a Full Database Backup</span></span>
  <span data-ttu-id="3b6fa-103">이 단원에서는 이전 단원에서 만든 전체 데이터베이스 백업에서 복원을 수행하는 tsql 문을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3b6fa-103">This lesson demonstrates the use of a tsql statement to perform a restore from a full database backup created in the previous lesson.</span></span>  
  
## <a name="perform-a-restore-of-a-database-backup"></a><span data-ttu-id="3b6fa-104">데이터베이스 백업에서 복원 수행</span><span class="sxs-lookup"><span data-stu-id="3b6fa-104">Perform a Restore of a Database Backup</span></span>  
 <span data-ttu-id="3b6fa-105">전체 데이터베이스 백업을 복원하려면 다음 절차를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="3b6fa-105">To restore a full database backup, use the following steps:</span></span>  
  
1.  <span data-ttu-id="3b6fa-106">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3b6fa-106">Connect to [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="3b6fa-107">**개체 탐색기**에서 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3b6fa-107">In the **Object Explorer**, connect to the instance of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
3.  <span data-ttu-id="3b6fa-108">표준 메뉴 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3b6fa-108">On the Standard menu bar, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="3b6fa-109">다음 예를 복사하여 쿼리 창에 붙여 넣고 필요한 대로 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="3b6fa-109">Copy and paste the following example into the query window, modify as needed.</span></span>  
  
    ```  
    RESTORE DATABASE AdventureWorks2012   
    FROM URL = 'https://mystorageaccount.blob.core.windows.net/privatecontainertest/AdventureWorks2012.bak'   
    WITH CREDENTIAL = 'mycredential';  
    , STATS = 5 - use this to see monitor the progress  
    GO  
  
    ```  
  
5.  <span data-ttu-id="3b6fa-110">T-sql 문을 확인 하 고 **실행** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b6fa-110">Verify the T-SQL statement and click **Execute**</span></span>  
  
### <a name="return-to-tutorials-portal"></a><span data-ttu-id="3b6fa-111">자습서 포털로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="3b6fa-111">Return to Tutorials Portal</span></span>  
 <span data-ttu-id="3b6fa-112">[자습서: 백업 및 Azure Blob Storage 서비스에 SQL Server 복원](../relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)</span><span class="sxs-lookup"><span data-stu-id="3b6fa-112">[Tutorial: SQL Server Backup and Restore to Azure Blob Storage Service](../relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md).</span></span>  
  
  
