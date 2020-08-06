---
title: 파생 계층 삭제(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting derived hierarchies [Master Data Services]
- derived hierarchies, deleting
ms.assetid: f46d660e-47f2-47ca-9372-1b5931540beb
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a49922c0d719415436d28eb48657a7fc93c547fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651752"
---
# <a name="delete-a-derived-hierarchy-master-data-services"></a><span data-ttu-id="b4ff7-102">파생 계층 삭제(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b4ff7-102">Delete a Derived Hierarchy (Master Data Services)</span></span>
  <span data-ttu-id="b4ff7-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서는 파생 계층이 더 이상 필요하지 않으면 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4ff7-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete a derived hierarchy when you are sure you no longer need it.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b4ff7-104">파생 계층을 삭제해도 해당 계층의 기준이 되는 특성 관계에는 아무 영향이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b4ff7-104">Deleting a derived hierarchy has no effect on the attribute relationships that the hierarchy is based on.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b4ff7-105">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="b4ff7-105">Prerequisites</span></span>  
 <span data-ttu-id="b4ff7-106">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="b4ff7-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="b4ff7-107">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4ff7-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="b4ff7-108">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4ff7-108">You must be a model administrator.</span></span> <span data-ttu-id="b4ff7-109">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b4ff7-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-a-derived-hierarchy"></a><span data-ttu-id="b4ff7-110">파생 계층을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="b4ff7-110">To delete a derived hierarchy</span></span>  
  
1.  <span data-ttu-id="b4ff7-111">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4ff7-111">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="b4ff7-112">**모델 뷰** 페이지의 메뉴 모음에서 **관리** 를 가리키고 **파생 계층**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4ff7-112">On the **Model View** page, from the menu bar, point to **Manage** and click **Derived Hierarchies**.</span></span>  
  
3.  <span data-ttu-id="b4ff7-113">**파생 계층 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b4ff7-113">On the **Derived Hierarchy Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="b4ff7-114">삭제하려는 파생 계층의 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b4ff7-114">Select the row for the derived hierarchy that you want to delete.</span></span>  
  
5.  <span data-ttu-id="b4ff7-115">**선택한 계층 삭제**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4ff7-115">Click **Delete selected hierarchy**.</span></span>  
  
6.  <span data-ttu-id="b4ff7-116">확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4ff7-116">In the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4ff7-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b4ff7-117">See Also</span></span>  
 <span data-ttu-id="b4ff7-118">[파생 계층 &#40;MDS(Master Data Services)를 만듭니다&#41;](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="b4ff7-118">[Create a Derived Hierarchy &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md) </span></span>  
 [<span data-ttu-id="b4ff7-119">파생 계층&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="b4ff7-119">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)  
  
  
