---
title: CDC 분할자 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsplitter.f1
ms.assetid: 167bc5c6-fa36-439d-987c-b20acd1a77e2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 45dd16602625b28d2ca7e16f2fa6b0d62294fe81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652242"
---
# <a name="cdc-splitter"></a><span data-ttu-id="6f7f9-102">CDC 분할자</span><span class="sxs-lookup"><span data-stu-id="6f7f9-102">CDC Splitter</span></span>
  <span data-ttu-id="6f7f9-103">CDC 분할자는 CDC 원본 데이터 흐름의 단일 변경 행 흐름을 삽입, 업데이트 및 삭제 작업을 위한 여러 데이터 흐름으로 분할합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7f9-103">The CDC splitter splits a single flow of change rows from a CDC source data flow into different data flows for Insert, Update and Delete operations.</span></span> <span data-ttu-id="6f7f9-104">데이터 흐름은 필요한 열인 `__$operation` 과 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 변경 테이블의 해당 표준 값을 기반으로 분할됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f7f9-104">The data flow is split based on the required column `__$operation` and its standard values in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] change tables.</span></span>  
  
|<span data-ttu-id="6f7f9-105">작업 값</span><span class="sxs-lookup"><span data-stu-id="6f7f9-105">Value of Operation</span></span>|<span data-ttu-id="6f7f9-106">출력</span><span class="sxs-lookup"><span data-stu-id="6f7f9-106">Output</span></span>|<span data-ttu-id="6f7f9-107">Description</span><span class="sxs-lookup"><span data-stu-id="6f7f9-107">Description</span></span>|  
|------------------------|------------|-----------------|  
|<span data-ttu-id="6f7f9-108">1</span><span class="sxs-lookup"><span data-stu-id="6f7f9-108">1</span></span>|<span data-ttu-id="6f7f9-109">DELETE</span><span class="sxs-lookup"><span data-stu-id="6f7f9-109">Delete</span></span>|<span data-ttu-id="6f7f9-110">삭제된 행</span><span class="sxs-lookup"><span data-stu-id="6f7f9-110">Deleted Row</span></span>|  
|<span data-ttu-id="6f7f9-111">2</span><span class="sxs-lookup"><span data-stu-id="6f7f9-111">2</span></span>|<span data-ttu-id="6f7f9-112">삽입</span><span class="sxs-lookup"><span data-stu-id="6f7f9-112">Insert</span></span>|<span data-ttu-id="6f7f9-113">삽입된 행( **병합을 사용한 순 변경 내용** CDC 모드를 사용하는 경우에는 제공되지 않음)</span><span class="sxs-lookup"><span data-stu-id="6f7f9-113">Inserted row (not available when using **Net with Merge** CDC mode)</span></span>|  
|<span data-ttu-id="6f7f9-114">3</span><span class="sxs-lookup"><span data-stu-id="6f7f9-114">3</span></span>|<span data-ttu-id="6f7f9-115">업데이트</span><span class="sxs-lookup"><span data-stu-id="6f7f9-115">Update</span></span>|<span data-ttu-id="6f7f9-116">업데이트 전 행( **이전 값이 포함된 모두** CDC 모드를 사용하는 경우에만 제공됨)</span><span class="sxs-lookup"><span data-stu-id="6f7f9-116">Before-update row (available only when using **All with Old Values** CDC mode)</span></span>|  
|<span data-ttu-id="6f7f9-117">4</span><span class="sxs-lookup"><span data-stu-id="6f7f9-117">4</span></span>|<span data-ttu-id="6f7f9-118">업데이트</span><span class="sxs-lookup"><span data-stu-id="6f7f9-118">Update</span></span>|<span data-ttu-id="6f7f9-119">업데이트 후 행(업데이트 전을 따름)</span><span class="sxs-lookup"><span data-stu-id="6f7f9-119">After-update row (follows the Before-update)</span></span>|  
|<span data-ttu-id="6f7f9-120">5</span><span class="sxs-lookup"><span data-stu-id="6f7f9-120">5</span></span>|<span data-ttu-id="6f7f9-121">업데이트</span><span class="sxs-lookup"><span data-stu-id="6f7f9-121">Update</span></span>|<span data-ttu-id="6f7f9-122">병합 행( **병합을 사용한 순 변경 내용** CDC 모드를 사용하는 경우에만 제공됨)</span><span class="sxs-lookup"><span data-stu-id="6f7f9-122">Merge row (available only when using **Net with Merge** CDC mode)</span></span>|  
|<span data-ttu-id="6f7f9-123">기타</span><span class="sxs-lookup"><span data-stu-id="6f7f9-123">Other</span></span>|<span data-ttu-id="6f7f9-124">Error</span><span class="sxs-lookup"><span data-stu-id="6f7f9-124">Error</span></span>||  
  
 <span data-ttu-id="6f7f9-125">분할자를 사용하여 미리 정의된 삽입, 삭제 및 업데이트 출력에 연결하여 해당 출력을 추가적으로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f7f9-125">You can use the splitter to connect to pre-defined INSERT, DELETE, and UPDATE outputs for further processing.</span></span>  
  
 <span data-ttu-id="6f7f9-126">CDC 분할자 변환에 하나의 일반 입력과 하나의 오류 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f7f9-126">The CDC Splitter transformation has one regular input and one error output.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="6f7f9-127">오류 처리</span><span class="sxs-lookup"><span data-stu-id="6f7f9-127">Error Handling</span></span>  
 <span data-ttu-id="6f7f9-128">CDC 분할자 변환에 하나의 오류 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f7f9-128">The CDC Splitter transformation has an error output.</span></span> <span data-ttu-id="6f7f9-129">$operation 열의 잘못된 값이 포함된 입력 행은 잘못된 것으로 간주되며 입력의 **ErrorRowDisposition** 속성에 따라 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f7f9-129">Input rows with an invalid value of the $operation column are considered erroneous and are handled according to the **ErrorRowDisposition** property of the input.</span></span>  
  
 <span data-ttu-id="6f7f9-130">구성 요소 오류 출력에 다음과 같은 출력 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f7f9-130">The component error output includes the following output columns:</span></span>  
  
-   <span data-ttu-id="6f7f9-131">**오류 코드**: 1로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7f9-131">**Error Code**: Set to 1.</span></span>  
  
-   <span data-ttu-id="6f7f9-132">**오류 열**: 오류의 원인이 되는 원본 열입니다(변환 오류의 경우).</span><span class="sxs-lookup"><span data-stu-id="6f7f9-132">**Error Column**: The source column causing the error (for conversion errors).</span></span>  
  
-   <span data-ttu-id="6f7f9-133">**오류 행 열**: 오류의 원인이 된 행의 입력 열입니다.</span><span class="sxs-lookup"><span data-stu-id="6f7f9-133">**Error Row Columns**: The input columns of the row that caused the error.</span></span>  
  
## <a name="configuring-the-cdc-splitter"></a><span data-ttu-id="6f7f9-134">CDC 분할자 구성</span><span class="sxs-lookup"><span data-stu-id="6f7f9-134">Configuring the CDC Splitter</span></span>  
 <span data-ttu-id="6f7f9-135">CDC 분할자에 대해 구성 가능한 속성은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f7f9-135">There are no configurable properties for the CDC splitter.</span></span>  
  
 <span data-ttu-id="6f7f9-136">CDC 분할자 사용에 대한 자세한 내용은 Microsoft SQL Server Integration Services용 CDC 구성 요소를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6f7f9-136">For more information about using the CDC splitter, see CDC Components for Microsoft SQL Server Integration Services.</span></span>  
  
 <span data-ttu-id="6f7f9-137">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f7f9-137">The **Advanced Editor** dialog box contains the properties that can be set programmatically.</span></span>  
  
 <span data-ttu-id="6f7f9-138">**고급 편집기** 대화 상자를 열려면</span><span class="sxs-lookup"><span data-stu-id="6f7f9-138">To open the **Advanced Editor** dialog box:</span></span>  
  
-   <span data-ttu-id="6f7f9-139">**프로젝트의** 데이터 흐름 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 화면에서 CDC 분할자를 마우스 오른쪽 단추로 클릭하고 **고급 편집기 표시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7f9-139">In the **Data Flow** screen of your [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project, right click the CDC splitter and select **Show Advanced Editor**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f7f9-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6f7f9-140">See Also</span></span>  
 [<span data-ttu-id="6f7f9-141">변경 유형에 따라 CDC 스트림 전송</span><span class="sxs-lookup"><span data-stu-id="6f7f9-141">Direct the CDC Stream According to the Type of Change</span></span>](direct-the-cdc-stream-according-to-the-type-of-change.md)  
  
  
