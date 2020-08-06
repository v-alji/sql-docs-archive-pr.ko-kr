---
title: '자습서: Azure Storage 서비스의 SQL Server 데이터 파일 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: e69be67d-da1c-41ae-8c9a-6b12c8c2fb61
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 21a0fc11706a0c5ee35cf71e1af69f2927adc9db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660971"
---
# <a name="tutorial-sql-server-data-files-in-azure-storage-service"></a><span data-ttu-id="3e876-102">자습서: Azure Storage의 SQL Server 데이터 파일 서비스</span><span class="sxs-lookup"><span data-stu-id="3e876-102">Tutorial: SQL Server Data Files in Azure Storage service</span></span>
  <span data-ttu-id="3e876-103">Azure Storage Service의 SQL Server 데이터 파일 자습서를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e876-103">Welcome to the  SQL Server Data Files in Azure Storage Service tutorial.</span></span> <span data-ttu-id="3e876-104">이 자습서는 Azure Blob Storage 서비스에서 SQL Server 데이터 파일을 직접 저장하는 방법을 이해하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e876-104">This tutorial helps you understand how to store SQL Server data files in the Azure Blob storage service directly.</span></span>  
  
 <span data-ttu-id="3e876-105">Azure Blob storage 서비스에 대 한 SQL Server 통합 지원은 SQL Server 2014 향상 된 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="3e876-105">SQL Server integration support for the Azure Blob storage service is a SQL Server 2014 enhancement.</span></span> <span data-ttu-id="3e876-106">이 기능을 사용 하는 기능 및 이점에 대 한 개요는 [Azure의 SQL Server 데이터 파일](databases/sql-server-data-files-in-microsoft-azure.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3e876-106">For an overview of the functionality and benefits of using this functionality, see [SQL Server Data Files in Azure](databases/sql-server-data-files-in-microsoft-azure.md).</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="3e876-107">알아볼 내용</span><span class="sxs-lookup"><span data-stu-id="3e876-107">What you will learn</span></span>  
 <span data-ttu-id="3e876-108">이 자습서에서는 여러 단원에서 Azure Storage 서비스에 SQL Server 데이터 파일을 저장 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3e876-108">This tutorial shows you how to store SQL Server Data Files in Azure Storage service in multiple lessons.</span></span> <span data-ttu-id="3e876-109">각 단원은 특정 태스크에 초점을 맞추고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e876-109">Each lesson is focused on a specific task.</span></span> <span data-ttu-id="3e876-110">먼저 Azure에서 저장소 계정 및 컨테이너를 만드는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="3e876-110">First, you will learn how to create a storage account and a container in Azure.</span></span> <span data-ttu-id="3e876-111">그런 다음 SQL Server Azure Storage와 통합할 수 있도록 SQL Server 자격 증명을 만드는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="3e876-111">Then, you will learn how to create a SQL Server credential to be able to integrate SQL Server with Azure Storage.</span></span> <span data-ttu-id="3e876-112">그런 다음 Azure Storage에서 직접 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3e876-112">Then, you will create a database in Azure Storage directly.</span></span> <span data-ttu-id="3e876-113">또한 이 자습서에서는 암호화, 마이그레이션, 백업 및 복원 시나리오를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3e876-113">In addition, the tutorial will demonstrate encryption, migration, and backup and restore scenarios.</span></span>  
  
 <span data-ttu-id="3e876-114">이 자습서는 다음 9개의 단원으로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e876-114">This tutorial is divided into nine lessons:</span></span>  
  
 <span data-ttu-id="3e876-115">**[1단원: Azure Storage 계정 및 컨테이너 만들기](../tutorials/lesson-1-create-windows-azure-storage-account-and-container.md)**</span><span class="sxs-lookup"><span data-stu-id="3e876-115">**[Lesson 1: Create Azure Storage Account and Container](../tutorials/lesson-1-create-windows-azure-storage-account-and-container.md)**</span></span>  
 <span data-ttu-id="3e876-116">이 단원에서는 Azure Storage 계정과 컨테이너를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3e876-116">In this lesson, you create an Azure Storage account and a container.</span></span>  
  
 <span data-ttu-id="3e876-117">**[2 단원. 컨테이너에서 정책을 만들고 SAS&#41; 키 &#40;공유 액세스 서명 생성](lesson-1-create-stored-access-policy-and-shared-access-signature.md)**</span><span class="sxs-lookup"><span data-stu-id="3e876-117">**[Lesson 2. Create a policy on container and generate a Shared Access Signature &#40;SAS&#41; key](lesson-1-create-stored-access-policy-and-shared-access-signature.md)**</span></span>  
 <span data-ttu-id="3e876-118">이 단원에서는 BLOB 컨테이너에서 정책을 만들고 공유 액세스 서명을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="3e876-118">In this lesson, you create a policy on the Blob container and also generate a shared access signature.</span></span>  
  
 <span data-ttu-id="3e876-119">**[3단원: SQL Server 자격 증명 만들기](lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)**</span><span class="sxs-lookup"><span data-stu-id="3e876-119">**[Lesson 3: Create a SQL Server Credential](lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)**</span></span>  
 <span data-ttu-id="3e876-120">이 단원에서는 Azure 스토리지 계정에 액세스하는 데 사용하는 보안 정보를 저장하는 자격 증명을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e876-120">In this lesson, you create a Credential to store security information used to access the Azure storage account.</span></span>  
  
 <span data-ttu-id="3e876-121">**[4단원: Azure Storage에서 데이터베이스 만들기](../relational-databases/lesson-3-database-backup-to-url.md)**</span><span class="sxs-lookup"><span data-stu-id="3e876-121">**[Lesson 4: Create a database in Azure Storage](../relational-databases/lesson-3-database-backup-to-url.md)**</span></span>  
 <span data-ttu-id="3e876-122">이 단원에서는 CREATE Database FILENAME 옵션을 사용 하 여 Azure Storage에서 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3e876-122">In this lesson, you create a database in Azure Storage using CREATE Database FILENAME option.</span></span>  
  
 <span data-ttu-id="3e876-123">**[5 단원. TDE를 사용 하 여 데이터베이스를 암호화 &#40;선택&#41;](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)**</span><span class="sxs-lookup"><span data-stu-id="3e876-123">**[Lesson 5. &#40;Optional&#41; Encrypt your database using TDE](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)**</span></span>  
 <span data-ttu-id="3e876-124">이 단원에서는 TDE(투명한 데이터 암호화)와 서버 인증서를 사용하여 데이터베이스를 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="3e876-124">In this lesson, you encrypt your database by using a transparent data encryption (TDE) and a server certificate.</span></span>  
  
 <span data-ttu-id="3e876-125">**[6단원: 온-프레미스의 원본 머신에서 Azure의 대상 머신으로 데이터베이스 마이그레이션](lesson-5-backup-database-using-file-snapshot-backup.md)**</span><span class="sxs-lookup"><span data-stu-id="3e876-125">**[Lesson 6: Migrate a database from a source machine on-premises to a destination machine in Azure](lesson-5-backup-database-using-file-snapshot-backup.md)**</span></span>  
 <span data-ttu-id="3e876-126">이 단원에서는 CREATE DATABASE FOR ATTACH 옵션을 사용 하 여 온-프레미스에서 Azure의 가상 머신으로 데이터베이스를 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="3e876-126">In this lesson, you migrate a database from on-premises to a virtual machine in Azure using CREATE DATABASE FOR ATTACH option.</span></span>  
  
 <span data-ttu-id="3e876-127">**[7단원: Azure Storage에 데이터 파일 이동](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)**</span><span class="sxs-lookup"><span data-stu-id="3e876-127">**[Lesson 7: Move your data files to Azure Storage](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)**</span></span>  
 <span data-ttu-id="3e876-128">이 단원에서는 ALTER DATABASE 문을 사용 하 여 데이터 파일을 Azure Storage로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e876-128">In this lesson, you move your data files to Azure Storage using ALTER DATABASE statement.</span></span>  
  
 <span data-ttu-id="3e876-129">**[단원 8. Azure Storage로 데이터베이스 복원](../relational-databases/lesson-7-restore-a-database-to-a-point-in-time.md)**</span><span class="sxs-lookup"><span data-stu-id="3e876-129">**[Lesson 8. Restore a database to Azure Storage](../relational-databases/lesson-7-restore-a-database-to-a-point-in-time.md)**</span></span>  
 <span data-ttu-id="3e876-130">이 단원에서는 RESTORE Database MOVE 옵션을 사용 하 여 Azure Storage 데이터베이스로 데이터베이스를 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e876-130">In this lesson, you restore a database to Azure Storage using RESTORE Database MOVE option.</span></span>  
  
 <span data-ttu-id="3e876-131">**[단원 9. Azure Storage에서 데이터베이스 복원](lesson-8-restore-as-new-database-from-log-backup.md)**</span><span class="sxs-lookup"><span data-stu-id="3e876-131">**[Lesson 9. Restore a database from Azure Storage](lesson-8-restore-as-new-database-from-log-backup.md)**</span></span>  
 <span data-ttu-id="3e876-132">이 단원에서는 RESTORE Database MOVE 옵션을 사용 하 여 Azure Storage에서 데이터베이스를 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e876-132">In this lesson, you restore a database from Azure Storage using RESTORE Database MOVE option.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e876-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3e876-133">See Also</span></span>  
 [<span data-ttu-id="3e876-134">Azure에서 데이터 파일 SQL Server</span><span class="sxs-lookup"><span data-stu-id="3e876-134">SQL Server Data Files in Azure</span></span>](databases/sql-server-data-files-in-microsoft-azure.md)  
  
  
