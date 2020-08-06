---
title: Server 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Server element
ms.assetid: 9fe0bfb4-3aa6-4eb2-a83e-c0d0e7d4e9f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: ab67e0303c2b629c3774886441474f5ef5b10a43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653090"
---
# <a name="server-element-dta"></a><span data-ttu-id="47e79-102">Server 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="47e79-102">Server Element (DTA)</span></span>
  <span data-ttu-id="47e79-103">튜닝할 데이터베이스가 상주하는 서버에 대한 식별 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="47e79-103">Contains the identifying information for the server on which the databases reside that you want to tune.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47e79-104">구문</span><span class="sxs-lookup"><span data-stu-id="47e79-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
    <Server>  
    ...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="47e79-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="47e79-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="47e79-106">특성</span><span class="sxs-lookup"><span data-stu-id="47e79-106">Characteristic</span></span>|<span data-ttu-id="47e79-107">Description</span><span class="sxs-lookup"><span data-stu-id="47e79-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="47e79-108">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="47e79-108">**Data type and length**</span></span>|<span data-ttu-id="47e79-109">없음</span><span class="sxs-lookup"><span data-stu-id="47e79-109">None.</span></span>|  
|<span data-ttu-id="47e79-110">**기본값**</span><span class="sxs-lookup"><span data-stu-id="47e79-110">**Default value**</span></span>|<span data-ttu-id="47e79-111">없음</span><span class="sxs-lookup"><span data-stu-id="47e79-111">None.</span></span>|  
|<span data-ttu-id="47e79-112">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="47e79-112">**Occurrence**</span></span>|<span data-ttu-id="47e79-113">각 `DTAInput` 요소 당 한 번씩만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="47e79-113">Required once per `DTAInput` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="47e79-114">요소 관계</span><span class="sxs-lookup"><span data-stu-id="47e79-114">Element Relationships</span></span>  
  
|<span data-ttu-id="47e79-115">관계</span><span class="sxs-lookup"><span data-stu-id="47e79-115">Relationship</span></span>|<span data-ttu-id="47e79-116">요소</span><span class="sxs-lookup"><span data-stu-id="47e79-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="47e79-117">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="47e79-117">**Parent element**</span></span>|[<span data-ttu-id="47e79-118">DTAInput 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="47e79-118">DTAInput Element &#40;DTA&#41;</span></span>](dtainput-element-dta.md)|  
|<span data-ttu-id="47e79-119">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="47e79-119">**Child elements**</span></span>|[<span data-ttu-id="47e79-120">Server의 Name 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="47e79-120">Name Element for Server &#40;DTA&#41;</span></span>](name-element-for-server-dta.md)<br /><br /> [<span data-ttu-id="47e79-121">Server의 Database 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="47e79-121">Database Element for Server &#40;DTA&#41;</span></span>](database-element-for-server-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="47e79-122">설명</span><span class="sxs-lookup"><span data-stu-id="47e79-122">Remarks</span></span>  
 <span data-ttu-id="47e79-123">`Server`요소에 대해 요소를 하나만 지정할 수 있습니다 `DTAInput` .</span><span class="sxs-lookup"><span data-stu-id="47e79-123">You can specify only one `Server` element for the `DTAInput` element.</span></span> <span data-ttu-id="47e79-124">이 요소는 DTA XML 스키마에서 **ServerDetailsTypecomplexType** 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="47e79-124">This element is of the **ServerDetailsTypecomplexType** name in the DTA XML schema.</span></span> <span data-ttu-id="47e79-125">이 `Server` 요소와 `Configuration` 요소의 자식 요소를 혼동하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="47e79-125">Do not confuse this `Server` element with the one that is the child of the `Configuration` element.</span></span> <span data-ttu-id="47e79-126">자세한 내용은 [Configuration의 Server 요소&#40;DTA&#41;](server-element-for-configuration-dta.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="47e79-126">For more information, see [Server Element for Configuration &#40;DTA&#41;](server-element-for-configuration-dta.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="47e79-127">예제</span><span class="sxs-lookup"><span data-stu-id="47e79-127">Example</span></span>  
 <span data-ttu-id="47e79-128">다음 예에서는 SERVER001에 있는 **AdventureWorks** 데이터베이스의 **Sales.SalesPerson** 테이블을 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="47e79-128">The following example shows how to specify the **Sales.SalesPerson** table in the **AdventureWorks** database on SERVER001:</span></span>  
  
```xml  
<Server>  
  <Name>SERVER001</Name>  
  <Database>  
    <Name>AdventureWorks</Name>  
    <Schema>  
      <Name>Sales</Name>  
      <Table>  
        <Name>SalesPerson</Name>  
      </Table>  
    </Schema>  
  </Database>  
</Server  
```  
  
## <a name="see-also"></a><span data-ttu-id="47e79-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47e79-129">See Also</span></span>  
 [<span data-ttu-id="47e79-130">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="47e79-130">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
