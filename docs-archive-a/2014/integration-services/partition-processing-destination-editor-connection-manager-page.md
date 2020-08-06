---
title: 파티션 처리 대상 편집기 (연결 관리자 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partprocessingtransformation.connection.f1
helpviewer_keywords:
- Partition Processing Destination Editor
ms.assetid: 7add6f82-eed1-47fc-a5d7-7b91f3f24d34
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5a0f79dfcc9c0d98d871a49618f4dabfb8a3bbac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650158"
---
# <a name="partition-processing-destination-editor-connection-manager-page"></a><span data-ttu-id="f0fcc-102">파티션 처리 대상 편집기(연결 관리자 페이지)</span><span class="sxs-lookup"><span data-stu-id="f0fcc-102">Partition Processing Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="f0fcc-103">**파티션 처리 대상 편집기** 대화 상자의 **연결 관리자** 페이지를 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 프로젝트나 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 대한 연결을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0fcc-103">Use the **Connection Manager** page of the **Partition Processing Destination Editor** dialog box to specify a connection to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project or to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f0fcc-104">파티션 처리 대상에 대한 자세한 내용은 [Partition Processing Destination](data-flow/partition-processing-destination.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f0fcc-104">To learn more abou the Partition Processing destination, see [Partition Processing Destination](data-flow/partition-processing-destination.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f0fcc-105">여기에서 설명하는 태스크는 Analysis Services 테이블 형식 모델에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f0fcc-105">Tasks described here do not apply to Analysis Services tabular models.</span></span>  <span data-ttu-id="f0fcc-106">테이블 형식 모델의 경우 입력 열을 파티션 열에 매핑할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f0fcc-106">You cannot map input columns to partition columns for tabular models.</span></span> <span data-ttu-id="f0fcc-107">대신 [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) 를 사용하여 파티션을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0fcc-107">You can instead use the Analysis Services Execute DDL task [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) to process the partition.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f0fcc-108">옵션</span><span class="sxs-lookup"><span data-stu-id="f0fcc-108">Options</span></span>  
 <span data-ttu-id="f0fcc-109">**Connection manager**</span><span class="sxs-lookup"><span data-stu-id="f0fcc-109">**Connection manager**</span></span>  
 <span data-ttu-id="f0fcc-110">목록에서 기존 연결 관리자를 선택하거나 **새로 만들기**를 클릭하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f0fcc-110">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="f0fcc-111">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="f0fcc-111">**New**</span></span>  
 <span data-ttu-id="f0fcc-112">**Analysis Services 연결 관리자 추가** 대화 상자를 사용하면 새 연결을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0fcc-112">Create a new connection by using the **Add Analysis Services Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="f0fcc-113">**사용 가능한 파티션 목록**</span><span class="sxs-lookup"><span data-stu-id="f0fcc-113">**List of available partitions**</span></span>  
 <span data-ttu-id="f0fcc-114">처리할 파티션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f0fcc-114">Select the partition to process.</span></span>  
  
 <span data-ttu-id="f0fcc-115">**처리 방법**</span><span class="sxs-lookup"><span data-stu-id="f0fcc-115">**Processing method**</span></span>  
 <span data-ttu-id="f0fcc-116">처리 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f0fcc-116">Select the processing method.</span></span> <span data-ttu-id="f0fcc-117">이 옵션의 기본값은 **전체**입니다.</span><span class="sxs-lookup"><span data-stu-id="f0fcc-117">The default value of this option is **Full**.</span></span>  
  
|<span data-ttu-id="f0fcc-118">값</span><span class="sxs-lookup"><span data-stu-id="f0fcc-118">Value</span></span>|<span data-ttu-id="f0fcc-119">Description</span><span class="sxs-lookup"><span data-stu-id="f0fcc-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f0fcc-120">추가(증분)</span><span class="sxs-lookup"><span data-stu-id="f0fcc-120">Add (incremental)</span></span>|<span data-ttu-id="f0fcc-121">파티션의 증분 처리를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0fcc-121">Perform an incremental processing of the partition.</span></span>|  
|<span data-ttu-id="f0fcc-122">전체</span><span class="sxs-lookup"><span data-stu-id="f0fcc-122">Full</span></span>|<span data-ttu-id="f0fcc-123">파티션의 전체 처리를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0fcc-123">Perform full processing of the partition.</span></span>|  
|<span data-ttu-id="f0fcc-124">데이터만</span><span class="sxs-lookup"><span data-stu-id="f0fcc-124">Data only</span></span>|<span data-ttu-id="f0fcc-125">파티션의 업데이트 처리를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0fcc-125">Perform an update processing of the partition.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0fcc-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f0fcc-126">See Also</span></span>  
 <span data-ttu-id="f0fcc-127">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="f0fcc-127">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="f0fcc-128">[파티션 처리 대상 편집기 &#40;매핑 페이지&#41;](../../2014/integration-services/partition-processing-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="f0fcc-128">[Partition Processing Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/partition-processing-destination-editor-mappings-page.md) </span></span>  
 [<span data-ttu-id="f0fcc-129">파티션 처리 대상 편집기&#40;고급 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="f0fcc-129">Partition Processing Destination Editor &#40;Advanced Page&#41;</span></span>](../../2014/integration-services/partition-processing-destination-editor-advanced-page.md)  
  
  
