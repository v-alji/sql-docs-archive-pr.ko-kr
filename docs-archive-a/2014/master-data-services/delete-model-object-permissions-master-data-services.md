---
title: 모델 개체 사용 권한 삭제(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting model object permissions [Master Data Services]
- permissions [Master Data Services], deleting model object permissions
- models [Master Data Services], deleting object permissions
ms.assetid: 859c5952-f600-4940-8064-1afd13f7f6dc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 98da869476e597d76a83b0b86cc9e6e4274a25e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731843"
---
# <a name="delete-model-object-permissions-master-data-services"></a><span data-ttu-id="777c2-102">모델 개체 사용 권한 삭제(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="777c2-102">Delete Model Object Permissions (Master Data Services)</span></span>
  <span data-ttu-id="777c2-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 모델 개체 사용 권한을 삭제하여 모든 할당을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="777c2-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete model object permissions to remove any assignments that have been made.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="777c2-104">필수 조건</span><span class="sxs-lookup"><span data-stu-id="777c2-104">Prerequisites</span></span>  
 <span data-ttu-id="777c2-105">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="777c2-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="777c2-106">**사용자 및 그룹 권한** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="777c2-106">You must have permission to access the **Users and Group Permissions** functional area.</span></span>  
  
-   <span data-ttu-id="777c2-107">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="777c2-107">You must be a model administrator.</span></span> <span data-ttu-id="777c2-108">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="777c2-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-model-object-permissions"></a><span data-ttu-id="777c2-109">모델 개체 사용 권한을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="777c2-109">To delete model object permissions</span></span>  
  
1.  <span data-ttu-id="777c2-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **사용자 및 그룹 권한**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="777c2-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="777c2-111">**사용자** 또는 **그룹** 페이지에서 편집하려는 사용자나 그룹의 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="777c2-111">On the **Users** or **Groups** page, select the row for the user or group that you want to edit.</span></span>  
  
3.  <span data-ttu-id="777c2-112">**선택한 사용자 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="777c2-112">Click **Edit selected user**.</span></span>  
  
4.  <span data-ttu-id="777c2-113">**모델** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="777c2-113">Click the **Models** tab.</span></span>  
  
5.  <span data-ttu-id="777c2-114">또는 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="777c2-114">Optionally, select a model from the **Model** list.</span></span>  
  
6.  <span data-ttu-id="777c2-115">**모델 권한 요약** 창에서 삭제 하려는 사용 권한의 행을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="777c2-115">In the **Model Permission Summary** pane, select the row for the permission that you want to delete.</span></span>  
  
7.  <span data-ttu-id="777c2-116">**선택한 사용 권한 삭제**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="777c2-116">Click **Delete selected permission**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="777c2-117">사용 권한이 그룹에서 상속되는 경우에는 사용자로부터 사용 권한을 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="777c2-117">You cannot remove a permission from a user if the permission is inherited from a group.</span></span> <span data-ttu-id="777c2-118">대신 그룹에서 사용 권한을 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="777c2-118">You must remove the permission from the group instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="777c2-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="777c2-119">See Also</span></span>  
 <span data-ttu-id="777c2-120">[모델 개체 사용 권한 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="777c2-120">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="777c2-121">모델 개체 사용 권한 할당&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="777c2-121">Assign Model Object Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)  
  
  
