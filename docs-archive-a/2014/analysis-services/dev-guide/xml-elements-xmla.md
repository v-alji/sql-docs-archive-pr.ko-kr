---
title: XML 요소 (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XMLA, elements
- XML for Analysis, elements
- elements [XML for Analysis]
ms.assetid: 40ab2360-efb6-4ba6-bf23-e84964e51008
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5c1e5b046bfa57302baefc43a4da989be9c70e08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659726"
---
# <a name="xml-elements-xmla"></a><span data-ttu-id="2f827-102">XML 요소(XMLA)</span><span class="sxs-lookup"><span data-stu-id="2f827-102">XML Elements (XMLA)</span></span>
  <span data-ttu-id="2f827-103">다음 항목에서는에서 지 원하는 XMLA (다양 한 XML for Analysis) 요소 범주에 대해 설명 합니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2f827-103">The following topics describe the various XML for Analysis (XMLA) element categories supported by [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2f827-104">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="2f827-104">In This Section</span></span>  
  
|<span data-ttu-id="2f827-105">속성</span><span class="sxs-lookup"><span data-stu-id="2f827-105">Property</span></span>|<span data-ttu-id="2f827-106">Description</span><span class="sxs-lookup"><span data-stu-id="2f827-106">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="2f827-107">XMLA &#40;헤더&#41;</span><span class="sxs-lookup"><span data-stu-id="2f827-107">Headers &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/xml-elements-headers)|<span data-ttu-id="2f827-108">프로토콜 수준의 기능을 관리하기 위해 애플리케이션 또는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 의해 SOAP Envelope의 SOAP 헤더에서 전송되는 요소를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2f827-108">Describes those elements sent in the SOAP header of a SOAP envelope, either by an application or by an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, to manage protocol-level features.</span></span>|  
|[<span data-ttu-id="2f827-109">XMLA &#40;메서드&#41;</span><span class="sxs-lookup"><span data-stu-id="2f827-109">Methods &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods)|<span data-ttu-id="2f827-110">데이터 또는 메타데이터를 검색하거나 인스턴스에 대한 동작을 수행하기 위해 애플리케이션에 의해 SOAP Envelope에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스로 전송되는 최상위 요소를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2f827-110">Describes the topmost elements sent by an application in a SOAP envelope to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance to retrieve data or metadata, or to perform actions on the instance.</span></span>|  
|[<span data-ttu-id="2f827-111">XMLA를 &#40;명령&#41;</span><span class="sxs-lookup"><span data-stu-id="2f827-111">Commands &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/xml-elements-commands)|<span data-ttu-id="2f827-112">특정 동작을 수행하기 위해 XMLA 메서드에서 전송되는 요소를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2f827-112">Describes the elements sent within an XMLA method to perform a specific action.</span></span>|  
|[<span data-ttu-id="2f827-113">XMLA&#41;개체 &#40;</span><span class="sxs-lookup"><span data-stu-id="2f827-113">Objects &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)|<span data-ttu-id="2f827-114">애플리케이션이 XMLA 메서드에 대한 응답으로 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스의 SOAP Envelope에서 받은 최상위 요소를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2f827-114">Describes the topmost elements received by an application in a SOAP envelope from an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance in response to an XMLA method.</span></span>|  
|[<span data-ttu-id="2f827-115">XMLA&#41;속성 &#40;</span><span class="sxs-lookup"><span data-stu-id="2f827-115">Properties &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/xml-elements-properties)|<span data-ttu-id="2f827-116">XMLA 헤더, 메서드, 개체 또는 명령에 대한 자식 요소를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2f827-116">Describes the child elements for XMLA headers, methods, objects, or commands.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2f827-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2f827-117">See Also</span></span>  
 <span data-ttu-id="2f827-118">[XML 데이터 형식 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-data-types/xml-data-types-xmla) </span><span class="sxs-lookup"><span data-stu-id="2f827-118">[XML Data Types &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-data-types/xml-data-types-xmla) </span></span>  
 [<span data-ttu-id="2f827-119">ASSL&#40;Analysis Services Scripting Language&#41;을 사용하여 개발</span><span class="sxs-lookup"><span data-stu-id="2f827-119">Developing with Analysis Services Scripting Language &#40;ASSL&#41;</span></span>](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
  
  
