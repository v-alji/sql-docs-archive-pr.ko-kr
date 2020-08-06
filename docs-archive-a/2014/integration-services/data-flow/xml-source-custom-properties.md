---
title: XML 원본 사용자 지정 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: eb29b28c-3159-41ec-b3d7-fce5b2f2be55
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5e152b23b4f59ca46cb8272ca677dc1161b3efec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659538"
---
# <a name="xml-source-custom-properties"></a><span data-ttu-id="78488-102">XML 원본 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="78488-102">XML Source Custom Properties</span></span>
  <span data-ttu-id="78488-103">XML 원본에는 사용자 지정 속성과 모든 데이터 흐름 구성 요소에 공통된 속성이 모두 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78488-103">The XML source has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="78488-104">다음 표에서는 XML 원본의 사용자 지정 속성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="78488-104">The following table describes the custom properties of the XML source.</span></span> <span data-ttu-id="78488-105">모든 속성은 읽기/쓰기가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="78488-105">All properties are read/write.</span></span>  
  
|<span data-ttu-id="78488-106">속성 이름</span><span class="sxs-lookup"><span data-stu-id="78488-106">Property name</span></span>|<span data-ttu-id="78488-107">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="78488-107">Data Type</span></span>|<span data-ttu-id="78488-108">Description</span><span class="sxs-lookup"><span data-stu-id="78488-108">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="78488-109">AccessMode</span><span class="sxs-lookup"><span data-stu-id="78488-109">AccessMode</span></span>|<span data-ttu-id="78488-110">정수</span><span class="sxs-lookup"><span data-stu-id="78488-110">Integer</span></span>|<span data-ttu-id="78488-111">XML 데이터에 액세스하는 데 사용되는 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="78488-111">The mode used to access the XML data.</span></span>|  
|<span data-ttu-id="78488-112">UseInlineSchema</span><span class="sxs-lookup"><span data-stu-id="78488-112">UseInlineSchema</span></span>|<span data-ttu-id="78488-113">부울</span><span class="sxs-lookup"><span data-stu-id="78488-113">Boolean</span></span>|<span data-ttu-id="78488-114">XML 원본 내에서 인라인 스키마 정의를 사용할지 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="78488-114">A value that indicates whether to use an inline schema definition within the XML source.</span></span> <span data-ttu-id="78488-115">이 속성의 기본값은 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="78488-115">The default value of this property is `False`.</span></span>|  
|<span data-ttu-id="78488-116">XMLData</span><span class="sxs-lookup"><span data-stu-id="78488-116">XMLData</span></span>|<span data-ttu-id="78488-117">String</span><span class="sxs-lookup"><span data-stu-id="78488-117">String</span></span>|<span data-ttu-id="78488-118">XML 데이터를 검색할 파일 또는 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="78488-118">The file or variables from which to retrieve the XML data.</span></span><br /><br /> <span data-ttu-id="78488-119">이 속성의 값은 속성 식을 사용하여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78488-119">The value of this property can be specified by using a property expression.</span></span>|  
|<span data-ttu-id="78488-120">XMLSchemaDefinition</span><span class="sxs-lookup"><span data-stu-id="78488-120">XMLSchemaDefinition</span></span>|<span data-ttu-id="78488-121">String</span><span class="sxs-lookup"><span data-stu-id="78488-121">String</span></span>|<span data-ttu-id="78488-122">스키마 정의 파일(.xsd)의 경로 및 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="78488-122">The path and file name of the schema definition file (.xsd).</span></span><br /><br /> <span data-ttu-id="78488-123">이 속성의 값은 속성 식을 사용하여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78488-123">The value of this property can be specified by using a property expression.</span></span>|  
  
 <span data-ttu-id="78488-124">다음 표에서는 XML 원본 출력의 사용자 지정 속성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="78488-124">The following table describes the custom properties of the output of the XML source.</span></span> <span data-ttu-id="78488-125">모든 속성은 읽기/쓰기가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="78488-125">All properties are read/write.</span></span>  
  
|<span data-ttu-id="78488-126">속성 이름</span><span class="sxs-lookup"><span data-stu-id="78488-126">Property name</span></span>|<span data-ttu-id="78488-127">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="78488-127">Data Type</span></span>|<span data-ttu-id="78488-128">Description</span><span class="sxs-lookup"><span data-stu-id="78488-128">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="78488-129">RowsetID</span><span class="sxs-lookup"><span data-stu-id="78488-129">RowsetID</span></span>|<span data-ttu-id="78488-130">String</span><span class="sxs-lookup"><span data-stu-id="78488-130">String</span></span>|<span data-ttu-id="78488-131">출력과 연결된 행 집합을 식별하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="78488-131">A value that identifies the rowset associated with the output.</span></span>|  
  
 <span data-ttu-id="78488-132">XML 원본의 출력 열에는 사용자 지정 속성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="78488-132">The output columns of the XML source have no custom properties.</span></span>  
  
 <span data-ttu-id="78488-133">자세한 내용은 [XML Source](xml-source.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="78488-133">For more information, see [XML Source](xml-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78488-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="78488-134">See Also</span></span>  
 [<span data-ttu-id="78488-135">Common Properties</span><span class="sxs-lookup"><span data-stu-id="78488-135">Common Properties</span></span>](../common-properties.md)  
  
  
