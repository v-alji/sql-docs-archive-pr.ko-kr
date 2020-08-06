---
title: 일반 관계 및 일반 관계 속성 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- granularity attribute
- relationships [Analysis Services], regular relationships
ms.assetid: 840280d8-20c3-46c0-99ea-62479469c36b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b4f49e219a85d5577fb1acddfe14e7afd3b105d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660165"
---
# <a name="define-a-regular-relationship-and-regular-relationship-properties"></a><span data-ttu-id="550b0-102">일반 관계 및 일반 관계 속성 정의</span><span class="sxs-lookup"><span data-stu-id="550b0-102">Define a Regular Relationship and Regular Relationship Properties</span></span>
  <span data-ttu-id="550b0-103">새 큐브 차원이나 새 측정값 그룹을 정의하면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서는 일반 관계가 존재하는지 확인한 후 차원 용도 설정을 `Regular`로 지정하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="550b0-103">When you define a new cube dimension or a new measure group, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will try to detect if a regular relationship exists and then set the dimension usage setting to `Regular`.</span></span> <span data-ttu-id="550b0-104">큐브 디자이너의 **차원 용도** 탭에서 일반 차원 관계를 보거나 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="550b0-104">You can view or edit a regular dimension relationship on the **Dimension Usage** tab of Cube Designer.</span></span>  
  
 <span data-ttu-id="550b0-105">측정값 그룹에 대한 큐브 차원 관계를 정의할 때 해당 관계에 대한 세분성 특성도 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="550b0-105">When you define the relationship of a cube dimension to a measure group, you also specify the granularity attribute for that relationship.</span></span> <span data-ttu-id="550b0-106">세분성 특성은 해당 차원에 대해 큐브에서 사용할 수 있는 가장 낮은 상세 수준을 정의하며 이 수준은 일반적으로 차원의 키 특성에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="550b0-106">The granularity attribute defines the lowest level of detail available in the cube for that dimension, which is generally the key attribute for the dimension.</span></span> <span data-ttu-id="550b0-107">그러나 가끔 특정 측정값 그룹의 특정 큐브 차원에 대한 세분성을 다르게 설정하려고 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="550b0-107">However, sometimes you may want to set the granularity of a particular cube dimension in a particular measure group to a different grain.</span></span> <span data-ttu-id="550b0-108">예를 들어 Sales Quotas 또는 Budget 측정값 그룹을 사용하는 경우 Time 차원에 대한 세분성 특성을 Day 특성이 아닌 Month 특성으로 설정하려고 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="550b0-108">For example, you may want to set the granularity attribute for the Time dimension to the Month attribute instead of to the Day attribute, if you are using a Sales Quotas or a Budget measure group.</span></span> <span data-ttu-id="550b0-109">세분성 특성을 키 특성 이외의 특성으로 지정하면 차원의 다른 모든 특성이 특성 관계를 통해 다른 특성에 직간접적으로 연결되는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="550b0-109">When you specify the granularity attribute to be an attribute other than the key attribute, you must guarantee that all other attributes in the dimension are directly or indirectly linked to this other attribute through attribute relationships.</span></span> <span data-ttu-id="550b0-110">그렇지 않으면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서는 데이터를 제대로 집계할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="550b0-110">If not, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will be unable to aggregate data correctly.</span></span>  
  
  
