---
title: '단원 1: Azure Storage 계정 및 컨테이너 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: efdbd930-cde5-41b0-90ad-58a6cc68dddc
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 07167c513d2c6ed3ae0f7b431461ee3915047636
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646763"
---
# <a name="lesson-1-create-azure-storage-account-and-container"></a><span data-ttu-id="e409b-102">1단원: Azure Storage 계정 및 컨테이너 만들기</span><span class="sxs-lookup"><span data-stu-id="e409b-102">Lesson 1: Create Azure Storage Account and Container</span></span>
  <span data-ttu-id="e409b-103">Azure Storage에서 SQL Server 데이터 파일 저장을 시작 하려면 먼저 Azure Storage 계정과 blob 컨테이너 및 공유 액세스 서명을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-103">Before you can start storing SQL Server data files in Azure Storage, you must first create an Azure Storage account and a blob container, and a shared access signature.</span></span> <span data-ttu-id="e409b-104">1 단원에서는 Azure 관리 포털에 로그인 하 여 저장소 계정, blob 컨테이너 및 공유 액세스 서명을 만드는 과정을 단계별로 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-104">Lesson 1 walks you through the steps of logging into the Azure Management Portal, creating a storage account, a blob container, and a shared access signature.</span></span>  
  
 <span data-ttu-id="e409b-105">기본적으로는 스토리지 계정 소유자만 해당 계정 내의 Blob, 테이블 및 큐에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-105">By default, only the owner of the storage account may access blobs, tables, and queues within that account.</span></span> <span data-ttu-id="e409b-106">스토리지 계정 액세스 키를 공유하지 않고 이 새로운 향상된 SQL Server 기능을 사용하여 이러한 리소스에 액세스할 수 있으려면 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-106">To be able to access these resources using this new SQL Server enhancement without sharing the storage account access key, you are required to do these:</span></span>  
  
-   <span data-ttu-id="e409b-107">컨테이너의 사용 권한을 프라이빗으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-107">Set the container's permissions to private.</span></span>  
  
-   <span data-ttu-id="e409b-108">공유 액세스 서명을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-108">Create a shared access signature.</span></span> <span data-ttu-id="e409b-109">이 서명을 사용하면 리소스를 사용할 수 있는 간격과 클라이언트에 부여할 사용 권한을 지정하여 컨테이너, BLOB, 테이블 또는 큐 리소스에 대한 제한된 액세스를 위임할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-109">It enables you to delegate restricted access to a container, blob, table, or queue resource by specifying the interval for which the resources are available and the permissions that a client will have to it.</span></span>  
  
-   <span data-ttu-id="e409b-110">저장된 액세스 정책을 사용하여 컨테이너 또는 해당 BLOB에 대한 공유 액세스 서명을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-110">Use a stored access policy to manage shared access signatures for a container or its blobs.</span></span> <span data-ttu-id="e409b-111">저장된 액세스 정책을 통해 공유 액세스 서명을 추가로 제어할 수 있을 뿐만 아니라 간단하게 취소할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-111">The stored access policy gives you an additional measure of control over your shared access signatures and also provides a straightforward means to revoke them.</span></span>  
  
 <span data-ttu-id="e409b-112">자세한 내용은 [Azure Storage 리소스에 대 한 액세스 관리](https://msdn.microsoft.com/library/windowsazure/ee393343.aspx)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e409b-112">For more information, see [Manage Access to Azure Storage Resources](https://msdn.microsoft.com/library/windowsazure/ee393343.aspx).</span></span>  
  
## <a name="create-storage-account"></a><span data-ttu-id="e409b-113">스토리지 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="e409b-113">Create Storage Account</span></span>  
 <span data-ttu-id="e409b-114">Azure 관리 포털에서 저장소 계정을 만들려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-114">To create a storage account on the Azure Management Portal, follow these steps:</span></span>  
  
1.  <span data-ttu-id="e409b-115">계정을 사용 하 여 [Azure 관리 포털](https://manage.windowsazure.com) 에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-115">Log in to the [Azure Management Portal](https://manage.windowsazure.com) using your account.</span></span> <span data-ttu-id="e409b-116">Azure 계정이 없는 경우 [Azure 평가판](https://www.windowsazure.com/pricing/free-trial/)을 방문하십시오.</span><span class="sxs-lookup"><span data-stu-id="e409b-116">If you do not have an Azure account, visit [Azure free trial](https://www.windowsazure.com/pricing/free-trial/).</span></span>  
  
     <span data-ttu-id="e409b-117">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-1.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="e409b-117">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-1.gif "SQL 14 CTP2")</span></span>  
  
2.  <span data-ttu-id="e409b-118">단계별 지침을 사용하여 [스토리지 계정을 만듭니다](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).</span><span class="sxs-lookup"><span data-stu-id="e409b-118">Use the step by step instructions to [create a storage account](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).</span></span> <span data-ttu-id="e409b-119">Azure의 SQL Server 데이터 파일 기능에 사용할 저장소 계정을 만드는 경우 지역에서 복제를 선택 취소 하거나 사용 하지 않도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-119">Note that when creating a storage account to be used for the SQL Server Data Files in Azure feature, you should unselect or disable the geo-replication.</span></span> <span data-ttu-id="e409b-120">이는 지리적 복제에 참여하는 여러 BLOB에 대해 쓰기 순서가 보장되지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-120">This is because write order is not guaranteed for multiple blobs participating in geo-replication.</span></span> <span data-ttu-id="e409b-121">스토리지 계정이 지리적으로 복제되고 복구가 필요한 경우 손상이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-121">If a storage account is geo-replicated and recovery is required, a corruption occurs.</span></span>  
  
     <span data-ttu-id="e409b-122">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-2.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="e409b-122">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-2.gif "SQL 14 CTP2")</span></span>  
  
## <a name="create-a-blob-container"></a><span data-ttu-id="e409b-123">Blob 컨테이너 만들기</span><span class="sxs-lookup"><span data-stu-id="e409b-123">Create a Blob container</span></span>  
 <span data-ttu-id="e409b-124">Azure에서 컨테이너는 blob 집합의 그룹화를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-124">In Azure, a container provides a grouping of a set of blobs.</span></span> <span data-ttu-id="e409b-125">모든 Blob은 컨테이너에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-125">All blobs must be in a container.</span></span> <span data-ttu-id="e409b-126">스토리지 계정은 개수에 제한 없이 컨테이너를 포함할 수 있지만 적어도 하나는 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-126">A storage account can contain an unlimited number of containers, but must have at least one container.</span></span> <span data-ttu-id="e409b-127">한 컨테이너에 저장될 수 있는 Blob 수에도 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-127">A container can store an unlimited number of blobs.</span></span> <span data-ttu-id="e409b-128">저장소 크기 제한에 대 한 최신 정보는 [.net에서 Azure Blob Storage 서비스를 사용 하는 방법](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e409b-128">For most up-to-date information on storage size limits, see [How to use the Azure Blob Storage Service in .NET](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/).</span></span>  
  
 <span data-ttu-id="e409b-129">Azure에서 컨테이너를 만들려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-129">To create a container in Azure, follow these steps:</span></span>  
  
1.  <span data-ttu-id="e409b-130">[Azure 관리 포털](https://manage.windowsazure.com)에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-130">Log in to the [Azure Management Portal](https://manage.windowsazure.com).</span></span>  
  
2.  <span data-ttu-id="e409b-131">저장소 계정을 선택 하 고 **컨테이너** 탭을 클릭 한 다음 화면 맨 아래에서 **컨테이너 추가** 를 클릭 하면 새 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-131">Select the storage account, click the **CONTAINERS** tab and click **ADD CONTAINER** at the bottom of the screen, which opens a new dialog box.</span></span>  
  
3.  <span data-ttu-id="e409b-132">컨테이너 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-132">Enter a name for the container.</span></span>  
  
4.  <span data-ttu-id="e409b-133">**액세스 형식**에 대해 **개인** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-133">Select **Private** for **Access Type**.</span></span> <span data-ttu-id="e409b-134">액세스 권한을 개인으로 설정 하는 경우 Azure 계정 소유자만 컨테이너 및 blob 데이터를 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-134">When you set the access to private, the container and blob data can be read by the Azure account owner only.</span></span>  
  
     <span data-ttu-id="e409b-135">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-4.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="e409b-135">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-4.gif "SQL 14 CTP2")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e409b-136">프로그래밍 방식으로 컨테이너를 만들려면 REST API를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e409b-136">To create a container programmatically, you can also use REST APIs.</span></span> <span data-ttu-id="e409b-137">자세한 내용은 [컨테이너 만들기](https://msdn.microsoft.com/library/windowsazure/dd179468.aspx) 및 [Azure Storage 서비스 REST API 참조](https://msdn.microsoft.com/library/windowsazure/dd179355.aspx)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e409b-137">For more information, see [Create Container](https://msdn.microsoft.com/library/windowsazure/dd179468.aspx) and also [Azure Storage Services REST API Reference](https://msdn.microsoft.com/library/windowsazure/dd179355.aspx).</span></span>  
  
 <span data-ttu-id="e409b-138">**다음 단원:**</span><span class="sxs-lookup"><span data-stu-id="e409b-138">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="e409b-139">2 단원. 컨테이너에서 정책을 만들고 SAS&#41; 키 &#40;공유 액세스 서명 생성</span><span class="sxs-lookup"><span data-stu-id="e409b-139">Lesson 2. Create a policy on container and generate a Shared Access Signature &#40;SAS&#41; key</span></span>](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md)  
  
