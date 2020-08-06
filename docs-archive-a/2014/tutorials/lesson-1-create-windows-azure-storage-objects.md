---
title: '1 단원: Azure Storage 개체 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 74edd1fd-ab00-46f7-9e29-7ba3f1a446c5
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: d46c6d22ffd92dbf8035bff140960af8ef56122d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647393"
---
# <a name="lesson-1-create-azure-storage-objects"></a><span data-ttu-id="03a10-102">1단원: Azure Storage 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="03a10-102">Lesson 1: Create Azure Storage Objects</span></span>
  <span data-ttu-id="03a10-103">클라우드 스토리지에 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 백업을 만들려면 먼저 스토리지 계정을 만든 다음 blob 컨테이너를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03a10-103">Before you can create [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] backups on cloud storage, you must first create a storage account, and then a blob container.</span></span> <span data-ttu-id="03a10-104">1 단원에서는 Azure 관리 포털에 로그인 하 여 저장소 계정 및 blob 컨테이너를 만드는 단계를 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="03a10-104">Lesson 1 walks you through the steps of Logging into the Azure Management Portal, creating a storage account and a blob container.</span></span>  
  
## <a name="create-a-storage-account"></a><span data-ttu-id="03a10-105">스토리지 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="03a10-105">Create a storage Account</span></span>  
 <span data-ttu-id="03a10-106">Azure 관리 포털에서 저장소 계정을 만들려면 다음 단계를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="03a10-106">To create a storage account from the Azure Management Portal, use the following steps:</span></span>  
  
1.  <span data-ttu-id="03a10-107">자신의 계정을 사용하여 Azure 관리 포털에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="03a10-107">Log in to the Azure Management Portal using your account.</span></span> <span data-ttu-id="03a10-108">Azure 계정이 없는 경우 [azure 3 개월 무료 평가판을 방문](https://go.microsoft.com/fwlink/?LinkId=271927)하세요.</span><span class="sxs-lookup"><span data-stu-id="03a10-108">If you do not have an Azure account, [visit Azure 3-Month free trial](https://go.microsoft.com/fwlink/?LinkId=271927).</span></span>  
  
     <span data-ttu-id="03a10-109">![Azure 로그인 화면](../../2014/tutorials/media/windowazurelogin-backuptocloud.gif "Azure 로그인 화면")</span><span class="sxs-lookup"><span data-stu-id="03a10-109">![Azure Login Screen](../../2014/tutorials/media/windowazurelogin-backuptocloud.gif "Azure Login Screen")</span></span>  
  
2.  <span data-ttu-id="03a10-110">[여기](https://go.microsoft.com/fwlink/?LinkId=271926)에서 자세한 단계별 지침을 사용하여 스토리지 계정을 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="03a10-110">Use the step by step instructions detailed [here](https://go.microsoft.com/fwlink/?LinkId=271926), to create a storage account.</span></span>  
  
3.  <span data-ttu-id="03a10-111">이전 단계에서 만든 스토리지 계정으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="03a10-111">Browse to the storage account you created in previous step.</span></span> <span data-ttu-id="03a10-112">웹 페이지의 아래쪽 가운데에서 **키 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="03a10-112">From the bottom center of the web page, click **MANAGE KEYS**.</span></span> <span data-ttu-id="03a10-113">계정 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="03a10-113">The account information is displayed.</span></span> <span data-ttu-id="03a10-114">스토리지 계정 이름과 액세스 키를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="03a10-114">Copy the storage account name, and the Access Keys.</span></span> <span data-ttu-id="03a10-115">이 정보는 SQL 저장된 자격 증명을 만드는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="03a10-115">This information is required to create SQL Stored Credentials.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]<span data-ttu-id="03a10-116">에서는 이 정보를 사용하여 스토리지 계정에 액세스하여 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03a10-116">uses this information to access the storage account and create backups.</span></span>  
  
     <span data-ttu-id="03a10-117">![Azure Storage 계정 키 스크린샷](../../2014/tutorials/media/manageaccesskeys-backuptocloud.gif "Azure Storage 계정 키 스크린샷")</span><span class="sxs-lookup"><span data-stu-id="03a10-117">![Screen shot of Azure Storage Account Keys](../../2014/tutorials/media/manageaccesskeys-backuptocloud.gif "Screen shot of Azure Storage Account Keys")</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="03a10-118">또한 REST API를 사용하여 프로그래밍 방식으로 스토리지 계정을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03a10-118">You can also create a storage account programmatically using REST APIs.</span></span> <span data-ttu-id="03a10-119">자세한 내용은 [스토리지 계정 만들기](https://go.microsoft.com/fwlink/?LinkId=271928)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="03a10-119">For more information, see [Create Storage Account](https://go.microsoft.com/fwlink/?LinkId=271928).</span></span>  
  
### <a name="create-a-blob-container"></a><span data-ttu-id="03a10-120">Blob 컨테이너 만들기</span><span class="sxs-lookup"><span data-stu-id="03a10-120">Create a Blob Container</span></span>  
 <span data-ttu-id="03a10-121">컨테이너는 Blob 집합의 그룹화를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="03a10-121">A container provides a grouping of a set of blobs.</span></span> <span data-ttu-id="03a10-122">모든 Blob은 컨테이너에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03a10-122">All blobs must be in a container.</span></span> <span data-ttu-id="03a10-123">계정에는 개수에 제한 없이 컨테이너를 포함할 수 있지만 적어도 하나 이상 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03a10-123">An account can contain an unlimited number of containers, but must have at least one container.</span></span> <span data-ttu-id="03a10-124">한 컨테이너에 저장될 수 있는 Blob 수에도 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="03a10-124">A container can store an unlimited number of blobs.</span></span>  
  
 <span data-ttu-id="03a10-125">컨테이너를 만들려면 다음 절차를 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="03a10-125">To create a Container, use the following steps:</span></span>  
  
1.  <span data-ttu-id="03a10-126">스토리지 계정을 선택하고 **컨테이너** 탭을 클릭한 다음 화면 맨 아래에서 **컨테이너 추가** 를 클릭하면 새 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="03a10-126">Select the storage account, click the **CONTAINERS** tab and click **ADD CONTAINER** at the bottom of the screen which opens a new dialog box.</span></span>  
  
     <span data-ttu-id="03a10-127">![관리 포털에서 컨테이너 만들기](../../2014/tutorials/media/backuptocloud.gif "관리 포털에서 컨테이너 만들기")</span><span class="sxs-lookup"><span data-stu-id="03a10-127">![Creating a Container in the Management Portal](../../2014/tutorials/media/backuptocloud.gif "Creating a Container in the Management Portal")</span></span>  
  
2.  <span data-ttu-id="03a10-128">컨테이너 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="03a10-128">Enter the name for the container.</span></span> <span data-ttu-id="03a10-129">지정한 컨테이너 이름을 적어 둡니다.</span><span class="sxs-lookup"><span data-stu-id="03a10-129">Make a note of the container name you specified.</span></span> <span data-ttu-id="03a10-130">이 정보는 3, 4단원에서 T-SQL 문의 URL(백업 파일 경로)에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="03a10-130">This information is used in the URL (path to backup file) in the T-SQL statements in lesson 3 and 4.</span></span>  
  
3.  <span data-ttu-id="03a10-131">**액세스 형식**에서 프라이빗을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="03a10-131">Select Private for **Access Type**.</span></span> <span data-ttu-id="03a10-132">백업 파일을 보호하기 위한 프라이빗 컨테이너를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="03a10-132">We recommend creating private containers for securing your backup files.</span></span>  
  
     <span data-ttu-id="03a10-133">![새 BLOB 컨테이너 만들기](../../2014/tutorials/media/backuptocloud-newblobcontainer.gif "새 BLOB 컨테이너 만들기")</span><span class="sxs-lookup"><span data-stu-id="03a10-133">![Creating a new blob container](../../2014/tutorials/media/backuptocloud-newblobcontainer.gif "Creating a new blob container")</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="03a10-134">공용 컨테이너를 만들도록 선택한 경우에도 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 백업 및 복원에 스토리지 계정 인증이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="03a10-134">Authentication to the storage account is required for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] backup and restore even if you choose to create a public container.</span></span>  
    >   
    >  <span data-ttu-id="03a10-135">또한 REST API를 사용하여 프로그래밍 방식으로 컨테이너를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03a10-135">You can also create a container programmatically using REST APIs.</span></span> <span data-ttu-id="03a10-136">자세한 내용은 [컨테이너 만들기](https://go.microsoft.com/fwlink/?LinkId=271946)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="03a10-136">For more information, see [Create Container](https://go.microsoft.com/fwlink/?LinkId=271946).</span></span>  
  
### <a name="next-lesson"></a><span data-ttu-id="03a10-137">다음 단원</span><span class="sxs-lookup"><span data-stu-id="03a10-137">Next Lesson</span></span>  
 <span data-ttu-id="03a10-138">[2 단원: SQL Server 자격 증명 만들기](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md)</span><span class="sxs-lookup"><span data-stu-id="03a10-138">[Lesson 2: Create a SQL Server Credential](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md).</span></span>  
  
  
