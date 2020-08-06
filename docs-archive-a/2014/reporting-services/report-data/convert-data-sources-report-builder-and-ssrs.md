---
title: 포함 된 데이터 원본에서 공유 데이터 원본으로 변환 (보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], embedded
- data sources [Reporting Services], shared
ms.assetid: 0e099c7e-8c03-43eb-9ea3-76e52d9ebbe3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5827bab564b58e7a2b7922f01a33f550a6f523f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647456"
---
# <a name="convert-a-data-source-from-embedded-to-shared-report-builder-and-ssrs"></a><span data-ttu-id="3a93c-102">포함된 데이터 원본에서 공유 데이터 원본으로 변환(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="3a93c-102">Convert a Data Source from Embedded to Shared (Report Builder and SSRS)</span></span>
  <span data-ttu-id="3a93c-103">보고서 데이터 창의 각 데이터 원본은 보고서에 관련 및 포함되거나 공유됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a93c-103">Each data source in the Report Data pane is embedded and specific to the report or is shared.</span></span> <span data-ttu-id="3a93c-104">보고서 작성기에서 공유 데이터 원본은 보고서 서버 또는 SharePoint 사이트의 게시된 공유 데이터 원본을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="3a93c-104">In Report Builder, a shared data source points to a published shared data source on a report server or SharePoint site.</span></span> <span data-ttu-id="3a93c-105">보고서 디자이너에서 공유 데이터 원본은 솔루션 탐색기의 **공유 데이터 원본** 폴더에 있는 공유 데이터 원본을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="3a93c-105">In Report Designer, a shared data source points to a shared data source in the **Shared Data Sources** folder in Solution Explorer.</span></span>  
  
 <span data-ttu-id="3a93c-106">포함된 데이터 원본과 공유 데이터 원본의 차이점에 대한 자세한 내용은 [포함된 데이터 연결 및 공유 데이터 연결 또는 데이터 원본&#40;보고서 작성기 및 SSRS&#41;](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a93c-106">For more information about the differences between embedded and shared data sources, see [Embedded and Shared Data Connections or Data Sources &#40;Report Builder and SSRS&#41;](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="3a93c-107">공유 데이터 원본을 만드는 방법에 대한 자세한 내용은 [포함된 데이터 원본 또는 공유 데이터 원본 만들기&#40;SSRS&#41;](../create-an-embedded-or-shared-data-source-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a93c-107">For more information on how to create a shared data source, see [Create an Embedded or Shared Data Source &#40;SSRS&#41;](../create-an-embedded-or-shared-data-source-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="report-designer"></a><span data-ttu-id="3a93c-108">보고서 디자이너</span><span class="sxs-lookup"><span data-stu-id="3a93c-108">Report Designer</span></span>  
  
#### <a name="to-convert-a-data-source-from-embedded-to-shared"></a><span data-ttu-id="3a93c-109">포함된 데이터 원본에서 공유 데이터 원본으로 변환</span><span class="sxs-lookup"><span data-stu-id="3a93c-109">To convert a data source from embedded to shared</span></span>  
  
-   <span data-ttu-id="3a93c-110">보고서 데이터 창에서 데이터 원본을 마우스 오른쪽 단추로 클릭한 다음 **공유 데이터 원본으로 변환**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a93c-110">In the Report Data pane, right-click the data source, and then click **Convert to Shared Data Source**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3a93c-111">보고서 데이터 창이 표시되지 않는 경우 **보기** 메뉴에서 **보고서 데이터**를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="3a93c-111">If the Report Data pane is not visible, on the **View** menu, click **Report Data**.</span></span> <span data-ttu-id="3a93c-112">해당 창이 부동 창으로 열리는 경우 도킹할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a93c-112">If the pane opens as a floating window, you can dock it.</span></span> <span data-ttu-id="3a93c-113">자세한 내용은 [보고서 디자이너에서 보고서 데이터 창 도킹&#40;SSRS&#41;](../tools/dock-the-report-data-pane-in-report-designer-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a93c-113">For more information, see [Dock the Report Data Pane in Report Designer &#40;SSRS&#41;](../tools/dock-the-report-data-pane-in-report-designer-ssrs.md).</span></span>  
  
     <span data-ttu-id="3a93c-114">보고서 데이터 창에서 데이터 원본 아이콘이 공유 데이터 원본 아이콘으로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a93c-114">In the Report Data pane, the data source icon changes to the shared data source icon.</span></span> <span data-ttu-id="3a93c-115">솔루션 탐색기의 **공유 데이터 원본** 폴더에 같은 이름의 공유 데이터 원본이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="3a93c-115">In Solution Explorer, a shared data source with the same name appears under the **Shared Data Source** folder.</span></span>  
  
### <a name="to-convert-a-data-source-from-shared-to-embedded"></a><span data-ttu-id="3a93c-116">공유 데이터 원본에서 포함된 데이터 원본으로 변환</span><span class="sxs-lookup"><span data-stu-id="3a93c-116">To convert a data source from shared to embedded</span></span>  
  
-   <span data-ttu-id="3a93c-117">보고서 데이터 창에서 데이터 원본을 마우스 오른쪽 단추로 클릭하여 **데이터 원본 속성** 대화 상자를 열고 **포함된 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a93c-117">In the Report Data pane, right-click the data source, open the **Data Source Properties** dialog box, and then click **Embedded Connection**.</span></span> <span data-ttu-id="3a93c-118">필요한 정보를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3a93c-118">Enter the required information.</span></span>  
  
     <span data-ttu-id="3a93c-119">보고서 데이터 창에서 데이터 원본 아이콘이 공유 데이터 원본 아이콘으로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a93c-119">In the Report Data pane, the data source icon changes to the shared data source icon.</span></span>  
  
## <a name="report-builder"></a><span data-ttu-id="3a93c-120">보고서 작성기</span><span class="sxs-lookup"><span data-stu-id="3a93c-120">Report Builder</span></span>  
  
#### <a name="to-convert-a-data-source-from-embedded-to-shared"></a><span data-ttu-id="3a93c-121">포함된 데이터 원본에서 공유 데이터 원본으로 변환</span><span class="sxs-lookup"><span data-stu-id="3a93c-121">To convert a data source from embedded to shared</span></span>  
  
-   <span data-ttu-id="3a93c-122">보고서 데이터 창에서 데이터 원본을 마우스 오른쪽 단추로 클릭하여 **데이터 원본 속성** 대화 상자를 열고 **포함된 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a93c-122">In the Report Data pane, right-click the data source to open the **Data Source Properties** dialog box, and then click **Embedded Connection**.</span></span> <span data-ttu-id="3a93c-123">필요한 정보를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3a93c-123">Enter the required information.</span></span>  
  
     <span data-ttu-id="3a93c-124">보고서 데이터 창에서 데이터 원본 아이콘이 공유 데이터 원본 아이콘으로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a93c-124">In the Report Data pane, the data source icon changes to the shared data source icon.</span></span>  
  
#### <a name="to-convert-a-data-source-from-shared-to-embedded"></a><span data-ttu-id="3a93c-125">공유 데이터 원본에서 포함된 데이터 원본으로 변환</span><span class="sxs-lookup"><span data-stu-id="3a93c-125">To convert a data source from shared to embedded</span></span>  
  
-   <span data-ttu-id="3a93c-126">보고서 데이터 창에서 데이터 원본을 마우스 오른쪽 단추로 클릭하여 **데이터 원본 속성** 대화 상자를 열고 **포함된 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a93c-126">In the Report Data pane, right-click the data source, open the **Data Source Properties** dialog box, and then click **Embedded Connection**.</span></span> <span data-ttu-id="3a93c-127">필요한 정보를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3a93c-127">Enter the required information.</span></span>  
  
     <span data-ttu-id="3a93c-128">보고서 데이터 창에서 데이터 원본 아이콘이 공유 데이터 원본 아이콘으로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a93c-128">In the Report Data pane, the data source icon changes to the shared data source icon.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a93c-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3a93c-129">See Also</span></span>  
 <span data-ttu-id="3a93c-130">[보고서 데이터 원본 관리](manage-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="3a93c-130">[Manage Report Data Sources](manage-report-data-sources.md) </span></span>  
 [<span data-ttu-id="3a93c-131">보고서 서비스의 데이터 연결, 데이터 원본 및 연결 문자열</span><span class="sxs-lookup"><span data-stu-id="3a93c-131">Data Connections, Data Sources, and Connection Strings in Reporting Services</span></span>](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
