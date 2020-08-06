---
title: 'Sql: identity 및 sql: guid 주석 사용 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:guid
- annotated XSD schemas, IDENTITY-type columns
- annotated XSD schemas, GUID values
- DiffGrams [SQLXML], annotations
- identity annotation
- XSD schemas [SQLXML], GUID values
- GUIDs [SQLXML]
- guid annotation
- sql:identity
- IDENTITY-type column
- XSD schemas [SQLXML], IDENTITY-type columns
- updategrams [SQLXML], GUID values
ms.assetid: 7661dfd0-6573-4692-a8f1-3597adcd33c4
author: rothja
ms.author: jroth
ms.openlocfilehash: dc5c08f158911edb0a1a0638fc4bcee1e05a248c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650901"
---
# <a name="using-the-sqlidentity-and-sqlguid-annotations"></a><span data-ttu-id="89b08-102">sql:identity 및 sql:guid 주석 사용</span><span class="sxs-lookup"><span data-stu-id="89b08-102">Using the sql:identity and sql:guid Annotations</span></span>
  <span data-ttu-id="89b08-103">`sql:identity` `sql:guid` 의 데이터베이스 열에 매핑되는 노드의 XSD 스키마에서 및 주석을 지정할 수 있습니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="89b08-103">You can specify the `sql:identity` and `sql:guid` annotations in an XSD schema on any node that maps to a database column in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="89b08-104">updategram 형식은 `updg:at-identity` 및 `updg:guid` 특성을 지원하지만 DiffGram 형식은 이러한 특성을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="89b08-104">Whereas the updategram format supports the `updg:at-identity` and `updg:guid` attributes, the DiffGram format does not.</span></span> <span data-ttu-id="89b08-105">`updg:at-identity` 특성은 IDENTITY 형식의 열을 업데이트할 때의 동작을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="89b08-105">The `updg:at-identity` attribute defines the behavior in updating an IDENTITY-type column.</span></span> <span data-ttu-id="89b08-106">`updg:guid` 특성을 사용하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 GUID 값을 가져와서 updategram에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b08-106">The `updg:guid` attribute allows you to obtain a GUID value from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and use it in the updategram.</span></span> <span data-ttu-id="89b08-107">자세한 내용 및 작업 예제는 [XML Updategrams을 사용 하 여 데이터 삽입 &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="89b08-107">For more information and working samples, see [Inserting Data Using XML Updategrams &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="89b08-108">`sql:identity` 및 `sql:guid` 주석은 이 기능을 DiffGram으로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="89b08-108">The `sql:identity` and `sql:guid` annotations extend this functionality to DiffGrams.</span></span>  
  
 <span data-ttu-id="89b08-109">DiffGram을 실행하면 DiffGram이 먼저 updategram으로 변환된 다음 이 updategram이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="89b08-109">When you execute a DiffGram, it is first converted to an updategram, and then the updategram is executed.</span></span> <span data-ttu-id="89b08-110">XSD 스키마에서 `sql:identity` 및 `sql:guid` 주석을 지정하는 것은 updategram의 동작을 정의하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="89b08-110">By specifying the `sql:identity` and `sql:guid` annotations in the XSD schema, you are in fact defining the behavior of an updategram.</span></span> <span data-ttu-id="89b08-111">따라서 모든 주석이 updategram의 컨텍스트에서 기술됩니다.</span><span class="sxs-lookup"><span data-stu-id="89b08-111">Therefore, all the annotations are described in the context of an updategram.</span></span> <span data-ttu-id="89b08-112">DiffGram과 updategram에 모두 주석을 사용할 수 있지만 이 중 updategram이 ID 및 GUID 값을 처리하는 더 강력한 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="89b08-112">The annotations can be used both for DiffGrams and updategrams; however, updategrams already provide a more powerful way of handling identity and GUID values.</span></span>  
  
 <span data-ttu-id="89b08-113">복합 콘텐츠 요소에 `sql:identity` 및 `sql:guid` 주석을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b08-113">The `sql:identity` and `sql:guid` annotations can be defined on a complex content element.</span></span>  
  
## <a name="sqlidentity-annotation"></a><span data-ttu-id="89b08-114">sql:identity 주석</span><span class="sxs-lookup"><span data-stu-id="89b08-114">sql:identity Annotation</span></span>  
 <span data-ttu-id="89b08-115">XSD 스키마에서 IDENTITY 형식의 데이터베이스 열에 매핑되는 임의의 노드에 `sql:identity` 주석을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b08-115">You can specify the `sql:identity` annotation in the XSD schema on any node that maps to an IDENTITY-type database column.</span></span> <span data-ttu-id="89b08-116">이 주석에 대해 지정 된 값은 updategram에 제공 된 값을 사용 하 여 열을 수정 하거나 값을 무시 하 여 ID 유형 열이 업데이트 되는 방법을 정의 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .이 경우이 열에 대해 생성 된 값이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="89b08-116">The value specified for this annotation defines how the IDENTITY-type column is updated (either by using the value provided in the updategram to modify the column or by ignoring the value, in which case a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-generated value is used for this column).</span></span>  
  
 <span data-ttu-id="89b08-117">`sql:identity` 주석에는 다음과 같은 두 가지 값을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b08-117">The `sql:identity` annotation can be assigned two values:</span></span>  
  
 <span data-ttu-id="89b08-118">ignore</span><span class="sxs-lookup"><span data-stu-id="89b08-118">ignore</span></span>  
 <span data-ttu-id="89b08-119">해당 열에 대해 updategram에 제공된 모든 값을 무시하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 통해 ID 값을 생성하도록 updategram에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="89b08-119">Directs the updategram to ignore any value that is provided in the updategram for that column and to rely on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to generate the identity value.</span></span>  
  
 <span data-ttu-id="89b08-120">useValue</span><span class="sxs-lookup"><span data-stu-id="89b08-120">useValue</span></span>  
 <span data-ttu-id="89b08-121">updategram에 제공된 값을 사용하여 IDENTITY 형식의 열을 업데이트하도록 updategram에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="89b08-121">Directs the updategram to use the value that is provided in the updategram to update the IDENTITY-type column.</span></span> <span data-ttu-id="89b08-122">updategram은 열이 ID 값인지 여부는 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="89b08-122">An updategram does not check whether the column is an identity value or not.</span></span>  
  
 <span data-ttu-id="89b08-123">updategram이 IDENTITY 형식의 열에 대한 값을 지정하는 경우 스키마에서 `sql:identity="useValue"`를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89b08-123">If the updategram specifies a value for the IDENTITY-type column, the `sql:identity="useValue"` must be specified in the schema.</span></span>  
  
## <a name="sqlguid-annotation"></a><span data-ttu-id="89b08-124">sql:guid 주석</span><span class="sxs-lookup"><span data-stu-id="89b08-124">sql:guid Annotation</span></span>  
 <span data-ttu-id="89b08-125">updategram은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 GUID 값을 생성하도록 하고 이 값을 updategram에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b08-125">An updategram can have [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generate a GUID value and then use this value in the updategram.</span></span> <span data-ttu-id="89b08-126">DiffGram의 컨텍스트에서 `sql:guid` 주석을 사용하면 SQL Server에서 생성한 GUID 값을 사용할 것인지 또는 해당 열에 대해 updategram에 제공된 값을 사용할 것인지를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b08-126">In the context of DiffGrams, you can use the `sql:guid` annotation to specify whether to use a GUID value that is generated by SQL Server or use the value that is provided in the updategram for that column.</span></span>  
  
 <span data-ttu-id="89b08-127">`sql:guid` 주석에는 다음과 같은 두 가지 값을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b08-127">The `sql:guid` annotation can be assigned two values:</span></span>  
  
 <span data-ttu-id="89b08-128">generate</span><span class="sxs-lookup"><span data-stu-id="89b08-128">generate</span></span>  
 <span data-ttu-id="89b08-129">업데이트 작업 시 해당 열에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 생성한 GUID를 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="89b08-129">Specifies that the GUID generated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] be used for that column in the update operation.</span></span>  
  
 <span data-ttu-id="89b08-130">useValue</span><span class="sxs-lookup"><span data-stu-id="89b08-130">useValue</span></span>  
 <span data-ttu-id="89b08-131">updategram에 지정된 값을 해당 열에 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="89b08-131">Specifies that the value specified in the updategram be used for the column.</span></span> <span data-ttu-id="89b08-132">기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="89b08-132">This is the default value.</span></span>  
  
  
