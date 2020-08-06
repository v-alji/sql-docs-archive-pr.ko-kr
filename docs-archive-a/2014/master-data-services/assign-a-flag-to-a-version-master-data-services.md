---
title: 버전에 플래그 할당(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- version flags [Master Data Services], assigning flags
- versions [Master Data Services], assigning flags
ms.assetid: 6629ec7e-32e7-4a1e-8b31-eb43c5923766
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2de0d0d8d8ea96814e13b9123fe4fcd4782d6bef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660658"
---
# <a name="assign-a-flag-to-a-version-master-data-services"></a><span data-ttu-id="c52f2-102">버전에 플래그 할당(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="c52f2-102">Assign a Flag to a Version (Master Data Services)</span></span>
  <span data-ttu-id="c52f2-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 사용자나 구독 시스템에서 사용해야 하는 버전을 지정하려면 버전에 플래그를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="c52f2-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], assign a flag to a version to indicate the version that users or subscribing systems should use.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c52f2-104">버전 플래그는 한 번에 한 버전에만 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c52f2-104">Version flags can be assigned to only one version at a time.</span></span> <span data-ttu-id="c52f2-105">다른 버전에 이미 할당되어 있는 플래그를 할당하는 경우에는 플래그가 선택한 버전으로 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="c52f2-105">If you assign a flag that is already assigned to another version, the flag is moved to the version you selected.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c52f2-106">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="c52f2-106">Prerequisites</span></span>  
 <span data-ttu-id="c52f2-107">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="c52f2-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="c52f2-108">**버전 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c52f2-108">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="c52f2-109">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c52f2-109">You must be a model administrator.</span></span> <span data-ttu-id="c52f2-110">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c52f2-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="c52f2-111">할당하려는 버전 플래그를 미리 만들어 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c52f2-111">You must have created a version flag to assign.</span></span> <span data-ttu-id="c52f2-112">자세한 내용은 [버전 플래그 만들기&#40;Master Data Services&#41;](../../2014/master-data-services/create-a-version-flag-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c52f2-112">For more information, see [Create a Version Flag &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-version-flag-master-data-services.md).</span></span>  
  
### <a name="to-assign-a-flag-to-a-version"></a><span data-ttu-id="c52f2-113">버전에 플래그를 할당하려면</span><span class="sxs-lookup"><span data-stu-id="c52f2-113">To assign a flag to a version</span></span>  
  
1.  <span data-ttu-id="c52f2-114">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **버전 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c52f2-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="c52f2-115">**버전 관리** 페이지에서 플래그를 할당하려는 버전 행의 **플래그** 열에 있는 셀을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c52f2-115">On the **Manage Versions** page, in the row for the version to which you want to assign a flag, double-click the cell in the **Flag** column.</span></span>  
  
3.  <span data-ttu-id="c52f2-116">목록에서 할당할 플래그를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c52f2-116">From the list, select the flag you want to assign.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c52f2-117">원하는 플래그를 사용할 수 없는 경우 **커밋됨** 버전에만 플래그를 사용할 수 있기 때문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c52f2-117">If the flag you want is not available, the flag might be available for **Committed** versions only.</span></span> <span data-ttu-id="c52f2-118">확인하려면 **버전 플래그 관리** 페이지로 이동하여 플래그의 **커밋된 버전만** 필드를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="c52f2-118">To confirm, go to the **Manage Version Flags** page and view the **Committed Versions Only** field for the flag.</span></span>  
  
4.  <span data-ttu-id="c52f2-119">Enter 키를 눌러 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c52f2-119">Press ENTER to save the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c52f2-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c52f2-120">See Also</span></span>  
 <span data-ttu-id="c52f2-121">[MDS(Master Data Services) &#40;버전 플래그를 만듭니다&#41;](../../2014/master-data-services/create-a-version-flag-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="c52f2-121">[Create a Version Flag &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-version-flag-master-data-services.md) </span></span>  
 [<span data-ttu-id="c52f2-122">버전&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="c52f2-122">Versions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/versions-master-data-services.md)  
  
  
