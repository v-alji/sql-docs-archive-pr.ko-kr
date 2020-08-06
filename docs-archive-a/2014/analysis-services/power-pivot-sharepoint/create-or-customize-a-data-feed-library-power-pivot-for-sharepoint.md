---
title: 데이터 피드 라이브러리 만들기 또는 사용자 지정 (SharePoint용 PowerPivot) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data feed library
- data feeds [Analysis Services with SharePoint]
ms.assetid: 699fbeb9-42ab-436b-beba-214db51ea3dd
author: minewiskan
ms.author: owend
ms.openlocfilehash: b86f63c1af094ea9e8a2a1149debeac387bccbf0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730928"
---
# <a name="create-or-customize-a-data-feed-library-powerpivot-for-sharepoint"></a><span data-ttu-id="33ae4-102">데이터 피드 라이브러리 만들기 또는 사용자 지정(SharePoint용 PowerPivot)</span><span class="sxs-lookup"><span data-stu-id="33ae4-102">Create or Customize a Data Feed Library (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="33ae4-103">*데이터 피드 라이브러리* 는 Atom 데이터 서비스 문서(.atomsvc)를 등록 및 공유할 수 있도록 해 주는 특수 용도의 SharePoint 라이브러리입니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-103">A *data feed library* is a special-purpose SharePoint library that enables you to register and share Atom data service documents (.atomsvc).</span></span> <span data-ttu-id="33ae4-104">이러한 문서는 Atom 데이터 피드 형식을 지원하는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 통합 문서나 기타 클라이언트 애플리케이션에 XML 데이터 피드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-104">These documents provide XML data feeds to [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] workbooks or other client applications that support the Atom data feed format.</span></span> <span data-ttu-id="33ae4-105">데이터 피드 라이브러리는 다음과 같은 기능을 제공하므로 다른 SharePoint 라이브러리와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-105">A data feed library is different from other SharePoint libraries because it gives you the ability to:</span></span>

-   <span data-ttu-id="33ae4-106">특정 피드에 대한 HTTP 연결을 지정하는 데 사용되는 *데이터 서비스 문서*만들기 또는 편집</span><span class="sxs-lookup"><span data-stu-id="33ae4-106">Create or edit a *data service document*, used to specify an HTTP connection to a specific feed.</span></span>

-   <span data-ttu-id="33ae4-107">중앙 위치에서 데이터 서비스 문서 공유 및 관리</span><span class="sxs-lookup"><span data-stu-id="33ae4-107">Share and manage data service documents in a central location.</span></span>

-   <span data-ttu-id="33ae4-108">서비스 문서를 동일한 라이브러리에 저장 된 다른 문서와 쉽게 구별할 수 있도록 아이콘으로 데이터 서비스 문서를 시각적으로 식별 합니다. ![GMNI_IconDataFeed](../media/gmni-icondatafeed.gif "GMNI_IconDataFeed")</span><span class="sxs-lookup"><span data-stu-id="33ae4-108">Visually identify data service documents by an icon, so that you can easily distinguish service documents from other documents stored in the same library: ![GMNI_IconDataFeed](../media/gmni-icondatafeed.gif "GMNI_IconDataFeed")</span></span>

 <span data-ttu-id="33ae4-109">데이터 피드 라이브러리에는 항상 데이터 서비스 문서(.atomsvc) 파일이 포함되어 있고 데이터 피드 자체는 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-109">A data feed library always contains data service document (.atomsvc) files, and never the data feed itself.</span></span> <span data-ttu-id="33ae4-110">정적 XML 데이터로 구성되는 데이터 피드와 달리 데이터 서비스 문서는 반복 가능한 가져오기 작업에 재사용 가능한 연결 정보를 제공하여 요청에 따라 피드를 생성하는 서비스 또는 애플리케이션에 대한 URL을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-110">Unlike a data feed, which consists of static XML data, the data service document specifies a URL to a service or application that generates a feed upon request, providing reusable connection information for repeatable import operations.</span></span>

 <span data-ttu-id="33ae4-111">이 항목에는 다음과 같은 섹션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-111">This topic contains the following sections:</span></span>

 [<span data-ttu-id="33ae4-112">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="33ae4-112">Prerequisites</span></span>](#prereq)

 [<span data-ttu-id="33ae4-113">새 데이터 피드 라이브러리 만들기</span><span class="sxs-lookup"><span data-stu-id="33ae4-113">Create a New Data Feed Library</span></span>](#createlib)

 [<span data-ttu-id="33ae4-114">모든 라이브러리에 데이터 피드 콘텐츠 형식 추가</span><span class="sxs-lookup"><span data-stu-id="33ae4-114">Add the Data Feed Content Type to Any Library</span></span>](#addtolib)

##  <a name="prerequisites"></a><a name="prereq"></a> <span data-ttu-id="33ae4-115">필수 조건</span><span class="sxs-lookup"><span data-stu-id="33ae4-115">Prerequisites</span></span>
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] <span data-ttu-id="33ae4-116">기능 통합을 활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-116">feature integration must be activated for the sites for which you are creating the data feed library.</span></span> <span data-ttu-id="33ae4-117">데이터 피드 라이브러리 템플릿 유형을 사용할 수 없는 경우 이 사전 요구 사항이 충족되지 않았을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-117">If the data feed library template type is not available, the most likely cause is that this prerequisite has not been met.</span></span> <span data-ttu-id="33ae4-118">자세한 내용은 [중앙 관리에서 사이트 모음에 대 한 PowerPivot 기능 통합 활성화](activate-power-pivot-integration-for-site-collections-in-ca.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="33ae4-118">For more information, see [Activate PowerPivot Feature Integration for Site Collections in Central Administration](activate-power-pivot-integration-for-site-collections-in-ca.md).</span></span>

 <span data-ttu-id="33ae4-119">라이브러리를 만들려면 사이트 소유자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-119">You must be a site owner to create the library.</span></span>

##  <a name="create-a-new-data-feed-library"></a><a name="createlib"></a> <span data-ttu-id="33ae4-120">새 데이터 피드 라이브러리 만들기</span><span class="sxs-lookup"><span data-stu-id="33ae4-120">Create a New Data Feed Library</span></span>
 <span data-ttu-id="33ae4-121">데이터 피드 라이브러리 만들기는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 통합 문서에 대해 데이터 피드를 사용하도록 설정하는 첫 번째 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-121">Creating a data feed library is the first step to enabling data feeds for [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] workbooks.</span></span> <span data-ttu-id="33ae4-122">데이터 피드 라이브러리는 데이터 서비스 문서에 대한 애플리케이션 및 관리 페이지를 제공하므로, 새 문서를 만들려면 이 라이브러리가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-122">Because a data feed library provides application and management pages for data service documents, you must have this library in place before you can create a new document.</span></span>

 <span data-ttu-id="33ae4-123">데이터 피드 라이브러리는 데이터 서비스 문서의 속성과 동작을 정의하는 미리 구성된 *데이터 서비스 문서 콘텐츠 형식* 과 기본 제공 템플릿을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-123">A data feed library is based on a built-in template and a preconfigured *data service document content type* that defines properties and behaviors for a data service document.</span></span>

1.  <span data-ttu-id="33ae4-124">페이지 왼쪽 위 모퉁이에 있는 **사이트 작업** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-124">Click **Site Actions** at the top left corner of the page.</span></span>

2.  <span data-ttu-id="33ae4-125">**기타 옵션**...을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-125">Click **More Options**...</span></span>

3.  <span data-ttu-id="33ae4-126">라이브러리에서 **데이터 피드 라이브러리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-126">Under Libraries, click **Data Feed Library**.</span></span>

4.  <span data-ttu-id="33ae4-127">이름, 설명, 시작 및 버전 기본 설정을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-127">Type the name, description, launch, and version preferences.</span></span> <span data-ttu-id="33ae4-128">사용자가 이 라이브러리를 데이터 서비스 문서에 대한 스토리지로 식별하는 데 도움이 되는 설명 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-128">Include descriptive information to help users identify this library as storage for data service documents.</span></span>

5.  <span data-ttu-id="33ae4-129">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-129">Click **Create**.</span></span>

 <span data-ttu-id="33ae4-130">데이터 피드 라이브러리에 대한 링크가 현재 사이트의 탐색 빠른 실행 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-130">A link to the data feed library will appear in the navigation Quick Launch pane for the current site.</span></span>

 <span data-ttu-id="33ae4-131">라이브러리를 만든 후 해당 라이브러리를 사용하여 데이터 서비스 문서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-131">After you create a library, you can use it to create data service documents.</span></span> <span data-ttu-id="33ae4-132">자세한 내용은 [데이터 피드 사용 &#40;SharePoint용 PowerPivot&#41;](use-data-feeds-power-pivot-for-sharepoint.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="33ae4-132">For more information, see [Use Data Feeds &#40;PowerPivot for SharePoint&#41;](use-data-feeds-power-pivot-for-sharepoint.md).</span></span>

##  <a name="add-the-data-feed-content-type-to-any-library"></a><a name="addtolib"></a> <span data-ttu-id="33ae4-133">라이브러리에 데이터 피드 콘텐츠 형식 추가</span><span class="sxs-lookup"><span data-stu-id="33ae4-133">Add the Data Feed Content Type to Any Library</span></span>
 <span data-ttu-id="33ae4-134">전용 데이터 피드 라이브러리를 만들지 않지만 SharePoint 사이트에서 데이터 서비스 문서를 만들고 관리하려는 경우 데이터 서비스 문서(.atomsvc) 파일을 공유하는 데 사용할 라이브러리에 대한 데이터 서비스 문서 콘텐츠 형식을 수동으로 추가하여 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-134">If you do not want to create a dedicated data feed library, but you still want to create and manage data service documents from a SharePoint site, you can manually add and configure the data service document content type for any library that you will use to share data service document (.atomsvc) files.</span></span>

 <span data-ttu-id="33ae4-135">콘텐츠 형식을 추가하고 구성하려면 최소한 목록 관리 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-135">You must have at least the Manage Lists permission to add and configure a content type.</span></span> <span data-ttu-id="33ae4-136">이 권한은 디자인 권한 수준 이상에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-136">This permission is built into the Design permission level and above.</span></span>

 <span data-ttu-id="33ae4-137">데이터 피드 등록 문서를 만들거나 편집하려는 라이브러리마다 다음 단계를 반복해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-137">The following steps must be repeated for each library in which you want to create or edit data feed registration documents.</span></span>

#### <a name="step-1-enable-content-type-management"></a><span data-ttu-id="33ae4-138">1단계: 콘텐츠 형식 관리 사용</span><span class="sxs-lookup"><span data-stu-id="33ae4-138">Step 1: Enable Content Type Management</span></span>

1.  <span data-ttu-id="33ae4-139">여러 콘텐츠 형식을 사용할 문서 라이브러리를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-139">Open the document library for which you want to enable multiple content types.</span></span>

2.  <span data-ttu-id="33ae4-140">SharePoint 리본의 라이브러리 도구에서 **라이브러리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-140">On the SharePoint ribbon, in Library Tools, click **Library**.</span></span>

3.  <span data-ttu-id="33ae4-141">**설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-141">Click **Settings**.</span></span>

4.  <span data-ttu-id="33ae4-142">**라이브러리 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-142">Click **Library Settings**.</span></span>

5.  <span data-ttu-id="33ae4-143">일반 설정에서 **고급 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-143">In General Settings, click **Advanced settings**.</span></span>

6.  <span data-ttu-id="33ae4-144">콘텐츠 형식의 "콘텐츠 형식 관리를 허용하시겠습니까?"</span><span class="sxs-lookup"><span data-stu-id="33ae4-144">In Content Types, in the "Allow management of content types?"</span></span> <span data-ttu-id="33ae4-145">섹션에서 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-145">section, click **Yes**.</span></span>

7.  <span data-ttu-id="33ae4-146">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-146">Click **OK**.</span></span>

#### <a name="step-2-add-the-data-service-document-content-type"></a><span data-ttu-id="33ae4-147">2단계: 데이터 서비스 문서 콘텐츠 형식 추가</span><span class="sxs-lookup"><span data-stu-id="33ae4-147">Step 2: Add the Data Service Document Content Type</span></span>

1.  <span data-ttu-id="33ae4-148">콘텐츠 형식 섹션에서 **기존 사이트 콘텐츠 형식에서 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-148">In the Content Types section, click **Add from existing site content types**.</span></span> <span data-ttu-id="33ae4-149">이 페이지가 표시되지 않는 경우 사이트로 돌아가서 라이브러리 도구에서 **라이브러리** 를 클릭한 다음 **라이브러리 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-149">If you do not see this page, go back to the site, click **Library** in Library Tools, and then click **Library Settings**.</span></span>

2.  <span data-ttu-id="33ae4-150">콘텐츠 형식에서 **기존 사이트 콘텐츠 형식에서 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-150">In Content Types, click **Add from existing site content types**.</span></span>

3.  <span data-ttu-id="33ae4-151">사이트 콘텐츠 형식 선택에서 **비즈니스 인텔리전스**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-151">In Select site content types from:, select **Business Intelligence**.</span></span>

4.  <span data-ttu-id="33ae4-152">사용 가능한 사이트 콘텐츠 형식에서 **데이터 서비스 문서**를 클릭한 다음 **추가** 를 클릭하여 선택한 콘텐츠 형식을 목록을 추가할 콘텐츠 형식으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-152">In Available Site Content Types, click **Data Service Document**, and then click **Add** to move the selected content type to the Content types to add list.</span></span>

5.  <span data-ttu-id="33ae4-153">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-153">Click **OK**.</span></span>

#### <a name="step-3-verify-data-service-document-configuration"></a><span data-ttu-id="33ae4-154">3단계: 데이터 서비스 문서 구성 확인</span><span class="sxs-lookup"><span data-stu-id="33ae4-154">Step 3: Verify Data Service Document Configuration</span></span>

1.  <span data-ttu-id="33ae4-155">사이트 홈 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-155">Open the site home page.</span></span>

2.  <span data-ttu-id="33ae4-156">라이브러리를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-156">Open the library.</span></span>

3.  <span data-ttu-id="33ae4-157">SharePoint 리본에서 **문서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-157">On the SharePoint ribbon, click **Documents**.</span></span>

4.  <span data-ttu-id="33ae4-158">새 문서에서 아래쪽 화살표를 클릭하고 **데이터 서비스 문서**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-158">Click the down arrow on New Document, and select **Data Service Document**.</span></span> <span data-ttu-id="33ae4-159">새 데이터 서비스 문서 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="33ae4-159">The New Data Service Document page should appear.</span></span>

## <a name="see-also"></a><span data-ttu-id="33ae4-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="33ae4-160">See Also</span></span>
 <span data-ttu-id="33ae4-161">[데이터 피드 &#40;SharePoint용 PowerPivot&#41;](use-data-feeds-power-pivot-for-sharepoint.md) [Powerpivot 데이터 피드 라이브러리 삭제](delete-a-power-pivot-data-feed-library.md) Powerpivot [서버 관리 및 구성 중앙 관리](power-pivot-server-administration-and-configuration-in-central-administration.md) [powerpivot 데이터 피드](power-pivot-data-feeds.md)</span><span class="sxs-lookup"><span data-stu-id="33ae4-161">[Use Data Feeds &#40;PowerPivot for SharePoint&#41;](use-data-feeds-power-pivot-for-sharepoint.md) [Delete a PowerPivot Data Feed Library](delete-a-power-pivot-data-feed-library.md) [PowerPivot Server Administration and Configuration in Central Administration](power-pivot-server-administration-and-configuration-in-central-administration.md) [PowerPivot Data Feeds](power-pivot-data-feeds.md)</span></span>


