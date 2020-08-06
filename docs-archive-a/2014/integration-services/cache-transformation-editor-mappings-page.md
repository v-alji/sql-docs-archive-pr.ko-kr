---
title: 캐시 변환 편집기 (매핑 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.cachetransmap.f1
ms.assetid: ffd53f18-9646-458a-a84a-f2467d601ea5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6bb31e479ea98133da34dcbf257d59e70f4ffe8f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659618"
---
# <a name="cache-transformation-editor-mappings-page"></a><span data-ttu-id="f9f55-102">캐시 변환 편집기(매핑 페이지)</span><span class="sxs-lookup"><span data-stu-id="f9f55-102">Cache Transformation Editor (Mappings Page)</span></span>
  <span data-ttu-id="f9f55-103">**캐시 변환 편집기** 의 **매핑** 페이지를 사용하여 캐시 변환의 입력 열을 캐시 연결 관리자의 대상 열에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f55-103">Use the **Mappings** page of the **Cache Transformation Editor** to map the input columns in the Cache Transform transformation to destination columns in the Cache connection manager.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f9f55-104">각 입력 열은 대상 열로 매핑되어야 하며 열 데이터 형식이 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9f55-104">Each input column must be mapped to a destination column, and the column data types must match.</span></span> <span data-ttu-id="f9f55-105">그렇지 않으면 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 디자이너에서 오류 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f9f55-105">Otherwise, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Designer displays an error message.</span></span>  
  
 <span data-ttu-id="f9f55-106">캐시 변환에 대한 자세한 내용은 [Cache Transform](data-flow/transformations/cache-transform.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f9f55-106">To learn more about the Cache Transform, see [Cache Transform](data-flow/transformations/cache-transform.md).</span></span>  
  
 <span data-ttu-id="f9f55-107">캐시 연결 관리자에 대한 자세한 내용은 [Cache Connection Manager](connection-manager/cache-connection-manager.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f9f55-107">To learn more about the Cache connection manager, see [Cache Connection Manager](connection-manager/cache-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="f9f55-108">옵션</span><span class="sxs-lookup"><span data-stu-id="f9f55-108">Options</span></span>  
 <span data-ttu-id="f9f55-109">**사용 가능한 입력 열**</span><span class="sxs-lookup"><span data-stu-id="f9f55-109">**Available Input Columns**</span></span>  
 <span data-ttu-id="f9f55-110">사용 가능한 입력 열 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f9f55-110">View the list of available input columns.</span></span> <span data-ttu-id="f9f55-111">끌어서 놓기 작업을 사용하여 사용 가능한 입력 열을 대상 열에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f55-111">Use a drag-and-drop operation to map available input columns to destination columns.</span></span>  
  
 <span data-ttu-id="f9f55-112">또한 키보드로 **사용 가능한 입력 열** 테이블의 열을 강조 표시하고 메뉴 키를 누른 다음 **일치하는 이름별 항목 매핑**을 선택하여 입력 열을 대상 열에 매핑할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f55-112">You can also map input columns to destination columns using the keyboard, by highlighting a column in the **Available Input Columns** table, pressing the menu key, and then selecting **Map Items By Matching Names**.</span></span>  
  
 <span data-ttu-id="f9f55-113">**사용 가능한 대상 열**</span><span class="sxs-lookup"><span data-stu-id="f9f55-113">**Available Destination Columns**</span></span>  
 <span data-ttu-id="f9f55-114">사용 가능한 대상 열의 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f9f55-114">View the list of available destination columns.</span></span> <span data-ttu-id="f9f55-115">끌어서 놓기 작업을 사용하여 사용 가능한 대상 열을 입력 열에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f55-115">Use a drag-and-drop operation to map available destination columns to input columns.</span></span>  
  
 <span data-ttu-id="f9f55-116">또한 키보드로 **사용 가능한 대상 열** 테이블의 열을 강조 표시하고 메뉴 키를 누른 다음 **일치하는 이름별 항목 매핑**을 선택하여 입력 열을 대상 열에 매핑할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f55-116">You can also map input columns to destination columns using the keyboard, by highlighting a column in the **Available Destination Columns** table, pressing the menu key, and then selecting **Map Items By Matching Names**.</span></span>  
  
 <span data-ttu-id="f9f55-117">**입력 열**</span><span class="sxs-lookup"><span data-stu-id="f9f55-117">**Input Column**</span></span>  
 <span data-ttu-id="f9f55-118">이 항목의 앞부분에서 선택한 입력 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f9f55-118">View input columns selected earlier in this topic.</span></span> <span data-ttu-id="f9f55-119">**사용 가능한 입력 열**의 목록을 사용하여 매핑을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f55-119">You can change the mappings by using the list of **Available Input Columns**.</span></span>  
  
 <span data-ttu-id="f9f55-120">**대상 열**</span><span class="sxs-lookup"><span data-stu-id="f9f55-120">**Destination Column**</span></span>  
 <span data-ttu-id="f9f55-121">사용 가능한 각 대상 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f9f55-121">View each available destination column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9f55-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f9f55-122">See Also</span></span>  
 [<span data-ttu-id="f9f55-123">캐시 변환 편집기&#40;연결 관리자 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="f9f55-123">Cache Transformation Editor &#40;Connection Manager Page&#41;</span></span>](../../2014/integration-services/cache-transformation-editor-connection-manager-page.md)  
  
  
