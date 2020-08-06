---
title: 처리 진행률 대화 상자 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.processprogress.f1
ms.assetid: f3bd5278-3a83-4fd9-9903-e81bdd4b6892
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4e436eeab21a37ae174a5003c01e77c05240238b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741355"
---
# <a name="process-progress-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="55707-102">처리 진행률 대화 상자(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="55707-102">Process Progress Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="55707-103">**및** 의 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 처리 진행률 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 대화 상자를 사용하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서의 처리 상황을 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55707-103">Use the **Process Progress** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to monitor processing in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="55707-104">**처리 진행률** 대화 상자는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체 처리를 시작할 때 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="55707-104">The **Process Progress** dialog box appears when processing begins on an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span>  
  
## <a name="options"></a><span data-ttu-id="55707-105">옵션</span><span class="sxs-lookup"><span data-stu-id="55707-105">Options</span></span>  
 <span data-ttu-id="55707-106">**상태 트리 뷰**</span><span class="sxs-lookup"><span data-stu-id="55707-106">**Status tree view**</span></span>  
 <span data-ttu-id="55707-107">시작 시간, 중지 시간 및 처리 정보를 비롯하여 처리 중인 개체에 대한 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스의 상태 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="55707-107">Displays status messages from the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance regarding the objects being processed, including start time, stop time, and progress information.</span></span> <span data-ttu-id="55707-108">상태 메시지의 상세 정보를 클립보드에 복사하려면 항목을 마우스 오른쪽 단추로 클릭한 다음 **복사**를 선택하고, **자세히 보기** 대화 상자를 표시하려면 항목을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="55707-108">Right-click an item and select **Copy** to copy the details of a status message to the clipboard, or double-click an item to display the **View Details** dialog box.</span></span> <span data-ttu-id="55707-109">**자세히 보기** 대화 상자에 대한 자세한 내용은 [자세히 보기 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](view-details-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="55707-109">For more information about the **View Details** dialog box, see [View Details Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](view-details-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="55707-110">**상태 설명**</span><span class="sxs-lookup"><span data-stu-id="55707-110">**Status description**</span></span>  
 <span data-ttu-id="55707-111">처리 중인 작업의 현재 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="55707-111">Displays the current status of the processing operation.</span></span>  
  
 <span data-ttu-id="55707-112">**중지**</span><span class="sxs-lookup"><span data-stu-id="55707-112">**Stop**</span></span>  
 <span data-ttu-id="55707-113">처리 작업을 중지하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="55707-113">Click to stop the processing operation.</span></span>  
  
 <span data-ttu-id="55707-114">**다시 처리**</span><span class="sxs-lookup"><span data-stu-id="55707-114">**Reprocess**</span></span>  
 <span data-ttu-id="55707-115">**처리 진행률** 대화 상자에 표시된 처리 작업을 반복하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="55707-115">Click to repeat the processing operation that displayed the **Process Progress** dialog box.</span></span>  
  
 <span data-ttu-id="55707-116">**세부 정보 보기**</span><span class="sxs-lookup"><span data-stu-id="55707-116">**View Details**</span></span>  
 <span data-ttu-id="55707-117">**자세히 보기** 대화 상자를 열어 **상태 트리 뷰**에서 선택한 항목의 상세 정보를 표시하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="55707-117">Click to open the **View Details** dialog box and display details regarding the item selected in **Status tree view**.</span></span> <span data-ttu-id="55707-118">**자세히 보기** 대화 상자에 대한 자세한 내용은 [자세히 보기 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](view-details-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="55707-118">For more information about the **View Details** dialog box, see [View Details Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](view-details-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55707-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="55707-119">See Also</span></span>  
 <span data-ttu-id="55707-120">[Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="55707-120">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="55707-121">다차원 모델 개체 처리</span><span class="sxs-lookup"><span data-stu-id="55707-121">Multidimensional Model Object Processing</span></span>](multidimensional-models/processing-a-multidimensional-model-analysis-services.md)  
  
  
