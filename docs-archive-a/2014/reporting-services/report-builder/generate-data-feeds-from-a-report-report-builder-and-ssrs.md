---
title: 보고서에서 데이터 피드 생성(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e68baae2-9f2a-4f13-9179-9ac7f29111c5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 340191396aaaa92fe14fe8c3c6b42539a713eb45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639370"
---
# <a name="generate-data-feeds-from-a-report-report-builder-and-ssrs"></a><span data-ttu-id="78519-102">보고서에서 데이터 피드 생성(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="78519-102">Generate Data Feeds from a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="78519-103">보고서에서 Atom 규격 데이터 피드를 생성 한 다음 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 데이터 피드를 사용할 수 있는 클라이언트와 같은 응용 프로그램의 데이터 피드를 사용할 수 있습니다 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="78519-103">You can generate Atom-compliant data feeds from reports, and then use the data feeds in applications, such as the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] client, that can consume data feeds.</span></span>  
  
 <span data-ttu-id="78519-104">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Atom 렌더링 확장 프로그램은 보고서에서 사용할 수 있는 데이터 피드를 나열하는 Atom 서비스 문서를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="78519-104">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Atom rendering extension generates an Atom service document that lists the data feeds available from a report.</span></span> <span data-ttu-id="78519-105">이 문서는 보고서의 각 데이터 영역에 대한 데이터 피드를 하나 이상 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="78519-105">The document lists at least one data feed for each data region in the report.</span></span> <span data-ttu-id="78519-106">데이터 영역의 유형과 데이터 영역에 표시되는 데이터에 따라 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 는 데이터 영역에서 여러 데이터 피드를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78519-106">Depending on the type of data region and the data that the data region displays, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] might generate multiple data feeds from a data region.</span></span>  
  
 <span data-ttu-id="78519-107">Atom 서비스 문서에는 각 데이터 피드에 대한 고유 식별자가 포함되며 URL에서 이 식별자를 사용하여 데이터 피드의 내용을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78519-107">Atom service document contains a unique identifier for each the data feed and you use the identifier in a URL to view the content of the data feed.</span></span>  
  
 <span data-ttu-id="78519-108">자세한 내용은 [보고서에서 데이터 피드 생성&#40;보고서 작성기 및 SSRS&#41;](generating-data-feeds-from-reports-report-builder-and-ssrs.md)에서 이 데이터로 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78519-108">For more information, see [Generating Data Feeds from Reports &#40;Report Builder and SSRS&#41;](generating-data-feeds-from-reports-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-generate-an-atom-service-document"></a><span data-ttu-id="78519-109">Atom 서비스 문서를 생성하려면</span><span class="sxs-lookup"><span data-stu-id="78519-109">To generate an Atom service document</span></span>  
  
1.  <span data-ttu-id="78519-110">보고서 관리자 **홈** 페이지에서 데이터 피드를 생성할 보고서를 찾아 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="78519-110">From the Report Manager **Home** page, navigate to the report from which you want to generate data feeds.</span></span>  
  
2.  <span data-ttu-id="78519-111">보고서를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="78519-111">Click the report.</span></span>  
  
     <span data-ttu-id="78519-112">보고서가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="78519-112">The report is run.</span></span>  
  
3.  <span data-ttu-id="78519-113">도구 모음에서 데이터 피드로 내보내기 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="78519-113">On the toolbar, click the Export to Data Feed icon.</span></span>  
  
     <span data-ttu-id="78519-114">데이터 피드가 포함된 Atom 문서를 저장하거나 열지 확인하는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="78519-114">A message appears asking you if you want to save or open the atom document that contains the data feed.</span></span>  
  
4.  <span data-ttu-id="78519-115">**저장** 을 클릭하여 파일 시스템에 문서를 저장하거나 저장하기 전에 **열기** 를 클릭하여 문서 내용을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="78519-115">Click **Save** to save the document to the file system, or click **Open** to view the document content before saving.</span></span> <span data-ttu-id="78519-116">**기본적으로 브라우저에서 문서가 열립니다.**</span><span class="sxs-lookup"><span data-stu-id="78519-116">**By default, the document opens in a browser.**</span></span>  
  
5.  <span data-ttu-id="78519-117">문서를 저장할 위치를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="78519-117">Browse to the location to save the document.</span></span>  
  
6.  <span data-ttu-id="78519-118">필요한 경우 문서 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="78519-118">Optionally, change the name of the document.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="78519-119">기본적으로 문서 이름은 보고서 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="78519-119">By default, the document name is the report name.</span></span>  
  
7.  <span data-ttu-id="78519-120">문서 유형이 **ATOMSVC 파일**인지 확인한 다음 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="78519-120">Verify the document type is **ATOMSVC File**, and then click **Save**.</span></span>  
  
8.  <span data-ttu-id="78519-121">필요한 경우 브라우저, 텍스트 편집기 또는 XML 편집기에서 .atomsvc 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="78519-121">Optionally, open the .atomsvc file in a browser or text or XML editor.</span></span>  
  
### <a name="to-view-an-atom-compliant-data-feed"></a><span data-ttu-id="78519-122">Atom 규격 데이터 피드를 보려면</span><span class="sxs-lookup"><span data-stu-id="78519-122">To view an Atom-compliant data feed</span></span>  
  
1.  <span data-ttu-id="78519-123">Atom 서비스 문서가 열려 있지 않으면 해당 문서를 찾아 Internet Explorer와 같은 브라우저에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="78519-123">If the Atom service document is not already open, locate it and open it in a browser such as Internet Explorer.</span></span>  
  
2.  <span data-ttu-id="78519-124">Atom 서비스 문서에서 보려는 데이터 피드의 URL을 브라우저에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="78519-124">Copy the URL of the data feed that you want to view from the Atom service document to the browser.</span></span>  
  
     <span data-ttu-id="78519-125">URL 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="78519-125">The format of the URL is the following:</span></span>  
  
 `http://<server name>/ReportServer?%2f<ReportName>rs%3aCommand=Render&rs%3aFormat=ATOM&rc%3aDataFeed=<Identifier>`  
  
1.  <span data-ttu-id="78519-126">Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="78519-126">Press ENTER.</span></span>  
  
     <span data-ttu-id="78519-127">데이터 피드가 포함된 Atom 문서를 저장하거나 열지 확인하는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="78519-127">A message appears asking you if you want to save or open the atom document that contains the data feed.</span></span>  
  
2.  <span data-ttu-id="78519-128">**저장** 을 클릭하여 파일 시스템에 문서를 저장하거나 저장하기 전에 **열기** 를 클릭하여 데이터 피드를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="78519-128">Click **Save** to save the document to the file system, or click **Open** to view the data feed before saving.</span></span>  
  
3.  <span data-ttu-id="78519-129">문서를 저장할 위치를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="78519-129">Browse to the location to save the document.</span></span>  
  
4.  <span data-ttu-id="78519-130">필요한 경우 문서 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="78519-130">Optionally, change the name of the document.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="78519-131">기본적으로 문서 이름은 보고서 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="78519-131">By default the document name is the report name.</span></span> <span data-ttu-id="78519-132">Atom 서비스 문서에 피드가 여러 개 있으면 기본적으로 모든 피드가 같은 이름인 보고서 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="78519-132">If the Atom service document has multiple feeds, by default all use the same name, the report name.</span></span> <span data-ttu-id="78519-133">피드를 구별하려면 피드 이름을 의미 있는 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="78519-133">To differentiate them, rename them to use meaningful names.</span></span>  
  
5.  <span data-ttu-id="78519-134">문서 유형이 **ATOM 파일**인지 확인한 다음 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="78519-134">Verify the document type is **ATOM File**, and then click **Save**.</span></span>  
  
6.  <span data-ttu-id="78519-135">필요한 경우 브라우저, 텍스트 편집기 또는 XML 편집기에서 .atom 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="78519-135">Optionally, open the .atom file in a browser or text editor or XML editor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78519-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="78519-136">See Also</span></span>  
 [<span data-ttu-id="78519-137">보고서 &#40;보고서 작성기 및 SSRS&#41;내보내기</span><span class="sxs-lookup"><span data-stu-id="78519-137">Exporting Reports &#40;Report Builder and SSRS&#41;</span></span>](export-reports-report-builder-and-ssrs.md)  
  
  
