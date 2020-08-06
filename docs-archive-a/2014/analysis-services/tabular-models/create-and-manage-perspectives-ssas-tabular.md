---
title: 큐브 뷰 만들기 및 관리 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.perspectivedb.f1
ms.assetid: 2a411c2b-2820-4086-ad7f-ce6a941fefc7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6d0029ff61aa05e2e83f34833c3d0af17ddb3beb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647294"
---
# <a name="create-and-manage-perspectives-ssas-tabular"></a><span data-ttu-id="1e69b-102">큐브 뷰 만들기 및 관리(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="1e69b-102">Create and Manage Perspectives (SSAS Tabular)</span></span>
  <span data-ttu-id="1e69b-103">큐브 뷰는 모델을 비즈니스 또는 애플리케이션 중심의 관점에서 파악할 수 있게 해주는 보기 가능한 모델 하위 집합을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="1e69b-103">Perspectives define viewable subsets of a model that provide focused, business-specific, or application-specific viewpoints of the model.</span></span> <span data-ttu-id="1e69b-104">이 항목의 태스크에서는 모델 디자이너의 **큐브 뷰** 를 사용하여 큐브 뷰를 만들고 관리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1e69b-104">The tasks in this topic describe how to create and manage perspectives by using the **Perspectives** dialog box in the model designer.</span></span>  
  
 <span data-ttu-id="1e69b-105">이 항목에는 다음 태스크가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e69b-105">This topic includes the following tasks:</span></span>  
  
-   [<span data-ttu-id="1e69b-106">큐브 뷰를 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="1e69b-106">To add a perspective</span></span>](#bkmk_add)  
  
-   [<span data-ttu-id="1e69b-107">큐브 뷰를 편집하려면</span><span class="sxs-lookup"><span data-stu-id="1e69b-107">To edit a perspective</span></span>](#bkmk_edit)  
  
-   [<span data-ttu-id="1e69b-108">큐브 뷰의 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="1e69b-108">To rename a perspective</span></span>](#bkmk_rename)  
  
-   [<span data-ttu-id="1e69b-109">큐브 뷰를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="1e69b-109">To delete a perspective</span></span>](#bkmk_delete)  
  
-   [<span data-ttu-id="1e69b-110">큐브 뷰를 복사하려면</span><span class="sxs-lookup"><span data-stu-id="1e69b-110">To copy a perspective</span></span>](#bkmk_copy)  
  
## <a name="tasks"></a><span data-ttu-id="1e69b-111">작업</span><span class="sxs-lookup"><span data-stu-id="1e69b-111">Tasks</span></span>  
 <span data-ttu-id="1e69b-112">큐브 뷰를 만들려면 **큐브 뷰** 대화 상자를 사용합니다. 이 대화 상자에서는 큐브 뷰를 추가, 편집, 삭제, 복사 및 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e69b-112">To create perspectives, you will use the **Perspectives** dialog box, where you can add, edit, delete, copy, and view perspectives.</span></span> <span data-ttu-id="1e69b-113">**큐브 뷰** 대화 상자를 보려면 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 **모델** 메뉴에서 **큐브 뷰**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e69b-113">To view the **Perspectives** dialog box, in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click on the **Model** menu, and then click **Perspectives**.</span></span>  
  
###  <a name="to-add-a-perspective"></a><a name="bkmk_add"></a> <span data-ttu-id="1e69b-114">큐브 뷰를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="1e69b-114">To add a perspective</span></span>  
  
-   <span data-ttu-id="1e69b-115">새 큐브 뷰를 추가하려면 **새 큐브 뷰**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e69b-115">To add a new perspective, click **New Perspective**.</span></span> <span data-ttu-id="1e69b-116">그런 다음 포함할 필드 개체를 선택하거나 선택 취소하고 새 큐브 뷰의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e69b-116">You can then check and uncheck field objects to be included and provide a name for the new perspective.</span></span>  
  
     <span data-ttu-id="1e69b-117">모든 필드 개체를 선택 취소하고 빈 큐브 뷰를 만들면 사용자가 이 큐브 뷰를 사용할 때 빈 필드 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e69b-117">If you create an empty perspective with all of the field object fields, then a user using this perspective will see an empty Field List.</span></span> <span data-ttu-id="1e69b-118">큐브 뷰에는 하나 이상의 테이블 및 열을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e69b-118">Perspectives should contain at least one table and column.</span></span>  
  
###  <a name="to-edit-a-perspective"></a><a name="bkmk_edit"></a><span data-ttu-id="1e69b-119">큐브 뷰를 편집 하려면</span><span class="sxs-lookup"><span data-stu-id="1e69b-119">To edit a perspective</span></span>  
  
-   <span data-ttu-id="1e69b-120">큐브 뷰를 수정 하려면 큐브 뷰 열에서 필드를 선택 하 고 선택 취소 합니다. 그러면 큐브 뷰에서 필드 개체가 추가 되거나 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e69b-120">To modify a perspective, check and uncheck fields in the perspective's column, which adds and removes field objects from the perspective.</span></span>  
  
###  <a name="to-rename-a-perspective"></a><a name="bkmk_rename"></a><span data-ttu-id="1e69b-121">큐브 뷰의 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="1e69b-121">To rename a perspective</span></span>  
  
-   <span data-ttu-id="1e69b-122">큐브 뷰 열 머리글 (큐브 뷰 이름) 위로 마우스를 가져가면 **이름 바꾸기** 단추가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1e69b-122">When you hover over a perspective's column header (the name of the perspective), the **Rename** button appears.</span></span> <span data-ttu-id="1e69b-123">큐브 뷰의 이름을 바꾸려면 **이름 바꾸기**를 클릭하고 새 이름을 입력하거나 기존 이름을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="1e69b-123">To rename the perspective, click **Rename**, and then enter a new name or edit the existing name.</span></span>  
  
###  <a name="to-delete-a-perspective"></a><a name="bkmk_delete"></a><span data-ttu-id="1e69b-124">큐브 뷰를 삭제 하려면</span><span class="sxs-lookup"><span data-stu-id="1e69b-124">To delete a perspective</span></span>  
  
-   <span data-ttu-id="1e69b-125">큐브 뷰 열 머리글 (큐브 뷰 이름) 위로 마우스를 이동 하면 **삭제** 단추가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1e69b-125">When you hover over a perspective's column header (the name of the perspective), the **Delete** button appears.</span></span> <span data-ttu-id="1e69b-126">큐브 뷰를 삭제하려면 **삭제** 단추를 클릭하고 확인 창에서 **예** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e69b-126">To delete the perspective, click the **Delete** button, and then click **Yes** in the confirmation window.</span></span>  
  
###  <a name="to-copy-a-perspective"></a><a name="bkmk_copy"></a><span data-ttu-id="1e69b-127">큐브 뷰를 복사 하려면</span><span class="sxs-lookup"><span data-stu-id="1e69b-127">To copy a perspective</span></span>  
  
-   <span data-ttu-id="1e69b-128">큐브 뷰 열 머리글을 마우스로 가리키면 **복사** 단추가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1e69b-128">When you hover over a perspective's column header, the **Copy** button appears.</span></span> <span data-ttu-id="1e69b-129">큐브 뷰의 복사본을 만들려면 **복사** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e69b-129">To create a copy of that perspective, click the **Copy** button.</span></span> <span data-ttu-id="1e69b-130">그러면 선택한 큐브 뷰의 복사본이 기존 큐브 뷰의 오른쪽에 새 큐브 뷰로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e69b-130">A copy of the selected perspective is added as a new perspective to the right of existing perspectives.</span></span> <span data-ttu-id="1e69b-131">새 큐브 뷰는 복사 원본 큐브 뷰의 이름을 상속하며, 이름 끝에 *- 복사본* 이라는 주석이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e69b-131">The new perspective inherits the name of the copied perspective and a *- Copy* annotation is appended to the end of the name.</span></span> <span data-ttu-id="1e69b-132">예를 들어 *sales* 큐브 뷰의 복사본을 만드는 경우 새 큐브 뷰를 *판매 복사본*이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e69b-132">For example, if a copy of the *Sales* perspective is created, the new perspective is called *Sales - Copy*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e69b-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1e69b-133">See Also</span></span>  
 <span data-ttu-id="1e69b-134">[SSAS 테이블 형식&#41;&#40;큐브 뷰](perspectives-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="1e69b-134">[Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="1e69b-135">계층 구조&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="1e69b-135">Hierarchies &#40;SSAS Tabular&#41;</span></span>](hierarchies-ssas-tabular.md)  
  
  
