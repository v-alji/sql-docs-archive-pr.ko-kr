---
title: 특성 그룹 삭제(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting attribute groups [Master Data Services]
- attribute groups [Master Data Services], deleting
ms.assetid: f915e89b-629d-4725-aea6-a7f051978244
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 833c5cf327034b25d68af123a1fc134372bd6f10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660652"
---
# <a name="delete-an-attribute-group-master-data-services"></a><span data-ttu-id="dca86-102">특성 그룹 삭제(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="dca86-102">Delete an Attribute Group (Master Data Services)</span></span>
  <span data-ttu-id="dca86-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서는 **의** 탐색기 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]기능 영역에 탭을 더 이상 표시하지 않아도 되는 경우 특성 그룹을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dca86-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete an attribute group when you no longer need the tab to display in the **Explorer** functional area of [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
-   <span data-ttu-id="dca86-104">**참고** 특성 그룹이 있는 경우 특성 그룹에 속하지 않은 특성은 **탐색기**에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dca86-104">**Note** When attribute groups exist, attributes that do not belong to an attribute group are not displayed in **Explorer**.</span></span> <span data-ttu-id="dca86-105">특성 그룹이 없는 경우 모든 특성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dca86-105">When no attribute groups exist, all attributes are displayed.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="dca86-106">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="dca86-106">Prerequisites</span></span>  
 <span data-ttu-id="dca86-107">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="dca86-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="dca86-108">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dca86-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="dca86-109">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dca86-109">You must be a model administrator.</span></span> <span data-ttu-id="dca86-110">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dca86-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-an-attribute-group"></a><span data-ttu-id="dca86-111">특성 그룹을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="dca86-111">To delete an attribute group</span></span>  
  
1.  <span data-ttu-id="dca86-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dca86-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="dca86-113">**모델 뷰** 페이지의 메뉴 모음에서 **관리** 를 가리키고 **특성 그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dca86-113">On the **Model View** page, from the menu bar, point to **Manage** and click **Attribute Groups**.</span></span>  
  
3.  <span data-ttu-id="dca86-114">**모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dca86-114">From the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="dca86-115">**엔터티** 목록에서 엔터티를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dca86-115">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="dca86-116">삭제 하려는 그룹의 유형에 따라 더하기 기호를 클릭 하 여 **리프 그룹**, **통합 그룹**또는 **컬렉션 그룹**을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="dca86-116">Click the plus sign to expand **Leaf Groups**, **Consolidated Groups**, or **Collection Groups**, depending on the type of group you want to delete.</span></span>  
  
6.  <span data-ttu-id="dca86-117">삭제할 특성 그룹을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dca86-117">Click the attribute group you want to delete.</span></span>  
  
7.  <span data-ttu-id="dca86-118">**선택한 그룹 삭제**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dca86-118">Click **Delete selected group**.</span></span>  
  
8.  <span data-ttu-id="dca86-119">확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dca86-119">In the confirmation dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="dca86-120">추가 확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dca86-120">In the additional confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dca86-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dca86-121">See Also</span></span>  
 <span data-ttu-id="dca86-122">[특성 그룹 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="dca86-122">[Attribute Groups &#40;Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span></span>  
 [<span data-ttu-id="dca86-123">특성 그룹 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="dca86-123">Create an Attribute Group &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)  
  
  
