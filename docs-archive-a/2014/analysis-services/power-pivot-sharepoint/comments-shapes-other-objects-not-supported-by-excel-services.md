---
title: 다음 기능은 Excel 서비스에서 지원 되지 않으며 표시 되지 않거나 부분적 으로만 표시 될 수 있습니다. 주석, 셰이프 또는 기타 개체 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ade92e15-dfbf-496b-9378-a00bd83ba750
author: minewiskan
ms.author: owend
ms.openlocfilehash: 67c2989ab89f242fdce2ca64f3c2f361e17d49ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732084"
---
# <a name="the-following-features-are-not-supported-by-excel-services-and-may-not-display-or-may-display-only-partially-comments-shapes-or-other-objects"></a><span data-ttu-id="19a74-102">다음 기능은 브라우저에서 지원되지 않으며 표시되지 않거나 부분적으로만 표시될 수 있습니다. 메모, 도형 또는 기타 개체</span><span class="sxs-lookup"><span data-stu-id="19a74-102">The following features are not supported by Excel Services and may not display or may display only partially: Comments, Shapes, or other objects</span></span>
  <span data-ttu-id="19a74-103">이 오류는 PowerPivot 필드 목록에서 PowerPivot 통합 문서에 슬라이서를 추가할 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="19a74-103">This error occurs when you add Slicers to a PowerPivot workbook from a PowerPivot Field List.</span></span>  
  
## <a name="details"></a><span data-ttu-id="19a74-104">세부 정보</span><span class="sxs-lookup"><span data-stu-id="19a74-104">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="19a74-105">적용 대상</span><span class="sxs-lookup"><span data-stu-id="19a74-105">Applies to</span></span>|<span data-ttu-id="19a74-106">SharePoint용 PowerPivot</span><span class="sxs-lookup"><span data-stu-id="19a74-106">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="19a74-107">제품 버전</span><span class="sxs-lookup"><span data-stu-id="19a74-107">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="19a74-108">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19a74-108">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="19a74-109">원인</span><span class="sxs-lookup"><span data-stu-id="19a74-109">Cause</span></span>|<span data-ttu-id="19a74-110">Excel Web Access가 PowerPivot 필드 목록에서 통합 문서에 추가된 슬라이서의 위치 지정 및 서식을 제어하는 데 사용되는 도형 개체를 렌더링할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="19a74-110">Excel Web Access cannot render the Shape object used to control positioning and formatting of Slicers added to a workbook from the PowerPivot Field List.</span></span>|  
|<span data-ttu-id="19a74-111">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="19a74-111">Message Text</span></span>|<span data-ttu-id="19a74-112">다음 기능은 브라우저에서 지원되지 않으며 표시되지 않거나 부분적으로만 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19a74-112">The following features are not supported by Excel Services and may not display or may display only partially:</span></span><br /><br /> <span data-ttu-id="19a74-113">메모, 도형 또는 기타 개체</span><span class="sxs-lookup"><span data-stu-id="19a74-113">Comments, Shapes, or other objects</span></span><br /><br /> <span data-ttu-id="19a74-114">외부 데이터 쿼리와 같은 일부 기능은 Microsoft Excel 클라이언트 버전에서만 새로 고칠 수 있는 캐시된 데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="19a74-114">Some features, such as external data queries, display cached data which can only be refreshed in Microsoft Excel.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="19a74-115">설명</span><span class="sxs-lookup"><span data-stu-id="19a74-115">Explanation</span></span>  
 <span data-ttu-id="19a74-116">브라우저에서 PowerPivot 통합 문서를 열고 **지원 되지 않는 기능, 지원 되지 않는 기능**에 대 한 **세부 정보** 단추를 클릭 하면 Excel 웹 액세스에이 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19a74-116">Excel Web Access shows this error when you open a PowerPivot workbook in a browser and you click the **Details** button for the message, **Unsupported Features This workbook may not display as intended**.</span></span>  
  
 <span data-ttu-id="19a74-117">이 오류가 발생하는 원인은 PowerPivot 통합 문서에 포함된 슬라이서의 레이아웃을 Excel의 숨겨진 도형 개체가 제어하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="19a74-117">This error occurs because the PowerPivot workbook contains Slicers whose layout is controlled by a hidden Shape object in Excel.</span></span> <span data-ttu-id="19a74-118">도형 개체는 가로 및 세로 배치 시 슬라이서의 위치 지정 및 서식을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="19a74-118">The Shape object controls the formatting and positioning of the Slicers in horizontal and vertical placements.</span></span>  
  
 <span data-ttu-id="19a74-119">Excel 서비스에서는 도형 개체를 렌더링할 수 없지만 개체가 숨겨져 있으므로 이는 문제가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19a74-119">Excel Services cannot render a Shape object, but because the object is hidden, the fact that it does not render is not an issue.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="19a74-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="19a74-120">User Action</span></span>  
 <span data-ttu-id="19a74-121">이 오류는 무시해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19a74-121">This error can be ignored.</span></span> <span data-ttu-id="19a74-122">**확인** 을 클릭하여 오류 메시지를 닫고 통합 문서 및 슬라이서를 계속 사용해도 아무런 문제가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="19a74-122">Click **OK** to close the error message and proceed to use the workbook and Slicers with no problem.</span></span>  
  
  
