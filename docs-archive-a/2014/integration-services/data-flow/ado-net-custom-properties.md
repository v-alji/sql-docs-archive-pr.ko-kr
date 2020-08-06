---
title: ADO.NET 사용자 지정 속성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e062a9ab-1e6b-4061-845a-4f8a0552b09d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bada6f512770d0f9f07ddc3693070c8aad309cb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728579"
---
# <a name="ado-net-custom-properties"></a><span data-ttu-id="5e4f0-102">ADO.NET 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="5e4f0-102">ADO NET Custom Properties</span></span>
  <span data-ttu-id="5e4f0-103">**원본 사용자 지정 속성**</span><span class="sxs-lookup"><span data-stu-id="5e4f0-103">**Source Custom Properties**</span></span>  
  
 <span data-ttu-id="5e4f0-104">ADO.NET 원본에는 사용자 지정 속성과 모든 데이터 흐름 구성 요소에 공통된 속성이 모두 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-104">The ADO NET source has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="5e4f0-105">다음 표에서는 ADO.NET 원본의 사용자 지정 속성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-105">The following table describes the custom properties of the ADO NET source.</span></span> <span data-ttu-id="5e4f0-106">모든 속성은 읽기/쓰기가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-106">All properties are read/write.</span></span>  
  
|<span data-ttu-id="5e4f0-107">속성 이름</span><span class="sxs-lookup"><span data-stu-id="5e4f0-107">Property name</span></span>|<span data-ttu-id="5e4f0-108">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="5e4f0-108">Data Type</span></span>|<span data-ttu-id="5e4f0-109">Description</span><span class="sxs-lookup"><span data-stu-id="5e4f0-109">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="5e4f0-110">CommandTimeout</span><span class="sxs-lookup"><span data-stu-id="5e4f0-110">CommandTimeout</span></span>|<span data-ttu-id="5e4f0-111">String</span><span class="sxs-lookup"><span data-stu-id="5e4f0-111">String</span></span>|<span data-ttu-id="5e4f0-112">SQL 명령이 종료되기 전의 제한 시간(초)을 지정하는 값입니다. 값 0은 명령의 제한 시간이 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-112">A value that specifies the number of seconds before the SQL command times out. A value of 0 indicates that the command never times out.</span></span>|  
|<span data-ttu-id="5e4f0-113">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="5e4f0-113">SqlCommand</span></span>|<span data-ttu-id="5e4f0-114">String</span><span class="sxs-lookup"><span data-stu-id="5e4f0-114">String</span></span>|<span data-ttu-id="5e4f0-115">ADO.NET 원본이 데이터 추출에 사용하는 SQL 문입니다.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-115">The SQL statement that the ADO NET source uses to extract data.</span></span><br /><br /> <span data-ttu-id="5e4f0-116">패키지가 로드되면 ADO.NET 원본이 사용할 SQL 문으로 이 속성을 동적으로 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-116">When the package loads, you can dynamically update this property with the SQL statement that the ADO NET source will use.</span></span> <span data-ttu-id="5e4f0-117">자세한 내용은 [Integration Services&#40;SSIS&#41; 식](../expressions/integration-services-ssis-expressions.md) 및 [패키지에서 속성 식 사용](../expressions/use-property-expressions-in-packages.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-117">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md) and [Use Property Expressions in Packages](../expressions/use-property-expressions-in-packages.md).</span></span>|  
|<span data-ttu-id="5e4f0-118">AllowImplicitStringConversion</span><span class="sxs-lookup"><span data-stu-id="5e4f0-118">AllowImplicitStringConversion</span></span>|<span data-ttu-id="5e4f0-119">부울</span><span class="sxs-lookup"><span data-stu-id="5e4f0-119">Boolean</span></span>|<span data-ttu-id="5e4f0-120">다음이 발생하는지 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-120">A value that indicates whether the following occurs:</span></span><br /><br /> <span data-ttu-id="5e4f0-121">문자열(DT_WSTR 또는 DT_NTEXT)인 출력 열 유형과 외부 메타데이터 유형이 일치하지 않을 경우 유효성 검사 오류를 생성하지 않음</span><span class="sxs-lookup"><span data-stu-id="5e4f0-121">No generation of a validation error if there is a mismatch between external metadata types and output column types that are strings (DT_WSTR or DT_NTEXT).</span></span><br /><br /> <span data-ttu-id="5e4f0-122">출력 열이 사용하는 문자열 데이터 형식으로 외부 메타데이터 유형을 암시적으로 변환</span><span class="sxs-lookup"><span data-stu-id="5e4f0-122">Implicit conversion of external metadata types to the string data type that the output column uses.</span></span><br /><br /> <br /><br /> <span data-ttu-id="5e4f0-123">기본값은 TRUE입니다.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-123">The default value is TRUE.</span></span><br /><br /> <span data-ttu-id="5e4f0-124">자세한 내용은 [ADO NET Source](ado-net-source.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-124">For more information, see [ADO NET Source](ado-net-source.md).</span></span>|  
  
 <span data-ttu-id="5e4f0-125">ADO.NET 원본의 출력 및 출력 열에는 사용자 지정 속성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-125">The output and the output columns of the ADO NET source have no custom properties.</span></span>  
  
 <span data-ttu-id="5e4f0-126">자세한 내용은 [ADO NET Source](ado-net-source.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-126">For more information, see [ADO NET Source](ado-net-source.md).</span></span>  
  
 <span data-ttu-id="5e4f0-127">**대상 사용자 지정 속성**</span><span class="sxs-lookup"><span data-stu-id="5e4f0-127">**Destination Custom Properties**</span></span>  
  
 <span data-ttu-id="5e4f0-128">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 대상에는 사용자 지정 속성과 모든 데이터 흐름 구성 요소에 공통된 속성이 모두 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-128">The [!INCLUDE[vstecado](../../includes/vstecado-md.md)] destination has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="5e4f0-129">다음 표에서는 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 대상의 사용자 지정 속성을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-129">The following table describes the custom properties of the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] destination.</span></span> <span data-ttu-id="5e4f0-130">모든 속성은 읽기/쓰기가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-130">All properties are read/write.</span></span> <span data-ttu-id="5e4f0-131">이러한 속성은 **ADO NET 대상 편집기**에서 사용할 수 없지만 **고급 편집기**를 사용하여 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-131">These properties are not available in the **ADO NET Destination Editor**, but can be set by using the **Advanced Editor**.</span></span>  
  
|<span data-ttu-id="5e4f0-132">속성</span><span class="sxs-lookup"><span data-stu-id="5e4f0-132">Property</span></span>|<span data-ttu-id="5e4f0-133">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="5e4f0-133">Data Type</span></span>|<span data-ttu-id="5e4f0-134">Description</span><span class="sxs-lookup"><span data-stu-id="5e4f0-134">Description</span></span>|  
|--------------|---------------|-----------------|  
|<span data-ttu-id="5e4f0-135">BatchSize</span><span class="sxs-lookup"><span data-stu-id="5e4f0-135">BatchSize</span></span>|<span data-ttu-id="5e4f0-136">정수</span><span class="sxs-lookup"><span data-stu-id="5e4f0-136">Integer</span></span>|<span data-ttu-id="5e4f0-137">일괄 처리를 통해 서버로 전송되는 행 수입니다.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-137">The number of rows in a batch that is sent to the server.</span></span> <span data-ttu-id="5e4f0-138">값 **0** 은 일괄 처리 크기가 내부 버퍼 크기와 일치함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-138">A value of **0** indicates that the batch size matches the internal buffer size.</span></span> <span data-ttu-id="5e4f0-139">이 속성의 기본값은 **0**입니다.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-139">The default value of this property is **0**.</span></span>|  
|<span data-ttu-id="5e4f0-140">CommandTimeOut</span><span class="sxs-lookup"><span data-stu-id="5e4f0-140">CommandTimeOut</span></span>|<span data-ttu-id="5e4f0-141">정수</span><span class="sxs-lookup"><span data-stu-id="5e4f0-141">Integer</span></span>|<span data-ttu-id="5e4f0-142">제한 시간이 초과될 때까지 SQL 명령을 실행할 수 있는 최대 시간(초)입니다. 값 **0** 은 제한 시간이 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-142">The maximum number of seconds that the SQL command can run before timing out. A value of **0** indicates an infinite time.</span></span> <span data-ttu-id="5e4f0-143">이 속성의 기본값은 **0**입니다.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-143">The default value of this property is **0**.</span></span>|  
|<span data-ttu-id="5e4f0-144">TableOrViewName</span><span class="sxs-lookup"><span data-stu-id="5e4f0-144">TableOrViewName</span></span>|<span data-ttu-id="5e4f0-145">String</span><span class="sxs-lookup"><span data-stu-id="5e4f0-145">String</span></span>|<span data-ttu-id="5e4f0-146">대상 테이블 또는 뷰의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-146">The name of the destination table or view.</span></span>|  
  
 <span data-ttu-id="5e4f0-147">자세한 내용은 [ADO NET Destination](ado-net-destination.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-147">For more information, see [ADO NET Destination](ado-net-destination.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e4f0-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5e4f0-148">See Also</span></span>  
 [<span data-ttu-id="5e4f0-149">Common Properties</span><span class="sxs-lookup"><span data-stu-id="5e4f0-149">Common Properties</span></span>](../common-properties.md)  
  
  
