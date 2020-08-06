---
title: 멤버 또는 컬렉션 다시 활성화(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], reactivating
- consolidated members [Master Data Services], reactivating
- reactivating members [Master Data Services]
- members [Master Data Services], reactivating
- reactivating collections [Master Data Services]
- leaf members [Master Data Services], reactivating
ms.assetid: bb4884c0-3658-4763-92d1-636804278b1c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c449a5a277128bbca6ae24e848bcf12cb0881968
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653490"
---
# <a name="reactivate-a-member-or-collection-master-data-services"></a><span data-ttu-id="d478b-102">멤버 또는 컬렉션 다시 활성화(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d478b-102">Reactivate a Member or Collection (Master Data Services)</span></span>
  <span data-ttu-id="d478b-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서는 다음과 같은 멤버를 다시 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d478b-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can reactivate a member that was either:</span></span>  
  
-   <span data-ttu-id="d478b-104">준비 프로세스로 비활성화된 멤버</span><span class="sxs-lookup"><span data-stu-id="d478b-104">Deactivated by the staging process.</span></span>  
  
-   <span data-ttu-id="d478b-105">MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]에서 삭제된 멤버</span><span class="sxs-lookup"><span data-stu-id="d478b-105">Deleted in the MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].</span></span>  
  
-   <span data-ttu-id="d478b-106">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 웹 애플리케이션에서 삭제된 멤버</span><span class="sxs-lookup"><span data-stu-id="d478b-106">Deleted in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
 <span data-ttu-id="d478b-107">멤버를 다시 활성화하면 계층 및 컬렉션에서 해당 특성 및 멤버 자격이 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="d478b-107">When you reactivate a member, its attributes and its membership in hierarchies and collections are restored.</span></span>  
  
 <span data-ttu-id="d478b-108">또한 컬렉션을 다시 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d478b-108">You can also reactivate collections.</span></span> <span data-ttu-id="d478b-109">컬렉션을 다시 활성화하면 컬렉션의 특성과 컬렉션에 속하는 멤버가 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="d478b-109">When you do, the collection's attributes and the members that belong to the collection are restored.</span></span>  
  
 <span data-ttu-id="d478b-110">컬렉션이나 멤버를 다시 활성화하면 이전 트랜잭션이 모두 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="d478b-110">When either a collection or member is reactivated, all previous transactions are restored.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d478b-111">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="d478b-111">Prerequisites</span></span>  
 <span data-ttu-id="d478b-112">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="d478b-112">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="d478b-113">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서는 **버전 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d478b-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], you must have permission to the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="d478b-114">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d478b-114">You must be a model administrator.</span></span> <span data-ttu-id="d478b-115">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d478b-115">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-reactivate-a-member-or-collection"></a><span data-ttu-id="d478b-116">멤버 또는 컬렉션을 다시 활성화하려면</span><span class="sxs-lookup"><span data-stu-id="d478b-116">To reactivate a member or collection</span></span>  
  
1.  <span data-ttu-id="d478b-117">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 홈 페이지에서 **버전 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d478b-117">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="d478b-118">메뉴 모음에서 **트랜잭션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d478b-118">On the menu bar, click **Transactions**.</span></span>  
  
3.  <span data-ttu-id="d478b-119">**트랜잭션** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d478b-119">On the **Transactions** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="d478b-120">**버전** 목록에서 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d478b-120">From the **Version** list, select a version.</span></span>  
  
5.  <span data-ttu-id="d478b-121">**트랜잭션** 창에서 다시 활성화할 멤버 또는 컬렉션의 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d478b-121">In the **Transactions** pane, click the row for the member or collection you want to reactivate.</span></span> <span data-ttu-id="d478b-122">이 행의 **이전 값** 열에 **활성** 이 표시되고 **새 값** 열에 **비활성화됨** 이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d478b-122">This row should have **Active** displayed in the **Prior Value** column and **De-Activated** in the **New Value** column.</span></span>  
  
6.  <span data-ttu-id="d478b-123">**트랜잭션 되돌리기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d478b-123">Click **Reverse Transaction**.</span></span>  
  
7.  <span data-ttu-id="d478b-124">확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d478b-124">On the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="d478b-125">새 트랜잭션이 추가되고 **새 값** 열에 **활성** 이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d478b-125">A new transaction is added, showing **Active** in the **New Value** column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d478b-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d478b-126">See Also</span></span>  
 <span data-ttu-id="d478b-127">[준비 프로세스를 사용 하 여 멤버를 비활성화 하거나 삭제 &#40;MDS(Master Data Services)&#41;](add-update-and-delete-data-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d478b-127">[Deactivate or Delete Members by Using the Staging Process &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md) </span></span>  
 <span data-ttu-id="d478b-128">[MDS(Master Data Services) &#40;멤버 또는 컬렉션을 삭제&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d478b-128">[Delete a Member or Collection &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md) </span></span>  
 <span data-ttu-id="d478b-129">[멤버가 MDS(Master Data Services)를 &#40;&#41;](../../2014/master-data-services/members-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d478b-129">[Members &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span></span>  
 [<span data-ttu-id="d478b-130">컬렉션&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d478b-130">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)  
  
  
