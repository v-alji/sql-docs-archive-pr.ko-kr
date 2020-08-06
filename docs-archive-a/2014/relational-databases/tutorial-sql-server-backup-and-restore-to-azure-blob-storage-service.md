---
title: Microsoft Azure Blob Storage 서비스로 SQL Server 백업 및 복원 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4
author: rothja
ms.author: jroth
ms.openlocfilehash: d15200968011cdb314829736512f39730782dc0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729340"
---
# <a name="tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service"></a><span data-ttu-id="672ad-102">자습서: Azure Blob Storage Service로 SQL Server 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="672ad-102">Tutorial: SQL Server Backup and Restore to Azure Blob Storage Service</span></span>
  <span data-ttu-id="672ad-103">Azure Blob Storage 서비스를 사용 하 여 SQL Server 백업 및 복원 자습서를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="672ad-103">Welcome to the Getting Started with SQL Server Backup and Restore with Azure Blob Storage Service tutorial.</span></span> <span data-ttu-id="672ad-104">이 자습서는 Azure Blob Storage 서비스에서 백업을 작성하고 복원하는 방법을 이해하도록 도와줍니다.</span><span class="sxs-lookup"><span data-stu-id="672ad-104">This tutorial helps you understand how to write backups to and restore from the Azure Blob storage service.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="672ad-105">학습 내용</span><span class="sxs-lookup"><span data-stu-id="672ad-105">What You Will Learn</span></span>  
 <span data-ttu-id="672ad-106">이 자습서에서는 Windows 스토리지 계정과 blob 컨테이너를 만들어서 스토리지 계정에 액세스할 자격 증명을 만들고 Blob 서비스에 백업을 작성하며 간단한 복원을 수행할 수 있는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="672ad-106">This tutorial shows you how to create a Windows Storage account, a blob container, creating credentials to access the storage account, writing a backup to the blob service, and performing a simple restore.</span></span> <span data-ttu-id="672ad-107">이 자습서는 다음 네 단원으로 이루어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="672ad-107">This tutorial is divided into four lessons:</span></span>  
  
 [<span data-ttu-id="672ad-108">1 단원: Azure Storage 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="672ad-108">Lesson 1: Create Azure Storage Objects</span></span>](../tutorials/lesson-1-create-windows-azure-storage-objects.md)  
 <span data-ttu-id="672ad-109">이 단원에서는 Azure 스토리지 계정 및 blob 컨테이너를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="672ad-109">In this lesson, you create an Azure storage account and a blob container.</span></span>  
  
 [<span data-ttu-id="672ad-110">2단원: SQL Server 자격 증명 만들기</span><span class="sxs-lookup"><span data-stu-id="672ad-110">Lesson 2: Create a SQL Server Credential</span></span>](../tutorials/lesson-2-create-a-sql-server-credential.md)  
 <span data-ttu-id="672ad-111">이 단원에서는 Azure 스토리지 계정에 액세스하는 데 사용하는 보안 정보를 저장하는 자격 증명을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="672ad-111">In this lesson, you create a Credential to store security information used to access the Azure storage account.</span></span>  
  
 [<span data-ttu-id="672ad-112">3단원: Azure Blob Storage Service로 전체 데이터베이스 백업 작성</span><span class="sxs-lookup"><span data-stu-id="672ad-112">Lesson 3: Write a Full Database Backup to the Azure Blob Storage Service</span></span>](../tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md)  
 <span data-ttu-id="672ad-113">이 단원에서는 Azure Blob Storage 서비스에 AdventureWorks2012 데이터베이스 백업을 작성하는 T-SQL 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="672ad-113">In this lesson, you issue a T-SQL statement to write a backup of the AdventureWorks2012 database to the Azure Blob storage service.</span></span>  
  
 [<span data-ttu-id="672ad-114">4단원: 전체 데이터베이스 백업에서 복원 수행</span><span class="sxs-lookup"><span data-stu-id="672ad-114">Lesson 4: Perform a Restore From a Full Database Backup</span></span>](../tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md)  
 <span data-ttu-id="672ad-115">이 단원에서는 이전 단원에서 만든 데이터베이스 백업에서 복원하는 T-SQL 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="672ad-115">In this lesson, you issue a T-SQL statement to restore from the database backup you created in the previous lesson.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="672ad-116">요구 사항</span><span class="sxs-lookup"><span data-stu-id="672ad-116">Requirements</span></span>  
 <span data-ttu-id="672ad-117">이 자습서를 완료하려면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 백업 및 복원 개념과 T-SQL 구문에 대해 잘 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="672ad-117">To complete this tutorial, you must be familiar with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] backup and restore concepts and T-SQL syntax.</span></span> <span data-ttu-id="672ad-118">이 자습서를 사용하려면 다음과 같은 시스템 요구 사항을 만족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="672ad-118">To use this tutorial, your system must meet the following requirements:</span></span>  
  
-   <span data-ttu-id="672ad-119">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 인스턴스와 AdventureWorks2012 데이터베이스가 설치되었습니다.</span><span class="sxs-lookup"><span data-stu-id="672ad-119">An instance of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], and AdventureWorks2012 database installed.</span></span>  
  
     <span data-ttu-id="672ad-120">SQL Server 인스턴스는 온-프레미스 또는 Azure 가상 머신에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="672ad-120">The SQL Server instance can be on-premises or in an Azure Virtual Machine.</span></span>  
  
     <span data-ttu-id="672ad-121">AdventureWorks2012 대신 사용자 데이터베이스를 사용하고 tsql 구문을 적절하게 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="672ad-121">You can use a user database in place of AdventureWorks2012, and modify the tsql syntax accordingly.</span></span>  
  
-   <span data-ttu-id="672ad-122">BACKUP 또는 RESTORE 명령을 실행하는 데 사용되는 사용자 계정은 **모든 자격 증명 변경** 권한이 있는 **db_backup operator** 데이터베이스 역할에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="672ad-122">The user account that is used to issue BACKUP or RESTORE commands should be in the **db_backup operator** database role with **Alter any credential** permissions.</span></span>  
  
### <a name="additional-reading"></a><span data-ttu-id="672ad-123">추가 자료</span><span class="sxs-lookup"><span data-stu-id="672ad-123">Additional Reading</span></span>  
 <span data-ttu-id="672ad-124">다음은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 백업에 Azure Blob Storage 서비스를 사용할 때 개념 및 최선의 구현 방법을 이해하기 위한 권장 참조 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="672ad-124">Following are some recommended reading to understand the concepts, best practices when using Azure Blob storage service for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] backups.</span></span>  
  
1.  [<span data-ttu-id="672ad-125">Azure Blob Storage Service로 SQL Server 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="672ad-125">SQL Server Backup and Restore with Azure Blob Storage Service</span></span>](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
2.  [<span data-ttu-id="672ad-126">URL에 SQL Server 백업 모범 사례 및 문제 해결</span><span class="sxs-lookup"><span data-stu-id="672ad-126">SQL Server Backup to URL Best Practices and Troubleshooting</span></span>](backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
  
