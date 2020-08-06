---
title: FOR XML에서 PATH 모드 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode
- characters [SQL Server], XML
- aliases [SQL Server], XML
- FOR XML clause, PATH mode
- FOR XML PATH mode
- column names [SQL Server]
- XPath queries [SQL Server]
ms.assetid: a685a9ad-3d28-4596-aa72-119202df3976
author: rothja
ms.author: jroth
ms.openlocfilehash: ce0cf811f1e610d14a94993b54c51ea079f613e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651555"
---
# <a name="use-path-mode-with-for-xml"></a><span data-ttu-id="10537-102">FOR XML에서 PATH 모드 사용</span><span class="sxs-lookup"><span data-stu-id="10537-102">Use PATH Mode with FOR XML</span></span>
  <span data-ttu-id="10537-103">[FOR XML을 사용하는 XML 생성](for-xml-sql-server.md)항목에 설명된 대로 PATH 모드를 사용하면 요소와 특성을 간단하게 혼합할 수 있고</span><span class="sxs-lookup"><span data-stu-id="10537-103">As described in [Constructing XML Using FOR XML](for-xml-sql-server.md), the PATH mode provides a simpler way to mix elements and attributes.</span></span> <span data-ttu-id="10537-104">추가 중첩을 간단하게 도입하여 복잡한 속성을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10537-104">PATH mode is also a simpler way to introduce additional nesting for representing complex properties.</span></span> <span data-ttu-id="10537-105">FOR XML EXPLICIT 모드 쿼리를 사용하여 행 집합에서 해당 XML을 생성할 수 있지만 PATH 모드를 사용할 경우 복잡해지기 쉬운 EXPLICIT 모드 쿼리의 대안을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10537-105">You can use FOR XML EXPLICIT mode queries to construct such XML from a rowset, but the PATH mode provides a simpler alternative to the potentially cumbersome EXPLICIT mode queries.</span></span> <span data-ttu-id="10537-106">**XML** 유형 인스턴스를 반환하는 중첩 FOR XML 쿼리 및 TYPE 지시어 작성 기능과 함께 PATH 모드를 사용하면 보다 간편하게 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10537-106">PATH mode, together with the ability to write nested FOR XML queries and the TYPE directive to return **xml** type instances, allows you to write queries with less complexity.</span></span>  
  
 <span data-ttu-id="10537-107">PATH 모드에서는 열 이름이나 열 별칭이 XPath 식으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="10537-107">In PATH mode, column names or column aliases are treated as XPath expressions.</span></span> <span data-ttu-id="10537-108">이러한 식은 값이 XML에 매핑되는 방법을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="10537-108">These expressions indicate how the values are being mapped to XML.</span></span> <span data-ttu-id="10537-109">각 XPath 식은 특성, 요소와 스칼라 값 및 행 요소에 대해 생성되는 노드의 이름과 계층 등의 항목 유형을 제공하는 상대 XPath입니다.</span><span class="sxs-lookup"><span data-stu-id="10537-109">Each XPath expression is a relative XPath that provides the item type., such as the attribute, element, and scalar value, and the name and hierarchy of the node that will be generated relative to the row element.</span></span>  
  
 <span data-ttu-id="10537-110">이 섹션에서는 다양한 조건에서 행 집합의 열을 매핑하는 방법에 대해 설명하고 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="10537-110">This section describes mapping columns in a rowset under various conditions, and provides examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="10537-111">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="10537-111">In This Section</span></span>  
  
-   [<span data-ttu-id="10537-112">이름이 없는 열</span><span class="sxs-lookup"><span data-stu-id="10537-112">Columns without a Name</span></span>](columns-without-a-name.md)  
  
-   [<span data-ttu-id="10537-113">이름이 있는 열</span><span class="sxs-lookup"><span data-stu-id="10537-113">Columns with a Name</span></span>](columns-with-a-name.md)  
  
-   [<span data-ttu-id="10537-114">이름이 와일드카드 문자로 지정된 열</span><span class="sxs-lookup"><span data-stu-id="10537-114">Columns with a Name Specified as a Wildcard Character</span></span>](columns-with-a-name-specified-as-a-wildcard-character.md)  
  
-   [<span data-ttu-id="10537-115">이름이 XPath 노드 테스트인 열</span><span class="sxs-lookup"><span data-stu-id="10537-115">Columns with the Name of an XPath Node Test</span></span>](columns-with-the-name-of-an-xpath-node-test.md)  
  
-   [<span data-ttu-id="10537-116">경로가 data&#40;&#41;로 지정된 열 이름</span><span class="sxs-lookup"><span data-stu-id="10537-116">Column Names with the Path Specified as data&#40;&#41;</span></span>](column-names-with-the-path-specified-as-data.md)  
  
-   [<span data-ttu-id="10537-117">기본적으로 Null 값을 포함하는 열</span><span class="sxs-lookup"><span data-stu-id="10537-117">Columns that Contain a Null Value By Default</span></span>](columns-that-contain-a-null-value-by-default.md)  
  
-   [<span data-ttu-id="10537-118">PATH 모드에서의 네임스페이스 지원</span><span class="sxs-lookup"><span data-stu-id="10537-118">Namespace Support in PATH Mode</span></span>](namespace-support-in-path-mode.md)  
  
-   [<span data-ttu-id="10537-119">예제: PATH 모드 사용</span><span class="sxs-lookup"><span data-stu-id="10537-119">Examples: Using PATH Mode</span></span>](examples-using-path-mode.md)  
  
## <a name="see-also"></a><span data-ttu-id="10537-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="10537-120">See Also</span></span>  
 <span data-ttu-id="10537-121">[WITH XMLNAMESPACES를 사용하여 쿼리에 네임스페이스 추가](add-namespaces-to-queries-with-with-xmlnamespaces.md) </span><span class="sxs-lookup"><span data-stu-id="10537-121">[Add Namespaces to Queries with WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md) </span></span>  
 <span data-ttu-id="10537-122">[SELECT&#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="10537-122">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="10537-123">FOR XML&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="10537-123">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
