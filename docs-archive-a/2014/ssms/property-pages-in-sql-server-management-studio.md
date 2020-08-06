---
title: SQL Server Management Studio의 속성 페이지 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- property pages [SQL Server Management Studio]
ms.assetid: 719282c3-e9cc-4e0e-9a83-7fb8b8b17f67
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3fae6a07fbaa2a259fcca5c3807094b31e0d52d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737413"
---
# <a name="property-pages-in-sql-server-management-studio"></a><span data-ttu-id="5cd04-102">SQL Server Management Studio의 속성 페이지</span><span class="sxs-lookup"><span data-stu-id="5cd04-102">Property Pages in SQL Server Management Studio</span></span>
  <span data-ttu-id="5cd04-103">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]의 모든 속성 페이지 대화 상자는 확대 및 축소 범주가 포함된 정보를 표시하는 공통된 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd04-103">Property page dialog boxes in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] all use a common format displaying information with expanding and collapsing categories.</span></span> <span data-ttu-id="5cd04-104">표시되는 필드는 특정 속성에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="5cd04-104">The fields shown depend on the particular property.</span></span> <span data-ttu-id="5cd04-105">회색으로 표시된 속성은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd04-105">Properties shown in gray are read-only.</span></span> <span data-ttu-id="5cd04-106">각 속성 페이지의 맨 위 근처에는 범주별 및 사전순 단추가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd04-106">Categorized and Alphabetic buttons are near the top of each property page.</span></span>  
  
 <span data-ttu-id="5cd04-107">다음 표에서는 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 속성 페이지 대화 상자의 공통 요소를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd04-107">The following table describes the common elements of [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] property page dialog boxes.</span></span>  
  
|<span data-ttu-id="5cd04-108">요소</span><span class="sxs-lookup"><span data-stu-id="5cd04-108">Element</span></span>|<span data-ttu-id="5cd04-109">Description</span><span class="sxs-lookup"><span data-stu-id="5cd04-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5cd04-110">**범주별**</span><span class="sxs-lookup"><span data-stu-id="5cd04-110">**Categorized**</span></span>|<span data-ttu-id="5cd04-111">선택한 개체에 대한 모든 속성과 속성 값을 범주별로 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd04-111">Lists all properties and property values for the selected object, sorted by category.</span></span> <span data-ttu-id="5cd04-112">범주별 보기에서 범주를 축소하여 표시되는 속성의 수를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd04-112">In category view, you can collapse a category to reduce the number of visible properties.</span></span> <span data-ttu-id="5cd04-113">범주를 확장하거나 축소할 경우 범주 이름 왼쪽에 있는 더하기(+) 또는 빼기(-) 기호를 각각 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd04-113">When you expand or collapse a category, you see a plus sign (+) or minus sign (-) to the left of the category name.</span></span> <span data-ttu-id="5cd04-114">범주는 사전순으로 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd04-114">Categories are listed alphabetically.</span></span>|  
|<span data-ttu-id="5cd04-115">**사전순**</span><span class="sxs-lookup"><span data-stu-id="5cd04-115">**Alphabetic**</span></span>|<span data-ttu-id="5cd04-116">선택한 개체에 대한 모든 속성과 속성 값을 사전순으로 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd04-116">Lists all properties and property values for the selected object, sorted alphabetically.</span></span>|  
|<span data-ttu-id="5cd04-117">속성 이름</span><span class="sxs-lookup"><span data-stu-id="5cd04-117">Property name</span></span>|<span data-ttu-id="5cd04-118">표의 첫 번째 열에는 속성 이름이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd04-118">The first column in the grid lists the property names.</span></span>|  
|<span data-ttu-id="5cd04-119">속성</span><span class="sxs-lookup"><span data-stu-id="5cd04-119">Properties</span></span>|<span data-ttu-id="5cd04-120">표의 두 번째 열에는 속성 값이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd04-120">The second column in the grid lists the property values.</span></span>|  
|<span data-ttu-id="5cd04-121">설명 창</span><span class="sxs-lookup"><span data-stu-id="5cd04-121">Description pane</span></span>|<span data-ttu-id="5cd04-122">설명 창은 페이지의 맨 아래에 나타나며 속성 유형과 속성에 대한 간단한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd04-122">The description pane appears at the bottom of the page and shows the property type and a short description of the property.</span></span> <span data-ttu-id="5cd04-123">바로 가기 메뉴의 **설명** 명령을 사용하여 속성 설명을 설정 및 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd04-123">You can turn the description of the property off and on using the **Description** command on the shortcut menu.</span></span>|  
  
  
