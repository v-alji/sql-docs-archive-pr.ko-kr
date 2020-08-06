---
title: XML 데이터 대량 로드 수행 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XML Bulk Load [SQLXML]
- bulk load [SQLXML]
- data insertions [SQLXML]
- SQLXML, bulk loading
- XSD schemas [SQLXML], XML Bulk Load
- XDR schemas [SQLXML], XML Bulk Load
- inserting data
ms.assetid: 3708b493-322e-4f3c-9b27-441d0c0ee346
author: rothja
ms.author: jroth
ms.openlocfilehash: ec540ff082b02fa43b9abd9f294752073eb68d5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728143"
---
# <a name="performing-bulk-load-of-xml-data-sqlxml-40"></a><span data-ttu-id="fab7b-102">XML 데이터 대량 로드 수행(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="fab7b-102">Performing Bulk Load of XML Data (SQLXML 4.0)</span></span>
  <span data-ttu-id="fab7b-103">XML 대량 로드는 반구조화된 XML 데이터를 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 테이블에 로드할 수 있게 해주는 독립 실행형 COM 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="fab7b-103">XML Bulk Load is a standalone COM object that allows you to load semistructured XML data into Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tables.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fab7b-104">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="fab7b-104">In This Section</span></span>  
 [<span data-ttu-id="fab7b-105">XML 대량 로드 소개 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="fab7b-105">Introduction to XML Bulk Load &#40;SQLXML 4.0&#41;</span></span>](introduction-to-xml-bulk-load-sqlxml-4-0.md)  
 <span data-ttu-id="fab7b-106">XML 대량 로드 유틸리티를 사용한 XML 데이터 대량 로드에 대한 일반적인 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fab7b-106">Provides general information about bulk loading XML data with the XML Bulk Load utility.</span></span> <span data-ttu-id="fab7b-107">XML 데이터 스트리밍, 트랜잭션 및 비트랜잭션 대량 로드 작업 등의 항목이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fab7b-107">Topics include XML data streaming and transacted vs. nontransacted bulk load operations.</span></span>  
  
 [<span data-ttu-id="fab7b-108">레코드 생성 프로세스 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="fab7b-108">Record Generation Process &#40;SQLXML 4.0&#41;</span></span>](record-generation-process-sqlxml-4-0.md)  
 <span data-ttu-id="fab7b-109">XML 대량 로드에 대해 레코드가 생성되는 프로세스 및 규칙에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fab7b-109">Describes the process and rules by which records are generated for XML Bulk Load.</span></span>  
  
 [<span data-ttu-id="fab7b-110">SQLXML 4.0 &#40;주석 해석&#41;</span><span class="sxs-lookup"><span data-stu-id="fab7b-110">Annotation Interpretation &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-sqlxml-4-0.md)  
 <span data-ttu-id="fab7b-111">XML 대량 로드에서 XSD 및 XDR 스키마의 주석을 해석하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fab7b-111">Describes how XML Bulk Load interprets annotations in XSD and XDR schemas.</span></span>  
  
 [<span data-ttu-id="fab7b-112">SQL Server XML 대량 로드 개체 모델 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="fab7b-112">SQL Server XML Bulk Load Object Model &#40;SQLXML 4.0&#41;</span></span>](sql-server-xml-bulk-load-object-model-sqlxml-4-0.md)  
 <span data-ttu-id="fab7b-113">SQLXMLBulkLoad 개체와 해당 메서드 및 속성에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="fab7b-113">Describes the SQLXMLBulkLoad object and its methods and properties.</span></span>  
  
 [<span data-ttu-id="fab7b-114">XML 대량 로드 예 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="fab7b-114">XML Bulk Load Examples &#40;SQLXML 4.0&#41;</span></span>](xml-bulk-load-examples-sqlxml-4-0.md)  
 <span data-ttu-id="fab7b-115">XML 대량 로드를 사용하는 예제 코드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fab7b-115">Provides example code that uses XML Bulk Load.</span></span>  
  
 [<span data-ttu-id="fab7b-116">SQLXML 4.0&#41;&#40;데이터 형식 및 XML 대량 로드 동작</span><span class="sxs-lookup"><span data-stu-id="fab7b-116">Data Types and XML Bulk Load Behavior &#40;SQLXML 4.0&#41;</span></span>](data-types-and-xml-bulk-load-behavior-sqlxml-4-0.md)  
 <span data-ttu-id="fab7b-117">XSD 및 XDR의 여러 유형에서의 XML 대량 로드 동작에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fab7b-117">Describes XML Bulk Load Behavior with different types in XSD and XDR.</span></span>  
  
 [<span data-ttu-id="fab7b-118">XML 대량 로드에 대 한 지침 및 제한 사항 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="fab7b-118">Guidelines and Limitations of XML Bulk Load &#40;SQLXML 4.0&#41;</span></span>](guidelines-and-limitations-of-xml-bulk-load-sqlxml-4-0.md)  
 <span data-ttu-id="fab7b-119">XML 대량 로드 작업을 수행할 때 주의할 몇 가지 문제를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fab7b-119">Lists some issues to be aware of when working with XML Bulk Load.</span></span>  
  
  
