---
title: RDL 스키마에서 생성 된 클래스를 사용 하 여 보고서 업데이트 (SSRS 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RDL [Reporting Services], generating
- RDL [Reporting Services], tutorials
- RDL [Reporting Services], serializing
ms.assetid: 8f81d48f-7ab9-4ef8-bce0-7d16d9a47fbd
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: f3972b8e1af6d50ccc6f5188c8f671fe333ebce8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647360"
---
# <a name="updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial"></a><span data-ttu-id="7c4db-102">RDL 스키마에서 생성한 클래스를 사용하여 보고서 업데이트(SSRS 자습서)</span><span class="sxs-lookup"><span data-stu-id="7c4db-102">Updating Reports Using Classes Generated from the RDL Schema (SSRS Tutorial)</span></span>
  <span data-ttu-id="7c4db-103">이 자습서에서는 Xsd.exe (XML 스키마 정의 도구)를 사용 하 여 클래스를 사용 하 여 보고서 정의 파일 (.rdl 및 .rdlc)을 serialize 및 deserialize 할 수 있도록 하는 클래스를 생성 하는 방법을 보여 줍니다 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="7c4db-103">This tutorial illustrates how to use the XML Schema Definition Tool (Xsd.exe) to generate classes that allow you to serialize and deserialize report definition files (.rdl and .rdlc) with the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="7c4db-104">학습 내용</span><span class="sxs-lookup"><span data-stu-id="7c4db-104">What You Will Learn</span></span>  
 <span data-ttu-id="7c4db-105">이 자습서를 통해 다음 작업을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="7c4db-105">During the course of this tutorial, you will complete the following activities:</span></span>  
  
-   <span data-ttu-id="7c4db-106">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 콘솔 응용 프로그램 프로젝트 템플릿을 사용 하 여 응용 프로그램을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7c4db-106">Create an application using the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Console Application project template.</span></span>  
  
-   <span data-ttu-id="7c4db-107">**xsd** 도구를 사용하여 RDL(Report Definition Language) 스키마의 클래스를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="7c4db-107">Generate classes from the Report Definition Language (RDL) schema using the **xsd** tool.</span></span>  
  
-   <span data-ttu-id="7c4db-108">보고서 서버에 연결하고 보고서 정의를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="7c4db-108">Connect to a report server and retrieve a report definition.</span></span>  
  
-   <span data-ttu-id="7c4db-109">코드를 작성하여 보고서 정의 파일을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="7c4db-109">Write code to update the report definition file.</span></span>  
  
-   <span data-ttu-id="7c4db-110">업데이트한 보고서 정의를 다시 보고서 서버에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="7c4db-110">Save the updated report definition back to the report server.</span></span>  
  
-   <span data-ttu-id="7c4db-111">RDL Schema 애플리케이션을 실행합니다(VB/C#).</span><span class="sxs-lookup"><span data-stu-id="7c4db-111">Run the RDL Schema Application (VB/C#).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7c4db-112">이 자습서에 제공되는 코드 예제는 설명이 없는 보고서의 경우 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c4db-112">The code samples provided in this tutorial might fail for reports having no description.</span></span> <span data-ttu-id="7c4db-113">설명이 지정되지 않은 보고서의 경우 설명 속성이 존재하지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="7c4db-113">The failure is because the description property does not exist for the reports with description not specified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c4db-114">요구 사항</span><span class="sxs-lookup"><span data-stu-id="7c4db-114">Requirements</span></span>  
 <span data-ttu-id="7c4db-115">이 자습서를 수행하려면 다음 항목이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7c4db-115">To complete the tutorial, you must have the following:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="7c4db-116">[!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7c4db-116">[!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="7c4db-117">[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7c4db-117">[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].</span></span>  
  
-   <span data-ttu-id="7c4db-118">보고서 서버가 있는 컴퓨터의 보고서 서버 웹 서비스에 액세스하고 보고서를 게시할 수 있는 권한</span><span class="sxs-lookup"><span data-stu-id="7c4db-118">Sufficient permissions to be able to access and publish reports to the Report Server Web service on the computer where your report server is located.</span></span>  
  
-   <span data-ttu-id="7c4db-119">[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 인스턴스에 설치된 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]예제 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="7c4db-119">The [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] sample database installed to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="7c4db-120">보고서 서버에 설치된 보고서.</span><span class="sxs-lookup"><span data-stu-id="7c4db-120">A report installed on your report server.</span></span> <span data-ttu-id="7c4db-121">이 자습서에서는 예제 보고서 Company Sales 2012를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7c4db-121">This tutorial uses the sample report, Company Sales 2012.</span></span> <span data-ttu-id="7c4db-122">예제 보고서에 대한 자세한 내용은 [SQL Server Reporting Services 제품 예제(SQL Server Reporting Services Product Samples)](https://go.microsoft.com/fwlink/?LinkId=177889)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7c4db-122">For more information about sample reports, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7c4db-123">설치 시 예제가 자동으로 설치되지 않지만 예제는 언제든지 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c4db-123">The samples are not installed automatically during setup, but you can install them at any time.</span></span> <span data-ttu-id="7c4db-124">예제에 대한 정보는 [SQL Server 제품 예제](https://go.microsoft.com/fwlink/?LinkId=182887)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7c4db-124">For information about samples, see [SQL Server Product Samples](https://go.microsoft.com/fwlink/?LinkId=182887).</span></span>  
  
 <span data-ttu-id="7c4db-125">**자습서에 소요되는 예상 시간:** 30분</span><span class="sxs-lookup"><span data-stu-id="7c4db-125">**Estimated time to complete the tutorial:** 30 minutes</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="7c4db-126">작업</span><span class="sxs-lookup"><span data-stu-id="7c4db-126">Tasks</span></span>  
 [<span data-ttu-id="7c4db-127">1단원: RDL Schema Visual Studio 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="7c4db-127">Lesson 1: Create the RDL Schema Visual Studio Project</span></span>](../../2014/tutorials/lesson-1-create-the-rdl-schema-visual-studio-project.md)  
  
 [<span data-ttu-id="7c4db-128">2단원: xsd 도구를 사용하여 RDL 스키마에서 클래스 생성</span><span class="sxs-lookup"><span data-stu-id="7c4db-128">Lesson 2: Generate Classes from the RDL Schema using the xsd Tool</span></span>](../../2014/tutorials/lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool.md)  
  
 [<span data-ttu-id="7c4db-129">3단원: 보고서 서버에서 보고서 정의 로드</span><span class="sxs-lookup"><span data-stu-id="7c4db-129">Lesson 3: Load a Report Definition from the Report Server</span></span>](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md)  
  
 [<span data-ttu-id="7c4db-130">4단원: 프로그래밍 방식으로 보고서 정의 업데이트</span><span class="sxs-lookup"><span data-stu-id="7c4db-130">Lesson 4: Update the Report Definition Programmatically</span></span>](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md)  
  
 [<span data-ttu-id="7c4db-131">5단원: 보고서 정의를 보고서 서버에 게시</span><span class="sxs-lookup"><span data-stu-id="7c4db-131">Lesson 5: Publish the Report Definition to the Report Server</span></span>](../../2014/tutorials/lesson-5-publish-the-report-definition-to-the-report-server.md)  
  
 [<span data-ttu-id="7c4db-132">6 단원: VB-C&#35;&#41;&#40;RDL 스키마 응용 프로그램 실행</span><span class="sxs-lookup"><span data-stu-id="7c4db-132">Lesson 6: Run the RDL Schema Application &#40;VB-C&#35;&#41;</span></span>](../../2014/tutorials/lesson-6-run-the-rdl-schema-application-vb-csharp.md)  
  
## <a name="see-also"></a><span data-ttu-id="7c4db-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7c4db-133">See Also</span></span>  
 [<span data-ttu-id="7c4db-134">보고서 정의 언어&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7c4db-134">Report Definition Language &#40;SSRS&#41;</span></span>](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
