---
title: 페이지 번호 또는 기타 보고서 속성 표시(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c7d95245-4709-4d04-acb4-59bf71e60d97
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: efc3d5d5de11af1fcdfefc52ed12d5057ee12668
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650733"
---
# <a name="display-page-numbers-or-other-report-properties-report-builder-and-ssrs"></a><span data-ttu-id="12052-102">페이지 번호 또는 기타 보고서 속성 표시(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="12052-102">Display Page Numbers or Other Report Properties (Report Builder and SSRS)</span></span>
  <span data-ttu-id="12052-103">보고서의 페이지 머리글이나 바닥글에 페이지 번호, 보고서 제목, 파일 이름 및 기타 보고서 속성을 간단히 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12052-103">It's easy to add page numbers, a report title, file name, and other report properties to the page headers or footers of your report.</span></span> <span data-ttu-id="12052-104">다음은 보고서 데이터 창의 기본 제공 필드 폴더에 필드로 저장되는 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="12052-104">These properties are stored as fields in the Built-in Fields folder in the Report Data pane:</span></span>  
  
-   <span data-ttu-id="12052-105">실행 시간</span><span class="sxs-lookup"><span data-stu-id="12052-105">Execution time</span></span>  
  
-   <span data-ttu-id="12052-106">페이지 번호</span><span class="sxs-lookup"><span data-stu-id="12052-106">Page number</span></span>  
  
-   <span data-ttu-id="12052-107">보고서 폴더</span><span class="sxs-lookup"><span data-stu-id="12052-107">Report folder</span></span>  
  
-   <span data-ttu-id="12052-108">보고서 이름</span><span class="sxs-lookup"><span data-stu-id="12052-108">Report name</span></span>  
  
-   <span data-ttu-id="12052-109">보고서 서버 URL</span><span class="sxs-lookup"><span data-stu-id="12052-109">Report server URL</span></span>  
  
-   <span data-ttu-id="12052-110">전체 페이지 수</span><span class="sxs-lookup"><span data-stu-id="12052-110">Total pages</span></span>  
  
-   <span data-ttu-id="12052-111">사용자 ID</span><span class="sxs-lookup"><span data-stu-id="12052-111">User ID</span></span>  
  
-   <span data-ttu-id="12052-112">언어</span><span class="sxs-lookup"><span data-stu-id="12052-112">Language</span></span>  
  
 <span data-ttu-id="12052-113">페이지 번호의 경우 번호 뒤에 "페이지"라는 단어를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12052-113">For a page number, you may want to add the word "Page" before the number.</span></span> <span data-ttu-id="12052-114">총 페이지 수도 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12052-114">You may also want to show the total number of pages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="12052-115">바닥글에 총 페이지 수를 추가할 경우 보고서를 실행하거나 미리 볼 때 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12052-115">Adding the total number of pages to the footer may slow performance when you run or preview your report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-page-number-or-other-report-properties"></a><span data-ttu-id="12052-116">페이지 번호 또는 기타 보고서 속성을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="12052-116">To add a page number or other report properties</span></span>  
  
1.  <span data-ttu-id="12052-117">보고서 데이터 창에서 기본 제공 필드 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="12052-117">In the Report Data pane, expand the Built-in Fields folder.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="12052-118">보고서 데이터 창이 표시되지 않는 경우 보기 탭에서 **보고서 데이터**를 선택하세요.</span><span class="sxs-lookup"><span data-stu-id="12052-118">If you don't see the Report Data pane, on the View tab, check **Report Data**.</span></span>  
  
2.  <span data-ttu-id="12052-119">**페이지 번호** 필드를 보고서 데이터 창에서 보고서 머리글이나 바닥글로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="12052-119">Drag the **Page Number** field from the Report Data pane to the report header or footer.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="12052-120">페이지 바닥글은 보고서에 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="12052-120">The page footer is added to the report automatically.</span></span> <span data-ttu-id="12052-121">페이지 머리글을 추가하려면 **삽입** 탭에서 **머리글**을 클릭한 다음 **머리글 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12052-121">To add a page header, on the **Insert** tab, click **Header**, and then click **Add Header**.</span></span>  
    >   
    >  <span data-ttu-id="12052-122">간단한 식 [&PageNumber]가 포함된 입력란이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="12052-122">A text box that contains the simple expression [&PageNumber] is added.</span></span>  
  
### <a name="to-add-the-word-page-before-the-page-number"></a><span data-ttu-id="12052-123">페이지 번호 뒤에 "페이지"라는 단어를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="12052-123">To add the word "Page" before the page number</span></span>  
  
1.  <span data-ttu-id="12052-124">[&PageNumber]가 들어 있는 입력란을 마우스 오른쪽 단추로 클릭한 다음 **식**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12052-124">Right-click the text box that contains [&PageNumber] and click **Expressions**.</span></span>  
  
     <span data-ttu-id="12052-125">**다음에 대한 식 설정: 값** 입력란에 식 =Globals!PageNumber가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="12052-125">The **Set Expression for: Value** text box contains the expression =Globals!PageNumber.</span></span>  
  
2.  <span data-ttu-id="12052-126">= 기호 뒤에 커서를 두고 `"Page " &`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="12052-126">Place the cursor after the = sign and type `"Page " &`.</span></span>  
  
     <span data-ttu-id="12052-127">식이 ="Page "&Globals!PageNumber로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="12052-127">The expression is now  ="Page "&Globals!PageNumber</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-add-total-number-of-pages-after-the-page-number"></a><span data-ttu-id="12052-128">페이지 번호 뒤에 총 페이지 수를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="12052-128">To add total number of pages after the page number</span></span>  
  
1.  <span data-ttu-id="12052-129">식이 들어 있는 입력란을 마우스 오른쪽 단추로 클릭한 다음 **식**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12052-129">Right click the text box with the expression and click **Expressions**.</span></span>  
  
2.  <span data-ttu-id="12052-130">식 끝에 **&" of "&** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="12052-130">Type **&" of "&** at the end of the expression.</span></span>  
  
3.  <span data-ttu-id="12052-131">범주 창에서 **기본 제공 필드** 를 확장한 다음 **TotalPages**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12052-131">In the Category pane, expand **Built-in Fields** and double-click **TotalPages**.</span></span>  
  
     <span data-ttu-id="12052-132">식이 ="Page "&Globals!PageNumber &" of "&Globals!TotalPages로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="12052-132">The expression is now ="Page "&Globals!PageNumber &" of "&Globals!TotalPages</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="12052-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="12052-133">See Also</span></span>  
 <span data-ttu-id="12052-134">[페이지 머리글 및 바닥글&#40;보고서 작성기 및 SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="12052-134">[Page Headers and Footers &#40;Report Builder and SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="12052-135">입력란의 텍스트 서식 지정&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="12052-135">Format Text in a Text Box &#40;Report Builder and SSRS&#41;</span></span>](format-text-in-a-text-box-report-builder-and-ssrs.md)  
  
  
