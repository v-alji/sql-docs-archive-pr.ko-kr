---
title: 사용자 지정 보고서 항목 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- extending Reporting Services
- Reporting Services, extending
- custom report items
ms.assetid: 64dcaf2c-1af5-4937-8ff7-98f1ec3b367e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 86b819cb4d305e537a52a2e7f25cdfa3aefa5f9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741635"
---
# <a name="custom-report-items"></a><span data-ttu-id="53956-102">사용자 지정 보고서 항목</span><span class="sxs-lookup"><span data-stu-id="53956-102">Custom Report Items</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<span data-ttu-id="53956-103">에서는 엔터프라이즈 보고서 작성 및 게시, 보안 및 구독 관리, 포괄적 API를 통한 보고 기능 확장 등을 위한 풍부한 도구 집합을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="53956-103">provides a rich set of tools for building and publishing enterprise reports, managing security and subscriptions, and extending the reporting functionality through a comprehensive API.</span></span> <span data-ttu-id="53956-104">보고서는 RDL(Report Definition Language)이라는 XML 기반 언어를 사용하여 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="53956-104">Reports are defined using an XML-based language called Report Definition Language (RDL).</span></span> <span data-ttu-id="53956-105">RDL은 보고서의 레이아웃, 쿼리 정보 및 항목 형식을 설명하는 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="53956-105">RDL provides a set of instructions that describe layout, query information, and item types for a report.</span></span> <span data-ttu-id="53956-106">사용자 지정 보고서 항목을 작성하여 RDL을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53956-106">It is possible to extend RDL by writing a custom report item.</span></span> <span data-ttu-id="53956-107">사용자 지정 보고서 항목은 런타임에 보고서 처리기에서 호출하는 런타임 구성 요소와 사용자 지정 보고서 항목을 보고서 디자이너에서 사용할 수 있도록 하는 디자인 타임 구성 요소로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="53956-107">The custom report item consists of a run-time component, which is called by the report processor at run time, and a design-time component, which allows the custom report item to be available in Report Designer.</span></span>  
  
 <span data-ttu-id="53956-108">완전히 구현된 사용자 지정 보고서 항목 예는 [SQL Server Reporting Services 제품 예제](https://go.microsoft.com/fwlink/?LinkId=177889)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="53956-108">For a sample of a fully implemented custom report item, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="custom-report-item-scenarios"></a><span data-ttu-id="53956-109">사용자 지정 보고서 항목 시나리오</span><span class="sxs-lookup"><span data-stu-id="53956-109">Custom Report Item Scenarios</span></span>  
 <span data-ttu-id="53956-110">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]를 애플리케이션에 통합해야 하는 개발자는 기본적으로 RDL에서 지원되지 않는 기능이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53956-110">Developers who need to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into their applications may require functionality that is not natively supported in RDL.</span></span> <span data-ttu-id="53956-111">이러한 기능에는 맵 컨트롤, 가로 목록, 열 목록, 피벗 재설정 가능 행렬 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="53956-111">This may include items such as: map controls, horizontal lists, columnar lists, and repivotable matrixes.</span></span> <span data-ttu-id="53956-112">애플리케이션으로 런타임 사용자 지정 보고서 항목 구성 요소를 개발하고 배포하여 필요한 기능을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53956-112">A run-time custom report item component can be developed and distributed with an application to fill this need.</span></span>  
  
 <span data-ttu-id="53956-113">기본적으로 지원되지 않는 기능을 제공하는 것 외에도 일부 개발자는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에 이미 포함되어 있는 컨트롤의 다른 버전으로 기존 기능을 확장해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53956-113">In addition to providing functionality that isn't natively supported, some developers may want to extend existing functionality with alternative versions of controls that are already included with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="53956-114">이 시나리오에서는 개발자가 런타임 구성 요소, 디자인 타임 구성 요소 및 디자인 타임 보고서 항목 변환 구성 요소의 세 가지 구성 요소를 제공할 수 있습니다. 이 중 디자인 타임 보고서 항목 변환 구성 요소는 요청 시 기존 보고서 항목을 사용자 지정 보고서 항목으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="53956-114">In this scenario, a developer could provide three components: a run-time component, a design-time component, and a design-time report item conversion component that converts an existing report item into a custom report item on demand.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="53956-115">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="53956-115">In This Section</span></span>  
 [<span data-ttu-id="53956-116">사용자 지정 보고서 항목 아키텍처</span><span class="sxs-lookup"><span data-stu-id="53956-116">Custom Report Item Architecture</span></span>](custom-report-item-architecture.md)  
 <span data-ttu-id="53956-117">사용자 지정 보고서 항목을 구성하는 구성 요소를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="53956-117">Describes the components that make up a custom report item.</span></span>  
  
 [<span data-ttu-id="53956-118">사용자 지정 보고서 항목 구현 요구 사항</span><span class="sxs-lookup"><span data-stu-id="53956-118">Custom Report Item Implementation Requirements</span></span>](custom-report-item-implementation-requirements.md)  
 <span data-ttu-id="53956-119">사용자 지정 보고서 항목을 만들기 위한 선행 조건을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="53956-119">Describes prerequisites for creating a custom report item.</span></span>  
  
 [<span data-ttu-id="53956-120">사용자 지정 보고서 항목 런타임 구성 요소 만들기</span><span class="sxs-lookup"><span data-stu-id="53956-120">Creating a Custom Report Item Run-Time Component</span></span>](creating-a-custom-report-item-run-time-component.md)  
 <span data-ttu-id="53956-121">사용자 지정 보고서 항목 런타임 구성 요소를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="53956-121">Describes how to create a custom report item run-time component.</span></span>  
  
 [<span data-ttu-id="53956-122">사용자 지정 보고서 항목 디자인 타임 구성 요소 만들기</span><span class="sxs-lookup"><span data-stu-id="53956-122">Creating a Custom Report Item Design-Time Component</span></span>](creating-a-custom-report-item-design-time-component.md)  
 <span data-ttu-id="53956-123">사용자 지정 보고서 항목 디자인 타임 구성 요소를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="53956-123">Describes how to create a custom report item design-time component.</span></span>  
  
 [<span data-ttu-id="53956-124">방법: 사용자 지정 보고서 항목 배포</span><span class="sxs-lookup"><span data-stu-id="53956-124">How to: Deploy a Custom Report Item</span></span>](how-to-deploy-a-custom-report-item.md)  
 <span data-ttu-id="53956-125">사용자 지정 보고서 항목을 배포하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="53956-125">Describes how to deploy a custom report item.</span></span>  
  
 [<span data-ttu-id="53956-126">사용자 지정 보고서 항목 클래스 라이브러리</span><span class="sxs-lookup"><span data-stu-id="53956-126">Custom Report Item Class Libraries</span></span>](custom-report-item-class-libraries.md)  
 <span data-ttu-id="53956-127">`Microsoft.ReportDesigner` 네임스페이스의 사용자 지정 보고서 항목 인프라 클래스 및 관리되는 래퍼 클래스를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="53956-127">Describes the custom report item infrastructure classes and managed wrapper classes in the `Microsoft.ReportDesigner` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53956-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="53956-128">See Also</span></span>  
 [<span data-ttu-id="53956-129">기술 참조&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="53956-129">Technical Reference &#40;SSRS&#41;</span></span>](../technical-reference-ssrs.md)  
  
  
