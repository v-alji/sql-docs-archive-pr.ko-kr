---
title: 예약어(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- reserved words [Master Data Services]
- Master Data Services, reserved words
ms.assetid: 88afd0d0-4362-4394-8357-4e65388fc0fc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c54bb371cd8f797cfb36f015387e0e21339c0426
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651749"
---
# <a name="reserved-words-master-data-services"></a><span data-ttu-id="c86c1-102">예약어(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="c86c1-102">Reserved Words (Master Data Services)</span></span>
  <span data-ttu-id="c86c1-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서는 모델 개체 또는 멤버를 만들 때 일부 단어를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c86c1-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], when you create model objects or members, some words cannot be used.</span></span> <span data-ttu-id="c86c1-104">이러한 단어를 사용하면 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c86c1-104">Using these words may cause errors.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c86c1-105">또한 특수 문자(기호, 하이픈 등) 사용을 제한해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c86c1-105">You should also limit your use of special characters (symbols, hyphenation, etc.).</span></span>  
  
-   [<span data-ttu-id="c86c1-106">모델</span><span class="sxs-lookup"><span data-stu-id="c86c1-106">Models</span></span>](#models)  
  
-   [<span data-ttu-id="c86c1-107">엔터티</span><span class="sxs-lookup"><span data-stu-id="c86c1-107">Entities</span></span>](#entities)  
  
-   [<span data-ttu-id="c86c1-108">명시적 계층</span><span class="sxs-lookup"><span data-stu-id="c86c1-108">Explicit Hierarchies</span></span>](#exhierarchies)  
  
-   [<span data-ttu-id="c86c1-109">특성</span><span class="sxs-lookup"><span data-stu-id="c86c1-109">Attributes</span></span>](#attributes)  
  
-   [<span data-ttu-id="c86c1-110">멤버</span><span class="sxs-lookup"><span data-stu-id="c86c1-110">Members</span></span>](#members)  
  
##  <a name="models"></a><a name="models"></a><span data-ttu-id="c86c1-111">모델인</span><span class="sxs-lookup"><span data-stu-id="c86c1-111">Models</span></span>  
 <span data-ttu-id="c86c1-112">이름으로 설정 된 모델을 만드는 경우 **이름을** 엔터티 **이름으로 사용할**수 없으므로 **모델과 이름이 같은 엔터티 만들기** 를 선택 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="c86c1-112">If you create a model with the name set to **Name**, do not select **Create entity with same name as model** because **Name** cannot be used for the name of an entity.</span></span>  
  
##  <a name="entities"></a><a name="entities"></a><span data-ttu-id="c86c1-113">엔터티</span><span class="sxs-lookup"><span data-stu-id="c86c1-113">Entities</span></span>  
 <span data-ttu-id="c86c1-114">엔터티 이름의 경우 **Name** 또는 **Code**를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c86c1-114">For entity names, you cannot use **Name** or **Code**.</span></span>  
  
##  <a name="explicit-hierarchies"></a><a name="exhierarchies"></a><span data-ttu-id="c86c1-115">명시적 계층</span><span class="sxs-lookup"><span data-stu-id="c86c1-115">Explicit Hierarchies</span></span>  
 <span data-ttu-id="c86c1-116">명시적 계층 이름의 경우 **Name** 또는 **Code**를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c86c1-116">For explicit hierarchy names, you cannot use **Name** or **Code**.</span></span>  
  
##  <a name="attributes"></a><a name="attributes"></a><span data-ttu-id="c86c1-117">특성</span><span class="sxs-lookup"><span data-stu-id="c86c1-117">Attributes</span></span>  
  
-   <span data-ttu-id="c86c1-118">**ID**</span><span class="sxs-lookup"><span data-stu-id="c86c1-118">**ID**</span></span>  
  
-   <span data-ttu-id="c86c1-119">**코드**</span><span class="sxs-lookup"><span data-stu-id="c86c1-119">**Code**</span></span>  
  
-   <span data-ttu-id="c86c1-120">**이름**</span><span class="sxs-lookup"><span data-stu-id="c86c1-120">**Name**</span></span>  
  
-   <span data-ttu-id="c86c1-121">**EnterDTM**</span><span class="sxs-lookup"><span data-stu-id="c86c1-121">**EnterDTM**</span></span>  
  
-   <span data-ttu-id="c86c1-122">**EnterUserID**</span><span class="sxs-lookup"><span data-stu-id="c86c1-122">**EnterUserID**</span></span>  
  
-   <span data-ttu-id="c86c1-123">**EnterUserName**</span><span class="sxs-lookup"><span data-stu-id="c86c1-123">**EnterUserName**</span></span>  
  
-   <span data-ttu-id="c86c1-124">**LastChgDTM**</span><span class="sxs-lookup"><span data-stu-id="c86c1-124">**LastChgDTM**</span></span>  
  
-   <span data-ttu-id="c86c1-125">**LastChgUserID**</span><span class="sxs-lookup"><span data-stu-id="c86c1-125">**LastChgUserID**</span></span>  
  
-   <span data-ttu-id="c86c1-126">**Status_ID**</span><span class="sxs-lookup"><span data-stu-id="c86c1-126">**Status_ID**</span></span>  
  
-   <span data-ttu-id="c86c1-127">**ValidationStatus_ID**</span><span class="sxs-lookup"><span data-stu-id="c86c1-127">**ValidationStatus_ID**</span></span>  
  
-   <span data-ttu-id="c86c1-128">**Version_ID**</span><span class="sxs-lookup"><span data-stu-id="c86c1-128">**Version_ID**</span></span>  
  
##  <a name="members"></a><a name="members"></a><span data-ttu-id="c86c1-129">멤버</span><span class="sxs-lookup"><span data-stu-id="c86c1-129">Members</span></span>  
 <span data-ttu-id="c86c1-130">멤버의 경우 **코드** 특성 값으로 **MDMMemberStatus** 또는 **ROOT** 를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c86c1-130">For members, you cannot use **MDMMemberStatus** or **ROOT** for the **Code** attribute value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c86c1-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c86c1-131">See Also</span></span>  
 [<span data-ttu-id="c86c1-132">MDS(Master Data Services) 개요</span><span class="sxs-lookup"><span data-stu-id="c86c1-132">Master Data Services Overview</span></span>](master-data-services-overview-mds.md)  
  
  
