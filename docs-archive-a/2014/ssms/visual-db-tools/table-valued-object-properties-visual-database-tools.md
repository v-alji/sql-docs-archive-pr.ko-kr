---
title: 테이블 반환 개체 속성(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.designers.properties.TVO
ms.assetid: eaf06cbf-8242-4483-894f-80ae02a4840e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6f1c1e6414d0059dfd1d43bbbb40eabdfc9470b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735767"
---
# <a name="table-valued-object-properties-visual-database-tools"></a><span data-ttu-id="af543-102">테이블 반환 개체 속성(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="af543-102">Table-Valued Object Properties (Visual Database Tools)</span></span>
  <span data-ttu-id="af543-103">이러한 속성은 **쿼리 및 뷰 디자이너**에서 테이블 반환 개체를 선택하면 속성 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="af543-103">These properties appear in the Properties window when you select a table-valued object in **Query and View Designer**.</span></span> <span data-ttu-id="af543-104">테이블 반환 개체는 뷰, 동의어, 파생 테이블 또는 테이블 반환 함수일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af543-104">The table-valued object could be a view, synonym, derived table, or table-valued function.</span></span> <span data-ttu-id="af543-105">다른 설명이 없는 한 이러한 속성은 **속성** 창에서 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="af543-105">Unless otherwise noted, these properties are read-only in the **Properties** window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af543-106">이 항목의 속성은 사전순 대신 범주별로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="af543-106">The properties in this topic are ordered by category rather than alphabet.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af543-107">활성 설정 또는 버전에 따라 표시되는 대화 상자 및 메뉴 명령이 도움말에 설명된 것과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af543-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="af543-108">설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="af543-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="af543-109">**ID 범주**</span><span class="sxs-lookup"><span data-stu-id="af543-109">**Identity Category**</span></span>  
 <span data-ttu-id="af543-110">확장하면 **이름** 및 **TVO 형식** 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="af543-110">Expands to show the **Name** and **TVO Type** properties.</span></span>  
  
 <span data-ttu-id="af543-111">**이름**</span><span class="sxs-lookup"><span data-stu-id="af543-111">**Name**</span></span>  
 <span data-ttu-id="af543-112">선택한 테이블 반환 개체의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="af543-112">Shows the name of the selected table-valued object.</span></span>  
  
 <span data-ttu-id="af543-113">**TVO 형식**</span><span class="sxs-lookup"><span data-stu-id="af543-113">**TVO Type**</span></span>  
 <span data-ttu-id="af543-114">테이블 반환 개체의 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="af543-114">Shows which type of table-valued object.</span></span> <span data-ttu-id="af543-115">유형은 기본 테이블, 뷰, 테이블 반환 함수 또는 파생 테이블일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af543-115">It can be either a base table, view, table-valued function, or a derived table.</span></span>  
  
 <span data-ttu-id="af543-116">**쿼리 디자이너 범주**</span><span class="sxs-lookup"><span data-stu-id="af543-116">**Query DesignerCategory**</span></span>  
 <span data-ttu-id="af543-117">확장하면 **별칭**, **열 목록**, **전체 이름**및 **매개 변수 목록**의 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="af543-117">Expands to show properties for **Alias**, **Column List**, **Full Name**, and **Parameter List**.</span></span>  
  
 <span data-ttu-id="af543-118">**별칭**</span><span class="sxs-lookup"><span data-stu-id="af543-118">**Alias**</span></span>  
 <span data-ttu-id="af543-119">선택한 테이블 반환 개체에 대한 별칭을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="af543-119">Shows the alias for the selected table-valued object.</span></span> <span data-ttu-id="af543-120">별칭을 추가하거나 변경하려면 필드에 별칭을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="af543-120">To add or change an alias, type it into the field.</span></span>  
  
 <span data-ttu-id="af543-121">**열 목록**</span><span class="sxs-lookup"><span data-stu-id="af543-121">**Column List**</span></span>  
 <span data-ttu-id="af543-122">선택한 테이블 반환 개체에 포함된 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="af543-122">Shows the columns included in the selected table-valued object.</span></span> <span data-ttu-id="af543-123">이러한 열을 별도의 창에 표시하려면 열 목록을 클릭한, 다음 속성의 오른쪽에 있는 줄임표(...)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="af543-123">To see them in a separate window, click Column List and then click the ellipses (...) to the right of the property.</span></span>  
  
 <span data-ttu-id="af543-124">**전체 이름**</span><span class="sxs-lookup"><span data-stu-id="af543-124">**Full Name**</span></span>  
 <span data-ttu-id="af543-125">개체의 스키마 또는 데이터 원본과 같은 추가 정보를 포함하여 선택한 테이블 반환 개체의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="af543-125">Shows the name of the selected table-valued object, including additional information such as the schema or data source of the object.</span></span>  
  
 <span data-ttu-id="af543-126">**매개 변수 목록**</span><span class="sxs-lookup"><span data-stu-id="af543-126">**Parameter List**</span></span>  
 <span data-ttu-id="af543-127">선택한 테이블 반환 함수에 대해 정의된 매개 변수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="af543-127">Shows the parameters defined for selected table-valued function.</span></span> <span data-ttu-id="af543-128">매개 변수의 값을 정의하려면 매개 변수 목록을 클릭한 다음, 속성의 오른쪽에 있는 줄임표(...)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="af543-128">To define a value for the parameters, click Parameter List and then click the ellipses (...) to the right of the property.</span></span> <span data-ttu-id="af543-129">함수 매개 변수 대화 상자에서 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="af543-129">In the Function Parameters dialog box, type in values.</span></span> <span data-ttu-id="af543-130">이 속성은 테이블 반환 함수를 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af543-130">This property is only available when a table-valued function is selected.</span></span>  
  
  
