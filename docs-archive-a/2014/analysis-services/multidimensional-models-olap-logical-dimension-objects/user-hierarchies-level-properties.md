---
title: 수준 속성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- user hierarchies [Analysis Services]
- hierarchies [Analysis Services], user
ms.assetid: dabb7335-887b-442a-b67c-4901ba1242b7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 553503b9d35142bcc998b4ec12ad2e29d4c66318
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647302"
---
# <a name="level-properties"></a><span data-ttu-id="9bed2-102">수준 속성</span><span class="sxs-lookup"><span data-stu-id="9bed2-102">Level Properties</span></span> 
  <span data-ttu-id="9bed2-103">다음 표에서는 사용자 정의 계층의 수준 속성을 나열하고 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9bed2-103">The following table lists and describes the properties of a level in a user-defined hierarchy.</span></span>  
  
|<span data-ttu-id="9bed2-104">속성</span><span class="sxs-lookup"><span data-stu-id="9bed2-104">Property</span></span>|<span data-ttu-id="9bed2-105">설명</span><span class="sxs-lookup"><span data-stu-id="9bed2-105">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="9bed2-106">설명</span><span class="sxs-lookup"><span data-stu-id="9bed2-106">Description</span></span>|<span data-ttu-id="9bed2-107">수준에 대한 설명을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="9bed2-107">Contains the description of the level.</span></span>|  
|<span data-ttu-id="9bed2-108">HideMemberIf</span><span class="sxs-lookup"><span data-stu-id="9bed2-108">HideMemberIf</span></span>|<span data-ttu-id="9bed2-109">클라이언트 애플리케이션에서 수준의 멤버를 숨길지 여부와 숨길 조건을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9bed2-109">Indicates whether and when a member in a level should be hidden from client applications.</span></span> <span data-ttu-id="9bed2-110">이 속성 값은 다음 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bed2-110">This property can have the following values:</span></span><br /><br /> <span data-ttu-id="9bed2-111">안 함</span><span class="sxs-lookup"><span data-stu-id="9bed2-111">Never</span></span><br /> <span data-ttu-id="9bed2-112">멤버를 숨기지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9bed2-112">Members are never hidden.</span></span> <span data-ttu-id="9bed2-113">기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="9bed2-113">This is the default value.</span></span><br /><br /> <span data-ttu-id="9bed2-114">OnlyChildWithNoName</span><span class="sxs-lookup"><span data-stu-id="9bed2-114">OnlyChildWithNoName</span></span><br /> <span data-ttu-id="9bed2-115">멤버가 부모의 유일한 자식이고 멤버의 이름이 비어 있는 경우 멤버를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="9bed2-115">A member is hidden when the member is the only child of its parent and the member's name is empty.</span></span><br /><br /> <span data-ttu-id="9bed2-116">OnlyChildWithParentName</span><span class="sxs-lookup"><span data-stu-id="9bed2-116">OnlyChildWithParentName</span></span><br /> <span data-ttu-id="9bed2-117">멤버가 부모의 유일한 자식이고 멤버와 부모의 이름이 같을 때 멤버를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="9bed2-117">A member is hidden when the member is the only child of its parent and the member's name is identical to that of its parent.</span></span><br /><br /> <span data-ttu-id="9bed2-118">NoName</span><span class="sxs-lookup"><span data-stu-id="9bed2-118">NoName</span></span><br /> <span data-ttu-id="9bed2-119">멤버의 이름이 비어 있을 때 멤버를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="9bed2-119">A member is hidden when the member's name is empty.</span></span><br /><br /> <span data-ttu-id="9bed2-120">ParentName</span><span class="sxs-lookup"><span data-stu-id="9bed2-120">ParentName</span></span><br /> <span data-ttu-id="9bed2-121">멤버와 부모의 이름이 같을 때 멤버를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="9bed2-121">A member is hidden when the member's name is identical to that of its parent.</span></span>|  
|<span data-ttu-id="9bed2-122">ID</span><span class="sxs-lookup"><span data-stu-id="9bed2-122">ID</span></span>|<span data-ttu-id="9bed2-123">수준의 고유 ID를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="9bed2-123">Contains the unique identifier (ID) of the level.</span></span>|  
|<span data-ttu-id="9bed2-124">이름</span><span class="sxs-lookup"><span data-stu-id="9bed2-124">Name</span></span>|<span data-ttu-id="9bed2-125">수준 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="9bed2-125">Contains the friendly name of the level.</span></span> <span data-ttu-id="9bed2-126">기본적으로 수준 이름은 원본 특성 이름과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9bed2-126">By default, the name of a level is the same as the name of the source attribute.</span></span>|  
|<span data-ttu-id="9bed2-127">SourceAttribute</span><span class="sxs-lookup"><span data-stu-id="9bed2-127">SourceAttribute</span></span>|<span data-ttu-id="9bed2-128">수준의 기반이 되는 원본 특성 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="9bed2-128">Contains the name of the source attribute on which the level is based.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9bed2-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9bed2-129">See Also</span></span>  
 [<span data-ttu-id="9bed2-130">사용자 계층 속성</span><span class="sxs-lookup"><span data-stu-id="9bed2-130">User Hierarchy Properties</span></span>](user-hierarchies-properties.md)  
  
  
