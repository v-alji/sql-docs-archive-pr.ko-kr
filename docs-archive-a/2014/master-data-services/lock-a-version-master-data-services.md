---
title: 버전 잠금(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- versions [Master Data Services], locking
- locking versions [Master Data Services]
ms.assetid: 7bb62a84-12d8-4b29-9b6e-6aa25410618e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 68ef979b14d9bd228c7ca89a260b31b2fc6efccd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738458"
---
# <a name="lock-a-version-master-data-services"></a><span data-ttu-id="37b38-102">버전 잠금(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="37b38-102">Lock a Version (Master Data Services)</span></span>
  <span data-ttu-id="37b38-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 모델의 멤버 및 특성이 변경되지 않도록 모델의 버전을 잠급니다.</span><span class="sxs-lookup"><span data-stu-id="37b38-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], lock a version of a model to prevent changes to the model's members and their attributes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="37b38-104">버전이 잠긴 경우 모델 관리자는 멤버를 계속 추가, 편집 및 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37b38-104">When a version is locked, model administrators can continue to add, edit, and remove members.</span></span> <span data-ttu-id="37b38-105">모델에 대한 사용 권한이 있는 다른 사용자는 멤버를 볼 수만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37b38-105">Other users with permission to the model can view members only.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="37b38-106">필수 조건</span><span class="sxs-lookup"><span data-stu-id="37b38-106">Prerequisites</span></span>  
 <span data-ttu-id="37b38-107">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="37b38-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="37b38-108">**버전 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37b38-108">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="37b38-109">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37b38-109">You must be a model administrator.</span></span> <span data-ttu-id="37b38-110">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="37b38-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="37b38-111">버전의 상태가 **열림**이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37b38-111">The version's status must be **Open**.</span></span>  
  
### <a name="to-lock-a-version"></a><span data-ttu-id="37b38-112">버전을 잠그려면</span><span class="sxs-lookup"><span data-stu-id="37b38-112">To lock a version</span></span>  
  
1.  <span data-ttu-id="37b38-113">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **버전 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="37b38-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="37b38-114">**버전 관리** 페이지에서 잠그려는 버전의 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="37b38-114">On the **Manage Versions** page, select the row for the version that you want to lock.</span></span>  
  
3.  <span data-ttu-id="37b38-115">**잠금**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="37b38-115">Click **Lock**.</span></span>  
  
4.  <span data-ttu-id="37b38-116">확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="37b38-116">In the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="37b38-117">다음 단계</span><span class="sxs-lookup"><span data-stu-id="37b38-117">Next Steps</span></span>  
  
-   [<span data-ttu-id="37b38-118">비즈니스 규칙에 대해 버전 유효성 검사&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="37b38-118">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   [<span data-ttu-id="37b38-119">버전 커밋&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="37b38-119">Commit a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/commit-a-version-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="37b38-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="37b38-120">See Also</span></span>  
 <span data-ttu-id="37b38-121">[버전 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/versions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="37b38-121">[Versions &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md) </span></span>  
 [<span data-ttu-id="37b38-122">버전 잠금 해제&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="37b38-122">Unlock a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/unlock-a-version-master-data-services.md)  
  
  
