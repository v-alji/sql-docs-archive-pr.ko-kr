---
title: 멤버 그룹 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- member groups [Analysis Services]
- grouping members
- DiscretizationMethod property
ms.assetid: 006cc915-c499-4781-b9a7-01ad31bebf6a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 95f9516c7a0077e97af348afa863fe15c8d4528b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741436"
---
# <a name="define-member-groups"></a><span data-ttu-id="4088f-102">멤버 그룹 정의</span><span class="sxs-lookup"><span data-stu-id="4088f-102">Define Member Groups</span></span>
  <span data-ttu-id="4088f-103">특성에 많은 수의 멤버가 있는 경우 해당 멤버를 버킷으로 그룹화하여 계층에서 데이터를 탐색할 때 사용자에게 표시되는 멤버 수를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4088f-103">If an attribute has a large number of members, you can choose to group those members into buckets, reducing the number of members that users see when they browse the data in a hierarchy.</span></span> <span data-ttu-id="4088f-104">멤버가 그룹인 버킷 수를 결정하고 버킷의 명명 구성표를 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4088f-104">You can also determine the number of buckets in which the members are groups and set a naming scheme for the buckets.</span></span> <span data-ttu-id="4088f-105">자세한 내용은 [특성 멤버 그룹화&#40;불연속화&#41;](attribute-properties-group-attribute-members.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4088f-105">For more information, see [Group Attribute Members &#40;Discretization&#41;](attribute-properties-group-attribute-members.md).</span></span>  
  
 <span data-ttu-id="4088f-106">**의** 속성 **창을 통해 액세스하는** DiscretizationMethod [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]속성을 설정하여 멤버를 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="4088f-106">You group members by setting the **DiscretizationMethod** property, which is accessed through the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="4088f-107">멤버 그룹을 만드는 경우 차원을 처리할 때까지 변경 내용이 사용자에게 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4088f-107">When you create member groups, your changes are not available to users until you process the dimension.</span></span> <span data-ttu-id="4088f-108">자세한 내용은 [다차원 모델 개체 처리](processing-a-multidimensional-model-analysis-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4088f-108">For more information, see [Multidimensional Model Object Processing](processing-a-multidimensional-model-analysis-services.md).</span></span>  
  
### <a name="to-create-member-groups"></a><span data-ttu-id="4088f-109">멤버 그룹을 만들려면</span><span class="sxs-lookup"><span data-stu-id="4088f-109">To create member groups</span></span>  
  
1.  <span data-ttu-id="4088f-110">작업할 차원을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4088f-110">Open the dimension that you want to work with.</span></span> <span data-ttu-id="4088f-111">기본적으로 **차원 구조** 탭이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="4088f-111">The **Dimension Structure** tab opens by default.</span></span>  
  
2.  <span data-ttu-id="4088f-112">**특성**에서 멤버를 그룹화할 특성을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4088f-112">In **Attributes**, right-click the attribute whose members you want to group, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="4088f-113">**DiscretizationMethod**옆의 드롭다운 목록에서 멤버 그룹화 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4088f-113">From the drop-down list next to **DiscretizationMethod**, select a method by which to group the members.</span></span> <span data-ttu-id="4088f-114">**DiscretizationMethod** 설정에 대한 자세한 내용은 [특성 멤버 그룹화&#40;불연속화&#41;](attribute-properties-group-attribute-members.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4088f-114">For more information about **DiscretizationMethod** settings, see [Group Attribute Members &#40;Discretization&#41;](attribute-properties-group-attribute-members.md).</span></span>  
  
  
