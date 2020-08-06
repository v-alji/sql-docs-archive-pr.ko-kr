---
title: 데이터 바인딩된 이미지 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: df4c38d4-bfcc-41c4-aa6d-952ca6fd7a2e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ea85bdcd6eab04ff51c879a9e790b6e12f73a771
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639312"
---
# <a name="add-a-data-bound-image-report-builder-and-ssrs"></a><span data-ttu-id="380f4-102">데이터 바인딩된 이미지 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="380f4-102">Add a Data-Bound Image (Report Builder and SSRS)</span></span>
  <span data-ttu-id="380f4-103">데이터베이스에 저장된 이미지에 대한 참조를 보고서에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="380f4-103">A report can include a reference to an image that is stored in a database.</span></span> <span data-ttu-id="380f4-104">이러한 이미지를 *데이터 바인딩된 이미지*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="380f4-104">Such an image is known as a *data-bound image*.</span></span> <span data-ttu-id="380f4-105">제품 목록에서 제품 이름과 함께 표시되는 그림을 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="380f4-105">The pictures that appear alongside product names in a product list are examples of data-bound images.</span></span>  
  
 <span data-ttu-id="380f4-106">데이터 바인딩된 이미지를 페이지 머리글이나 페이지 바닥글에 추가하려면 별도의 단계가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="380f4-106">Adding a data-bound image to a page header or page footer requires additional steps.</span></span> <span data-ttu-id="380f4-107">자세한 내용은 [페이지 머리글 및 바닥글&#40;보고서 작성기 및 SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="380f4-107">For more information, see [Page Headers and Footers &#40;Report Builder and SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-data-bound-image"></a><span data-ttu-id="380f4-108">데이터 바인딩된 이미지를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="380f4-108">To add a data-bound image</span></span>  
  
1.  <span data-ttu-id="380f4-109">보고서 디자인 뷰에서 데이터 원본 연결이 있는 테이블과 이진 이미지 데이터가 포함된 필드가 있는 데이터 세트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="380f4-109">In report design view, create a table with a data source connection and a dataset with a field that contains binary image data.</span></span> <span data-ttu-id="380f4-110">자세한 내용은 [테이블&#40;보고서 작성기 및 SSRS&#41;](tables-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="380f4-110">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="380f4-111">테이블에 열을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="380f4-111">Insert a column in your table.</span></span> <span data-ttu-id="380f4-112">자세한 내용은 [열 삽입 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="380f4-112">For more information, see [Insert or Delete a Column &#40;Report Builder and SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).</span></span>  
  
3.  <span data-ttu-id="380f4-113">**삽입** 메뉴에서 **이미지**를 클릭한 다음 새 열의 데이터 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="380f4-113">On the **Insert** menu, click **Image**, and then click in the data row of the new column.</span></span>  
  
4.  <span data-ttu-id="380f4-114">**이미지 속성** 대화 상자의 일반 페이지에 있는 **이름** 입력란에 이름을 입력하거나 기본값을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="380f4-114">On the General page of the **Image Properties** dialog box, type a name in the **Name** text box or accept the default.</span></span>  
  
5.  <span data-ttu-id="380f4-115">(옵션) HTML용으로 렌더링된 보고서에서 사용자가 마우스로 이미지를 가리킬 때 표시할 텍스트를 **도구 설명** 입력란에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="380f4-115">(Optional) In the **Tooltip** text box, type text to display when the user hovers over the image in the report rendered for HTML.</span></span>  
  
6.  <span data-ttu-id="380f4-116">**이미지 원본 선택**에서 **데이터베이스**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="380f4-116">In **Select the image source**, select **Database**.</span></span>  
  
7.  <span data-ttu-id="380f4-117">**이 필드 사용**에서 보고서의 이미지를 포함하는 필드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="380f4-117">In **Use this Field**, select the field that contains images in your report.</span></span>  
  
8.  <span data-ttu-id="380f4-118">**이 MIME 형식 사용**에서 이미지의 MIME 형식 또는 파일 형식(예: bmp)을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="380f4-118">In **Use this MIME type**, select the MIME type, or file format, of the image-for example, bmp.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="380f4-119">이미지 자리 표시자가 보고서 디자인 화면에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="380f4-119">An image placeholder appears on the report design surface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="380f4-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="380f4-120">See Also</span></span>  
 <span data-ttu-id="380f4-121">[이미지&#40;보고서 작성기 및 SSRS&#41;](images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="380f4-121">[Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="380f4-122">[보고서에 이미지 포함&#40;보고서 작성기 및 SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="380f4-122">[Embed an Image in a Report &#40;Report Builder and SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="380f4-123">[외부 이미지 추가&#40;보고서 작성기 및 SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="380f4-123">[Add an External Image &#40;Report Builder and SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="380f4-124">이미지 속성 대화 상자, 일반&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="380f4-124">Image Properties Dialog Box, General &#40;Report Builder and SSRS&#41;</span></span>](../image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
