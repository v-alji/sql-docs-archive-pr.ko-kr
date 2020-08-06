---
title: 그룹 추가(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- groups [Master Data Services], adding
- adding groups [Master Data Services]
ms.assetid: c7a88381-3b2c-4af7-9cf7-3a930c1abdee
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8f9da1d558ccb648af8fbc0dd3b802751bd5ae44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736484"
---
# <a name="add-a-group-master-data-services"></a><span data-ttu-id="603c4-102">그룹 추가(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="603c4-102">Add a Group (Master Data Services)</span></span>
  <span data-ttu-id="603c4-103">**의** 그룹 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 목록에 그룹을 추가하여 웹 애플리케이션에 사용 권한을 할당하는 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="603c4-103">Add a group to the **Groups** list in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] to begin the process of assigning permission to the Web application.</span></span> <span data-ttu-id="603c4-104">그룹의 사용자가 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에 액세스할 수 있게 하려면 하나 이상의 기능 영역과 모델 개체에 그룹 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="603c4-104">Before a user in the group can access [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], you must give the group permission to one or more functional areas and model objects.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="603c4-105">필수 조건</span><span class="sxs-lookup"><span data-stu-id="603c4-105">Prerequisites</span></span>  
 <span data-ttu-id="603c4-106">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="603c4-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="603c4-107">**사용자 및 그룹 권한** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="603c4-107">You must have permission to access the **Users and Group Permissions** functional area.</span></span>  
  
### <a name="to-add-a-group"></a><span data-ttu-id="603c4-108">그룹을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="603c4-108">To add a group</span></span>  
  
1.  <span data-ttu-id="603c4-109">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **사용자 및 그룹 권한**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="603c4-109">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="603c4-110">**사용자** 페이지의 메뉴 모음에서 **그룹 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="603c4-110">On the **Users** page, from the menu bar, click **Manage Groups**.</span></span>  
  
3.  <span data-ttu-id="603c4-111">**그룹 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="603c4-111">Click **Add groups**.</span></span>  
  
4.  <span data-ttu-id="603c4-112">*domain\group_name* 또는 *computer\group_name*과 같이 Active Directory 도메인 이름이나 서버 컴퓨터 이름과 그룹 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="603c4-112">Type the group's name preceded by the Active Directory domain name or by the server computer's name, as in *domain\group_name* or *computer\group_name*.</span></span>  
  
5.  <span data-ttu-id="603c4-113">또는 **이름 확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="603c4-113">Optionally, click **Check names**.</span></span>  
  
6.  <span data-ttu-id="603c4-114">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="603c4-114">Click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="603c4-115">사용자가 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에 처음으로 액세스하면 사용자의 이름이 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 사용자 목록에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="603c4-115">When the user first accesses [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], the user's name is added to the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] list of users.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="603c4-116">다음 단계</span><span class="sxs-lookup"><span data-stu-id="603c4-116">Next Steps</span></span>  
  
-   [<span data-ttu-id="603c4-117">기능 영역 권한 할당&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="603c4-117">Assign Functional Area Permissions &#40;Master Data Services&#41;</span></span>](assign-functional-area-permissions-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="603c4-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="603c4-118">See Also</span></span>  
 [<span data-ttu-id="603c4-119">보안&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="603c4-119">Security &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/security-master-data-services.md)  
  
  
