---
title: 라이브러리에 BI 의미 체계 모델 연결 콘텐츠 형식 추가 (SharePoint용 PowerPivot) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 145505ed-50bc-4528-912b-2a5cd2566011
author: minewiskan
ms.author: owend
ms.openlocfilehash: ecd40193b382aa692beeadd55ab8f9388c328620
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659687"
---
# <a name="add-a-bi-semantic-model-connection-content-type-to-a-library-powerpivot-for-sharepoint"></a><span data-ttu-id="69c86-102">라이브러리에 BI 의미 체계 모델 연결 콘텐츠 형식 추가(SharePoint용 PowerPivot)</span><span class="sxs-lookup"><span data-stu-id="69c86-102">Add a BI Semantic Model Connection Content Type to a Library (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="69c86-103">BI 의미 체계 모델 연결은 SharePoint에서 만들어지며 네트워크 서버의 PowerPivot 통합 문서 또는 Analysis Services 테이블 형식 모델 데이터베이스에 있는 비즈니스 인텔리전스 의미 체계 모델 데이터에 대한 리디렉션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="69c86-103">A BI semantic model connection is created in SharePoint and provides redirection to business intelligence semantic model data in a PowerPivot workbook or Analysis Services tabular model database on a network server.</span></span> <span data-ttu-id="69c86-104">SharePoint에서 BI 의미 체계 모델 연결을 만들려면 .bism 파일을 만들 수 있도록 문서 라이브러리를 확장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69c86-104">Before you can create a BI semantic model connection in SharePoint, you must extend a document library to allow the creation of a .bism file.</span></span> <span data-ttu-id="69c86-105">이 단계는 각 라이브러리에 대해 한 번만 수행해야 하지만 .bism 파일을 만들려는 모든 라이브러리에 대해 반복해서 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69c86-105">This step only needs to be performed once for each library, but you will need to repeat it for any library from which you want to create .bism files.</span></span> <span data-ttu-id="69c86-106">한 곳에서 사용 권한을 관리할 수 있도록 .bism 파일을 저장하기 위한 중앙 집중식 라이브러리를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="69c86-106">Best practices recommend that you create a centralized library for storing .bism files so that you can manage permissions in one place.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="69c86-107">이미 SharePoint 데이터 연결 라이브러리를 사용하는 경우 BI 의미 체계 모델 연결 콘텐츠 형식이 해당 라이브러리 템플릿에 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="69c86-107">If you already use SharePoint Data Connection Libraries, the BI Semantic Model Connection content type is automatically added to that library template.</span></span> <span data-ttu-id="69c86-108">이미 새 BI 의미 체계 모델 연결 문서를 만들 수 있게 하는 데이터 연결 라이브러리를 사용하는 경우에는 이 섹션의 단계를 건너뛸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69c86-108">You can skip the steps in this section if you use a data connection library that already lets you create new BI semantic model connection documents.</span></span>  
  
##  <a name="add-the-content-type-to-a-document-library"></a><a name="bkmk_addtype"></a> <span data-ttu-id="69c86-109">문서 라이브러리에 콘텐츠 형식 추가</span><span class="sxs-lookup"><span data-stu-id="69c86-109">Add the content type to a document library</span></span>  
 <span data-ttu-id="69c86-110">콘텐츠 형식을 추가하고 구성하려면 최소한 목록 관리 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69c86-110">You must have at least the Manage Lists permission to add and configure a content type.</span></span> <span data-ttu-id="69c86-111">이 권한은 디자인 권한 수준 이상에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69c86-111">This permission is built into the Design permission level and above.</span></span>  
  
 <span data-ttu-id="69c86-112">문서 라이브러리가 포함된 사이트에서는 SharePoint용 PowerPivot에 대한 기능이 활성화되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69c86-112">The site that contains the document library must have feature activation for PowerPivot for SharePoint.</span></span> <span data-ttu-id="69c86-113">자세한 내용은 [중앙 관리에서 사이트 모음에 대 한 PowerPivot 기능 통합 활성화](activate-power-pivot-integration-for-site-collections-in-ca.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="69c86-113">For more information, see [Activate PowerPivot Feature Integration for Site Collections in Central Administration](activate-power-pivot-integration-for-site-collections-in-ca.md).</span></span>  
  
1.  <span data-ttu-id="69c86-114">BI 의미 체계 모델 연결 콘텐츠 형식을 사용하도록 설정할 문서 라이브러리를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="69c86-114">Open the document library for which you want to enable the BI Semantic Model Connection content type.</span></span>  
  
2.  <span data-ttu-id="69c86-115">SharePoint 리본의 라이브러리 도구에서 **라이브러리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69c86-115">On the SharePoint ribbon, in Library Tools, click **Library**.</span></span>  
  
3.  <span data-ttu-id="69c86-116">**라이브러리 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69c86-116">Click **Library Settings**.</span></span>  
  
4.  <span data-ttu-id="69c86-117">일반 설정에서 **고급 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69c86-117">In General Settings, click **Advanced settings**.</span></span>  
  
5.  <span data-ttu-id="69c86-118">콘텐츠 형식의 "콘텐츠 형식 관리를 허용하시겠습니까?"</span><span class="sxs-lookup"><span data-stu-id="69c86-118">In Content Types, in the "Allow management of content types?"</span></span> <span data-ttu-id="69c86-119">섹션에서 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69c86-119">section, click **Yes**.</span></span>  
  
6.  <span data-ttu-id="69c86-120">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69c86-120">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="69c86-121">콘텐츠 형식 섹션에서 **기존 사이트 콘텐츠 형식에서 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69c86-121">In the Content Types section, click **Add from existing site content types**.</span></span> <span data-ttu-id="69c86-122">이 페이지가 표시되지 않는 경우 사이트로 돌아가서 라이브러리 도구에서 **라이브러리** 를 클릭한 다음 **라이브러리 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69c86-122">If you do not see this page, go back to the site, click **Library** in Library Tools, and then click **Library Settings**.</span></span>  
  
8.  <span data-ttu-id="69c86-123">콘텐츠 형식에서 **기존 사이트 콘텐츠 형식에서 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69c86-123">In Content Types, click **Add from existing site content types**.</span></span>  
  
9. <span data-ttu-id="69c86-124">사이트 콘텐츠 형식 선택에서 **비즈니스 인텔리전스**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="69c86-124">In Select site content types from:, select **Business Intelligence**.</span></span>  
  
10. <span data-ttu-id="69c86-125">사용 가능한 사이트 콘텐츠 형식에서 **BI 의미 체계 모델 연결 파일**을 클릭한 다음 **추가** 를 클릭하여 목록을 추가할 콘텐츠 형식으로 선택한 콘텐츠 형식을 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="69c86-125">In Available Site Content Types, click **BI Semantic Model Connection File**, and then click **Add** to move the selected content type to the Content types to add list.</span></span>  
  
11. <span data-ttu-id="69c86-126">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69c86-126">Click **OK**.</span></span>  
  
12. <span data-ttu-id="69c86-127">콘텐츠 형식을 추가했는지 확인하려면 라이브러리로 돌아가서 라이브러리 리본 메뉴의 문서 영역에서 **새 문서** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69c86-127">To verify you added the content type, go back to the library and click **New Document** on the Documents area of the library ribbon.</span></span> <span data-ttu-id="69c86-128">새 문서 목록에 **BI 의미 체계 모델 연결 파일** 이 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69c86-128">You should see **BI Semantic Model Connection File** in the New Documents list.</span></span>  
  
     <span data-ttu-id="69c86-129">![SharePoint 라이브러리의 새 문서 하위 메뉴](../media/ssas-bismconnection-new.gif "SharePoint 라이브러리의 새 문서 하위 메뉴")</span><span class="sxs-lookup"><span data-stu-id="69c86-129">![New Document submenu in a SharePoint library](../media/ssas-bismconnection-new.gif "New Document submenu in a SharePoint library")</span></span>  
  
 <span data-ttu-id="69c86-130">라이브러리에 대한 BI 의미 체계 모델 연결 콘텐츠 형식을 사용하도록 설정한 후 Excel 또는 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 보고서에 사용할 수 있는 비즈니스 의미 체계 모델 데이터에 대한 리디렉션을 제공하는 연결을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69c86-130">After you enable the BI semantic model connection content type for a library, you can create a connection that provides redirection to business semantic model data that can be used by Excel or [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] reports.</span></span> <span data-ttu-id="69c86-131">이 다음 단계에 대해 자세히 알아보려면 다음 링크를 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="69c86-131">Choose from the following links to learn more about this next step:</span></span>  
  
 [<span data-ttu-id="69c86-132">PowerPivot 통합 문서에 대한 BI 의미 체계 모델 연결 만들기</span><span class="sxs-lookup"><span data-stu-id="69c86-132">Create a BI Semantic Model Connection to a PowerPivot Workbook</span></span>](create-a-bi-semantic-model-connection-to-a-power-pivot-workbook.md)  
  
 [<span data-ttu-id="69c86-133">Create a BI Semantic Model Connection to a Tabular Model Database</span><span class="sxs-lookup"><span data-stu-id="69c86-133">Create a BI Semantic Model Connection to a Tabular Model Database</span></span>](create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)  
  
## <a name="see-also"></a><span data-ttu-id="69c86-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="69c86-134">See Also</span></span>  
 <span data-ttu-id="69c86-135">[PowerPivot BI 의미 체계 모델 연결 &#40;. bism&#41;](power-pivot-bi-semantic-model-connection-bism.md) </span><span class="sxs-lookup"><span data-stu-id="69c86-135">[PowerPivot BI Semantic Model Connection &#40;.bism&#41;](power-pivot-bi-semantic-model-connection-bism.md) </span></span>  
 [<span data-ttu-id="69c86-136">Excel 또는 Reporting Services에서 BI 의미 체계 모델 연결 사용</span><span class="sxs-lookup"><span data-stu-id="69c86-136">Use a BI Semantic Model Connection in Excel or Reporting Services</span></span>](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md)  
  
  
