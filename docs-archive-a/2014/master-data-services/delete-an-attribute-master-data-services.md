---
title: 특성 삭제(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], deleting
- deleting attributes [Master Data Services]
ms.assetid: ec3e66f7-0e35-43d7-a80d-64899948ebfe
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 96db56dac9356b1131e722fc7f6b779c93305bb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728419"
---
# <a name="delete-an-attribute-master-data-services"></a><span data-ttu-id="a66e5-102">특성 삭제(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="a66e5-102">Delete an Attribute (Master Data Services)</span></span>
  <span data-ttu-id="a66e5-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서는 특성 및 연결된 모든 특성 값을 영구적으로 삭제하려는 경우 특성을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a66e5-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete an attribute when you want to permanently delete the attribute and all associated attribute values.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a66e5-104">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="a66e5-104">Prerequisites</span></span>  
 <span data-ttu-id="a66e5-105">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="a66e5-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="a66e5-106">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a66e5-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="a66e5-107">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a66e5-107">You must be a model administrator.</span></span> <span data-ttu-id="a66e5-108">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a66e5-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-an-attribute"></a><span data-ttu-id="a66e5-109">특성을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="a66e5-109">To delete an attribute</span></span>  
  
1.  <span data-ttu-id="a66e5-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a66e5-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="a66e5-111">**모델 뷰** 페이지의 메뉴 모음에서 **관리** 를 가리키고 **엔터티**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a66e5-111">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="a66e5-112">**엔터티 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a66e5-112">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="a66e5-113">삭제할 특성이 포함된 엔터티의 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a66e5-113">Select the row for the entity that contains the attribute you want to delete.</span></span>  
  
5.  <span data-ttu-id="a66e5-114">**선택한 엔터티 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a66e5-114">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="a66e5-115">**엔터티 편집** 페이지에서 삭제 하려는 특성을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a66e5-115">On the **Edit Entity** page, click the attribute you want to delete.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a66e5-116">Name 또는 Code 특성은 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a66e5-116">You cannot delete the Name or Code attributes.</span></span>  
  
7.  <span data-ttu-id="a66e5-117">**선택한 특성 삭제**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a66e5-117">Click **Delete selected attribute**.</span></span>  
  
8.  <span data-ttu-id="a66e5-118">확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a66e5-118">In the confirmation dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="a66e5-119">추가 확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a66e5-119">In the additional confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a66e5-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a66e5-120">See Also</span></span>  
 <span data-ttu-id="a66e5-121">[특성 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="a66e5-121">[Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="a66e5-122">[도메인 기반 특성 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="a66e5-122">[Domain-Based Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="a66e5-123">[텍스트 특성 &#40;MDS(Master Data Services)를 만듭니다&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="a66e5-123">[Create a Text Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="a66e5-124">도메인 기반 특성 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a66e5-124">Create a Domain-Based Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
  
