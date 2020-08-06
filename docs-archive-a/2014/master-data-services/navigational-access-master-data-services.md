---
title: 탐색 액세스 권한(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- navigational access [Master Data Services]
- security [Master Data Services], navigational access
ms.assetid: 3403b7b0-44e2-48c3-a1b7-9c4612b874b8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7af3c16d98320b6fea3d4611e9e4c6d37c6015bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638867"
---
# <a name="navigational-access-master-data-services"></a><span data-ttu-id="998e5-102">탐색 액세스 권한(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="998e5-102">Navigational Access (Master Data Services)</span></span>
  <span data-ttu-id="998e5-103">탐색 액세스 권한은 **모델** 탭에 지정된 모델 개체 보안에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="998e5-103">Navigational access applies to model object security, which is assigned on the **Models** tab.</span></span>  
  
 <span data-ttu-id="998e5-104">탐색 액세스 권한은 보안 할당 수준보다 높은 수준의 액세스 권한입니다.</span><span class="sxs-lookup"><span data-stu-id="998e5-104">Navigational access is the access you get to levels higher than where you've assigned security.</span></span>  
  
 <span data-ttu-id="998e5-105">이 예에서는 사용 권한이 엔터티에 할당되므로 탐색 액세스 권한은 모델 수준에서 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="998e5-105">In this example, permissions are assigned to an entity, and so navigational access is granted at the model level.</span></span>  
  
 <span data-ttu-id="998e5-106">![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")</span><span class="sxs-lookup"><span data-stu-id="998e5-106">![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")</span></span>  
  
 <span data-ttu-id="998e5-107">**엔터티**</span><span class="sxs-lookup"><span data-stu-id="998e5-107">**Entities**</span></span>  
  
 <span data-ttu-id="998e5-108">엔터티, 엔터티의 리프 멤버 또는 엔터티의 통합 멤버에 사용 권한을 할당할 경우 탐색 액세스 권한을 통해 모든 멤버의 이름 및 코드를 읽거나 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="998e5-108">When you assign permission to an entity, its leaf members, or its consolidated members, navigational access means you can read or update the name and code for all members.</span></span> <span data-ttu-id="998e5-109">모델 이름을 읽을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="998e5-109">You can also read the model name.</span></span>  
  
 <span data-ttu-id="998e5-110">**특성**</span><span class="sxs-lookup"><span data-stu-id="998e5-110">**Attributes**</span></span>  
  
 <span data-ttu-id="998e5-111">특성에 사용 권한을 할당할 경우 탐색 액세스 권한을 통해 엔터티에 있는 모든 멤버의 이름 및 코드를 읽거나 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="998e5-111">When you assign permission to an attribute, navigational access means you can read or update the name and code for all members in the entity.</span></span> <span data-ttu-id="998e5-112">모델 이름을 읽을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="998e5-112">You can also read the model name.</span></span>  
  
 <span data-ttu-id="998e5-113">**컬렉션**</span><span class="sxs-lookup"><span data-stu-id="998e5-113">**Collections**</span></span>  
  
 <span data-ttu-id="998e5-114">컬렉션에 사용 권한을 할당할 경우 이름, 코드, 설명 및 소유자 ID를 읽거나 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="998e5-114">When you assign permissions to collections, you can read or update the name, code, description and owner ID.</span></span> <span data-ttu-id="998e5-115">모델 이름을 읽을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="998e5-115">You can also read the model name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="998e5-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="998e5-116">See Also</span></span>  
 [<span data-ttu-id="998e5-117">사용 권한이 결정되는 방식&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="998e5-117">How Permissions Are Determined &#40;Master Data Services&#41;</span></span>](how-permissions-are-determined-master-data-services.md)  
  
  
