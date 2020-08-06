---
title: OData 원본 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4fde5bb0-6d78-4ec4-8f0b-67f91c53fe99
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8139f79ed595ca3e6204f96823f6bc95e6fb40df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741140"
---
# <a name="odata-source-properties"></a><span data-ttu-id="110ff-102">OData 원본 속성</span><span class="sxs-lookup"><span data-stu-id="110ff-102">OData Source Properties</span></span>
  <span data-ttu-id="110ff-103">데이터 흐름에서 **OData 원본** 을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭하면 **속성** 창에 **OData 원본** 구성 요소의 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="110ff-103">When you right-click **OData Source** in the data flow and click **Properties**, you will see properties for the **OData Source** component in the **Properties** window.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="110ff-104">속성</span><span class="sxs-lookup"><span data-stu-id="110ff-104">Property</span></span>|<span data-ttu-id="110ff-105">설명</span><span class="sxs-lookup"><span data-stu-id="110ff-105">Description</span></span>|  
|<span data-ttu-id="110ff-106">CollectionName</span><span class="sxs-lookup"><span data-stu-id="110ff-106">CollectionName</span></span>|<span data-ttu-id="110ff-107">OData 서비스에서 검색할 컬렉션의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="110ff-107">Name of the collection you wish to retrieve from the OData service.</span></span> <span data-ttu-id="110ff-108">**CollectionName** 속성은 **UseResourcePath** 가 False인 경우 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="110ff-108">The **CollectionName** property is used when **UseResourcePath** is False.</span></span><br /><br /> <span data-ttu-id="110ff-109">이 속성에는 식이 적용될 수 있으므로 속성 값이 런타임에 설정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="110ff-109">This property is expression-able, allowing the value to be set at runtime.</span></span> <span data-ttu-id="110ff-110">그러나 컬렉션의 메타데이터가 디자인 타임에 사용된 메타데이터와 일치하지 않는 경우 유효성 검사 오류가 발생하여 데이터 흐름 실행이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="110ff-110">However, if the metadata of the collection does not match the metadata that was used at design time, a validation error will occur, causing the data flow execution to fail.</span></span>|  
|<span data-ttu-id="110ff-111">DefaultStringLength</span><span class="sxs-lookup"><span data-stu-id="110ff-111">DefaultStringLength</span></span>|<span data-ttu-id="110ff-112">이 값은 최대 길이가 없는 문자열 열의 기본 길이를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="110ff-112">This value specifies default length for string columns that have no max length.</span></span><br /><br /> <span data-ttu-id="110ff-113">**기본값:** 4000</span><span class="sxs-lookup"><span data-stu-id="110ff-113">**Default:** 4000</span></span>|  
|<span data-ttu-id="110ff-114">쿼리</span><span class="sxs-lookup"><span data-stu-id="110ff-114">Query</span></span>|<span data-ttu-id="110ff-115">OData 쿼리 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="110ff-115">The OData query parameters.</span></span> <span data-ttu-id="110ff-116">이 속성에는 식이 적용될 수 있으므로 속성 값이 런타임에 설정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="110ff-116">This property is expression-able and can be set at runtime.</span></span>|  
|<span data-ttu-id="110ff-117">ResourcePath</span><span class="sxs-lookup"><span data-stu-id="110ff-117">ResourcePath</span></span>|<span data-ttu-id="110ff-118">컬렉션 이름을 선택하는 대신 전체 리소스 경로를 지정해야 하는 경우 이 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="110ff-118">Use this property when you need to specify a full resource path, rather than just selecting a collection name.</span></span> <span data-ttu-id="110ff-119">이 속성은 **UseResourcePath** 가 True인 경우 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="110ff-119">This property is used when **UseResourcePath** is True.</span></span>|  
|<span data-ttu-id="110ff-120">UseResourcePath</span><span class="sxs-lookup"><span data-stu-id="110ff-120">UseResourcePath</span></span>|<span data-ttu-id="110ff-121">True로 설정되면 OData 피드 위치를 결정하기 위해 **ResourcePath** 값이 기본 URL에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="110ff-121">When set to True, the **ResourcePath** value is appended to the base URL to determine the OData feed location.</span></span> <span data-ttu-id="110ff-122">False로 설정되면 **CollectionName** 값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="110ff-122">When set to False, the **CollectionName** value is used.</span></span><br /><br /> <span data-ttu-id="110ff-123">**기본값:** 허위</span><span class="sxs-lookup"><span data-stu-id="110ff-123">**Default:** False</span></span>|  
  
  
