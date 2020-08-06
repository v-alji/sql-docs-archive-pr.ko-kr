---
title: 연결 된 측정값 그룹 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- linked measure groups [Analysis Services]
- referencing measure groups
- Linked Measure Group Wizard
- measure groups [Analysis Services], linked
- linked dimensions [Analysis Services]
ms.assetid: 7f838452-8669-4194-8e15-7afdc7f15251
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2a7d7443b8c25f5cbafa5af83364ef05d8053145
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651364"
---
# <a name="linked-measure-groups"></a><span data-ttu-id="f533a-102">연결된 측정값 그룹</span><span class="sxs-lookup"><span data-stu-id="f533a-102">Linked Measure Groups</span></span>
  <span data-ttu-id="f533a-103">연결된 측정값 그룹은 동일한 데이터베이스 또는 다른 Analysis Services 데이터베이스 내에 있는 다른 큐브의 또 다른 측정값 그룹을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-103">A linked measure group is based on another measure group in a different cube within the same database or a different Analysis Services database.</span></span> <span data-ttu-id="f533a-104">측정값 집합을 다시 사용하려는 경우 여러 큐브에서 연결된 측정값 그룹과 해당 데이터 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-104">You might use a linked measure group if you want to reuse a set of measures, and the corresponding data values, in multiple cubes.</span></span>  
  
 <span data-ttu-id="f533a-105">원본 측정값 그룹과 연결된 측정값 그룹은 동일한 서버에서 실행되는 솔루션에 상주하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-105">Microsoft recommends that the original and linked measure groups reside in solutions that run on the same server.</span></span> <span data-ttu-id="f533a-106">원격 서버의 측정값 그룹에 연결 하는 기능은 이후 릴리스에서 사용 중단 될 예정입니다 ( [SQL Server 2014에서 사용 되지 않는 Analysis Services 기능](../deprecated-analysis-services-features-in-sql-server-2014.md)참조).</span><span class="sxs-lookup"><span data-stu-id="f533a-106">Linking to a measure group on a remote server is scheduled for deprecation in a future release (see [Deprecated Analysis Services Features in SQL Server 2014](../deprecated-analysis-services-features-in-sql-server-2014.md)).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f533a-107">연결된 측정값 그룹은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-107">Linked measure groups are read-only.</span></span> <span data-ttu-id="f533a-108">최근 변경 사항을 선택하려면 모든 연결된 측정값을 삭제하고 수정된 원본 개체를 기반으로 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-108">To pick up the latest changes, you must delete and recreate all linked measure groups based on the modified source object.</span></span> <span data-ttu-id="f533a-109">따라서 이후에 측정값 그룹 수정이 필요할 경우에는 프로젝트 사이에 측정값 그룹을 복사하고 붙여넣는 방식을 고려해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-109">For this reason, copy and pasting measure groups between projects is an alternative approach that you should consider in case future modifications to the measure group are required.</span></span>  
  
## <a name="usage-limitations"></a><span data-ttu-id="f533a-110">사용 제한 사항</span><span class="sxs-lookup"><span data-stu-id="f533a-110">Usage Limitations</span></span>  
 <span data-ttu-id="f533a-111">앞에서 설명한 대로 연결된 측정값을 사용하는 데 있어서 중요한 제한 사항은 연결된 측정값을 직접 사용자 지정할 수 없다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-111">As noted previously, an important constraint to using linked measures is an inability to customize a linked measure directly.</span></span> <span data-ttu-id="f533a-112">데이터 형식, 형식, 데이터 바인딩 및 표시 유형뿐만 아니라 측정값 그룹 자체에 있는 항목의 멤버 자격에 대한 수정 사항은 모두 원래 측정값 그룹에서 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-112">Modifications to the data type, format, data binding, and visibility, as well as membership of the items in the measure group itself, are all changes that must be made in the original measure group.</span></span>  
  
 <span data-ttu-id="f533a-113">작업 측면에서 연결된 측정값 그룹은 클라이언트 애플리케이션에서 액세스하면 다른 측정값 그룹과 동일하므로 다른 측정값 그룹과 동일한 방식으로 쿼리됩니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-113">Operationally, linked measure groups are identical to other measure groups when accessed by client applications, and are queried in the same manner as other measure groups.</span></span>  
  
 <span data-ttu-id="f533a-114">연결된 측정값 그룹을 포함하는 큐브를 쿼리하는 경우 대상 큐브에 대한 첫 번째 계산 패스 동안 연결이 설정되고 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-114">When you query a cube that contains a linked measure group, the link is established and resolved during the first calculation pass of the destination cube.</span></span> <span data-ttu-id="f533a-115">이러한 동작으로 인해 쿼리가 평가되기 전에는 연결된 측정값 그룹에 저장되는 어떠한 계산도 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-115">Because of this behavior, any calculations that are stored in the linked measure group cannot be resolved before the query is evaluated.</span></span> <span data-ttu-id="f533a-116">즉, 계산 측정값과 계산 셀은 원본 큐브에서 상속받지 말고 대상 큐브에서 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-116">In other words, calculated measures and calculated cells must be recreated in the destination cube rather than inherited from the source cube.</span></span>  
  
 <span data-ttu-id="f533a-117">사용 제한 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-117">The following list summarizes usage limitations.</span></span>  
  
-   <span data-ttu-id="f533a-118">연결된 다른 측정값 그룹에서는 연결된 측정값 그룹을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-118">You cannot create a linked measure group from another linked measure group.</span></span>  
  
-   <span data-ttu-id="f533a-119">연결된 측정값 그룹에서 측정값을 추가하거나 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-119">You cannot add or remove measures in a linked measure group.</span></span> <span data-ttu-id="f533a-120">멤버 자격은 원래 측정값 그룹에서만 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-120">Membership is defined only in the original measure group.</span></span>  
  
-   <span data-ttu-id="f533a-121">연결된 측정값 그룹에서는 쓰기 저장(writeback)이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-121">Writeback is not supported in linked measure groups.</span></span>  
  
-   <span data-ttu-id="f533a-122">연결된 측정값 그룹은 여러 다 대 다 관계에서 사용할 수 없으며 특히 해당 관계가 서로 다른 큐브에 있는 경우에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-122">Linked measure groups cannot be used in multiple many-to-many relationships, especially when those relationships are in different cubes.</span></span> <span data-ttu-id="f533a-123">사용하면 모호한 집계가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-123">Doing so can result in ambiguous aggregations.</span></span> <span data-ttu-id="f533a-124">자세한 내용은 [다 대 다 관계가 포함된 큐브의 연결된 측정값에 대한 잘못된 집계](https://social.technet.microsoft.com/wiki/contents/articles/22911.incorrect-amounts-for-linked-measures-in-cubes-containing-many-to-many-relationships-ssas-troubleshooting.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f533a-124">For more information, see [Incorrect Amounts for Linked Measures in Cubes containing Many-to-Many Relationships](https://social.technet.microsoft.com/wiki/contents/articles/22911.incorrect-amounts-for-linked-measures-in-cubes-containing-many-to-many-relationships-ssas-troubleshooting.aspx).</span></span>  
  
 <span data-ttu-id="f533a-125">연결된 측정값 그룹에 포함된 측정값은 동일한 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스에서 검색한 연결된 차원과만 직접 구성이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-125">The measures contained in a linked measure group can be directly organized only along linked dimensions retrieved from the same [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="f533a-126">그러나 계산 멤버를 사용하면 연결된 측정값 그룹의 정보를 큐브 내의 연결되지 않은 다른 차원과 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-126">However, you can use calculated members to relate information from linked measure groups to the other, non-linked dimensions in your cube.</span></span> <span data-ttu-id="f533a-127">또한 참조 또는 다 대 다 관계 등의 간접 관계를 사용하여 연결되지 않은 차원을 연결된 측정값 그룹에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-127">You can also use an indirect relationship, such as a reference or many-to-many relationship, to relate non-linked dimensions to a linked measure group.</span></span>  
  
## <a name="create-or-modify-a-linked-measure"></a><span data-ttu-id="f533a-128">연결된 측정값 만들기 또는 수정</span><span class="sxs-lookup"><span data-stu-id="f533a-128">Create or modify a linked measure</span></span>  
 <span data-ttu-id="f533a-129">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 를 사용하여 연결된 측정값 그룹을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-129">Use [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] to create a linked measure group.</span></span>  
  
1.  <span data-ttu-id="f533a-130">이제 원본 큐브에서 원래 측정값 그룹에 대한 수정을 모두 완료합니다. 이에 따라 나중에 이후 큐브에서 연결된 측정값 그룹을 다시 만들 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-130">Finalize any modifications to the original measure group now, in the source cube, so that you don't have to recreate the linked measure groups later in subsequent cubes.</span></span> <span data-ttu-id="f533a-131">연결된 개체의 이름을 바꿀 수 있지만 다른 속성을 변경할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-131">You can rename a linked object, but you cannot change any other properties.</span></span>  
  
2.  <span data-ttu-id="f533a-132">솔루션 탐색기에서 연결된 측정값 그룹을 추가할 큐브를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-132">In Solution Explorer, double-click the cube to which you are adding the linked measure group.</span></span> <span data-ttu-id="f533a-133">이 단계에서는 큐브 디자이너에서 큐브를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-133">This step opens the cube in Cube Designer.</span></span>  
  
3.  <span data-ttu-id="f533a-134">큐브 디자이너에서 측정값 창이나 차원 창을 마우스 오른쪽 단추로 클릭한 다음 **새 연결된 개체**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-134">In Cube Designer, in either the Measures pane or Dimensions pane, right-click anywhere in either pane, then select **New Linked Object**.</span></span> <span data-ttu-id="f533a-135">연결된 개체 마법사가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-135">This starts the Linked Object Wizard.</span></span>  
  
4.  <span data-ttu-id="f533a-136">첫 번째 페이지에서 데이터 원본을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-136">On the first page, specify the data source.</span></span> <span data-ttu-id="f533a-137">이 단계에서는 원본 측정값 그룹의 위치를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-137">This step establishes the location of the original measure group.</span></span> <span data-ttu-id="f533a-138">기본값은 현재 데이터베이스의 현재 큐브이지만 다른 Analysis Services 데이터베이스를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-138">The default is the current cube in the current database, but you can also choose a different Analysis Services database.</span></span>  
  
5.  <span data-ttu-id="f533a-139">다음 페이지에서 연결할 측정값 그룹 또는 차원을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-139">On the next page, choose the measure group or dimension you want to link.</span></span> <span data-ttu-id="f533a-140">측정값 그룹 등의 큐브 개체 및 차원이 별도로 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-140">Dimensions and Cube objects, such as measure groups, are listed separately.</span></span> <span data-ttu-id="f533a-141">현재 큐브에 없는 개체만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-141">Only those objects not already present in the current cube are available.</span></span>  
  
6.  <span data-ttu-id="f533a-142">**마침** 을 클릭하여 연결된 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-142">Click **Finish** to create the linked object.</span></span> <span data-ttu-id="f533a-143">연결된 개체가 측정값 및 차원 창에서 링크 아이콘으로 표시되어 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-143">Linked objects appear in the Measures and Dimensions pane, indicated by the link icon.</span></span>  
  
## <a name="secure-a-linked-measure"></a><span data-ttu-id="f533a-144">연결된 측정값 보안</span><span class="sxs-lookup"><span data-stu-id="f533a-144">Secure a linked measure</span></span>  
 <span data-ttu-id="f533a-145">연결이 정의된 다음에는 연결된 측정값 그룹의 측정값에 대한 액세스가 다른 측정값 그룹에 대한 액세스와 동일한 방법으로 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-145">After the link has been defined, access to the measures in a linked measure group, is managed in the same manner as access to other measure groups.</span></span> <span data-ttu-id="f533a-146">연결된 개체가 역할 디자이너에서 연결되지 않은 해당 항목과 함께 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-146">A linked object appears alongside its non-linked counterparts in Role Designer.</span></span> <span data-ttu-id="f533a-147">측정값 그룹의 보안 관리에 대한 자세한 내용은 [큐브 또는 모델 권한 부여&#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f533a-147">For more information on managing security for a measure group, see [Grant cube or model permissions &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md).</span></span>  
  
 <span data-ttu-id="f533a-148">연결된 측정값 그룹을 정의하거나 사용하려면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 대한 Windows 서비스 계정이 원본 큐브 및 측정값 그룹에 대해 원본 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 대한 `ReadDefinition` 및 `Read` 액세스 권한이 있는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스 역할에 속하거나 원본 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 대한 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 관리자 역할에 속해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f533a-148">In order to define or use a linked measure group, the Windows service account for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance must belong to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database role that has `ReadDefinition` and `Read` access rights on the source [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance to the source cube and measure group, or must belong to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Administrators role for the source [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f533a-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f533a-149">See Also</span></span>  
 [<span data-ttu-id="f533a-150">연결된 차원 정의</span><span class="sxs-lookup"><span data-stu-id="f533a-150">Define Linked Dimensions</span></span>](define-linked-dimensions.md)  
  
  
