---
title: 버전 커밋(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- committing versions [Master Data Services]
- versions [Master Data Services], committing
ms.assetid: 6b967a39-b333-4b84-9e5f-4fb07e156826
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cec3244d4ddaa78d9168e3ede503fa16756633a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731859"
---
# <a name="commit-a-version-master-data-services"></a><span data-ttu-id="03b61-102">버전 커밋(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="03b61-102">Commit a Version (Master Data Services)</span></span>
  <span data-ttu-id="03b61-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 모델의 멤버 및 특성이 변경되지 않게 하려면 모델의 버전을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="03b61-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], commit a version of a model to prevent changes to the model's members and their attributes.</span></span> <span data-ttu-id="03b61-104">커밋된 버전의 잠금은 해제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="03b61-104">Committed versions cannot be unlocked.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="03b61-105">필수 조건</span><span class="sxs-lookup"><span data-stu-id="03b61-105">Prerequisites</span></span>  
 <span data-ttu-id="03b61-106">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="03b61-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="03b61-107">**버전 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03b61-107">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="03b61-108">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03b61-108">You must be a model administrator.</span></span> <span data-ttu-id="03b61-109">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="03b61-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="03b61-110">버전의 상태가 **잠금**이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03b61-110">The version's status must be **Locked**.</span></span> <span data-ttu-id="03b61-111">자세한 내용은 [버전 잠금&#40;Master Data Services&#41;](../../2014/master-data-services/lock-a-version-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="03b61-111">For more information, see [Lock a Version &#40;Master Data Services&#41;](../../2014/master-data-services/lock-a-version-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="03b61-112">모든 멤버가 유효성 검사를 통과해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03b61-112">All members must have validated successfully.</span></span>  
  
### <a name="to-commit-a-version"></a><span data-ttu-id="03b61-113">버전을 커밋하려면</span><span class="sxs-lookup"><span data-stu-id="03b61-113">To commit a version</span></span>  
  
1.  <span data-ttu-id="03b61-114">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **버전 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="03b61-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="03b61-115">**버전 관리** 페이지의 메뉴 모음에서 **버전 유효성 검사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="03b61-115">On the **Manage Versions** page, on the menu bar, click **Validate Version**.</span></span>  
  
3.  <span data-ttu-id="03b61-116">**버전 유효성 검사** 페이지에서 커밋하려는 모델과 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="03b61-116">On the **Validate Version** page, select the model and version you want to commit.</span></span>  
  
4.  <span data-ttu-id="03b61-117">**커밋**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="03b61-117">Click **Commit**.</span></span>  
  
5.  <span data-ttu-id="03b61-118">확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="03b61-118">In the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="03b61-119">다음 단계</span><span class="sxs-lookup"><span data-stu-id="03b61-119">Next Steps</span></span>  
  
-   [<span data-ttu-id="03b61-120">버전 플래그 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="03b61-120">Create a Version Flag &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-version-flag-master-data-services.md)  
  
-   [<span data-ttu-id="03b61-121">버전에 플래그 할당&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="03b61-121">Assign a Flag to a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
-   [<span data-ttu-id="03b61-122">버전 복사&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="03b61-122">Copy a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/copy-a-version-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="03b61-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="03b61-123">See Also</span></span>  
 [<span data-ttu-id="03b61-124">버전&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="03b61-124">Versions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/versions-master-data-services.md)  
  
  
