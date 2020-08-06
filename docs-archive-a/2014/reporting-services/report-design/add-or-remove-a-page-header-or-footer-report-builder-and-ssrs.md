---
title: 페이지 머리글/바닥글 추가 또는 제거(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 72988623-fee8-4a05-9f72-8fcb8e668576
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b29db3f72323c460360c872a0f60d13a808e3e05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735036"
---
# <a name="add-or-remove-a-page-header-or-footer-report-builder-and-ssrs"></a><span data-ttu-id="4e46e-102">페이지 머리글/바닥글 추가 또는 제거(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="4e46e-102">Add or Remove a Page Header or Footer (Report Builder and SSRS)</span></span>
  <span data-ttu-id="4e46e-103">페이지 머리글 또는 바닥글에 정적 텍스트, 이미지, 선, 사각형 및 테두리를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e46e-103">You can add static text, images, lines, rectangles, and borders to page headers or footers.</span></span> <span data-ttu-id="4e46e-104">머리글 또는 바닥글에 변수나 계산된 데이터를 포함하려면 입력란에 식 및 데이터 바인딩된 이미지를 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="4e46e-104">You can place expressions and data-bound images in a textbox if you want variable or computed data in a header or footer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4e46e-105">각 렌더링 확장 프로그램은 페이지 머리글과 바닥글을 서로 다르게 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="4e46e-105">Each rendering extension processes page headers and footers differently.</span></span> <span data-ttu-id="4e46e-106">자세한 내용은 [페이지 머리글 및 바닥글&#40;보고서 작성기 및 SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) 및 [Reporting Services의 페이지 매김&#40;보고서 작성기 및 SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4e46e-106">For more information, see [Page Headers and Footers &#40;Report Builder and SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) and [Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-page-header-or-footer"></a><span data-ttu-id="4e46e-107">페이지 머리글/바닥글을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="4e46e-107">To add a page header or footer</span></span>  
  
1.  <span data-ttu-id="4e46e-108">보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4e46e-108">Open a report.</span></span>  
  
2.  <span data-ttu-id="4e46e-109">디자인 화면에서 보고서를 마우스 오른쪽 단추로 클릭하고 **삽입**을 가리킨 다음 **머리글** 또는 **바닥글**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4e46e-109">On the design surface, right-click the report, point to **Insert**, and then click **Header** or **Footer**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4e46e-110">**머리글** 및 **바닥글** 옵션은 보고서에 아직 머리글 또는 바닥글이 포함되어 있지 않은 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e46e-110">The **Header** and **Footer** options appear only when a header or footer is not already part of the report.</span></span>  
  
### <a name="to-configure-a-page-header-or-footer"></a><span data-ttu-id="4e46e-111">페이지 머리글/바닥글을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="4e46e-111">To configure a page header or footer</span></span>  
  
1.  <span data-ttu-id="4e46e-112">디자인 화면에서 페이지 머리글 또는 바닥글을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4e46e-112">On the design surface, right-click the page header or footer.</span></span>  
  
2.  <span data-ttu-id="4e46e-113">**삽입**을 가리킨 후 다음 항목 중 하나를 클릭하여 머리글 또는 바닥글 영역에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4e46e-113">Point to **Insert**, and then click one of the following items to add it to the header or footer area:</span></span>  
  
    -   <span data-ttu-id="4e46e-114">**입력란**</span><span class="sxs-lookup"><span data-stu-id="4e46e-114">**Textbox**</span></span>  
  
    -   <span data-ttu-id="4e46e-115">**선**</span><span class="sxs-lookup"><span data-stu-id="4e46e-115">**Line**</span></span>  
  
    -   <span data-ttu-id="4e46e-116">**사각형**</span><span class="sxs-lookup"><span data-stu-id="4e46e-116">**Rectangle**</span></span>  
  
    -   <span data-ttu-id="4e46e-117">**이미지**</span><span class="sxs-lookup"><span data-stu-id="4e46e-117">**Image**</span></span>  
  
3.  <span data-ttu-id="4e46e-118">페이지 머리글을 마우스 오른쪽 단추로 클릭하고 **머리글 속성** 을 클릭하여 테두리, 배경 이미지 또는 색을 추가하거나 머리글의 너비를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="4e46e-118">Right-click the page header, and then click **Header Properties** to add borders, background images, or colors, or to adjust the width of the header.</span></span> <span data-ttu-id="4e46e-119">그런 후 **OK**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4e46e-119">Then click **OK**.</span></span>  
  
4.  <span data-ttu-id="4e46e-120">페이지 바닥글을 마우스 오른쪽 단추로 클릭하고 **바닥글 속성** 을 클릭하여 테두리, 배경 이미지 또는 색을 추가하거나 바닥글의 너비를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="4e46e-120">Right-click the page footer, and then click **Footer Properties** to add borders, background images, or colors, or to adjust the width of the footer.</span></span> <span data-ttu-id="4e46e-121">그런 후 **OK**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4e46e-121">Then click **OK**.</span></span>  
  
### <a name="to-remove-a-page-header-or-footer"></a><span data-ttu-id="4e46e-122">페이지 머리글/바닥글을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="4e46e-122">To remove a page header or footer</span></span>  
  
1.  <span data-ttu-id="4e46e-123">보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4e46e-123">Open a report.</span></span>  
  
2.  <span data-ttu-id="4e46e-124">디자인 화면에서 페이지 머리글 또는 바닥글을 마우스 오른쪽 단추로 클릭하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4e46e-124">On the design surface, right-click the page header or footer, and then click **Delete**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4e46e-125">페이지 머리글 또는 바닥글을 제거하면 보고서에서 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e46e-125">When you remove a page header or footer, you delete it from the report.</span></span> <span data-ttu-id="4e46e-126">이전에 페이지 머리글 또는 바닥글에 추가한 항목은 이후에 페이지 머리글 또는 바닥글을 다시 추가해도 더 이상 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4e46e-126">Any items that you previously added to the page header or footer will not reappear if you subsequently add the header or footer again.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e46e-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4e46e-127">See Also</span></span>  
 [<span data-ttu-id="4e46e-128">페이지 머리글 및 바닥글&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4e46e-128">Page Headers and Footers &#40;Report Builder and SSRS&#41;</span></span>](page-headers-and-footers-report-builder-and-ssrs.md)  
  
  
