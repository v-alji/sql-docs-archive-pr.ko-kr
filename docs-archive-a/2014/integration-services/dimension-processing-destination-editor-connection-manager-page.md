---
title: 차원 처리 대상 편집기 (연결 관리자 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dimprocessingtransformation.connection.f1
helpviewer_keywords:
- Dimension Processing Destination Editor
ms.assetid: 44aab631-d62d-4895-8fc7-7f1f3b1b68ce
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 50ba42292c1f48c9b1cdf2ba00c709dacd2f9675
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660697"
---
# <a name="dimension-processing-destination-editor-connection-manager-page"></a><span data-ttu-id="3856f-102">차원 처리 대상 편집기(연결 관리자 페이지)</span><span class="sxs-lookup"><span data-stu-id="3856f-102">Dimension Processing Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="3856f-103">**차원 처리 대상 편집기** 대화 상자의 **연결 관리자** 페이지를 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 프로젝트나 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 대한 연결을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3856f-103">Use the **Connection Manager** page of the **Dimension Processing Destination Editor** dialog box to specify a connection to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project or to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="3856f-104">차원 처리 대상에 대한 자세한 내용은 [Dimension Processing Destination](data-flow/dimension-processing-destination.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3856f-104">To learn more about the Dimension Processing destination, see [Dimension Processing Destination](data-flow/dimension-processing-destination.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="3856f-105">옵션</span><span class="sxs-lookup"><span data-stu-id="3856f-105">Options</span></span>  
 <span data-ttu-id="3856f-106">**Connection manager**</span><span class="sxs-lookup"><span data-stu-id="3856f-106">**Connection manager**</span></span>  
 <span data-ttu-id="3856f-107">목록에서 기존 연결 관리자를 선택하거나 **새로 만들기** 를 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3856f-107">Select an existing connection manager from the list, or click **New** to create a new connection manager.</span></span>  
  
 <span data-ttu-id="3856f-108">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="3856f-108">**New**</span></span>  
 <span data-ttu-id="3856f-109">**Analysis Services 연결 관리자 추가** 대화 상자를 사용하면 새 연결을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3856f-109">Create a new connection by using the **Add Analysis Services Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="3856f-110">**사용 가능한 차원 목록**</span><span class="sxs-lookup"><span data-stu-id="3856f-110">**List of available dimensions**</span></span>  
 <span data-ttu-id="3856f-111">처리할 차원을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3856f-111">Select the dimension to process.</span></span>  
  
 <span data-ttu-id="3856f-112">**처리 방법**</span><span class="sxs-lookup"><span data-stu-id="3856f-112">**Processing method**</span></span>  
 <span data-ttu-id="3856f-113">목록에서 선택한 차원에 적용할 처리 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3856f-113">Select the processing method to apply to the dimension selected in the list.</span></span> <span data-ttu-id="3856f-114">이 옵션의 기본값은 **전체**입니다.</span><span class="sxs-lookup"><span data-stu-id="3856f-114">The default value of this option is **Full**.</span></span>  
  
|<span data-ttu-id="3856f-115">값</span><span class="sxs-lookup"><span data-stu-id="3856f-115">Value</span></span>|<span data-ttu-id="3856f-116">Description</span><span class="sxs-lookup"><span data-stu-id="3856f-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3856f-117">**추가(증분)**</span><span class="sxs-lookup"><span data-stu-id="3856f-117">**Add (incremental)**</span></span>|<span data-ttu-id="3856f-118">차원의 증분 처리를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3856f-118">Perform an incremental processing of the dimension.</span></span>|  
|<span data-ttu-id="3856f-119">**전체**</span><span class="sxs-lookup"><span data-stu-id="3856f-119">**Full**</span></span>|<span data-ttu-id="3856f-120">차원의 전체 처리를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3856f-120">Perform full processing of the dimension.</span></span>|  
|<span data-ttu-id="3856f-121">**Update**</span><span class="sxs-lookup"><span data-stu-id="3856f-121">**Update**</span></span>|<span data-ttu-id="3856f-122">차원의 업데이트 처리를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3856f-122">Perform an update processing of the dimension.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3856f-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3856f-123">See Also</span></span>  
 <span data-ttu-id="3856f-124">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3856f-124">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="3856f-125">[차원 처리 대상 편집기 &#40;매핑 페이지&#41;](../../2014/integration-services/dimension-processing-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="3856f-125">[Dimension Processing Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/dimension-processing-destination-editor-mappings-page.md) </span></span>  
 [<span data-ttu-id="3856f-126">차원 처리 대상 편집기&#40;고급 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="3856f-126">Dimension Processing Destination Editor &#40;Advanced Page&#41;</span></span>](../../2014/integration-services/dimension-processing-destination-editor-advanced-page.md)  
  
  
