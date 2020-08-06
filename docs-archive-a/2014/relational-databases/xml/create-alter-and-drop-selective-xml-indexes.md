---
title: 선택적 XML 인덱스 만들기, 변경 및 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: c398f396-f630-4a2d-a264-f243c5346de1
author: rothja
ms.author: jroth
ms.openlocfilehash: bf4123a46cc13359c936e6f9cfc0db3dcfdaa175
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730248"
---
# <a name="create-alter-and-drop-selective-xml-indexes"></a><span data-ttu-id="f34ff-102">선택적 XML 인덱스 만들기, 변경 및 삭제</span><span class="sxs-lookup"><span data-stu-id="f34ff-102">Create, Alter, and Drop Selective XML Indexes</span></span>
  <span data-ttu-id="f34ff-103">새 선택적 XML 인덱스를 만들거나 기존 선택적 XML 인덱스를 변경 또는 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f34ff-103">Describes how to create a new selective XML index, or alter or drop an existing selective XML index.</span></span>  
  
 <span data-ttu-id="f34ff-104">선택적 XML 인덱스에 대한 자세한 내용은 [SXI&#40;선택적 XML 인덱스&#41;](selective-xml-indexes-sxi.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f34ff-104">For more information about selective XML indexes, see [Selective XML Indexes &#40;SXI&#41;](selective-xml-indexes-sxi.md).</span></span>  
  
##  <a name="creating-a-selective-xml-index"></a><a name="create"></a> <span data-ttu-id="f34ff-105">선택적 XML 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="f34ff-105">Creating a Selective XML Index</span></span>  
  
### <a name="how-to-create-a-selective-xml-index"></a><span data-ttu-id="f34ff-106">방법: 선택적 XML 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="f34ff-106">How to: Create a Selective XML Index</span></span>  
 <span data-ttu-id="f34ff-107">**Transact-SQL을 사용하여 선택적 XML 인덱스 만들기**</span><span class="sxs-lookup"><span data-stu-id="f34ff-107">**Create a Selective XML Index by Using Transact-SQL**</span></span>  
 <span data-ttu-id="f34ff-108">CREATE SELECTIVE XML INDEX 문을 호출하여 선택적 XML 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f34ff-108">Create a selective XML index by calling the CREATE SELECTIVE XML INDEX statement.</span></span> <span data-ttu-id="f34ff-109">자세한 내용은 [CREATE SELECTIVE XML INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f34ff-109">For more information, see [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql).</span></span>  
  
 <span data-ttu-id="f34ff-110">**예제**</span><span class="sxs-lookup"><span data-stu-id="f34ff-110">**Example**</span></span>  
  
 <span data-ttu-id="f34ff-111">다음 예에서는 선택적 XML 인덱스를 만드는 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f34ff-111">The following example shows the syntax for creating a selective XML index.</span></span> <span data-ttu-id="f34ff-112">또한 이 예에서는 선택적 최적화 힌트를 사용하여 인덱싱할 경로를 설명하는 구문의 여러 변형도 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f34ff-112">It also shows several variations of the syntax for describing the paths to be indexed, with optional optimization hints.</span></span>  
  
```sql  
CREATE SELECTIVE XML INDEX sxi_index  
ON Tbl(xmlcol)  
  
FOR(  
    pathab   = '/a/b' as XQUERY 'node()'  
    pathabc  = '/a/b/c' as XQUERY 'xs:double',   
    pathdtext = '/a/b/d/text()' as XQUERY 'xs:string' MAXLENGTH(200) SINGLETON  
    pathabe = '/a/b/e' as SQL NVARCHAR(100)  
)  
```  
  
  
  
##  <a name="altering-a-selective-xml-index"></a><a name="alter"></a> <span data-ttu-id="f34ff-113">선택적 XML 인덱스 변경</span><span class="sxs-lookup"><span data-stu-id="f34ff-113">Altering a Selective XML Index</span></span>  
  
### <a name="how-to-alter-a-selective-xml-index"></a><span data-ttu-id="f34ff-114">방법: 선택적 XML 인덱스 변경</span><span class="sxs-lookup"><span data-stu-id="f34ff-114">How to: Alter a Selective XML Index</span></span>  
 <span data-ttu-id="f34ff-115">**Transact-SQL을 사용하여 선택적 XML 인덱스 변경**</span><span class="sxs-lookup"><span data-stu-id="f34ff-115">**Alter a Selective XML Index by Using Transact-SQL**</span></span>  
 <span data-ttu-id="f34ff-116">ALTER INDEX 문을 호출하여 기존 선택적 XML 인덱스를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f34ff-116">Alter an existing selective XML index by calling the ALTER INDEX statement.</span></span> <span data-ttu-id="f34ff-117">자세한 내용은 [ALTER INDEX&#40;선택적 XML 인덱스&#41;](../indexes/indexes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f34ff-117">For more information, see [ALTER INDEX &#40;Selective XML Indexes&#41;](../indexes/indexes.md).</span></span>  
  
 <span data-ttu-id="f34ff-118">**예제**</span><span class="sxs-lookup"><span data-stu-id="f34ff-118">**Example**</span></span>  
  
 <span data-ttu-id="f34ff-119">다음 예에서는 ALTER INDEX 문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f34ff-119">The following example shows an ALTER INDEX statement.</span></span> <span data-ttu-id="f34ff-120">이 문은 인덱스의 XQuery 부분에 `'/a/b/m'` 경로를 추가하고 [CREATE SELECTIVE XML INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql) 항목의 예에서 만든 인덱스의 SQL 부분에서 `'/a/b/e'` 경로를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="f34ff-120">This statement adds the path `'/a/b/m'` to the XQuery part of the index and deletes the path `'/a/b/e'` from the SQL part of the index created in the example in the topic [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql).</span></span> <span data-ttu-id="f34ff-121">삭제할 경로는 해당 경로를 만들 때 지정한 경로 이름으로 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="f34ff-121">The path to delete is identified by the name that was given to it when it was created.</span></span>  
  
```sql  
ALTER INDEX sxi_index  
ON Tbl  
FOR   
(  
    ADD pathm = '/a/b/m' as XQUERY 'node()' ,  
    REMOVE pathabe  
)  
```  
  
  
  
##  <a name="dropping-a-selective-xml-index"></a><a name="drop"></a> <span data-ttu-id="f34ff-122">선택적 XML 인덱스 삭제</span><span class="sxs-lookup"><span data-stu-id="f34ff-122">Dropping a Selective XML Index</span></span>  
  
### <a name="how-to-drop-a-selective-xml-index"></a><span data-ttu-id="f34ff-123">방법: 선택적 XML 인덱스 삭제</span><span class="sxs-lookup"><span data-stu-id="f34ff-123">How to: Drop a Selective XML Index</span></span>  
 <span data-ttu-id="f34ff-124">**Transact-SQL을 사용하여 선택적 XML 인덱스 삭제**</span><span class="sxs-lookup"><span data-stu-id="f34ff-124">**Drop a Selective XML Index by Using Transact-SQL**</span></span>  
 <span data-ttu-id="f34ff-125">DROP INDEX 문을 호출하여 선택적 XML 인덱스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="f34ff-125">Drop a selective XML index by calling the DROP INDEX statement.</span></span> <span data-ttu-id="f34ff-126">자세한 내용은 [DROP INDEX&#40;선택적 XML 인덱스&#41;](/sql/t-sql/statements/drop-index-selective-xml-indexes)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f34ff-126">For more information, see [DROP INDEX &#40;Selective XML Indexes&#41;](/sql/t-sql/statements/drop-index-selective-xml-indexes).</span></span>  
  
 <span data-ttu-id="f34ff-127">**예제**</span><span class="sxs-lookup"><span data-stu-id="f34ff-127">**Example**</span></span>  
  
 <span data-ttu-id="f34ff-128">다음 예에서는 DROP INDEX 문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f34ff-128">The following example shows a DROP INDEX statement.</span></span>  
  
```sql  
DROP INDEX sxi_index ON tbl  
```  
  
 
  
  
