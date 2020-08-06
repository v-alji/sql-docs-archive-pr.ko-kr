---
title: 모델 만들기(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], creating models
- creating models [Master Data Services]
ms.assetid: 9bb3b3b3-bde8-44aa-ad62-eaae21188141
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 07b2f44798a689a7ceca7ec39a2ffc95f015d9b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652890"
---
# <a name="create-a-model-master-data-services"></a><span data-ttu-id="3a974-102">모델 만들기(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3a974-102">Create a Model (Master Data Services)</span></span>
  <span data-ttu-id="3a974-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 모델 개체를 포함할 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3a974-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a model to contain model objects.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3a974-104">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="3a974-104">Prerequisites</span></span>  
 <span data-ttu-id="3a974-105">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="3a974-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="3a974-106">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a974-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
### <a name="to-create-a-model"></a><span data-ttu-id="3a974-107">모델을 만들려면</span><span class="sxs-lookup"><span data-stu-id="3a974-107">To create a model</span></span>  
  
1.  <span data-ttu-id="3a974-108">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a974-108">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="3a974-109">**모델 뷰** 페이지의 메뉴 모음에서 **관리** 를 가리키고 **모델**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a974-109">On the **Model View** page, from the menu bar, point to **Manage** and click **Models**.</span></span>  
  
3.  <span data-ttu-id="3a974-110">**모델 유지 관리** 페이지에서 **모델 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a974-110">On the **Model Maintenance** page, click **Add model**.</span></span>  
  
4.  <span data-ttu-id="3a974-111">**모델 이름** 상자에 모델의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a974-111">In the **Model name** box, type the name of the model.</span></span>  
  
5.  <span data-ttu-id="3a974-112">또는 **모델과 이름이 같은 엔터티 만들기** 를 선택하여 모델과 이름이 같은 엔터티를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3a974-112">Optionally, select **Create entity with same name as model** to create an entity with the same name as the model.</span></span>  
  
6.  <span data-ttu-id="3a974-113">필요에 따라 모델과 이름이 같은 명시적 **계층 만들기** 를 선택 하 여 모델과 이름이 같은 명시적 계층을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3a974-113">Optionally, select **Create explicit hierarchy with same name as model** to create an explicit hierarchy with the same name as the model.</span></span> <span data-ttu-id="3a974-114">이 옵션을 선택하면 컬렉션에 엔터티를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a974-114">This option also enables the entity for collections.</span></span>  
  
7.  <span data-ttu-id="3a974-115">필요에 따라 **필수 계층 (모든 리프 멤버 포함)** 을 선택 하 여 명시적 계층을 필수 계층으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3a974-115">Optionally, select **Mandatory hierarchy (all leaf members are included** to create the explicit hierarchy as a mandatory hierarchy.</span></span>  
  
8.  <span data-ttu-id="3a974-116">**모델 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a974-116">Click **Save model**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3a974-117">다음 단계</span><span class="sxs-lookup"><span data-stu-id="3a974-117">Next Steps</span></span>  
  
-   [<span data-ttu-id="3a974-118">엔터티 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="3a974-118">Create an Entity &#40;Master Data Services&#41;</span></span>](create-an-entity-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="3a974-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3a974-119">See Also</span></span>  
 <span data-ttu-id="3a974-120">[모델 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/models-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="3a974-120">[Models &#40;Master Data Services&#41;](../../2014/master-data-services/models-master-data-services.md) </span></span>  
 <span data-ttu-id="3a974-121">[엔터티 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/entities-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="3a974-121">[Entities &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md) </span></span>  
 <span data-ttu-id="3a974-122">[모델 &#40;MDS(Master Data Services) 삭제&#41;](../../2014/master-data-services/delete-a-model-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="3a974-122">[Delete a Model &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-model-master-data-services.md) </span></span>  
 [<span data-ttu-id="3a974-123">모델 이름 &#40;MDS(Master Data Services)&#41;변경</span><span class="sxs-lookup"><span data-stu-id="3a974-123">Change a Model Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-model-name-master-data-services.md)  
  
  
