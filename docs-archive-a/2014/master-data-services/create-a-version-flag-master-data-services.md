---
title: 버전 플래그 만들기(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating version flags [Master Data Services]
- version flags [Master Data Services], creating
- versions [Master Data Services], creating flags
ms.assetid: 3067e1e3-05b7-4f11-9206-c612ef4e7e42
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f04c93f8315ccd5b53e07db169783da53afe0156
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652885"
---
# <a name="create-a-version-flag-master-data-services"></a><span data-ttu-id="afd97-102">버전 플래그 만들기(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="afd97-102">Create a Version Flag (Master Data Services)</span></span>
  <span data-ttu-id="afd97-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 버전에 할당할 버전 플래그를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="afd97-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a version flag to assign to a version.</span></span> <span data-ttu-id="afd97-104">플래그는 사용자나 구독 시스템에서 사용해야 하는 버전을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afd97-104">The flag can indicate the version that users or subscribing systems should use.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="afd97-105">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="afd97-105">Prerequisites</span></span>  
 <span data-ttu-id="afd97-106">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="afd97-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="afd97-107">**버전 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="afd97-107">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="afd97-108">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="afd97-108">You must be a model administrator.</span></span> <span data-ttu-id="afd97-109">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="afd97-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-create-a-version-flag"></a><span data-ttu-id="afd97-110">버전 플래그를 만들려면</span><span class="sxs-lookup"><span data-stu-id="afd97-110">To create a version flag</span></span>  
  
1.  <span data-ttu-id="afd97-111">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **버전 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="afd97-111">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="afd97-112">**버전 관리** 페이지의 메뉴 모음에서 **관리** 를 가리킨 다음 **플래그**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="afd97-112">On the **Manage Versions** page, from the menu bar, point to **Manage** and then click **Flags**.</span></span>  
  
3.  <span data-ttu-id="afd97-113">**버전 플래그 관리** 페이지의 **모델** 필드에서 플래그를 만들 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="afd97-113">On the **Manage Version Flags** page, from the **Model** field, select the model for which you want to create a flag.</span></span>  
  
4.  <span data-ttu-id="afd97-114">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="afd97-114">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="afd97-115">**이름** 상자에 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="afd97-115">In the **Name** box, type a name.</span></span>  
  
6.  <span data-ttu-id="afd97-116">**설명** 상자에 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="afd97-116">In the **Description** box, type a description.</span></span>  
  
7.  <span data-ttu-id="afd97-117">상태가 **커밋됨** 인 버전에만 플래그를 할당할 수 있도록 지정하려면 **커밋된 버전만** 필드에서 **True** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="afd97-117">In the **Committed Versions Only** field, select **True** to indicate that the flag can be assigned to versions with a status of **Committed** only.</span></span> <span data-ttu-id="afd97-118">모든 상태의 버전에 플래그를 할당할 수 있도록 지정하려면 **False** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="afd97-118">Select **False** to indicate that the flag can be assigned to versions with any status.</span></span>  
  
8.  <span data-ttu-id="afd97-119">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="afd97-119">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="afd97-120">다음 단계</span><span class="sxs-lookup"><span data-stu-id="afd97-120">Next Steps</span></span>  
  
-   [<span data-ttu-id="afd97-121">버전에 플래그 할당&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="afd97-121">Assign a Flag to a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="afd97-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="afd97-122">See Also</span></span>  
 <span data-ttu-id="afd97-123">[버전 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/versions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="afd97-123">[Versions &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md) </span></span>  
 [<span data-ttu-id="afd97-124">버전 플래그 이름 변경&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="afd97-124">Change a Version Flag Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-version-flag-name-master-data-services.md)  
  
  
