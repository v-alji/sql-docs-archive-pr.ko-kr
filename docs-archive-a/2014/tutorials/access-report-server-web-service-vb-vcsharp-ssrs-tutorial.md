---
title: 'Visual Basic 또는 Visual c #을 사용 하 여 보고서 서버 웹 서비스에 액세스 (SSRS 자습서) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- walkthroughs [Reporting Services]
- Reporting Services, Web service
- Web service [Reporting Services], tutorials
ms.assetid: cf688163-4ac0-475b-b6dd-6f2f05b553c6
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 3dc2599b4fafe682d74089d637918e04db9ed219
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735684"
---
# <a name="accessing-the-report-server-web-service-using-visual-basic-or-visual-c-ssrs-tutorial"></a><span data-ttu-id="2003d-102">Visual Basic 또는 Visual C#을 사용하여 보고서 서버 웹 서비스에 액세스(SSRS 자습서)</span><span class="sxs-lookup"><span data-stu-id="2003d-102">Accessing the Report Server Web Service Using Visual Basic or Visual C# (SSRS Tutorial)</span></span>
  <span data-ttu-id="2003d-103">다음 자습서에서는 또는을 사용 하 여 만든 응용 프로그램에서 보고서 서버 웹 서비스에 액세스 하는 방법을 보여 줍니다 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[csprcs](../includes/csprcs-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2003d-103">The following tutorial shows you how to access the Report Server Web service from an application created with [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] or [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[csprcs](../includes/csprcs-md.md)].</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="2003d-104">학습 내용</span><span class="sxs-lookup"><span data-stu-id="2003d-104">What You Will Learn</span></span>  
 <span data-ttu-id="2003d-105">이 자습서에서는 다음 작업을 완성합니다.</span><span class="sxs-lookup"><span data-stu-id="2003d-105">During the course of this tutorial, you will complete the following:</span></span>  
  
-   <span data-ttu-id="2003d-106">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 콘솔 응용 프로그램 프로젝트 템플릿을 사용 하 여 클라이언트 응용 프로그램을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2003d-106">Create a client application using the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Console Application project template.</span></span>  
  
-   <span data-ttu-id="2003d-107">보고서 서버 웹 서비스에 대한 웹 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2003d-107">Add a Web reference for the Report Server Web service.</span></span>  
  
-   <span data-ttu-id="2003d-108">웹 서비스에 액세스하는 코드를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="2003d-108">Write code to access the Web service.</span></span>  
  
-   <span data-ttu-id="2003d-109">디버그 모드로 콘솔 애플리케이션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2003d-109">Run the console application in debug mode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2003d-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="2003d-110">Requirements</span></span>  
 <span data-ttu-id="2003d-111">이 자습서를 수행하려면 다음 항목이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2003d-111">To complete the tutorial, you must have the following:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="2003d-112">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2003d-112">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="2003d-113">[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]또는 유사한 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 호환 가능한 개발 도구.</span><span class="sxs-lookup"><span data-stu-id="2003d-113">[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] or a similar [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-compatible development tool.</span></span>  
  
-   <span data-ttu-id="2003d-114">보고서 서버가 있는 컴퓨터의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 보고서 서버 웹 서비스에 액세스할 수 있는 권한</span><span class="sxs-lookup"><span data-stu-id="2003d-114">Sufficient permissions to be able to access the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Report Server Web service on the computer where your report server is located.</span></span>  
  
-   <span data-ttu-id="2003d-115">보고서 서버에 설치된 보고서.</span><span class="sxs-lookup"><span data-stu-id="2003d-115">A report installed on your report server.</span></span> <span data-ttu-id="2003d-116">이 자습서에서는 예제 보고서 Company Sales를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2003d-116">This tutorial uses the sample report, Company Sales.</span></span> <span data-ttu-id="2003d-117">예제 보고서에 대한 자세한 내용은 [SQL Server Reporting Services 제품 예제(SQL Server Reporting Services Product Samples)](https://go.microsoft.com/fwlink/?LinkId=177889)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2003d-117">For more information about sample reports, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2003d-118">설치 시 예제가 자동으로 설치되지 않지만 예제는 언제든지 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2003d-118">The samples are not installed automatically during setup, but you can install them at any time.</span></span> <span data-ttu-id="2003d-119">예제에 대한 정보는 [SQL Server 제품 예제](https://go.microsoft.com/fwlink/?LinkId=182887)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2003d-119">For information about samples, see [SQL Server Product Samples](https://go.microsoft.com/fwlink/?LinkId=182887).</span></span>  
  
 <span data-ttu-id="2003d-120">**자습서에 소요되는 예상 시간:** 60분</span><span class="sxs-lookup"><span data-stu-id="2003d-120">**Estimated time to complete the tutorial:** 60 minutes</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="2003d-121">작업</span><span class="sxs-lookup"><span data-stu-id="2003d-121">Tasks</span></span>  
 [<span data-ttu-id="2003d-122">1단원: Web Service 클라이언트 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="2003d-122">Lesson 1: Creating the Web Service Client Project</span></span>](../../2014/tutorials/lesson-1-creating-the-web-service-client-project.md)  
  
 [<span data-ttu-id="2003d-123">2단원: 웹 참조 추가</span><span class="sxs-lookup"><span data-stu-id="2003d-123">Lesson 2: Adding a Web Reference</span></span>](../../2014/tutorials/lesson-2-adding-a-web-reference.md)  
  
 [<span data-ttu-id="2003d-124">3단원: Web Service에 액세스</span><span class="sxs-lookup"><span data-stu-id="2003d-124">Lesson 3: Accessing the Web Service</span></span>](../../2014/tutorials/lesson-3-accessing-the-web-service.md)  
  
 [<span data-ttu-id="2003d-125">4 단원: 응용 프로그램 실행 &#40;VB-VC&#35;&#41;</span><span class="sxs-lookup"><span data-stu-id="2003d-125">Lesson 4: Running the Application &#40;VB-VC&#35;&#41;</span></span>](../../2014/tutorials/lesson-4-running-the-application-vb-vcsharp.md)  
  
  
