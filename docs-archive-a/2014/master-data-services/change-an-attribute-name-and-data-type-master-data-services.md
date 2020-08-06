---
title: 특성 이름 변경 (MDS(Master Data Services)) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], changing name
ms.assetid: d348f238-f59d-41c7-ad20-3ccd55bfd9e5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: abbe5f666daed42b25b46f02e954343b57446145
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734227"
---
# <a name="change-an-attribute-name-master-data-services"></a><span data-ttu-id="8c714-102">특성 이름 변경(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="8c714-102">Change an Attribute Name (Master Data Services)</span></span>
  <span data-ttu-id="8c714-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 특성의 이름을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c714-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can change the name of an attribute.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8c714-104">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="8c714-104">Prerequisites</span></span>  
 <span data-ttu-id="8c714-105">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="8c714-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="8c714-106">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c714-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="8c714-107">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c714-107">You must be a model administrator.</span></span> <span data-ttu-id="8c714-108">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8c714-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-change-an-attribute-name"></a><span data-ttu-id="8c714-109">특성 이름을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="8c714-109">To change an attribute name</span></span>  
  
1.  <span data-ttu-id="8c714-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c714-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="8c714-111">**모델 뷰** 페이지의 메뉴 모음에서 **관리** 를 가리키고 **엔터티**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c714-111">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="8c714-112">**엔터티 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8c714-112">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="8c714-113">이름을 변경할 특성을 포함하는 엔터티의 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c714-113">Click the row for the entity that contains the attribute with the name you want to change.</span></span>  
  
5.  <span data-ttu-id="8c714-114">**선택한 엔터티 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c714-114">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="8c714-115">**엔터티 편집** 페이지에서 이름을 변경 하려는 특성을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c714-115">On the **Edit Entity** page, click the attribute with the name you want to change.</span></span>  
  
7.  <span data-ttu-id="8c714-116">**선택한 특성 편집**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c714-116">Click **Edit selected attribute**.</span></span>  
  
8.  <span data-ttu-id="8c714-117">**이름** 상자에 특성의 업데이트된 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8c714-117">In the **Name** box, type the updated name of the attribute.</span></span> <span data-ttu-id="8c714-118">특성 이름으로 사용 하지 않아야 하는 단어의 목록을 보려면 [예약어 &#40;MDS(Master Data Services)&#41;](reserved-words-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8c714-118">For a list of words that should not be used as attribute names, see [Reserved Words &#40;Master Data Services&#41;](reserved-words-master-data-services.md).</span></span>  
  
9. <span data-ttu-id="8c714-119">**특성 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c714-119">Click **Save attribute**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c714-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8c714-120">See Also</span></span>  
 <span data-ttu-id="8c714-121">[텍스트 특성 &#40;MDS(Master Data Services)를 만듭니다&#41;](create-a-text-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="8c714-121">[Create a Text Attribute &#40;Master Data Services&#41;](create-a-text-attribute-master-data-services.md) </span></span>  
 <span data-ttu-id="8c714-122">[MDS(Master Data Services) &#40;특성을 삭제&#41;](delete-an-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="8c714-122">[Delete an Attribute &#40;Master Data Services&#41;](delete-an-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="8c714-123">특성&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8c714-123">Attributes &#40;Master Data Services&#41;</span></span>](attributes-master-data-services.md)  
  
  
