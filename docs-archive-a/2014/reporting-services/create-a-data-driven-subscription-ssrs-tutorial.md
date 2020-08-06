---
title: 데이터 기반 구독 만들기(SSRS 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], tutorials
- walkthroughs [Reporting Services]
- data-driven subscriptions
ms.assetid: 79ab0572-43e9-4dc4-9b5a-cd8b627b8274
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 53be7cf793d8fa38d177643c7f366115d4df8b7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735107"
---
# <a name="create-a-data-driven-subscription-ssrs-tutorial"></a><span data-ttu-id="29397-102">데이터 기반 구독 만들기(SSRS 자습서)</span><span class="sxs-lookup"><span data-stu-id="29397-102">Create a Data-Driven Subscription (SSRS Tutorial)</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="29397-103">에서 데이터 기반 구독을 제공하므로 동적 구독자 데이터를 기반으로 보고서 배포를 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29397-103">provides data-driven subscriptions so that you can customize the distribution of a report based on dynamic subscriber data.</span></span> <span data-ttu-id="29397-104">데이터 기반 구독은 다음과 같은 종류의 시나리오에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="29397-104">Data-driven subscriptions are intended for the following kinds of scenarios:</span></span>  
  
-   <span data-ttu-id="29397-105">배포마다 멤버가 변경될 수 있는 대규모 받는 사람 풀에 보고서 배포.</span><span class="sxs-lookup"><span data-stu-id="29397-105">Distributing reports to a large recipient pool whose membership may change from one distribution to the next.</span></span> <span data-ttu-id="29397-106">예를 들면 모든 현재 고객에게 월별 보고서를 배포하는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="29397-106">For example, distribute a monthly report to all current customers.</span></span>  
  
-   <span data-ttu-id="29397-107">미리 정의된 조건을 기반으로 특정 받는 사람 그룹에 보고서 배포.</span><span class="sxs-lookup"><span data-stu-id="29397-107">Distributing reports to a specific group of recipients based on predefined criteria.</span></span> <span data-ttu-id="29397-108">예를 들면 조직의 최고 판매 관리자 10명에게 판매 실적 보고서를 보내는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="29397-108">For example, send a sales performance report to the top ten sales managers in an organization.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="29397-109">학습 내용</span><span class="sxs-lookup"><span data-stu-id="29397-109">What You Will Learn</span></span>  
 <span data-ttu-id="29397-110">이 자습서에서는 개념을 설명하는 간단한 예제를 통해 데이터 기반 구독을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="29397-110">This tutorial shows you how to use data-driven subscriptions using a simple example to illustrate the concepts.</span></span>  
  
 <span data-ttu-id="29397-111">이 자습서는 다음 3개의 단원으로 이루어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29397-111">This tutorial is divided into three lessons:</span></span>  
  
 [<span data-ttu-id="29397-112">1단원: 샘플 구독자 데이터베이스 만들기</span><span class="sxs-lookup"><span data-stu-id="29397-112">Lesson 1: Creating a Sample Subscriber Database</span></span>](lesson-1-creating-a-sample-subscriber-database.md)  
 <span data-ttu-id="29397-113">이 단원에서는 구독자 정보가 있는 로컬 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스를 만드는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="29397-113">In this lesson you will learn how to create a local [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database that contains subscriber information.</span></span>  
  
 [<span data-ttu-id="29397-114">2단원: 보고서 데이터 원본 속성 수정</span><span class="sxs-lookup"><span data-stu-id="29397-114">Lesson 2: Modifying the Report Data Source Properties</span></span>](lesson-2-modifying-the-report-data-source-properties.md)  
 <span data-ttu-id="29397-115">이 단원에서는 보고서가 무인 모드로 실행되도록 보고서 데이터 원본 속성을 수정하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="29397-115">In this lesson, you will learn how to modify report data source properties so that the report can run unattended.</span></span> <span data-ttu-id="29397-116">무인 처리를 위해서는 저장된 자격 증명이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="29397-116">Unattended processing requires stored credentials.</span></span> <span data-ttu-id="29397-117">또한 구독자 데이터로 공급되는 매개 변수를 포함하도록 보고서 데이터 세트를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="29397-117">You will also modify the report dataset to include a parameter that is supplied by the subscriber data.</span></span>  
  
 [<span data-ttu-id="29397-118">3단원: 데이터 기반 구독 정의</span><span class="sxs-lookup"><span data-stu-id="29397-118">Lesson 3: Defining a Data-Driven Subscription</span></span>](lesson-3-defining-a-data-driven-subscription.md)  
 <span data-ttu-id="29397-119">이 단원에서는 데이터 기반 구독을 정의하는 방법을 배우며</span><span class="sxs-lookup"><span data-stu-id="29397-119">In this lesson you will learn how to define a data-driven subscription.</span></span> <span data-ttu-id="29397-120">데이터 기반 구독 마법사의 각 페이지를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="29397-120">This lesson guides you through each page in the Data-Driven Subscription Wizard.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29397-121">요구 사항</span><span class="sxs-lookup"><span data-stu-id="29397-121">Requirements</span></span>  
 <span data-ttu-id="29397-122">데이터 기반 구독은 대개 보고서 서버 관리자가 만들고 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="29397-122">Data-driven subscriptions are typically created and maintained by report server administrators.</span></span> <span data-ttu-id="29397-123">데이터 기반 구독을 만들려면 쿼리 작성에 대한 전문 지식, 구독자 데이터가 포함된 데이터 원본에 대한 지식, 보고서 서버에서 승격된 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="29397-123">The ability to create data-driven subscriptions requires expertise in building queries, knowledge of data sources that contain subscriber data, and elevated permissions on a report server.</span></span>  
  
 <span data-ttu-id="29397-124">이 자습서에서는 기본 테이블 보고서 만들기 자습서에서 만든 보고서를 사용 하 여 [&#40;SSRS 자습서&#41;](create-a-basic-table-report-ssrs-tutorial.md) 및 데이터를 사용 합니다.[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29397-124">The tutorial will use the report created in the tutorial [Create a Basic Table Report &#40;SSRS Tutorial&#41;](create-a-basic-table-report-ssrs-tutorial.md) and data from [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]</span></span>  
  
 <span data-ttu-id="29397-125">이 자습서를 사용하려면 시스템에 다음 항목이 설치되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="29397-125">Your system must have the following installed to use this tutorial:</span></span>  
  
-   <span data-ttu-id="29397-126">데이터 기반 구독을 지원하는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 버전.</span><span class="sxs-lookup"><span data-stu-id="29397-126">An edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that supports data-driven subscriptions.</span></span> <span data-ttu-id="29397-127">자세한 내용은 [SQL Server 2014의 버전 및 구성 요소](../sql-server/editions-and-components-of-sql-server-2016.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="29397-127">For more information, see [Editions and Components of SQL Server 2014](../sql-server/editions-and-components-of-sql-server-2016.md).</span></span>  
  
-   <span data-ttu-id="29397-128">기본 모드로 보고서 서버가 실행되고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="29397-128">The report server must be running in native mode.</span></span> <span data-ttu-id="29397-129">이 자습서에 설명된 사용자 인터페이스는 기본 모드 보고서 서버를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="29397-129">The user interface described in this tutorial is based on a native mode report server.</span></span> <span data-ttu-id="29397-130">구독은 SharePoint 모드 보고서 서버에서 지원되지만 사용자 인터페이스는 이 자습서에 설명된 것과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="29397-130">Subscriptions are supported on SharePoint mode report servers but the user interface will be different than what is described in this tutorial.</span></span>  
  
-   <span data-ttu-id="29397-131">SQL Server 에이전트 서비스가 실행되고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="29397-131">SQL Server Agent service must be running.</span></span>  
  
-   <span data-ttu-id="29397-132">매개 변수가 들어 있는 보고서가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="29397-132">A report that includes parameters.</span></span> <span data-ttu-id="29397-133">이 자습서에서는 `Sales Orders` 기본 테이블 보고서 만들기&#40;SSRS 자습서&#41; [기본 테이블 보고서 만들기&amp;#40;SSRS 자습서&amp;#41;](create-a-basic-table-report-ssrs-tutorial.md)의 데이터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="29397-133">This tutorial assumes the sample report, `Sales Orders` you create using the tutorial [Create a Basic Table Report &#40;SSRS Tutorial&#41;](create-a-basic-table-report-ssrs-tutorial.md).</span></span>  
  
-   <span data-ttu-id="29397-134">예제 보고서에 데이터를 제공하는 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 예제 데이터베이스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="29397-134">The [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] sample database, which provides data to the sample report.</span></span>  
  
-   <span data-ttu-id="29397-135">예제 보고서에 대한 모든 구독 관리 태스크를 포함하는 역할 할당이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="29397-135">A role assignment that includes the Manage all subscriptions task on the sample report.</span></span> <span data-ttu-id="29397-136">이 태스크는 데이터 기반 구독 정의에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="29397-136">This task is required for defining a data-driven subscription.</span></span> <span data-ttu-id="29397-137">컴퓨터 관리자인 경우 로컬 관리자에 대한 기본 역할 할당을 통해 데이터 기반 구독을 만드는 데 필요한 권한을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29397-137">If you are an administrator on the computer, the default role assignment for local administrators provides the permissions necessary for creating data-driven subscriptions.</span></span> <span data-ttu-id="29397-138">자세한 내용은 [기본 모드 보고서 서버에 대한 사용 권한 부여](security/granting-permissions-on-a-native-mode-report-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="29397-138">For more information, see [Granting Permissions on a Native Mode Report Server](security/granting-permissions-on-a-native-mode-report-server.md).</span></span>  
  
-   <span data-ttu-id="29397-139">쓰기 권한이 있는 공유 폴더가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="29397-139">A shared folder for which you have write permissions.</span></span> <span data-ttu-id="29397-140">이 공유 폴더는 네트워크 연결을 통해 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="29397-140">The shared folder must be accessible over a network connection.</span></span>  
  
 <span data-ttu-id="29397-141">**자습서를 완료 하는 데 소요 되는 예상 시간:** 30 분</span><span class="sxs-lookup"><span data-stu-id="29397-141">**Estimated time to complete the tutorial:** 30 minutes.</span></span> <span data-ttu-id="29397-142">기본 보고서 자습서를 완료하지 않은 경우 추가 30분이 소요됩니다.</span><span class="sxs-lookup"><span data-stu-id="29397-142">An additional 30 minutes if you have not completed the basic report tutorial.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29397-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="29397-143">See Also</span></span>  
 <span data-ttu-id="29397-144">[Data-Driven Subscriptions](subscriptions/data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="29397-144">[Data-Driven Subscriptions](subscriptions/data-driven-subscriptions.md) </span></span>  
 [<span data-ttu-id="29397-145">기본 테이블 보고서 만들기&#40;SSRS 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="29397-145">Create a Basic Table Report &#40;SSRS Tutorial&#41;</span></span>](create-a-basic-table-report-ssrs-tutorial.md)  
  
  
