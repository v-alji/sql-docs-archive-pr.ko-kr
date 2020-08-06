---
title: 계층 내에서 멤버 이동 (MDS(Master Data Services)) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services], moving members
- explicit hierarchies, moving members
- derived hierarchies, moving members
- members [Master Data Services], moving
ms.assetid: 049c9a15-89c1-478c-8438-028fffc9e187
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 37167f76b965197dbf8e37e365778395ec640d38
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649586"
---
# <a name="move-members-within-a-hierarchy-master-data-services"></a><span data-ttu-id="0c114-102">계층 내에서 멤버 이동(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0c114-102">Move Members within a Hierarchy (Master Data Services)</span></span>
  <span data-ttu-id="0c114-103">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서는 계층 내에서 멤버를 이동하여 할당된 위치나 부모를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c114-103">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], move members within a hierarchy to change their location or parent assignment.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0c114-104">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="0c114-104">Prerequisites</span></span>  
 <span data-ttu-id="0c114-105">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="0c114-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="0c114-106">**탐색기** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c114-106">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="0c114-107">명시적 계층의 경우 엔터티에 대 한 **업데이트** 이상의 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c114-107">For explicit hierarchies, you must have a minimum of **Update** permission to the entity.</span></span>  
  
-   <span data-ttu-id="0c114-108">파생 계층의 경우 모델에 대 한 **업데이트** 와 계층에 사용 되는 모든 도메인 기반 특성이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c114-108">For derived hierarchies, you must have a minimum of **Update** to the model and to any domain-based attributes used in the hierarchy.</span></span>  
  
### <a name="to-move-members-within-a-hierarchy"></a><span data-ttu-id="0c114-109">계층 내에서 멤버를 이동하려면</span><span class="sxs-lookup"><span data-stu-id="0c114-109">To move members within a hierarchy</span></span>  
  
1.  <span data-ttu-id="0c114-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 홈 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0c114-110">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="0c114-111">**버전** 목록에서 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0c114-111">From the **Version** list, select a version.</span></span>  
  
3.  <span data-ttu-id="0c114-112">**탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0c114-112">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="0c114-113">메뉴 모음에서 **계층** 을 가리키고 *hierarchy_name*를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c114-113">From the menu bar, point to **Hierarchies** and click *hierarchy_name*.</span></span>  
  
5.  <span data-ttu-id="0c114-114">**계층 구조 창에서** 계층 구조가 트리 구조로 표시 되 면 이동할 각 멤버의 확인란을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c114-114">In the **Hierarchy** pane, where the hierarchy is displayed in a tree structure, click the check box for each member you want to move.</span></span>  
  
6.  <span data-ttu-id="0c114-115">**계층** 창 맨 위에서 **잘라내기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c114-115">At the top of the **Hierarchy** pane, click **Cut**.</span></span>  
  
7.  <span data-ttu-id="0c114-116">**계층** 창에서 멤버를 이동할 멤버의 확인란을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c114-116">In the **Hierarchy** pane, click the check box for the member you want to move the members to.</span></span>  
  
8.  <span data-ttu-id="0c114-117">**붙여넣기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c114-117">Click **Paste**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0c114-118">파생 계층에서는 같은 수준으로만 멤버를 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c114-118">In derived hierarchies, you can move members to the same level only.</span></span> <span data-ttu-id="0c114-119">또한 멤버 정렬 순서는 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0c114-119">Also, you cannot change the sort order of members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c114-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0c114-120">See Also</span></span>  
 <span data-ttu-id="0c114-121">[MDS(Master Data Services) &#40;준비 프로세스를 사용 하 여 명시적 계층 멤버를 이동&#41;](add-update-and-delete-data-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="0c114-121">[Move Explicit Hierarchy Members by Using the Staging Process &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md) </span></span>  
 <span data-ttu-id="0c114-122">[파생 계층 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="0c114-122">[Derived Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md) </span></span>  
 [<span data-ttu-id="0c114-123">명시적 계층&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0c114-123">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
