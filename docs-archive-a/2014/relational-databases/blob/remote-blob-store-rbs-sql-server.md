---
title: RBS(원격 Blob 저장소)(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Remote Blob Store (RBS) [SQL Server]
- RBS (Remote Blob Store) [SQL Server]
ms.assetid: 31c947cf-53e9-4ff4-939b-4c1d034ea5b1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8f3425474ec3b9013355536424ffcf55d9426b9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728368"
---
# <a name="remote-blob-store-rbs-sql-server"></a><span data-ttu-id="63821-102">RBS(Remote Blob Store)(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="63821-102">Remote Blob Store (RBS) (SQL Server)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="63821-103">RBS(Remote BLOB Store)는 데이터베이스 관리자가 기본 데이터베이스 서버에 직접 저장하지 않고 상용 스토리지 솔루션에 BLOB(Binary Large Object)를 저장할 수 있도록 해 주는 선택적 추가 기능 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="63821-103">Remote BLOB Store (RBS) is an optional add-on component that lets database administrators store binary large objects in commodity storage solutions instead of directly on the main database server.</span></span>  
  
 <span data-ttu-id="63821-104">RBS는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 설치 미디어에 포함되어 있지만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 프로그램에 의해 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63821-104">RBS is included on the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installation media, but is not installed by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup program.</span></span>  
  
 <span data-ttu-id="63821-105">RBS에 대한 자세한 내용은 이 항목에서 [RBS 리소스](#rbsresources) 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63821-105">For more information about RBS, see [RBS Resources](#rbsresources) in this topic.</span></span>  
  
## <a name="benefits-of-rbs"></a><span data-ttu-id="63821-106">RBS의 이점</span><span class="sxs-lookup"><span data-stu-id="63821-106">Benefits of RBS</span></span>  
 <span data-ttu-id="63821-107">RBS는 다음과 같은 이점을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="63821-107">RBS provides the following benefits:</span></span>  
  
### <a name="optimized-database-storage-and-performance"></a><span data-ttu-id="63821-108">최적화된 데이터베이스 스토리지 및 성능</span><span class="sxs-lookup"><span data-stu-id="63821-108">Optimized database storage and performance</span></span>  
 <span data-ttu-id="63821-109">데이터베이스에 BLOB을 저장하면 많은 양의 파일 공간과 값비싼 서버 리소스를 소비할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63821-109">Storing BLOBs in the database can consume large amounts of file space and expensive server resources.</span></span> <span data-ttu-id="63821-110">RBS는 BLOB을 사용자가 선택하는 전용 스토리지 솔루션에 효율적으로 전송하고 데이터베이스에 해당 BLOB에 대한 참조를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="63821-110">RBS efficiently transfers the BLOBs to a dedicated storage solution of your choosing, and stores references to them in the database.</span></span> <span data-ttu-id="63821-111">이렇게 하면 구조화된 데이터용 서버 스토리지와 데이터베이스 작업용 서버 리소스가 확보됩니다.</span><span class="sxs-lookup"><span data-stu-id="63821-111">This frees server storage for structured data, and frees server resources for database operations.</span></span>  
  
### <a name="efficient-management-of-blobs"></a><span data-ttu-id="63821-112">BLOB의 효율적 관리</span><span class="sxs-lookup"><span data-stu-id="63821-112">Efficient management of BLOBs</span></span>  
 <span data-ttu-id="63821-113">여러 RBS 기능이 저장된 BLOB의 간편한 관리를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="63821-113">Several RBS features support the convenient management of stored BLOBs:</span></span>  
  
-   <span data-ttu-id="63821-114">BLOB은 ACID(원자성, 일관성, 격리성 및 내구성) 트랜잭션을 사용하여 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="63821-114">BLOBS are managed with ACID (atomic consistency isolation durable) transactions.</span></span>  
  
-   <span data-ttu-id="63821-115">BLOB은 컬렉션으로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63821-115">BLOBs are organized into collections.</span></span>  
  
-   <span data-ttu-id="63821-116">가비지 수집, 일관성 검사 및 기타 유지 관리 기능이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="63821-116">Garbage collection, consistency checking, and other maintenance functions are included.</span></span>  
  
### <a name="standardized-api"></a><span data-ttu-id="63821-117">표준화된 API</span><span class="sxs-lookup"><span data-stu-id="63821-117">Standardized API</span></span>  
 <span data-ttu-id="63821-118">RBS는 애플리케이션의 BLOB 저장소 액세스 및 수정을 위한 표준화된 프로그래밍 모델을 제공하는 API 집합을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="63821-118">RBS defines a set of APIs that provide a standardized programming model for applications to access and modify any BLOB store.</span></span> <span data-ttu-id="63821-119">각 BLOB 저장소에서는 자체 공급자 라이브러리를 지정할 수 있는데, 이 라이브러리는 RBS 클라이언트 라이브러리에 연결되어 BLOB을 저장하고 액세스하는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="63821-119">Each BLOB store can specify its own provider library, which plugs into the RBS client library and specifies how BLOBs are stored and accessed.</span></span>  
  
 <span data-ttu-id="63821-120">많은 타사 스토리지 솔루션 공급업체가 이러한 표준 API를 준수하고 다양한 스토리지 플랫폼에서 BLOB 스토리지를 지원하는 RBS 공급자를 개발했습니다.</span><span class="sxs-lookup"><span data-stu-id="63821-120">A number of third-party storage solution vendors have developed RBS providers that conform to these standard APIs and support BLOB storage on various storage platforms.</span></span>  
  
## <a name="rbs-requirements"></a><span data-ttu-id="63821-121">RBS 요구 사항</span><span class="sxs-lookup"><span data-stu-id="63821-121">RBS Requirements</span></span>  
 <span data-ttu-id="63821-122">RBS를 사용하려면 BLOB 메타데이터가 저장된 기본 데이터베이스 서버용 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="63821-122">RBS requires [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise for the main database server in which the BLOB metadata is stored.</span></span> <span data-ttu-id="63821-123">그러나 제공된 FILESTREAM 공급자를 사용하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard에 BLOB 자체를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63821-123">However, if you use the supplied FILESTREAM provider, you can store the BLOBs themselves on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard.</span></span>  
  
 <span data-ttu-id="63821-124">RBS에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 인스턴스에 RBS가 BLOB을 저장할 수 있는 FILESTREAM 공급자가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63821-124">RBS includes a FILESTREAM provider that lets you use RBS to store BLOBs on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="63821-125">다른 스토리지 솔루션에 RBS를 사용하여 BLOB을 저장하려면 해당 스토리지 솔루션을 위해 개발된 타사 RBS 공급자를 사용하거나 RBS API를 사용하여 사용자 지정 RBS 공급자를 개발해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63821-125">If you want use RBS to store BLOBs in a different storage solution, you have to use a third party RBS provider developed for that storage solution, or develop a custom RBS provider using the RBS API.</span></span> <span data-ttu-id="63821-126">NTFS 파일 시스템에 BLOB을 저장하는 예제 공급자는 [Codeplex](https://go.microsoft.com/fwlink/?LinkId=210190)에서 학습 리소스로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63821-126">A sample provider that stores BLOBs in the NTFS file system is available as a learning resource on [Codeplex](https://go.microsoft.com/fwlink/?LinkId=210190).</span></span>  
  
## <a name="rbs-security"></a><span data-ttu-id="63821-127">RBS 보안</span><span class="sxs-lookup"><span data-stu-id="63821-127">RBS Security</span></span>  
 <span data-ttu-id="63821-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 외부에서 사용자 지정 공급자를 사용하여 BLOB를 저장하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 보안 시스템을 우회하는 다른 프로세스에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63821-128">When you use a custom provider to store BLOBs outside of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], they may be available to other processes that bypass the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security system.</span></span> <span data-ttu-id="63821-129">사용자 지정 공급자가 사용하는 스토리지 미디어에 적합한 권한과 암호화 옵션을 사용하여 저장된 BLOB를 보호해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63821-129">Make sure that you protect the stored BLOBs with permissions and encryption options that are appropriate to the storage medium used by the custom provider.</span></span>  
  
##  <a name="rbs-resources"></a><a name="rbsresources"></a><span data-ttu-id="63821-130">RBS 리소스</span><span class="sxs-lookup"><span data-stu-id="63821-130">RBS Resources</span></span>  
 <span data-ttu-id="63821-131">**RBS 설명서**</span><span class="sxs-lookup"><span data-stu-id="63821-131">**RBS documentation**</span></span>  
 <span data-ttu-id="63821-132">RBS 설명서는 Windows 설치 관리자 패키지에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63821-132">The RBS documentation is included in the Windows installer package.</span></span> <span data-ttu-id="63821-133">RBS를 설치하지 않고 RBS 설명서를 검토하고 싶으면 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] MSDN Library에서 온라인으로 [설명서의](https://go.microsoft.com/fwlink/?LinkId=210192)버전을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63821-133">If you want to review the RBS documentation without installing RBS, you can view the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] version of the documentation [online in the MSDN Library](https://go.microsoft.com/fwlink/?LinkId=210192).</span></span>  
  
 <span data-ttu-id="63821-134">**RBS 백서**</span><span class="sxs-lookup"><span data-stu-id="63821-134">**RBS white paper**</span></span>  
 <span data-ttu-id="63821-135">Microsoft Word 문서로 다운로드할 수 있는 백서 "[Remote BLOB Storage](https://go.microsoft.com/fwlink/?LinkId=210422)"는 RBS 설치와 구성에 대한 자세한 내용을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="63821-135">The white paper "[Remote BLOB Storage](https://go.microsoft.com/fwlink/?LinkId=210422)", which is available for download as a Microsoft Word document, provides detailed information about installing and configuring RBS.</span></span>  
  
 <span data-ttu-id="63821-136">**RBS 예제**</span><span class="sxs-lookup"><span data-stu-id="63821-136">**RBS samples**</span></span>  
 <span data-ttu-id="63821-137">[Codeplex](https://go.microsoft.com/fwlink/?LinkId=210190) 에서 제공하는 RBS 샘플은 RBS 애플리케이션을 개발하는 방법과 사용자 지정 RBS 공급자를 설치하고 사용자 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="63821-137">The RBS samples available on [Codeplex](https://go.microsoft.com/fwlink/?LinkId=210190) demonstrate how to develop an RBS application, and how to develop and install a custom RBS provider.</span></span>  
  
 <span data-ttu-id="63821-138">**RBS 블로그**</span><span class="sxs-lookup"><span data-stu-id="63821-138">**RBS blog**</span></span>  
 <span data-ttu-id="63821-139">[RBS 블로그](https://go.microsoft.com/fwlink/?LinkId=210315) 는 RBS를 이해하고 배포하고 유지하는 데 도움이 되는 추가 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="63821-139">The [RBS blog](https://go.microsoft.com/fwlink/?LinkId=210315) provides additional information to help you understand, deploy, and maintain RBS.</span></span>  
  
  
