---
title: 데이터 원본 정보 속성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- information properties [OLE DB]
- OLE DB data source properties [SQL Server Native Client]
ms.assetid: 7fd80e47-5bd9-41e2-a3d3-091a7c8c5f2b
author: rothja
ms.author: jroth
ms.openlocfilehash: c10a4e762bbe3421e720753941f5e0a5702832ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740879"
---
# <a name="data-source-information-properties"></a><span data-ttu-id="af904-102">데이터 원본 정보 속성</span><span class="sxs-lookup"><span data-stu-id="af904-102">Data Source Information Properties</span></span>
  <span data-ttu-id="af904-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 공급자별 속성 집합 DBPROPSET_SQLSERVERDATASOURCEINFO에 다음과 같은 데이터 원본 정보 속성을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="af904-103">In the provider-specific property set DBPROPSET_SQLSERVERDATASOURCEINFO, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the following data source information properties.</span></span>  
  
|<span data-ttu-id="af904-104">속성 ID</span><span class="sxs-lookup"><span data-stu-id="af904-104">Property ID</span></span>|<span data-ttu-id="af904-105">Description</span><span class="sxs-lookup"><span data-stu-id="af904-105">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="af904-106">SSPROP_COLUMNLEVELCOLLATION</span><span class="sxs-lookup"><span data-stu-id="af904-106">SSPROP_COLUMNLEVELCOLLATION</span></span>|<span data-ttu-id="af904-107">유형: VT_BOOL</span><span class="sxs-lookup"><span data-stu-id="af904-107">Type: VT_BOOL</span></span><br /><br /> <span data-ttu-id="af904-108">R/W: Read</span><span class="sxs-lookup"><span data-stu-id="af904-108">R/W: Read</span></span><br /><br /> <span data-ttu-id="af904-109">기본값: VARIANT_TRUE</span><span class="sxs-lookup"><span data-stu-id="af904-109">Default: VARIANT_TRUE</span></span><br /><br /> <span data-ttu-id="af904-110">설명: 열 데이터 정렬이 지원되는지 확인하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="af904-110">Description: Used to determine if column collation is supported.</span></span><br /><br /> <span data-ttu-id="af904-111">VARIANT_TRUE: 열 수준 데이터 정렬이 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af904-111">VARIANT_TRUE: Column level collation is supported.</span></span><br /><br /> <span data-ttu-id="af904-112">VARIANT_FALSE: 열 수준 데이터 정렬은 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="af904-112">VARIANT_FALSE: Column level collation is not supported.</span></span>|  
|<span data-ttu-id="af904-113">SSPROP_UNICODELCID</span><span class="sxs-lookup"><span data-stu-id="af904-113">SSPROP_UNICODELCID</span></span>|<span data-ttu-id="af904-114">형식: VT_I4 R/W: Read</span><span class="sxs-lookup"><span data-stu-id="af904-114">Type: VT_I4 R/W: Read</span></span><br /><br /> <span data-ttu-id="af904-115">설명: 유니코드 로캘 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="af904-115">Description: Unicode locale ID.</span></span><br /><br /> <span data-ttu-id="af904-116">유니코드 데이터 정렬에 사용되는 로캘입니다.</span><span class="sxs-lookup"><span data-stu-id="af904-116">This is the locale used for Unicode data sorting.</span></span>|  
|<span data-ttu-id="af904-117">SSPROP_UNICODECOMPARISONSTYLE</span><span class="sxs-lookup"><span data-stu-id="af904-117">SSPROP_UNICODECOMPARISONSTYLE</span></span>|<span data-ttu-id="af904-118">형식: VT_I4 R/W: Read</span><span class="sxs-lookup"><span data-stu-id="af904-118">Type: VT_I4 R/W: Read</span></span><br /><br /> <span data-ttu-id="af904-119">설명: 유니코드 비교 스타일입니다.</span><span class="sxs-lookup"><span data-stu-id="af904-119">Description: Unicode comparison style.</span></span><br /><br /> <span data-ttu-id="af904-120">유니코드 데이터 정렬에 사용되는 정렬 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="af904-120">The sorting options used for Unicode data sorting.</span></span>|  
  
 <span data-ttu-id="af904-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 공급자별 속성 집합 DBPROPSET_SQLSERVERSTREAM에 다음과 같은 추가 속성을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="af904-121">In the provider-specific property set DBPROPSET_SQLSERVERSTREAM, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the following additional property.</span></span>  
  
|<span data-ttu-id="af904-122">속성 ID</span><span class="sxs-lookup"><span data-stu-id="af904-122">Property ID</span></span>|<span data-ttu-id="af904-123">Description</span><span class="sxs-lookup"><span data-stu-id="af904-123">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="af904-124">SSPROP_STREAM_XMLROOT</span><span class="sxs-lookup"><span data-stu-id="af904-124">SSPROP_STREAM_XMLROOT</span></span>|<span data-ttu-id="af904-125">형식: VT_BSTR R/W: 읽기/쓰기</span><span class="sxs-lookup"><span data-stu-id="af904-125">Type: VT_BSTR R/W: Read/Write</span></span><br /><br /> <span data-ttu-id="af904-126">설명: FOR XML 쿼리 결과가 올바른 형식의 문서가 아닐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af904-126">Description: The result of a FOR XML query may not be a well-formed document.</span></span> <span data-ttu-id="af904-127">이 속성이 지정되면 ‘select ... for XML’ 쿼리의 결과가 이 속성에서 제공한 루트 태그에 래핑되어 올바른 형식의 XML 문서가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="af904-127">When this property is specified, the result of a 'select ... for XML' query is wrapped in the root tag provided by this property to return a well formed XML document.</span></span> <span data-ttu-id="af904-128">쿼리가 브라우저에서 실행되는 경우에는 결과를 로드할 때 브라우저에서 파서 오류가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af904-128">If the query is executed in the browser it may cause the browser to display parser errors when loading the result.</span></span> <span data-ttu-id="af904-129">오류를 방지하기 위해 SQL ISAPI는 ROOT 키워드를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="af904-129">To avoid the error, SQL ISAPI supports the keyword ROOT.</span></span> <span data-ttu-id="af904-130">이 키워드는 SSPROP_STREAM_XMLROOT 속성에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="af904-130">This keyword maps to SSPROP_STREAM_XMLROOT property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="af904-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="af904-131">See Also</span></span>  
 [<span data-ttu-id="af904-132">데이터 원본 개체 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="af904-132">Data Source Objects &#40;OLE DB&#41;</span></span>](data-source-objects-ole-db.md)  
  
  
