---
title: 팩트 관계 및 팩트 관계 속성 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- fact dimensions [Analysis Services]
ms.assetid: d8e41724-da77-4ac1-bc42-956b5d91ea5d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 15f67a4bdf699bbc6443fc76ce54bcfb35831827
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730971"
---
# <a name="define-a-fact-relationship-and-fact-relationship-properties"></a><span data-ttu-id="43267-102">팩트 관계 및 팩트 관계 속성 정의</span><span class="sxs-lookup"><span data-stu-id="43267-102">Define a Fact Relationship and Fact Relationship Properties</span></span>
  <span data-ttu-id="43267-103">새 큐브 차원이나 새 측정값 그룹을 정의하면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서는 팩트 차원 관계가 존재하는지 확인한 후 차원 용도 설정을 `Fact`로 지정하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="43267-103">When you define a new cube dimension or a new measure group, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will try to detect if a fact dimension relationship exists and then set the dimension usage setting to `Fact`.</span></span> <span data-ttu-id="43267-104">큐브 디자이너의 **차원 용도** 탭에서 팩트 차원 관계를 보거나 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43267-104">You can view or edit a fact dimension relationship on the **Dimension Usage** tab of Cube Designer.</span></span> <span data-ttu-id="43267-105">차원과 측정값 그룹 간의 팩트 관계에는 다음과 같은 제약 조건이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43267-105">The fact relationship between a dimension and a measure group has the following constraints:</span></span>  
  
-   <span data-ttu-id="43267-106">큐브 차원은 특정 측정값 그룹에 대해 하나의 팩트 관계만 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43267-106">A cube dimension can have only one fact relationship to a particular measure group.</span></span>  
  
-   <span data-ttu-id="43267-107">큐브 차원은 여러 측정값 그룹에 대해 별도의 팩트 관계를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43267-107">A cube dimension can have separate fact relationships to multiple measure groups.</span></span>  
  
-   <span data-ttu-id="43267-108">관계에 대한 세분성 특성은 차원에 대한 키 특성(예: Transaction Number)이어야 하므로</span><span class="sxs-lookup"><span data-stu-id="43267-108">The granularity attribute for the relationship must be the key attribute (such as Transaction Number) for the dimension.</span></span> <span data-ttu-id="43267-109">차원과 팩트 테이블의 팩트 간에 일 대 일 관계가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="43267-109">This creates a one-to-one relationship between the dimension and facts in the fact table.</span></span>  
  
  
