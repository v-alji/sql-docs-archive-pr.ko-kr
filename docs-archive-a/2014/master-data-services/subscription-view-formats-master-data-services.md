---
title: 구독 뷰 형식(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: ff1e2566-ac8f-467d-a6d9-12c3f13879b9
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: da2fbc6f3f4c4f577f432cb048c6f392981baf3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661210"
---
# <a name="subscription-view-formats-master-data-services"></a><span data-ttu-id="dbbdb-102">구독 뷰 형식(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="dbbdb-102">Subscription View Formats (Master Data Services)</span></span>
  <span data-ttu-id="dbbdb-103">선택한 엔터티 또는 파생 계층을 기준으로, 다음 형식을 구독 뷰에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-103">Based on the entity or derived hierarchy you select, the following formats are available for your subscription view.</span></span>  
  
## <a name="subscription-view-formats"></a><span data-ttu-id="dbbdb-104">구독 뷰 형식</span><span class="sxs-lookup"><span data-stu-id="dbbdb-104">Subscription View Formats</span></span>  
  
|<span data-ttu-id="dbbdb-105">Name</span><span class="sxs-lookup"><span data-stu-id="dbbdb-105">Name</span></span>|<span data-ttu-id="dbbdb-106">Description</span><span class="sxs-lookup"><span data-stu-id="dbbdb-106">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="dbbdb-107">**리프 멤버**</span><span class="sxs-lookup"><span data-stu-id="dbbdb-107">**Leaf Members**</span></span>|<span data-ttu-id="dbbdb-108">리프 멤버 및 해당 특성 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-108">Contains leaf members and their associated attribute values.</span></span>|  
|<span data-ttu-id="dbbdb-109">**통합 멤버**</span><span class="sxs-lookup"><span data-stu-id="dbbdb-109">**Consolidated Members**</span></span>|<span data-ttu-id="dbbdb-110">통합 멤버 및 해당 특성 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-110">Contains consolidated members and their associated attribute values.</span></span>|  
|<span data-ttu-id="dbbdb-111">**컬렉션 멤버 자격**</span><span class="sxs-lookup"><span data-stu-id="dbbdb-111">**Collection Memberships**</span></span>|<span data-ttu-id="dbbdb-112">컬렉션 목록 및 해당 특성 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-112">Contains a list of collections and their associated attribute values.</span></span>|  
|<span data-ttu-id="dbbdb-113">**컬렉션**</span><span class="sxs-lookup"><span data-stu-id="dbbdb-113">**Collections**</span></span>|<span data-ttu-id="dbbdb-114">컬렉션 목록 및 각 멤버를 가중치 및 정렬 순서와 함께 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-114">Contains a list of collections and the members in each, along with weight values and sort order.</span></span>|  
|<span data-ttu-id="dbbdb-115">**명시적 부모 자식**</span><span class="sxs-lookup"><span data-stu-id="dbbdb-115">**Explicit Parent Child**</span></span>|<span data-ttu-id="dbbdb-116">엔터티의 명시적 계층 구조를 부모 자식 형식으로 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-116">Contains explicit hierarchy structures for an entity in a parent child format.</span></span>|  
|<span data-ttu-id="dbbdb-117">**명시적 수준**</span><span class="sxs-lookup"><span data-stu-id="dbbdb-117">**Explicit Levels**</span></span>|<span data-ttu-id="dbbdb-118">엔터티의 명시적 계층 구조를 수준 형식으로 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-118">Contains explicit hierarchy structures for an entity in level format.</span></span>|  
|<span data-ttu-id="dbbdb-119">**파생 부모 자식(파생 계층 뷰)**</span><span class="sxs-lookup"><span data-stu-id="dbbdb-119">**Derived Parent Child (Derived Hierarchy View)**</span></span>|<span data-ttu-id="dbbdb-120">파생 계층 구조를 부모 자식 형식으로 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-120">Contains a derived hierarchy structure in parent child format.</span></span>|  
|<span data-ttu-id="dbbdb-121">**파생 수준(파생 계층 뷰)**</span><span class="sxs-lookup"><span data-stu-id="dbbdb-121">**Derived Levels (Derived Hierarchy View)**</span></span>|<span data-ttu-id="dbbdb-122">파생 계층 구조를 수준 형식으로 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-122">Contains a derived hierarchy structure in level format.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dbbdb-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dbbdb-123">See Also</span></span>  
 <span data-ttu-id="dbbdb-124">[데이터 &#40;MDS(Master Data Services)&#41;내보내기](overview-exporting-data-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="dbbdb-124">[Exporting Data &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md) </span></span>  
 [<span data-ttu-id="dbbdb-125">MDS(Master Data Services) &#40;구독 뷰를 만듭니다&#41;</span><span class="sxs-lookup"><span data-stu-id="dbbdb-125">Create a Subscription View &#40;Master Data Services&#41;</span></span>](create-a-subscription-view-to-export-data-master-data-services.md)  
  
  
