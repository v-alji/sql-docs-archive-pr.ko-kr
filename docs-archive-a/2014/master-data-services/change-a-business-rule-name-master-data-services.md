---
title: 비즈니스 규칙 이름 변경(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], changing name
ms.assetid: cffcae43-a208-443f-9f43-a0ec9e05f79c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0e99047ffe27332aaed4514394ca2357942a1297
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661230"
---
# <a name="change-a-business-rule-name-master-data-services"></a><span data-ttu-id="69eb5-102">비즈니스 규칙 이름 변경(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="69eb5-102">Change a Business Rule Name (Master Data Services)</span></span>
  <span data-ttu-id="69eb5-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서는 할당된 이름이 비즈니스 요구에 맞지 않으면 비즈니스 규칙 이름을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69eb5-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], change a business rule name when the name assigned does not meet your business needs.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="69eb5-104">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="69eb5-104">Prerequisites</span></span>  
 <span data-ttu-id="69eb5-105">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="69eb5-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="69eb5-106">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69eb5-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="69eb5-107">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69eb5-107">You must be a model administrator.</span></span> <span data-ttu-id="69eb5-108">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="69eb5-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="69eb5-109">비즈니스 규칙이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69eb5-109">A business rule must exist.</span></span> <span data-ttu-id="69eb5-110">자세한 내용은 [비즈니스 규칙 만들기 및 게시&#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69eb5-110">For more information, see [Create and Publish a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md).</span></span>  
  
### <a name="to-change-the-name-of-a-business-rule"></a><span data-ttu-id="69eb5-111">비즈니스 규칙의 이름을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="69eb5-111">To change the name of a business rule</span></span>  
  
1.  <span data-ttu-id="69eb5-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69eb5-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="69eb5-113">메뉴 모음에서 **관리** 를 가리키고 **비즈니스 규칙**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69eb5-113">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="69eb5-114">**비즈니스 규칙 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="69eb5-114">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="69eb5-115">**엔터티** 목록에서 엔터티를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="69eb5-115">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="69eb5-116">**멤버 유형** 목록에서 멤버 유형을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="69eb5-116">From the **Member Type** list, select a type of member.</span></span>  
  
6.  <span data-ttu-id="69eb5-117">**특성** 목록에서 특성을 선택하거나 기본값인 **모두**를 그대로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="69eb5-117">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="69eb5-118">표 형태의 비즈니스 규칙 행에서 **이름** 필드를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="69eb5-118">In the grid, in the row for the business rule, double-click the **Name** field.</span></span>  
  
8.  <span data-ttu-id="69eb5-119">비즈니스 규칙의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="69eb5-119">Type a name for the business rule.</span></span>  
  
9. <span data-ttu-id="69eb5-120">Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="69eb5-120">Press ENTER.</span></span>  
  
10. <span data-ttu-id="69eb5-121">**비즈니스 규칙 게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69eb5-121">Click **Publish business rules**.</span></span>  
  
11. <span data-ttu-id="69eb5-122">확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69eb5-122">On the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="69eb5-123">규칙의 상태가 **활성**으로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="69eb5-123">The rule's status changes to **Active**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69eb5-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="69eb5-124">See Also</span></span>  
 [<span data-ttu-id="69eb5-125">비즈니스 규칙&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="69eb5-125">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
