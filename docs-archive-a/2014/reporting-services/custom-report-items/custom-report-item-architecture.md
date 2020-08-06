---
title: 사용자 지정 보고서 항목 아키텍처 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, architecture
ms.assetid: 2a88ea46-c9f8-4dd7-aad1-16de11da4f06
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a053eb55547da9030eebe9036667cca2e14606f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639415"
---
# <a name="custom-report-item-architecture"></a><span data-ttu-id="2520b-102">사용자 지정 보고서 항목 아키텍처</span><span class="sxs-lookup"><span data-stu-id="2520b-102">Custom Report Item Architecture</span></span>
  <span data-ttu-id="2520b-103">사용자 지정 보고서 항목은 RDL(Report Definition Language)의 확장으로서 개발자는 이를 통해 RDL에서 기본적으로 지원되지 않는 기능을 추가하거나 기존 컨트롤의 기능을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2520b-103">A custom report item is an extension to the Report Definition Language (RDL) that allows developers to add functionality that's not natively supported in RDL or extend the functionality of existing controls.</span></span> <span data-ttu-id="2520b-104">사용자 지정 보고서 항목에는 런타임 구성 요소와 디자인 타임 구성 요소의 두 가지 기본 구성 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2520b-104">There are two main components to a custom report item: the run-time component and the design-time component.</span></span> <span data-ttu-id="2520b-105">이러한 구성 요소는 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 어셈블리로 구현되고 CLS 호환 언어로 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2520b-105">These components are implemented as [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] assemblies, and can be written in any CLS-compliant language.</span></span>  
  
## <a name="the-run-time-component"></a><span data-ttu-id="2520b-106">런타임 구성 요소</span><span class="sxs-lookup"><span data-stu-id="2520b-106">The Run-Time Component</span></span>  
 <span data-ttu-id="2520b-107">사용자 지정 보고서 항목에 대한 런타임 구성 요소는 런타임에 보고서 처리기에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="2520b-107">The run-time component for a custom report item is called by the report processor at run time.</span></span> <span data-ttu-id="2520b-108">런타임 구성 요소는 런타임에 보고서 처리기에서 전달된 데이터를 수신하고 이 데이터를 처리하며 렌더링된 사용자 지정 보고서 항목이 포함된 이미지를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2520b-108">The run-time component accepts data passed by the report processor at run time, processes this data, and returns an image containing the rendered custom report item.</span></span>  
  
 <span data-ttu-id="2520b-109">![사용자 지정 보고서 항목 런타임 구성 요소](../../../2014/reporting-services/media/customreportitemrun-timecomponentarchitecture.gif "사용자 지정 보고서 항목 런타임 구성 요소")</span><span class="sxs-lookup"><span data-stu-id="2520b-109">![Custom report item run-time component](../../../2014/reporting-services/media/customreportitemrun-timecomponentarchitecture.gif "Custom report item run-time component")</span></span>  
  
## <a name="the-design-time-component"></a><span data-ttu-id="2520b-110">디자인 타임 구성 요소</span><span class="sxs-lookup"><span data-stu-id="2520b-110">The Design-Time Component</span></span>  
 <span data-ttu-id="2520b-111">디자인 타임 구성 요소를 활용하여 사용자 지정 보고서 항목을 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]의 보고서 디자이너 인터페이스에서 정의하고 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2520b-111">The design-time component allows the custom report item to be defined and manipulated in the Report Designer interface in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="2520b-112">디자인 타임 구성 요소는 디자인 환경에서 사용자 지정 보고서 항목의 모양과 속성을 제어하는 다수의 하위 컨트롤로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="2520b-112">The design-time component consists of several sub-controls that control the appearance and properties of the custom report item in the design environment.</span></span>  
  
 <span data-ttu-id="2520b-113">![사용자 지정 보고서 항목 디자인 타임 구성 요소](../../../2014/reporting-services/media/customreportitemdesign-timecomponentarchitecture.gif "사용자 지정 보고서 항목 디자인 타임 구성 요소")</span><span class="sxs-lookup"><span data-stu-id="2520b-113">![Custom report item design-time component](../../../2014/reporting-services/media/customreportitemdesign-timecomponentarchitecture.gif "Custom report item design-time component")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2520b-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2520b-114">See Also</span></span>  
 <span data-ttu-id="2520b-115">[사용자 지정 보고서 항목 런타임 구성 요소 만들기](../custom-report-items/creating-a-custom-report-item-run-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="2520b-115">[Creating a Custom Report Item Run-Time Component](../custom-report-items/creating-a-custom-report-item-run-time-component.md) </span></span>  
 <span data-ttu-id="2520b-116">[사용자 지정 보고서 항목 디자인 타임 구성 요소 만들기](../custom-report-items/creating-a-custom-report-item-design-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="2520b-116">[Creating a Custom Report Item Design-Time Component](../custom-report-items/creating-a-custom-report-item-design-time-component.md) </span></span>  
 [<span data-ttu-id="2520b-117">방법: 사용자 지정 보고서 항목 배포</span><span class="sxs-lookup"><span data-stu-id="2520b-117">How to: Deploy a Custom Report Item</span></span>](../custom-report-items/how-to-deploy-a-custom-report-item.md)  
  
  
