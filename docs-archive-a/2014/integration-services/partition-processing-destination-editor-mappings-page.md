---
title: 파티션 처리 대상 편집기 (매핑 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partprocessingtransformation.mapping.f1
helpviewer_keywords:
- Partition Processing Destination Editor
ms.assetid: e75b766c-85ba-453e-9576-4a1a34f91ecc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3855b15c7ebf1f6fa95c941931869064d552680e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660042"
---
# <a name="partition-processing-destination-editor-mappings-page"></a><span data-ttu-id="1a6bd-102">파티션 처리 대상 편집기(매핑 페이지)</span><span class="sxs-lookup"><span data-stu-id="1a6bd-102">Partition Processing Destination Editor (Mappings Page)</span></span>
  <span data-ttu-id="1a6bd-103">**파티션 처리 대상 편집기** 대화 상자의 **매핑** 페이지를 사용하여 입력 열을 파티션 열에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a6bd-103">Use the **Mappings** page of the **Partition Processing Destination Editor** dialog box to map input columns to partition columns.</span></span>  
  
 <span data-ttu-id="1a6bd-104">파티션 처리 대상에 대한 자세한 내용은 [Partition Processing Destination](data-flow/partition-processing-destination.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1a6bd-104">To learn more abou the Partition Processing destination, see [Partition Processing Destination](data-flow/partition-processing-destination.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1a6bd-105">여기에서 설명하는 태스크는 Analysis Services 테이블 형식 모델에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1a6bd-105">Tasks described here do not apply to Analysis Services tabular models.</span></span>  <span data-ttu-id="1a6bd-106">테이블 형식 모델의 경우 입력 열을 파티션 열에 매핑할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1a6bd-106">You cannot map input columns to partition columns for tabular models.</span></span> <span data-ttu-id="1a6bd-107">대신 [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) 를 사용하여 파티션을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a6bd-107">You can instead use the Analysis Services Execute DDL task [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) to process the partition.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1a6bd-108">옵션</span><span class="sxs-lookup"><span data-stu-id="1a6bd-108">Options</span></span>  
 <span data-ttu-id="1a6bd-109">**사용 가능한 입력 열**</span><span class="sxs-lookup"><span data-stu-id="1a6bd-109">**Available Input Columns**</span></span>  
 <span data-ttu-id="1a6bd-110">사용 가능한 입력 열 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1a6bd-110">View the list of available input columns.</span></span> <span data-ttu-id="1a6bd-111">끌어서 놓기 작업을 사용하여 테이블에서 사용 가능한 입력 열을 대상 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="1a6bd-111">Use a drag-and-drop operation to map available input columns in the table to destination columns.</span></span>  
  
 <span data-ttu-id="1a6bd-112">**사용 가능한 대상 열**</span><span class="sxs-lookup"><span data-stu-id="1a6bd-112">**Available Destination Columns**</span></span>  
 <span data-ttu-id="1a6bd-113">사용 가능한 대상 열의 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1a6bd-113">View the list of available destination columns.</span></span> <span data-ttu-id="1a6bd-114">끌어서 놓기 작업을 사용하여 테이블에서 사용 가능한 대상 열을 입력 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="1a6bd-114">Use a drag-and-drop operation to map available destination columns in the table to input columns.</span></span>  
  
 <span data-ttu-id="1a6bd-115">**입력 열**</span><span class="sxs-lookup"><span data-stu-id="1a6bd-115">**Input Column**</span></span>  
 <span data-ttu-id="1a6bd-116">위 테이블에서 선택한 입력 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1a6bd-116">View input columns selected from the table above.</span></span> <span data-ttu-id="1a6bd-117">**사용 가능한 입력 열**의 목록을 사용하여 매핑을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a6bd-117">You can change the mappings by using the list of **Available Input Columns**.</span></span>  
  
 <span data-ttu-id="1a6bd-118">**대상 열**</span><span class="sxs-lookup"><span data-stu-id="1a6bd-118">**Destination Column**</span></span>  
 <span data-ttu-id="1a6bd-119">매핑 여부에 관계없이 사용 가능한 각 대상 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1a6bd-119">View each available destination column, whether it is mapped or not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a6bd-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1a6bd-120">See Also</span></span>  
 <span data-ttu-id="1a6bd-121">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="1a6bd-121">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="1a6bd-122">[파티션 처리 대상 편집기 &#40;연결 관리자 페이지&#41;](../../2014/integration-services/partition-processing-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="1a6bd-122">[Partition Processing Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/partition-processing-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="1a6bd-123">파티션 처리 대상 편집기&#40;고급 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="1a6bd-123">Partition Processing Destination Editor &#40;Advanced Page&#41;</span></span>](../../2014/integration-services/partition-processing-destination-editor-advanced-page.md)  
  
  
