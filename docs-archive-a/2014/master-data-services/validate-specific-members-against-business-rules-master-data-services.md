---
title: 비즈니스 규칙에 대해 특정 멤버 유효성 검사(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- applying business rules [Master Data Services]
- business rules [Master Data Services], applying to select members
ms.assetid: 2288ef43-5392-47ea-b651-ec25e5692a14
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 18af83146679eb77638dfbc98b31f198dc8e07b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650154"
---
# <a name="validate-specific-members-against-business-rules-master-data-services"></a><span data-ttu-id="d42cc-102">비즈니스 규칙에 대해 특정 멤버 유효성 검사(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d42cc-102">Validate Specific Members against Business Rules (Master Data Services)</span></span>
  <span data-ttu-id="d42cc-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 비즈니스 규칙에 따라 멤버의 하위 집합을 업데이트하거나 유효성을 검사하려는 경우 비즈니스 규칙을 선택적으로 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="d42cc-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], apply business rules selectively when you want to update or validate subsets of members against business rules.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d42cc-104">모델 버전의 모든 멤버에 비즈니스 규칙을 적용하려면 [비즈니스 규칙에 대해 버전 유효성 검사&#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d42cc-104">If you want to apply business rules to all members in a version of a model, see [Validate a Version against Business Rules &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d42cc-105">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="d42cc-105">Prerequisites</span></span>  
 <span data-ttu-id="d42cc-106">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="d42cc-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="d42cc-107">**탐색기** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d42cc-107">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="d42cc-108">비즈니스 규칙을 적용할 모델 개체에 대한 **업데이트** 이상의 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d42cc-108">You must have a minimum of **Update** permission to the model object you are applying business rules to.</span></span>  
  
### <a name="to-apply-business-rules-selectively"></a><span data-ttu-id="d42cc-109">비즈니스 규칙을 선택적으로 적용하려면</span><span class="sxs-lookup"><span data-stu-id="d42cc-109">To apply business rules selectively</span></span>  
  
1.  <span data-ttu-id="d42cc-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 홈 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d42cc-110">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="d42cc-111">**버전** 목록에서 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d42cc-111">From the **Version** list, select a version.</span></span>  
  
3.  <span data-ttu-id="d42cc-112">**탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d42cc-112">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="d42cc-113">메뉴 모음에서 **엔터티** 를 가리키고 규칙을 적용할 멤버를 포함하는 엔터티의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d42cc-113">From the menu bar, point to **Entities** and click the name of the entity that contains members you want to apply rules to.</span></span>  
  
5.  <span data-ttu-id="d42cc-114">**비즈니스 규칙 적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d42cc-114">Click **Apply business rules**.</span></span> <span data-ttu-id="d42cc-115">비즈니스 규칙은 표에 표시된 멤버에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d42cc-115">Business rules are applied only to the members displayed in the grid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d42cc-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d42cc-116">See Also</span></span>  
 <span data-ttu-id="d42cc-117">[비즈니스 규칙에 대해 버전의 유효성을 검사 하 &#40;MDS(Master Data Services)&#41;](validate-a-version-against-business-rules-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d42cc-117">[Validate a Version against Business Rules &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md) </span></span>  
 [<span data-ttu-id="d42cc-118">비즈니스 규칙&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d42cc-118">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
