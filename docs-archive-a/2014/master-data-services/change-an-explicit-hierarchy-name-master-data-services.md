---
title: 명시적 계층 이름 변경(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- explicit hierarchies, changing name
ms.assetid: 12991603-474e-4042-b160-b1f7979694b1
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3cb8d1108650395ebd970edbb2ea31f5daebbd27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736478"
---
# <a name="change-an-explicit-hierarchy-name-master-data-services"></a><span data-ttu-id="e7f96-102">명시적 계층 이름 변경(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="e7f96-102">Change an Explicit Hierarchy Name (Master Data Services)</span></span>
  <span data-ttu-id="e7f96-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 명시적 계층의 이름을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7f96-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can change the name of an explicit hierarchy.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e7f96-104">필수 조건</span><span class="sxs-lookup"><span data-stu-id="e7f96-104">Prerequisites</span></span>  
 <span data-ttu-id="e7f96-105">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="e7f96-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="e7f96-106">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f96-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="e7f96-107">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f96-107">You must be a model administrator.</span></span> <span data-ttu-id="e7f96-108">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e7f96-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-change-the-name-of-an-explicit-hierarchy"></a><span data-ttu-id="e7f96-109">명시적 계층의 이름을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="e7f96-109">To change the name of an explicit hierarchy</span></span>  
  
1.  <span data-ttu-id="e7f96-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f96-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="e7f96-111">**모델 뷰** 페이지의 메뉴 모음에서 **관리** 를 가리키고 **엔터티**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f96-111">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="e7f96-112">**엔터티 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f96-112">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="e7f96-113">이름을 바꿀 명시적 계층이 포함된 엔터티의 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f96-113">Select the row for the entity that contains the explicit hierarchy you want to rename.</span></span>  
  
5.  <span data-ttu-id="e7f96-114">**선택한 엔터티 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f96-114">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="e7f96-115">**엔터티 편집** 페이지에서 이름을 바꾸려는 명시적 계층을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f96-115">On the **Edit Entity** page, click the explicit hierarchy you want to rename.</span></span>  
  
7.  <span data-ttu-id="e7f96-116">**선택한 계층 편집**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f96-116">Click **Edit selected hierarchy**.</span></span>  
  
8.  <span data-ttu-id="e7f96-117">**명시적 계층 이름** 상자에 계층의 업데이트 된 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f96-117">In the **Explicit hierarchy name** box, type the updated name of the hierarchy.</span></span>  
  
9. <span data-ttu-id="e7f96-118">**계층 저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f96-118">Click **Save hierarchy**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7f96-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e7f96-119">See Also</span></span>  
 <span data-ttu-id="e7f96-120">[명시적 계층 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="e7f96-120">[Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span></span>  
 <span data-ttu-id="e7f96-121">[명시적 계층 &#40;MDS(Master Data Services)를 만듭니다&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="e7f96-121">[Create an Explicit Hierarchy &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) </span></span>  
 [<span data-ttu-id="e7f96-122">명시적 계층 삭제&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e7f96-122">Delete an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-explicit-hierarchy-master-data-services.md)  
  
  
