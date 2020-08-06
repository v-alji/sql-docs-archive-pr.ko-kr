---
title: 이미지, 입력란, 사각형 및 선(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: aa7ad08f-dd49-401e-9619-522e27055bb9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2fb9a47bb3b8d68d48be42f8f0a2adddfc3ba130
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730180"
---
# <a name="images-text-boxes-rectangles-and-lines-report-builder-and-ssrs"></a><span data-ttu-id="9a797-102">이미지, 입력란, 사각형 및 선(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="9a797-102">Images, Text Boxes, Rectangles, and Lines (Report Builder and SSRS)</span></span>
  <span data-ttu-id="9a797-103">보고서에 테이블, 행렬 및 차트 같은 데이터 영역 외에도 이미지, 입력란 및 사각형과 같은 다른 보고서 항목을 사용하여 시각적 효과를 추가하고 핵심 정보를 강조 표시하거나 관련 정보를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a797-103">In addition to data regions like tables, matrices, and charts, reports use other report items like images, text boxes, and rectangles to add visual interest, highlight key information, or provide related information.</span></span> <span data-ttu-id="9a797-104">또한 보고서 항목의 서식을 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a797-104">You can change the formatting of a report item.</span></span> <span data-ttu-id="9a797-105">예를 들어 테두리 또는 패딩을 추가하거나 초기 표시 유형 또는 방향을 변경하거나 항목의 정확한 크기와 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a797-105">For example, you can add a border or padding, change the initial visibility or direction, or specify an exact size and location for the item.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a><span data-ttu-id="9a797-106">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="9a797-106">In This Section</span></span>  
 [<span data-ttu-id="9a797-107">입력란&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9a797-107">Text Boxes &#40;Report Builder and SSRS&#41;</span></span>](text-boxes-report-builder-and-ssrs.md)  
 <span data-ttu-id="9a797-108">입력란은 보고서의 어느 위치에나 배치될 수 있으며 레이블, 필드 또는 계산된 데이터를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a797-108">Text boxes can be placed anywhere on a report and can contain labels, fields, or calculated data.</span></span> <span data-ttu-id="9a797-109">보고서를 볼 때 입력란에 표시되는 값은 식을 사용하여 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9a797-109">You use expressions to define the value to display in a text box when you view a report.</span></span>  
  
 <span data-ttu-id="9a797-110">테이블 또는 행렬의 각 셀에는 독립 실행형 입력란과 같은 방법으로 서식을 지정할 수 있는 입력란이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a797-110">Every cell in a table or matrix is also a text box, which you can format in the same way that you format stand-alone text boxes.</span></span>  
  
 [<span data-ttu-id="9a797-111">사각형 및 선&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9a797-111">Rectangles and Lines &#40;Report Builder and SSRS&#41;</span></span>](rectangles-and-lines-report-builder-and-ssrs.md)  
 <span data-ttu-id="9a797-112">**선** 은 가로, 세로 또는 대각선 방향으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a797-112">**Lines** display horizontally, vertically, or diagonally.</span></span> <span data-ttu-id="9a797-113">선은 시작점과 끝점으로 정의되며 다양한 스타일을 적용할 수 있습니다(예: 두께 및 색).</span><span class="sxs-lookup"><span data-stu-id="9a797-113">A line is defined with a start and end point and can have various styles (for example, weight and color) assigned to it.</span></span> <span data-ttu-id="9a797-114">또한 선에는 연결된 데이터가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9a797-114">A line has no data associated with it.</span></span>  
  
 <span data-ttu-id="9a797-115">**사각형** 은 다른 보고서 항목의 컨테이너로 사용하거나 그래픽 요소로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a797-115">**Rectangles** can be used as a graphical element, or as a container for other report items.</span></span> <span data-ttu-id="9a797-116">그래픽 요소로 사용하는 경우 직사각형은 선과 같은 속성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="9a797-116">As a graphical element, a rectangle has the same properties as a line.</span></span> <span data-ttu-id="9a797-117">컨테이너로 사용할 경우 사각형은 안에 포함된 모든 보고서 항목에 대한 부모 컨테이너 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a797-117">As a container, a rectangle acts as a parent container for all report items inside it.</span></span> <span data-ttu-id="9a797-118">부모 컨테이너에 보고서 항목을 배치하면 각 보고서 페이지에 보고서 항목이 표시되는 방법을 제어하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a797-118">Placing report items in a parent container helps control how they appear on each report page.</span></span>  
  
 [<span data-ttu-id="9a797-119">이미지&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9a797-119">Images &#40;Report Builder and SSRS&#41;</span></span>](images-report-builder-and-ssrs.md)  
 <span data-ttu-id="9a797-120">이미지는 보고서의 이진 이미지 데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9a797-120">Images display binary image data in a report.</span></span> <span data-ttu-id="9a797-121">이미지의 원본은 사용자가 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9a797-121">You provide the source for the image.</span></span> <span data-ttu-id="9a797-122">원본은 웹 서버에 저장된 이미지에 대한 URL 참조, 포함된 이미지 데이터에 대한 참조, 데이터베이스의 이진 이미지 데이터에 대한 참조일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a797-122">The source can be a URL reference to an image stored on a Web server, a reference to embedded image data, or a reference to binary image data in a database.</span></span> <span data-ttu-id="9a797-123">보고서 작성기 및 보고서 디자이너에서는 .bmp, .jpeg, .gif 및 .png 파일을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9a797-123">Report Builder and Report Designer support .bmp, .jpeg, .gif, and .png files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a797-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9a797-124">See Also</span></span>  
 [<span data-ttu-id="9a797-125">보고서 항목 서식 지정&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9a797-125">Formatting Report Items &#40;Report Builder and SSRS&#41;</span></span>](formatting-report-items-report-builder-and-ssrs.md)  
  
  
