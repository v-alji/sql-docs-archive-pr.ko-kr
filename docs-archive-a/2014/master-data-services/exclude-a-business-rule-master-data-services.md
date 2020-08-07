---
title: 비즈니스 규칙 제외(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], excluding
ms.assetid: bdbc9df0-23f7-40b9-8aba-4445c1482580
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 317964dcbc7b2cbe212c415b3aa4f9f1a0743301
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731839"
---
# <a name="exclude-a-business-rule-master-data-services"></a><span data-ttu-id="ef2c8-102">비즈니스 규칙 제외(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="ef2c8-102">Exclude a Business Rule (Master Data Services)</span></span>
  <span data-ttu-id="ef2c8-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서는 비즈니스 규칙을 영구적으로 삭제하지는 않되 규칙에 대해 데이터 유효성을 검사하지 않으려면 규칙을 제외합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2c8-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], exclude a business rule when you do not want to delete the rule permanently, but you do not want to validate data against it.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ef2c8-104">필수 조건</span><span class="sxs-lookup"><span data-stu-id="ef2c8-104">Prerequisites</span></span>  
 <span data-ttu-id="ef2c8-105">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="ef2c8-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="ef2c8-106">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2c8-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="ef2c8-107">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2c8-107">You must be a model administrator.</span></span> <span data-ttu-id="ef2c8-108">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ef2c8-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-exclude-a-business-rule"></a><span data-ttu-id="ef2c8-109">비즈니스 규칙을 제외하려면</span><span class="sxs-lookup"><span data-stu-id="ef2c8-109">To exclude a business rule</span></span>  
  
1.  <span data-ttu-id="ef2c8-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2c8-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="ef2c8-111">메뉴 모음에서 **관리** 를 가리키고 **비즈니스 규칙**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2c8-111">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="ef2c8-112">**비즈니스 규칙 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2c8-112">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="ef2c8-113">**엔터티** 목록에서 엔터티를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2c8-113">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="ef2c8-114">**멤버 유형** 목록에서 멤버 유형을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2c8-114">From the **Member Type** list, select a type of member.</span></span>  
  
6.  <span data-ttu-id="ef2c8-115">**특성** 목록에서 특성을 선택하거나 기본값인 **모두**를 그대로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2c8-115">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="ef2c8-116">표에서 비즈니스 규칙에 대 한 행의 **제외** 열에 있는 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2c8-116">In the grid, in the row for the business rule, select the check box in the **Exclude** column.</span></span> <span data-ttu-id="ef2c8-117">**상태** 열의 값은 **제외 보류 중**입니다.</span><span class="sxs-lookup"><span data-stu-id="ef2c8-117">The value in the **Status** column is **Exclusion pending**.</span></span>  
  
8.  <span data-ttu-id="ef2c8-118">**비즈니스 규칙 게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2c8-118">Click **Publish business rules**.</span></span>  
  
9. <span data-ttu-id="ef2c8-119">확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2c8-119">In the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="ef2c8-120">**상태** 열의 값은 **제외**됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef2c8-120">The value in the **Status** column is **Excluded**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef2c8-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ef2c8-121">See Also</span></span>  
 <span data-ttu-id="ef2c8-122">[비즈니스 규칙을 삭제 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/delete-a-business-rule-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="ef2c8-122">[Delete a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-business-rule-master-data-services.md) </span></span>  
 <span data-ttu-id="ef2c8-123">[비즈니스 규칙을 만들고 게시 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="ef2c8-123">[Create and Publish a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md) </span></span>  
 [<span data-ttu-id="ef2c8-124">비즈니스 규칙&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ef2c8-124">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
