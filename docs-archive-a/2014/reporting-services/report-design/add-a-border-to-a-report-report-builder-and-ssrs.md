---
title: 보고서에 테두리 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 81412f94-2991-4e58-bc05-5ccc0cbf2a75
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bf4a0c2c117774a0f3b25ca0644796fd067bc971
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739381"
---
# <a name="add-a-border-to-a-report-report-builder-and-ssrs"></a><span data-ttu-id="f012f-102">보고서에 테두리 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="f012f-102">Add a Border to a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f012f-103">선이나 사각형을 추가하지 않고 머리글, 바닥글 및 보고서 본문 자체에 테두리를 추가하여 보고서에 테두리를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f012f-103">You can add a border to a report by adding borders to the headers, footers, and report body themselves, without adding lines or rectangles.</span></span>  
  
 <span data-ttu-id="f012f-104">페이지 머리글과 바닥글에 표시되는 보고서 테두리를 추가할 경우 보고서의 첫 페이지와 마지막 페이지에서 머리글과 바닥글을 표시하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="f012f-104">If you add a report border that appears on the page header and footer, do not suppress the header and footer on the first and last pages of the report.</span></span> <span data-ttu-id="f012f-105">이를 표시할 경우 보고서의 첫 페이지와 마지막 페이지의 위쪽이나 아래쪽에서 테두리가 잘려서 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f012f-105">If you do, the border may appear cut off at the top or bottom of the first and last pages of the report.</span></span> <span data-ttu-id="f012f-106">자세한 내용은 [페이지 머리글 및 바닥글&#40;보고서 작성기 및 SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f012f-106">For more information, see [Page Headers and Footers &#40;Report Builder and SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-border-to-a-report"></a><span data-ttu-id="f012f-107">보고서에 테두리를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="f012f-107">To add a border to a report</span></span>  
  
1.  <span data-ttu-id="f012f-108">머리글에서 임의의 항목 바깥쪽 머리글을 마우스 오른쪽 단추로 클릭하고 **머리글 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f012f-108">Right-click in the header outside any items in the header, and click **Header Properties**.</span></span> <span data-ttu-id="f012f-109">**테두리** 탭에서 원하는 스타일의 왼쪽, 위쪽 및 오른쪽 테두리를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f012f-109">On the **Border** tab, add a left, top, and right border with the style you want.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f012f-110">보고서에 머리글을 사용하지 않는 경우 보고서 본문 주위에만 테두리를 추가하거나 **삽입** 탭에서 머리글을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f012f-110">If you do not use headers in your report, you can place borders around just the report body, or you can add headers from the **Insert** tab.</span></span>  
  
2.  <span data-ttu-id="f012f-111">디자인 화면에서 임의의 항목 바깥쪽 본문을 마우스 오른쪽 단추로 클릭하고 **본문 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f012f-111">Right-click in the body outside any items on the design surface, and click **Body Properties**.</span></span> <span data-ttu-id="f012f-112">**테두리** 탭에서 원하는 스타일의 왼쪽 및 오른쪽 테두리를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f012f-112">On the **Border** tab, add a left and right border with the style you want.</span></span>  
  
3.  <span data-ttu-id="f012f-113">바닥글에서 임의의 항목 바깥쪽 바닥글을 마우스 오른쪽 단추로 클릭하고 **바닥글 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f012f-113">Right-click in the footer outside any items in the footer, and click **Footer Properties**.</span></span> <span data-ttu-id="f012f-114">**테두리** 탭에서 원하는 스타일의 왼쪽, 아래쪽 및 오른쪽 테두리를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f012f-114">On the **Border** tab, add a left, bottom, and right border with the style you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f012f-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f012f-115">See Also</span></span>  
 [<span data-ttu-id="f012f-116">사각형 및 선&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f012f-116">Rectangles and Lines &#40;Report Builder and SSRS&#41;</span></span>](rectangles-and-lines-report-builder-and-ssrs.md)  
  
  
