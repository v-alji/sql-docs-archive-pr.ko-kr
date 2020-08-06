---
title: 기본 테이블 보고서 만들기(SSRS 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [Reporting Services]
- tutorials [Reporting Services]
- reports [Reporting Services], creating
ms.assetid: 3b539b4b-26f2-4c0b-b506-80f175679a46
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 02e0f42869a3bfa88e0c6646fd447968c8ba3a10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638555"
---
# <a name="create-a-basic-table-report-ssrs-tutorial"></a><span data-ttu-id="3748d-102">기본 테이블 보고서 만들기(SSRS 자습서)</span><span class="sxs-lookup"><span data-stu-id="3748d-102">Create a Basic Table Report (SSRS Tutorial)</span></span>
  <span data-ttu-id="3748d-103">이 자습서에서는 보고서 디자이너를 사용하여 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 데이터베이스를 기반으로 하는 기본 테이블 보고서를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3748d-103">This tutorial is designed to help you create a basic table report based on the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database using Report Designer.</span></span> <span data-ttu-id="3748d-104">또한 보고서 작성기나 보고서 마법사를 사용하여 보고서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3748d-104">You can also use Report Builder or the Report Wizard to create reports.</span></span> <span data-ttu-id="3748d-105">이 자습서에서는 보고서 프로젝트를 만들고, 연결 정보를 설정하고, 쿼리를 정의하고, 테이블 데이터 영역을 추가하고, 필드를 그룹화하거나 필드 합계를 구하고, 보고서를 미리 보는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="3748d-105">In this tutorial, you will create a report project, set up connection information, define a query, add a Table data region, group and total some fields, and preview the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3748d-106">이 자습서를 완료하려면 기본 모드로 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]가 실행되고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3748d-106">To complete this tutorial, you must be running [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in native mode.</span></span> <span data-ttu-id="3748d-107">SharePoint 통합 모드로 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]를 실행하는 경우 보고서 서버 URL을 사용하는 단계가 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3748d-107">If you are running [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in SharePoint integrated mode, the steps that use report server URLs do not work.</span></span> <span data-ttu-id="3748d-108">모드에 대 한 자세한 내용은 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [Reporting Services Report Server](reporting-services-report-server.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3748d-108">For more information about [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] modes, see [Reporting Services Report Server](reporting-services-report-server.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3748d-109">요구 사항</span><span class="sxs-lookup"><span data-stu-id="3748d-109">Requirements</span></span>  
 <span data-ttu-id="3748d-110">이 자습서를 사용하려면 시스템에 다음 항목이 설치되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3748d-110">Your system must have the following installed to use this tutorial:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="3748d-111">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]데이터베이스 엔진.</span><span class="sxs-lookup"><span data-stu-id="3748d-111">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] database engine.</span></span>  
  
-   <span data-ttu-id="3748d-112">[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 데이터베이스.</span><span class="sxs-lookup"><span data-stu-id="3748d-112">The [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span>  <span data-ttu-id="3748d-113">자세한 내용은 [SQL Server 2012에 대 한 놀이 works (SQL Server 2012 용 놀이 works) ()](https://go.microsoft.com/fwlink/?LinkId=245471) 를 참조 하세요 https://go.microsoft.com/fwlink/?LinkId=245471). .</span><span class="sxs-lookup"><span data-stu-id="3748d-113">For more information, see [Adventure Works for SQL Server 2012 (Adventure Works for SQL Server 2012)](https://go.microsoft.com/fwlink/?LinkId=245471) (https://go.microsoft.com/fwlink/?LinkId=245471)..</span></span> <span data-ttu-id="3748d-114">예제 데이터베이스 및 예제 코드에 대 한 지원에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] CodePlex 웹 사이트에서 [데이터베이스 및 예제 개요](https://go.microsoft.com/fwlink/?LinkId=110391) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="3748d-114">For more information about support for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sample databases and sample code for [!INCLUDE[ssExpress](../includes/ssexpress-md.md)], see [Databases and Samples Overview](https://go.microsoft.com/fwlink/?LinkId=110391) on the CodePlex Web site.</span></span>  
  
-   [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]<span data-ttu-id="3748d-115">.</span><span class="sxs-lookup"><span data-stu-id="3748d-115">.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="3748d-116">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3748d-116">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNote64Samp](../includes/ssnote64samp-md.md)]  
  
 <span data-ttu-id="3748d-117">또한 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 데이터베이스에서 데이터를 검색하려면 읽기 전용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3748d-117">You must also have read-only permissions to retrieve data from the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="3748d-118">작업</span><span class="sxs-lookup"><span data-stu-id="3748d-118">Tasks</span></span>  
 [<span data-ttu-id="3748d-119">1단원: 보고서 서버 프로젝트 만들기&#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="3748d-119">Lesson 1: Creating a Report Server Project &#40;Reporting Services&#41;</span></span>](lesson-1-creating-a-report-server-project-reporting-services.md)  
  
 [<span data-ttu-id="3748d-120">2단원: 연결 정보 지정&#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="3748d-120">Lesson 2: Specifying Connection Information &#40;Reporting Services&#41;</span></span>](lesson-2-specifying-connection-information-reporting-services.md)  
  
 [<span data-ttu-id="3748d-121">3단원: 테이블 보고서에 대한 데이터 세트 정의&#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="3748d-121">Lesson 3: Defining a Dataset for the Table Report &#40;Reporting Services&#41;</span></span>](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md)  
  
 [<span data-ttu-id="3748d-122">4단원: 보고서에 테이블 추가&#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="3748d-122">Lesson 4: Adding a Table to the Report &#40;Reporting Services&#41;</span></span>](lesson-4-adding-a-table-to-the-report-reporting-services.md)  
  
 [<span data-ttu-id="3748d-123">5단원: 보고서 서식 지정&#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="3748d-123">Lesson 5: Formatting a Report &#40;Reporting Services&#41;</span></span>](lesson-5-formatting-a-report-reporting-services.md)  
  
 [<span data-ttu-id="3748d-124">6단원: 그룹화 및 합계 추가&#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="3748d-124">Lesson 6: Adding Grouping and Totals &#40;Reporting Services&#41;</span></span>](lesson-6-adding-grouping-and-totals-reporting-services.md)  
  
> [!NOTE]  
>  <span data-ttu-id="3748d-125">자습서를 검토할 때는 문서 뷰어 도구 모음에 **다음** 단추 및 **이전** 단추를 추가 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3748d-125">When reviewing tutorials, we recommend that you add **Next** and **Previous** buttons to the document viewer toolbar.</span></span> <span data-ttu-id="3748d-126">자세한 내용은 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3748d-126">For more information, see.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3748d-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3748d-127">See Also</span></span>  
 [<span data-ttu-id="3748d-128">Reporting Services&#40;SSRS&#41; 자습서</span><span class="sxs-lookup"><span data-stu-id="3748d-128">Reporting Services Tutorials &#40;SSRS&#41;</span></span>](reporting-services-tutorials-ssrs.md)  
  
  
