---
title: 컬렉션에 멤버 추가(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], adding members
ms.assetid: 1a7155e6-2d4a-4ed1-a72c-edb37fa1a46b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ce2038f3bc90a2f17506b0aadaaf9707fa911896
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660661"
---
# <a name="add-members-to-a-collection-master-data-services"></a><span data-ttu-id="15b46-102">컬렉션에 멤버 추가(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="15b46-102">Add Members to a Collection (Master Data Services)</span></span>
  <span data-ttu-id="15b46-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 컬렉션에 리프 멤버 및 통합 멤버를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15b46-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can add leaf and consolidated members to a collection.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="15b46-104">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="15b46-104">Prerequisites</span></span>  
 <span data-ttu-id="15b46-105">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="15b46-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="15b46-106">**탐색기** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15b46-106">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="15b46-107">멤버를 추가할 컬렉션 모델 개체에 대한 **업데이트** 이상의 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15b46-107">You must have a minimum of **Update** permission to the collection model object that you are adding members to.</span></span>  
  
-   <span data-ttu-id="15b46-108">컬렉션이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15b46-108">A collection must exist.</span></span> <span data-ttu-id="15b46-109">자세한 내용은 [컬렉션 만들기&#40;Master Data Services&#41;](create-a-collection-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15b46-109">For more information, see [Create a Collection &#40;Master Data Services&#41;](create-a-collection-master-data-services.md).</span></span>  
  
### <a name="to-add-members-to-a-collection"></a><span data-ttu-id="15b46-110">컬렉션에 멤버를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="15b46-110">To add members to a collection</span></span>  
  
1.  <span data-ttu-id="15b46-111">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 홈 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15b46-111">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="15b46-112">**버전** 목록에서 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15b46-112">From the **Version** list, select a version.</span></span>  
  
3.  <span data-ttu-id="15b46-113">**탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15b46-113">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="15b46-114">메뉴 모음에서 **컬렉션** 을 가리키고 *entity_name*을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15b46-114">From the menu bar, point to **Collections** and click *entity_name*.</span></span>  
  
5.  <span data-ttu-id="15b46-115">표 형태에서 멤버를 삭제할 컬렉션 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15b46-115">In the grid, click the row for the collection you want to add members to.</span></span>  
  
6.  <span data-ttu-id="15b46-116">**컬렉션 멤버** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15b46-116">Click the **Collection Members** tab.</span></span>  
  
7.  <span data-ttu-id="15b46-117">**멤버 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15b46-117">Click **Edit Members**.</span></span>  
  
8.  <span data-ttu-id="15b46-118">사용 가능한 멤버 목록을 필터링하려면 목록 왼쪽에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15b46-118">To filter the list of available members, select from the list on the left.</span></span>  
  
9. <span data-ttu-id="15b46-119">추가할 멤버가 있는 행을 클릭하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15b46-119">Click the row with the member you want to add and click **Add**.</span></span>  
  
10. <span data-ttu-id="15b46-120">필요에 따라 **위로** 또는 **아래로**를 클릭하여 컬렉션 멤버를 다시 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="15b46-120">Optionally, rearrange collection members by clicking **Up** or **Down**.</span></span>  
  
11. <span data-ttu-id="15b46-121">필요에 따라 **가중치** 열에서 값을 클릭하여 가중치를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="15b46-121">Optionally, set weight values by clicking the value in the **Weight** column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15b46-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15b46-122">See Also</span></span>  
 [<span data-ttu-id="15b46-123">컬렉션&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="15b46-123">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)  
  
  
