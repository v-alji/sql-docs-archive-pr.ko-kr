---
title: DISCOVER_XEVENT_TRACE_DEFINITION 행 집합 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: e1ce2d2d-f994-4318-801a-ee0385aecd84
author: minewiskan
ms.author: owend
ms.openlocfilehash: bedd6ec66a188738ac9a522b4802b3b431e82f36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734567"
---
# <a name="discover_xevent_trace_definition-rowset"></a><span data-ttu-id="1023c-102">DISCOVER_XEVENT_TRACE_DEFINITION 행 집합</span><span class="sxs-lookup"><span data-stu-id="1023c-102">DISCOVER_XEVENT_TRACE_DEFINITION Rowset</span></span>
  <span data-ttu-id="1023c-103">서버에서 현재 활성 상태인 XEvent 추적에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1023c-103">Provides information about XEvent traces that are currently active on the server.</span></span>  
  
 <span data-ttu-id="1023c-104">**적용 대상:** 테이블 형식 모델, 다차원 모델</span><span class="sxs-lookup"><span data-stu-id="1023c-104">**Applies to:** tabular models, multidimensional models</span></span>  
  
## <a name="rowset-columns"></a><span data-ttu-id="1023c-105">행 집합 열</span><span class="sxs-lookup"><span data-stu-id="1023c-105">Rowset Columns</span></span>  
 <span data-ttu-id="1023c-106">`DISCOVER_XEVENT_TRACE_DEFINITION` 행 집합에는 다음 열이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1023c-106">The `DISCOVER_XEVENT_TRACE_DEFINITION` rowset contains the following columns.</span></span>  
  
|<span data-ttu-id="1023c-107">열 이름</span><span class="sxs-lookup"><span data-stu-id="1023c-107">Column name</span></span>|<span data-ttu-id="1023c-108">유형 표시기</span><span class="sxs-lookup"><span data-stu-id="1023c-108">Type indicator</span></span>|<span data-ttu-id="1023c-109">길이</span><span class="sxs-lookup"><span data-stu-id="1023c-109">Length</span></span>|<span data-ttu-id="1023c-110">설명</span><span class="sxs-lookup"><span data-stu-id="1023c-110">Description</span></span>|  
|-----------------|--------------------|------------|-----------------|  
|`Data`|`DBTYPE_WSTR`||<span data-ttu-id="1023c-111">XEvent 추적의 XML 정의입니다.</span><span class="sxs-lookup"><span data-stu-id="1023c-111">The XML definition of the XEvent trace.</span></span>|  
  
 <span data-ttu-id="1023c-112">이 스키마 행 집합은 정렬되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1023c-112">This schema rowset is not sorted.</span></span>  
  
## <a name="using-adomdnet-to-return-the-rowset"></a><span data-ttu-id="1023c-113">ADOMD.NET을 사용하여 행 집합 반환</span><span class="sxs-lookup"><span data-stu-id="1023c-113">Using ADOMD.NET to return the rowset</span></span>  
 <span data-ttu-id="1023c-114">ADOMD.NET 및 스키마 행 집합을 사용하여 메타데이터를 검색할 때 GUID 또는 문자열을 사용하여 GetSchemaDataSet 메서드의 스키마 행 집합 개체를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1023c-114">When using ADOMD.NET and the schema rowset to retrieve metadata, you can use either the GUID or string to reference a schema rowset object in the GetSchemaDataSet method.</span></span> <span data-ttu-id="1023c-115">자세한 내용은 [Working with Schema Rowsets in ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1023c-115">For more information, see [Working with Schema Rowsets in ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets).</span></span>  
  
 <span data-ttu-id="1023c-116">다음 표에서는 이 행 집합을 식별하는 GUID와 문자열 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1023c-116">The following table provides the GUID and string values that identify this rowset.</span></span>  
  
|<span data-ttu-id="1023c-117">인수</span><span class="sxs-lookup"><span data-stu-id="1023c-117">Argument</span></span>|<span data-ttu-id="1023c-118">값</span><span class="sxs-lookup"><span data-stu-id="1023c-118">Value</span></span>|  
|--------------|-----------|  
|<span data-ttu-id="1023c-119">GUID</span><span class="sxs-lookup"><span data-stu-id="1023c-119">GUID</span></span>|<span data-ttu-id="1023c-120">a07ccd1c-8148-11d0-87bb-00c04fc33942</span><span class="sxs-lookup"><span data-stu-id="1023c-120">a07ccd1c-8148-11d0-87bb-00c04fc33942</span></span>|  
|<span data-ttu-id="1023c-121">String</span><span class="sxs-lookup"><span data-stu-id="1023c-121">String</span></span>|<span data-ttu-id="1023c-122">DISCOVER_XEVENT_TRACE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="1023c-122">DISCOVER_XEVENT_TRACE_DEFINITION</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1023c-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1023c-123">See Also</span></span>  
 <span data-ttu-id="1023c-124">[XML for Analysis 스키마 행 집합](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/xml-for-analysis-schema-rowsets) </span><span class="sxs-lookup"><span data-stu-id="1023c-124">[XML for Analysis Schema Rowsets](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/xml-for-analysis-schema-rowsets) </span></span>  
 <span data-ttu-id="1023c-125">[SQL Server 확장 이벤트 &#40;Xevent&#41;를 사용 하 여 모니터링 Analysis Services](../instances/monitor-analysis-services-with-sql-server-extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="1023c-125">[Use SQL Server Extended Events &#40;XEvents&#41; to Monitor Analysis Services](../instances/monitor-analysis-services-with-sql-server-extended-events.md) </span></span>  
 [<span data-ttu-id="1023c-126">DMV&#40;동적 관리 뷰&#41;를 사용하여 Analysis Services 모니터링</span><span class="sxs-lookup"><span data-stu-id="1023c-126">Use Dynamic Management Views &#40;DMVs&#41; to Monitor Analysis Services</span></span>](../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
