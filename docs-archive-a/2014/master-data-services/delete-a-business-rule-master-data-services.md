---
title: 비즈니스 규칙 삭제(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting business rules [Master Data Services]
- business rules [Master Data Services], deleting
ms.assetid: b97aa4f9-569f-451d-ad62-65b81f980299
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8e6db486f71634cf025c57eabbedeeb9efdbc437
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728415"
---
# <a name="delete-a-business-rule-master-data-services"></a><span data-ttu-id="963c2-102">비즈니스 규칙 삭제(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="963c2-102">Delete a Business Rule (Master Data Services)</span></span>
  <span data-ttu-id="963c2-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서는 비즈니스 규칙이 더 이상 필요하지 않으면 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="963c2-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete a business rule when it is no longer needed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="963c2-104">비즈니스 규칙을 삭제하지 않고 제외하면 비즈니스 규칙에 대해 데이터 유효성을 검사하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="963c2-104">You can prevent data from being validated against a business rule by excluding it, rather than deleting it.</span></span> <span data-ttu-id="963c2-105">자세한 내용은 [비즈니스 규칙 제외&#40;Master Data Services&#41;](exclude-a-business-rule-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="963c2-105">For more information, see [Exclude a Business Rule &#40;Master Data Services&#41;](exclude-a-business-rule-master-data-services.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="963c2-106">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="963c2-106">Prerequisites</span></span>  
 <span data-ttu-id="963c2-107">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="963c2-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="963c2-108">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="963c2-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="963c2-109">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="963c2-109">You must be a model administrator.</span></span> <span data-ttu-id="963c2-110">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="963c2-110">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-a-business-rule"></a><span data-ttu-id="963c2-111">비즈니스 규칙을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="963c2-111">To delete a business rule</span></span>  
  
1.  <span data-ttu-id="963c2-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="963c2-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="963c2-113">메뉴 모음에서 **관리** 를 가리키고 **비즈니스 규칙**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="963c2-113">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="963c2-114">**비즈니스 규칙 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="963c2-114">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="963c2-115">**엔터티** 목록에서 엔터티를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="963c2-115">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="963c2-116">**멤버 유형** 목록에서 비즈니스 규칙을 적용할 멤버 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="963c2-116">From the **Member Type** list, select a type of member for the business rule to apply to.</span></span>  
  
6.  <span data-ttu-id="963c2-117">**특성** 목록에서 특성을 선택하거나 기본값인 **모두**를 그대로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="963c2-117">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="963c2-118">표 형태에서 삭제할 비즈니스 규칙 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="963c2-118">In the grid, click the row for the business rule you want to delete.</span></span>  
  
8.  <span data-ttu-id="963c2-119">**선택한 비즈니스 규칙 삭제**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="963c2-119">Click **Delete selected business rule**.</span></span>  
  
9. <span data-ttu-id="963c2-120">확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="963c2-120">In the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="963c2-121">**상태** 열의 값은 **삭제 보류 중**입니다.</span><span class="sxs-lookup"><span data-stu-id="963c2-121">The value in the **Status** column is **Deletion pending**.</span></span>  
  
10. <span data-ttu-id="963c2-122">**비즈니스 규칙 게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="963c2-122">Click **Publish business rules**.</span></span>  
  
11. <span data-ttu-id="963c2-123">확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="963c2-123">In the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="963c2-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="963c2-124">See Also</span></span>  
 <span data-ttu-id="963c2-125">[비즈니스 규칙 &#40;MDS(Master Data Services)를 제외&#41;](exclude-a-business-rule-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="963c2-125">[Exclude a Business Rule &#40;Master Data Services&#41;](exclude-a-business-rule-master-data-services.md) </span></span>  
 <span data-ttu-id="963c2-126">[비즈니스 규칙을 만들고 게시 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="963c2-126">[Create and Publish a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md) </span></span>  
 [<span data-ttu-id="963c2-127">비즈니스 규칙&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="963c2-127">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
