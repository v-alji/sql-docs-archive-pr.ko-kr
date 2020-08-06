---
title: Excel에서 MDS로 데이터 게시 (Excel용 MDS 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 89fce454-a816-4b33-a26a-d1b9741d269b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 597a954760816d8938628974998fe8f6daad1af5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659501"
---
# <a name="publish-data-from-excel-to-mds-mds-add-in-for-excel"></a><span data-ttu-id="649dc-102">Excel에서 MDS로 데이터 게시(Excel용 MDS 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="649dc-102">Publish Data from Excel to MDS (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="649dc-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]에서는 Excel에서 작업을 마치고 다른 사용자가 데이터 액세스할 수 있도록 변경 내용을 저장하려는 경우 데이터를 MDS 리포지토리에 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="649dc-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], publish data to the MDS repository when you are finished working in Excel and want to save your changes so other users have access to them.</span></span>  
  
> [!NOTE]
>  -   <span data-ttu-id="649dc-104">변경 내용을 게시하면 MDS 관리 셀에 대한 주석이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="649dc-104">When you publish changes, comments on MDS-managed cells are deleted.</span></span>  
> -   <span data-ttu-id="649dc-105">MDS 관리 셀에서는 수식을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="649dc-105">A formula is not supported in an MDS-managed cell.</span></span> <span data-ttu-id="649dc-106">MDS 관리 셀의 수식은 텍스트 값으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="649dc-106">A formula in an MDS-managed cell is handled as a text value.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="649dc-107">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="649dc-107">Prerequisites</span></span>  
 <span data-ttu-id="649dc-108">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="649dc-108">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="649dc-109">**탐색기** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="649dc-109">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="649dc-110">활성 워크시트에는 MDS 관리 데이터가 포함되어야 하며, 사용자가 MDS 관리 데이터에서 항목을 변경했거나 추가했어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="649dc-110">The active worksheet must contain MDS-managed data and you must have made changes or additions to the MDS-managed data.</span></span>  
  
-   <span data-ttu-id="649dc-111">멤버를 추가하는 경우 엔터티에 대한 코드를 자동으로 생성하는 경우 **코드** 값을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="649dc-111">If you are adding members, you do not have to specify a **Code** value if codes for the entity are being automatically generated.</span></span> <span data-ttu-id="649dc-112">자세한 내용은 [MDS(Master Data Services)&#41;&#40;자동 코드 만들기 ](../automatic-code-creation-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="649dc-112">For more information, see [Automatic Code Creation &#40;Master Data Services&#41;](../automatic-code-creation-master-data-services.md).</span></span>  
  
### <a name="to-publish-data-to-the-mds-repository"></a><span data-ttu-id="649dc-113">MDS 저장소에 데이터를 게시하려면</span><span class="sxs-lookup"><span data-stu-id="649dc-113">To publish data to the MDS repository</span></span>  
  
1.  <span data-ttu-id="649dc-114">**게시 및 유효성 검사** 그룹에서 **게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="649dc-114">In the **Publish and Validate** group, click **Publish**.</span></span>  
  
2.  <span data-ttu-id="649dc-115">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="649dc-115">Optional.</span></span> <span data-ttu-id="649dc-116">**게시 및 주석** 대화 상자가 표시되면 모든 업데이트에 대해 동일한 주석(설명)을 공유하거나 각 변경 내용에 대해 개별적으로 주석을 달도록 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="649dc-116">If the **Publish and Annotate** dialog box is displayed, choose to share the same annotation (comment) for all updates, or to annotate each change individually.</span></span>  
  
3.  <span data-ttu-id="649dc-117">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="649dc-117">Optional.</span></span> <span data-ttu-id="649dc-118">**이 대화 상자를 다시 표시 안 함** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="649dc-118">Select the **Do not show this dialog box again** check box.</span></span> <span data-ttu-id="649dc-119">이후에 언제라도 **설정** 을 선택하고 **게시할 때 게시 및 주석 대화 상자 표시** 확인란을 선택하여 대화 상자를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="649dc-119">You can always show the dialog box in the future by choosing **Settings** and selecting the **Show Publish and Annotate dialog box when publishing** check box.</span></span>  
  
4.  <span data-ttu-id="649dc-120">**게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="649dc-120">Click **Publish**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="649dc-121">워크시트에 새 멤버(행)를 추가하는 중이고 MDS 리포지토리에 성공적으로 게시할 수 없으면 사용자에게 워크시트에 있는 모든 특성에 대한 **업데이트** 권한이 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="649dc-121">If you are adding new members (rows) to your worksheet and you cannot successfully publish them to the MDS repository, you may not have **Update** permission to all of the attributes in the worksheet.</span></span> <span data-ttu-id="649dc-122">**검토** 탭의 **변경 내용** 그룹에서 **시트 보호 해제** 를 클릭하여 다시 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="649dc-122">On the **Review** tab, in the **Changes** group, click **Unprotect Sheet** and try to publish again.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="649dc-123">다음 단계</span><span class="sxs-lookup"><span data-stu-id="649dc-123">Next Steps</span></span>  
 [<span data-ttu-id="649dc-124">비즈니스 규칙 적용&#40;Excel용 MDS 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="649dc-124">Apply Business Rules &#40;MDS Add-in for Excel&#41;</span></span>](apply-business-rules-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a><span data-ttu-id="649dc-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="649dc-125">See Also</span></span>  
 <span data-ttu-id="649dc-126">[데이터 &#40;Excel용 MDS 추가 기능&#41;게시](overview-importing-data-from-excel-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="649dc-126">[Publishing Data &#40;MDS Add-in for Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="649dc-127">데이터 유효성 검사&#40;Excel용 MDS 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="649dc-127">Validating Data &#40;MDS Add-in for Excel&#41;</span></span>](validating-data-mds-add-in-for-excel.md)  
  
  
