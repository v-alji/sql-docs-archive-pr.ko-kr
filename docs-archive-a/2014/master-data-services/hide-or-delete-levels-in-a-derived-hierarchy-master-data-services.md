---
title: 파생 계층의 수준 숨기기 또는 삭제(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies, hiding levels
- derived hierarchies, deleting levels
ms.assetid: e00582b9-9415-4b66-b4a7-9f590d83875f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 039b05633bcd1fdc69d226e565b3dc5211e9734f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652180"
---
# <a name="hide-or-delete-levels-in-a-derived-hierarchy-master-data-services"></a><span data-ttu-id="7b7ff-102">파생 계층의 수준 숨기기 또는 삭제(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="7b7ff-102">Hide or Delete Levels in a Derived Hierarchy (Master Data Services)</span></span>
  <span data-ttu-id="7b7ff-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서는 그룹화용으로 수준이 필요하지만 해당 수준을 표시할 필요는 없는 경우 파생 계층의 수준을 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b7ff-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], hide a level in a derived hierarchy when you require the level for grouping but you do not need to show the level.</span></span> <span data-ttu-id="7b7ff-104">그룹화에 수준을 사용하지 않으려면 수준을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7ff-104">Delete a level when you do not want to use it for grouping.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7b7ff-105">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="7b7ff-105">Prerequisites</span></span>  
 <span data-ttu-id="7b7ff-106">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="7b7ff-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="7b7ff-107">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7ff-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="7b7ff-108">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7ff-108">You must be a model administrator.</span></span> <span data-ttu-id="7b7ff-109">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7b7ff-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-hide-or-delete-levels-in-a-derived-hierarchy"></a><span data-ttu-id="7b7ff-110">파생 계층의 수준을 숨기거나 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="7b7ff-110">To hide or delete levels in a derived hierarchy</span></span>  
  
1.  <span data-ttu-id="7b7ff-111">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7ff-111">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="7b7ff-112">**모델 뷰** 페이지의 메뉴 모음에서 **관리** 를 가리키고 **파생 계층**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7ff-112">On the **Model View** page, from the menu bar, point to **Manage** and click **Derived Hierarchies**.</span></span>  
  
3.  <span data-ttu-id="7b7ff-113">**파생 계층 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7ff-113">On the **Derived Hierarchy Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="7b7ff-114">편집하려는 파생 계층의 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7ff-114">Select the row for the derived hierarchy you want to edit.</span></span>  
  
5.  <span data-ttu-id="7b7ff-115">**선택한 파생 계층 편집**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7ff-115">Click **Edit selected derived hierarchy**.</span></span>  
  
6.  <span data-ttu-id="7b7ff-116">**현재 수준** 창에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7ff-116">In the **Current Levels** pane:</span></span>  
  
    -   <span data-ttu-id="7b7ff-117">수준을 숨기려면 맨 위 또는 맨 아래 수준 외의 수준을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7ff-117">To hide a level, click a level other than the top or bottom.</span></span> <span data-ttu-id="7b7ff-118">**표시** 목록에서 **아니요**를 선택하고</span><span class="sxs-lookup"><span data-stu-id="7b7ff-118">From the **Visible** list, select **No**.</span></span> <span data-ttu-id="7b7ff-119">**선택한 계층 항목 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7ff-119">Then click **Save selected hierarchy item**.</span></span>  
  
    -   <span data-ttu-id="7b7ff-120">최상위 수준을 삭제하려면 **선택한 계층 항목 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7ff-120">To delete the top level, click **Delete selected hierarchy item**.</span></span> <span data-ttu-id="7b7ff-121">확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7ff-121">In the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="7b7ff-122">최상위 수준만 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b7ff-122">You can delete the top level only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b7ff-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7b7ff-123">See Also</span></span>  
 <span data-ttu-id="7b7ff-124">[계층 내에서 멤버를 이동 하 여 MDS(Master Data Services) &#40;&#41;](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="7b7ff-124">[Move Members within a Hierarchy &#40;Master Data Services&#41;](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md) </span></span>  
 [<span data-ttu-id="7b7ff-125">파생 계층&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="7b7ff-125">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)  
  
  
