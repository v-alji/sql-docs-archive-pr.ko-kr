---
title: 구독 뷰 만들기 (MDS(Master Data Services)) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- subscription views [Master Data Services], creating
- creating subscription views [Master Data Services]
ms.assetid: a5e28961-af16-414a-9845-d2e06aac5214
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e5e2b901e56d75e97a444fd2858ef95872f3b766
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652888"
---
# <a name="create-a-subscription-view-master-data-services"></a><span data-ttu-id="f8031-102">구독 뷰 만들기(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f8031-102">Create a Subscription View (Master Data Services)</span></span>
  <span data-ttu-id="f8031-103">구독 시스템에서 사용할 데이터베이스의 데이터 뷰를 만들려면 구독 뷰를 만듭니다 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f8031-103">Create a subscription view when you want to create a view of your data in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database for use by subscribing systems.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f8031-104">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="f8031-104">Prerequisites</span></span>  
 <span data-ttu-id="f8031-105">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="f8031-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="f8031-106">**통합 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8031-106">You must have permission to access the **Integration Management** functional area.</span></span>  
  
-   <span data-ttu-id="f8031-107">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8031-107">You must be a model administrator.</span></span> <span data-ttu-id="f8031-108">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f8031-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-create-a-subscription-view"></a><span data-ttu-id="f8031-109">구독 뷰를 만들려면</span><span class="sxs-lookup"><span data-stu-id="f8031-109">To create a subscription view</span></span>  
  
1.  <span data-ttu-id="f8031-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **통합 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f8031-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Integration Management**.</span></span>  
  
2.  <span data-ttu-id="f8031-111">메뉴 모음에서 **뷰 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f8031-111">From the menu bar, click **Create Views**.</span></span>  
  
3.  <span data-ttu-id="f8031-112">**구독 뷰** 페이지에서 **구독 뷰 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8031-112">On the **Subscription Views** page, click **Add subscription view**.</span></span>  
  
4.  <span data-ttu-id="f8031-113">**구독 뷰 만들기** 창의 **구독 뷰 이름** 상자에 뷰의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8031-113">In the **Create Subscription View** pane, in the **Subscription view name** box, type a name for the view.</span></span>  
  
5.  <span data-ttu-id="f8031-114">**모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f8031-114">From the **Model** list, select a model.</span></span>  
  
6.  <span data-ttu-id="f8031-115">**버전** 또는 **버전 플래그** 옵션을 선택한 다음 해당 목록에서를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8031-115">Select either the **Version** or **Version Flag** option, and then select from the corresponding list.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="f8031-116">버전 플래그를 기반으로 구독 뷰를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f8031-116">Create a subscription view based on a version flag.</span></span> <span data-ttu-id="f8031-117">버전을 잠그는 경우에는 구독 뷰를 업데이트하지 않고 플래그를 열린 버전에 다시 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8031-117">When you lock a version, you can reassign the flag to an open version without updating the subscription view.</span></span>  
  
7.  <span data-ttu-id="f8031-118">**엔터티** 또는 **파생 계층** 옵션을 선택 하 고 해당 하는 목록에서 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8031-118">Select either the **Entity** or **Derived hierarchy** option, and then select from the corresponding list.</span></span>  
  
8.  <span data-ttu-id="f8031-119">**형식** 목록에서 구독 뷰 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f8031-119">From the **Format** list, select a subscription view format.</span></span>  
  
9. <span data-ttu-id="f8031-120">**형식** 목록에서 **명시적 수준** 또는 **파생 수준** 을 선택한 경우에는 뷰에 포함할 계층의 수준 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f8031-120">If you chose **Explicit levels** or **Derived levels** from the **Format** list, type the number of levels in the hierarchy to include in the view.</span></span>  
  
10. <span data-ttu-id="f8031-121">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f8031-121">Click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8031-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f8031-122">See Also</span></span>  
 <span data-ttu-id="f8031-123">[데이터 &#40;MDS(Master Data Services)&#41;내보내기](overview-exporting-data-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f8031-123">[Exporting Data &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md) </span></span>  
 <span data-ttu-id="f8031-124">[구독 뷰를 삭제 &#40;MDS(Master Data Services)&#41;](delete-a-subscription-view-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f8031-124">[Delete a Subscription View &#40;Master Data Services&#41;](delete-a-subscription-view-master-data-services.md) </span></span>  
 [<span data-ttu-id="f8031-125">버전 플래그 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f8031-125">Create a Version Flag &#40;Master Data Services&#41;</span></span>](create-a-version-flag-master-data-services.md)  
  
  
