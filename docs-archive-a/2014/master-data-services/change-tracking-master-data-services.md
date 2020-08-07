---
title: 변경 내용 추적(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- change tracking [SQL Server]
ms.assetid: 5e879c65-0d38-454f-9a20-62a6e72c89f7
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2d3b69057b02884f41a43aa9a009ab3db937ed25
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732728"
---
# <a name="change-tracking-master-data-services"></a><span data-ttu-id="eb61f-102">변경 내용 추적(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="eb61f-102">Change Tracking (Master Data Services)</span></span>
  <span data-ttu-id="eb61f-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 변경 내용 추적 그룹을 사용하여 특성 값이 변경될 때 동작을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb61f-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can use change tracking groups to take action when an attribute value changes.</span></span> <span data-ttu-id="eb61f-104">새 값이 무엇인지 모르지만 대신 변경이 발생했는지 알고 싶으면 변경 내용 추적을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="eb61f-104">Use change tracking when you don't know what the new value will be, but instead want to know if any change occurred.</span></span>  
  
## <a name="configuring-change-tracking"></a><span data-ttu-id="eb61f-105">변경 내용 추적 구성</span><span class="sxs-lookup"><span data-stu-id="eb61f-105">Configuring Change Tracking</span></span>  
 <span data-ttu-id="eb61f-106">변경 내용 추적을 구성하려면 변경 내용 추적 그룹에 특성을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="eb61f-106">To configure change tracking, you add an attribute to a change tracking group.</span></span> <span data-ttu-id="eb61f-107">그룹에 하나 이상의 특성을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb61f-107">The group can contain one or many attributes.</span></span> <span data-ttu-id="eb61f-108">그런 다음 비즈니스 규칙을 만들어 그룹의 특성이 변경될 때 수행할 동작을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="eb61f-108">Then, you create a business rule to define the action that is taken when any of the attributes in the group change.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eb61f-109">변경 내용 추적 비즈니스 규칙은 준비된(가져온) 데이터가 변경된다고 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="eb61f-109">Change tracking business rules consider staged (imported) data to be changed.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="eb61f-110">관련 작업</span><span class="sxs-lookup"><span data-stu-id="eb61f-110">Related Tasks</span></span>  
  
|<span data-ttu-id="eb61f-111">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="eb61f-111">Task Description</span></span>|<span data-ttu-id="eb61f-112">항목</span><span class="sxs-lookup"><span data-stu-id="eb61f-112">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="eb61f-113">변경 내용 추적 그룹에 특성 추가</span><span class="sxs-lookup"><span data-stu-id="eb61f-113">Add attributes to a change tracking group.</span></span>|[<span data-ttu-id="eb61f-114">변경 내용 추적 그룹에 특성 추가&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="eb61f-114">Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;</span></span>](add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|<span data-ttu-id="eb61f-115">특성 변경을 기반으로 하는 동작을 시작하는 비즈니스 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="eb61f-115">Create a business rule that initiates actions based on attribute changes.</span></span>|[<span data-ttu-id="eb61f-116">특성 값 변경 기반 동작 시작&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="eb61f-116">Initiate Actions Based on Attribute Value Changes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="eb61f-117">관련 내용</span><span class="sxs-lookup"><span data-stu-id="eb61f-117">Related Content</span></span>  
  
-   [<span data-ttu-id="eb61f-118">유효성 검사&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="eb61f-118">Validation &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validation-master-data-services.md)  
  
-   [<span data-ttu-id="eb61f-119">비즈니스 규칙&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="eb61f-119">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
-   [<span data-ttu-id="eb61f-120">특성&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="eb61f-120">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
