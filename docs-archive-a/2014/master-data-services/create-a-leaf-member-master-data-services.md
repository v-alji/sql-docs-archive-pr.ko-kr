---
title: 리프 멤버 만들기(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- leaf members [Master Data Services], creating
- creating leaf members [Master Data Services]
- members [Master Data Services], creating leaf members
ms.assetid: 0499d3b3-d508-4d43-a740-19cf53ade9f1
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fe0245dd30019e1cb9112754bd8b8eeafed93aa5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638888"
---
# <a name="create-a-leaf-member-master-data-services"></a><span data-ttu-id="f8f19-102">리프 멤버 만들기(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f8f19-102">Create a Leaf Member (Master Data Services)</span></span>
  <span data-ttu-id="f8f19-103">에서는 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 시스템에 마스터 데이터를 추가 하 고 준비 테이블 또는를 사용 하 여 데이터를 가져오지 않으려는 경우 리프 멤버를 만듭니다 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f8f19-103">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], create a leaf member when you want to add master data to your system and are not using staging tables or the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] to import data.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f8f19-104">전제 조건</span><span class="sxs-lookup"><span data-stu-id="f8f19-104">Prerequisites</span></span>  
 <span data-ttu-id="f8f19-105">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="f8f19-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="f8f19-106">**탐색기** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f19-106">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="f8f19-107">멤버를 추가할 엔터티의 리프 모델 개체에 대 한 **업데이트** 이상의 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f19-107">You must have a minimum of **Update** permission to the leaf model object for the entity you are adding a member to.</span></span>  
  
### <a name="to-create-a-leaf-member"></a><span data-ttu-id="f8f19-108">리프 멤버를 만들려면</span><span class="sxs-lookup"><span data-stu-id="f8f19-108">To create a leaf member</span></span>  
  
1.  <span data-ttu-id="f8f19-109">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 홈 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f19-109">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="f8f19-110">사용자의 경우는 **버전** 목록에서 열린 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f19-110">If you are a user, select an open version from the **Version** list.</span></span> <span data-ttu-id="f8f19-111">관리자의 경우는 **버전** 목록에서 열린 상태 또는 잠긴 상태의 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f19-111">If you are an administrator, select a version with open or locked status from the **Version** list.</span></span>  
  
3.  <span data-ttu-id="f8f19-112">**탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f19-112">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="f8f19-113">메뉴 모음에서 **엔터티** 를 가리키고 멤버를 추가하려는 엔터티의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f19-113">From the menu bar, point to **Entities** and click the name of the entity you want to add a member to.</span></span>  
  
5.  <span data-ttu-id="f8f19-114">**멤버 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f19-114">Click **Add member**.</span></span>  
  
6.  <span data-ttu-id="f8f19-115">**세부 정보** 창의 필드에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f19-115">In the **Details** pane, complete the fields.</span></span>  
  
7.  <span data-ttu-id="f8f19-116">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="f8f19-116">Optional.</span></span> <span data-ttu-id="f8f19-117">**주석** 상자에 멤버를 추가한 이유에 대한 주석을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f19-117">In the **Annotations** box, type a comment about why the member was added.</span></span> <span data-ttu-id="f8f19-118">멤버에 액세스할 수 있는 모든 사용자가 주석을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f19-118">All users who have access to the member can view the annotation.</span></span>  
  
8.  <span data-ttu-id="f8f19-119">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f19-119">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8f19-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f8f19-120">See Also</span></span>  
 <span data-ttu-id="f8f19-121">[준비 프로세스를 사용 하 여 MDS(Master Data Services)에서 멤버 로드 또는 업데이트](add-update-and-delete-data-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f8f19-121">[Load or Update Members in Master Data Services by Using the Staging Process](add-update-and-delete-data-master-data-services.md) </span></span>  
 <span data-ttu-id="f8f19-122">[MDS(Master Data Services) &#40;통합 멤버를 만듭니다&#41;](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f8f19-122">[Create a Consolidated Member &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md) </span></span>  
 [<span data-ttu-id="f8f19-123">멤버&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f8f19-123">Members &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/members-master-data-services.md)  
  
  
