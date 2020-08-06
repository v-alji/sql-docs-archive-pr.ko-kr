---
title: 코드 특성 값 자동 생성(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 19b354ee-2906-4cc7-ba2f-32b4543bddcf
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6c442f37ffe322985ba55b29b2c4cd539b8a3e05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659514"
---
# <a name="automatically-generate-code-attribute-values-master-data-services"></a><span data-ttu-id="a31fa-102">코드 특성 값 자동 생성(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="a31fa-102">Automatically Generate Code Attribute Values (Master Data Services)</span></span>
  <span data-ttu-id="a31fa-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 새 멤버를 만들 때마다 코드 값에 정수가 자동 할당되도록 하려면 엔터티의 코드 특성에 대해 값을 자동으로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="a31fa-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], automatically generate values for an entity's Code attribute when you want an integer to be automatically assigned to the Code value each time a new member is created.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a31fa-104">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="a31fa-104">Prerequisites</span></span>  
 <span data-ttu-id="a31fa-105">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="a31fa-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="a31fa-106">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a31fa-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="a31fa-107">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a31fa-107">You must be a model administrator.</span></span> <span data-ttu-id="a31fa-108">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a31fa-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="a31fa-109">엔터티가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a31fa-109">The entity must exist.</span></span> <span data-ttu-id="a31fa-110">자세한 내용은 [&#41;MDS(Master Data Services) 엔터티 &#40;만들기 ](../../2014/master-data-services/create-an-entity-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a31fa-110">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-automatically-generate-code-values"></a><span data-ttu-id="a31fa-111">코드 값을 자동으로 생성하려면</span><span class="sxs-lookup"><span data-stu-id="a31fa-111">To automatically generate Code values</span></span>  
  
1.  <span data-ttu-id="a31fa-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a31fa-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="a31fa-113">**모델 탐색기** 페이지의 메뉴 모음에서 **관리** 를 가리키고 **엔터티**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a31fa-113">On the **Model Explorer** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="a31fa-114">**엔터티 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a31fa-114">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="a31fa-115">코드를 생성하려는 엔터티의 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a31fa-115">Select the row for the entity that you want to generate codes for.</span></span>  
  
5.  <span data-ttu-id="a31fa-116">**선택한 엔터티 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a31fa-116">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="a31fa-117">**코드 값 자동으로 만들기** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a31fa-117">Select the **Create Code values automatically** check box.</span></span>  
  
7.  <span data-ttu-id="a31fa-118">**시작 값** 상자에 증가를 시작할 숫자를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a31fa-118">In the **Start with** box, type a number to begin incrementing.</span></span> <span data-ttu-id="a31fa-119">멤버가 이미 있는 경우 가장 높은 기존 값을 기반으로 코드가 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a31fa-119">If members already exist, the Code will be set based on the highest existing value.</span></span> <span data-ttu-id="a31fa-120">예를 들어 가장 높은 기존 코드 값이 299인 경우 다음 멤버의 코드 값은 300으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a31fa-120">For example, if the highest existing Code value is 299, the next member's Code value will be set to 300.</span></span>  
  
8.  <span data-ttu-id="a31fa-121">**엔터티 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a31fa-121">Click **Save entity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a31fa-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a31fa-122">See Also</span></span>  
 <span data-ttu-id="a31fa-123">[MDS(Master Data Services)&#41;&#40;자동 코드 만들기](../../2014/master-data-services/automatic-code-creation-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="a31fa-123">[Automatic Code Creation &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md) </span></span>  
 [<span data-ttu-id="a31fa-124">코드 외의 특성 값 자동 생성&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a31fa-124">Automatically Generate Attribute Values Other Than Code &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)  
  
  
