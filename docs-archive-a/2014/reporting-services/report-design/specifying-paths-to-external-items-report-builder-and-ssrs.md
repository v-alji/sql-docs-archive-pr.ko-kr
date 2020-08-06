---
title: 외부 항목에 대한 경로 지정(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4fe513da-f3c5-479c-9fec-8662b91a0d6d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 097a3566f914e7810039ee07bc3d3bf3185d7f06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639274"
---
# <a name="specifying-paths-to-external-items-report-builder-and-ssrs"></a><span data-ttu-id="44bce-102">외부 항목에 대한 경로 지정(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="44bce-102">Specifying Paths to External Items (Report Builder and SSRS)</span></span>
  <span data-ttu-id="44bce-103">드릴스루 보고서, 하위 보고서 및 이미지 파일과 같이 보고서 서버에 저장되어 있고 보고서 정의 파일 외부에 있는 항목을 참조하기 위해 보고서 항목 속성에 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44bce-103">You specify paths in report item properties to reference items such as drillthrough reports, subreports, and image files that are external to the report definition file and are stored on a report server.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
> [!NOTE]  
>  <span data-ttu-id="44bce-104">보고서 작성기에서 항목 경로는 보고서 서버의 항목을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44bce-104">In Report Builder, paths to items must specify items on a report server.</span></span> <span data-ttu-id="44bce-105">파일 시스템에 있는 항목의 경로는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="44bce-105">Paths to items on a file system are not supported.</span></span> <span data-ttu-id="44bce-106">항목이 있는 보고서 서버에 연결된 경우에만 해당 항목을 사용하는 보고서를 미리 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44bce-106">You can preview a report that uses these items only if you are connected to the report server where the items are located.</span></span>  
  
 <span data-ttu-id="44bce-107">동작, 하위 보고서 또는 이미지에 대한 대화 상자에서 외부 항목에 대한 경로를 지정할 때는 직접 보고서 서버를 찾아서 항목을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44bce-107">When you specify a path for an external item in a dialog box for actions, subreports, or images, you can browse directly to the report server and select the item.</span></span> <span data-ttu-id="44bce-108">드릴스루 보고서 또는 하위 보고서를 지정할 때는 직접 항목을 찾아서 선택하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="44bce-108">Browsing to an item and selecting it directly is the recommended way to specify a drillthrough report or subreport.</span></span> <span data-ttu-id="44bce-109">이 방식을 사용할 경우 보고서 또는 하위 보고서 매개 변수를 지정할 때 드롭다운 목록에 올바른 매개 변수 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="44bce-109">That way the correct parameter names will be available in a drop-down list when you specify report or subreport parameters.</span></span> <span data-ttu-id="44bce-110">항목 경로를 다른 항목에 대한 경로로 변경할 때는 필요에 따라 올바른 매개 변수 이름과 값을 수동으로 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44bce-110">When you change an item path to point to a different item, you must manually update the correct parameter names and values as needed.</span></span>  
  
 <span data-ttu-id="44bce-111">기본 모드로 구성된 보고서 서버의 경우 .rdl 파일 확장명 없이 드릴스루 보고서 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="44bce-111">On a report server configured in native mode, specify a drillthrough report name without the file extension .rdl.</span></span>  
  
 <span data-ttu-id="44bce-112">SharePoint 통합 모드로 구성된 보고서 서버의 경우 파일 확장명 .rdl을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44bce-112">On a report server configured in SharePoint integrated mode, you must include the file extension .rdl.</span></span> <span data-ttu-id="44bce-113">경로는 다음 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44bce-113">The path can be one of the following:</span></span>  
  
-   <span data-ttu-id="44bce-114">**주 보고서에서 항목에 대한 상대 경로.**</span><span class="sxs-lookup"><span data-stu-id="44bce-114">**A relative path to the item from the main report.**</span></span> <span data-ttu-id="44bce-115">예를 들면 ../AllSubreports/Subreport1과 같은 형태입니다.</span><span class="sxs-lookup"><span data-stu-id="44bce-115">For example, ../AllSubreports/Subreport1.</span></span> <span data-ttu-id="44bce-116">이 예에서 **..**</span><span class="sxs-lookup"><span data-stu-id="44bce-116">In this example, the **..**</span></span> <span data-ttu-id="44bce-117">는 주 보고서가 있는 폴더의 상위 폴더를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="44bce-117">indicates the folder above the folder where the main report is located.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="44bce-118">보고서가 보고서 작성기 안에서 실행될 때는 상대 경로가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="44bce-118">Relative paths are not supported when the report is run inside Report Builder.</span></span> <span data-ttu-id="44bce-119">외부 항목에 대한 상대 경로를 사용하는 보고서를 보려면 보고서를 보고서 서버에 저장하고 이 위치에서 보고서를 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="44bce-119">To view a report that uses relative paths to external items, save the report to the report server, and run the report from there</span></span>  
  
-   <span data-ttu-id="44bce-120">**항목에 대한 전체 경로.**</span><span class="sxs-lookup"><span data-stu-id="44bce-120">**A full path to the item.**</span></span>  
  
    -   <span data-ttu-id="44bce-121">**보고서 서버에서:** 경로는 홈 폴더인 **/** 부터 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="44bce-121">**On a report server:** The path starts from **/**, the Home folder.</span></span> <span data-ttu-id="44bce-122">예를 들면 /Reports/AllSubreports/Subreport1과 같은 형태입니다.</span><span class="sxs-lookup"><span data-stu-id="44bce-122">For example, /Reports/AllSubreports/Subreport1.</span></span>  
  
    -   <span data-ttu-id="44bce-123">**SharePoint 사이트에서:** 항목의 전체 URL 및 파일 확장명 .rdl과 함께 보고서 이름을 식에 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44bce-123">**On a SharePoint site:** You must specify the report name in an expression, with the full URL of the item and the file extension .rdl.</span></span> <span data-ttu-id="44bce-124">`="http://server/site/library/folder/Report1.rdl"`)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="44bce-124">For example, `="http://server/site/library/folder/Report1.rdl"`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44bce-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="44bce-125">See Also</span></span>  
 <span data-ttu-id="44bce-126">[외부 이미지 추가&#40;보고서 작성기 및 SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="44bce-126">[Add an External Image &#40;Report Builder and SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="44bce-127">[하위 보고서 및 매개 변수 추가&#40;보고서 작성기 및 SSRS&#41;](add-a-subreport-and-parameters-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="44bce-127">[Add a Subreport and Parameters &#40;Report Builder and SSRS&#41;](add-a-subreport-and-parameters-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="44bce-128">보고서에 드릴스루 동작 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="44bce-128">Add a Drillthrough Action on a Report &#40;Report Builder and SSRS&#41;</span></span>](add-a-drillthrough-action-on-a-report-report-builder-and-ssrs.md)  
  
  
