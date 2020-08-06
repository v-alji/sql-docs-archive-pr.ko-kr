---
title: 보조 선택적 XML 인덱스 만들기, 변경 및 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: 45128105-833b-40a9-9cc9-1ae03ac0b52b
author: rothja
ms.author: jroth
ms.openlocfilehash: e6f7296896b6421db5329565403cdcbaf10b26a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730251"
---
# <a name="create-alter-and-drop-secondary-selective-xml-indexes"></a><span data-ttu-id="54873-102">보조 선택적 XML 인덱스 만들기, 변경 및 삭제</span><span class="sxs-lookup"><span data-stu-id="54873-102">Create, Alter, and Drop Secondary Selective XML Indexes</span></span>
  <span data-ttu-id="54873-103">새 보조 선택적 XML 인덱스를 만들거나 기존 보조 선택적 XML 인덱스를 변경 또는 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="54873-103">Describes how to create a new secondary selective XML index, or alter or drop an existing secondary selective XML index.</span></span>  
  
##  <a name="creating-a-secondary-selective-xml-index"></a><a name="create"></a> <span data-ttu-id="54873-104">보조 선택적 XML 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="54873-104">Creating a Secondary Selective XML Index</span></span>  
  
### <a name="how-to-create-a-secondary-selective-xml-index"></a><span data-ttu-id="54873-105">방법: 보조 선택적 XML 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="54873-105">How to: Create a Secondary Selective XML Index</span></span>  
 <span data-ttu-id="54873-106">**Transact-SQL을 사용하여 보조 선택적 XML 인덱스 만들기**</span><span class="sxs-lookup"><span data-stu-id="54873-106">**Create a Secondary Selective XML Index by Using Transact-SQL**</span></span>  
 <span data-ttu-id="54873-107">CREATE XML INDEX 문을 호출하여 보조 선택적 XML 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="54873-107">Create a secondary selective XML index by calling the CREATE XML INDEX statement.</span></span> <span data-ttu-id="54873-108">자세한 내용은 [CREATE XML INDEX &#40;선택적 XML 인덱스&#41;] (~/t-sql/statements/create-xml-index-selective-xml-indexes.를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="54873-108">For more information, see [CREATE XML INDEX &#40;Selective XML Indexes&#41;](~/t-sql/statements/create-xml-index-selective-xml-indexes.</span></span>  
  
 <span data-ttu-id="54873-109">**예제**</span><span class="sxs-lookup"><span data-stu-id="54873-109">**Example**</span></span>  
  
 <span data-ttu-id="54873-110">다음 예에서는 `'pathabc'`경로에서 보조 선택적 XML 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="54873-110">The following example creates a secondary selective XML index on the path `'pathabc'`.</span></span> <span data-ttu-id="54873-111">인덱싱할 경로는 CREATE SELECTIVE XML INDEX 문을 사용하여 해당 경로를 만들 때 지정한 경로 이름으로 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="54873-111">The path to index is identified by the name that was given to it when it was created with the CREATE SELECTIVE XML INDEX statement.</span></span> <span data-ttu-id="54873-112">자세한 내용은 [CREATE SELECTIVE XML INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54873-112">For more information, see [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql).</span></span>  
  
```sql  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR  
(  
    pathabc  
)  
```  
  
  
##  <a name="altering-a-secondary-selective-xml-index"></a><a name="alter"></a> <span data-ttu-id="54873-113">보조 선택적 XML 인덱스 변경</span><span class="sxs-lookup"><span data-stu-id="54873-113">Altering a Secondary Selective XML Index</span></span>  
 <span data-ttu-id="54873-114">보조 선택적 XML 인덱스에 대해서는 ALTER 문이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="54873-114">The ALTER statement is not supported for secondary selective XML indexes.</span></span> <span data-ttu-id="54873-115">보조 선택적 XML 인덱스를 변경하려면 기존 인덱스를 삭제하고 다시 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="54873-115">To change a secondary selective XML index, drop the existing index and recreate it.</span></span>  
  
### <a name="how-to-alter-a-secondary-selective-xml-index"></a><span data-ttu-id="54873-116">방법: 보조 선택적 XML 인덱스 변경</span><span class="sxs-lookup"><span data-stu-id="54873-116">How to: Alter a Secondary Selective XML Index</span></span>  
 <span data-ttu-id="54873-117">**Transact-SQL을 사용하여 보조 선택적 XML 인덱스 변경**</span><span class="sxs-lookup"><span data-stu-id="54873-117">**Alter a Secondary Selective XML Index by Using Transact-SQL**</span></span>  
 1.  <span data-ttu-id="54873-118">DROP INDEX 문을 호출하여 기존의 보조 선택적 XML 인덱스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="54873-118">Drop the existing secondary selective XML index by calling the DROP INDEX statement.</span></span> <span data-ttu-id="54873-119">자세한 내용은 [DROP INDEX&#40;선택적 XML 인덱스&#41;](../indexes/indexes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54873-119">For more information, see [DROP INDEX &#40;Selective XML Indexes&#41;](../indexes/indexes.md).</span></span>  
  
2.  <span data-ttu-id="54873-120">CREATE XML INDEX 문을 호출하여 원하는 옵션으로 인덱스를 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="54873-120">Recreate the index with the desired options by calling the CREATE XML INDEX statement.</span></span> <span data-ttu-id="54873-121">자세한 내용은 [CREATE XML INDEX &#40;선택적 XML 인덱스&#41;] (~/t-sql/statements/create-xml-index-selective-xml-indexes.를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="54873-121">For more information, see [CREATE XML INDEX &#40;Selective XML Indexes&#41;](~/t-sql/statements/create-xml-index-selective-xml-indexes.</span></span>  
  
 <span data-ttu-id="54873-122">**예제**</span><span class="sxs-lookup"><span data-stu-id="54873-122">**Example**</span></span>  
  
 <span data-ttu-id="54873-123">다음 예에서는 보조 선택적 XML 인덱스를 삭제하고 다시 만들어 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="54873-123">The following example changes a secondary selective XML index by dropping it and recreating it.</span></span>  
  
```sql  
DROP INDEX filt_sxi_index_c  
  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR  
(  
    pathabc  
)  
```  
  
  
##  <a name="dropping-a-secondary-selective-xml-index"></a><a name="drop"></a> <span data-ttu-id="54873-124">보조 선택적 XML 인덱스 삭제</span><span class="sxs-lookup"><span data-stu-id="54873-124">Dropping a Secondary Selective XML Index</span></span>  
  
### <a name="how-to-drop-a-secondary-selective-xml-index"></a><span data-ttu-id="54873-125">방법: 보조 선택적 XML 인덱스 삭제</span><span class="sxs-lookup"><span data-stu-id="54873-125">How to: Drop a Secondary Selective XML Index</span></span>  
 <span data-ttu-id="54873-126">**Transact-SQL을 사용하여 보조 선택적 XML 인덱스 삭제**</span><span class="sxs-lookup"><span data-stu-id="54873-126">**Drop a Secondary Selective XML Index by Using Transact-SQL**</span></span>  
 <span data-ttu-id="54873-127">DROP INDEX 문을 호출하여 보조 선택적 XML 인덱스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="54873-127">Drop a secondary selective XML index by calling the DROP INDEX statement.</span></span> <span data-ttu-id="54873-128">자세한 내용은 [DROP INDEX&#40;선택적 XML 인덱스&#41;](../indexes/indexes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54873-128">For more information, see [DROP INDEX &#40;Selective XML Indexes&#41;](../indexes/indexes.md).</span></span>  
  
 <span data-ttu-id="54873-129">**예제**</span><span class="sxs-lookup"><span data-stu-id="54873-129">**Example**</span></span>  
  
 <span data-ttu-id="54873-130">다음 예에서는 DROP INDEX 문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="54873-130">The following example shows a DROP INDEX statement.</span></span>  
  
```sql  
DROP INDEX ssxi_index  
ON tbl  
```  
  
  
## <a name="see-also"></a><span data-ttu-id="54873-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="54873-131">See Also</span></span>  
 [<span data-ttu-id="54873-132">SXI&#40;선택적 XML 인덱스&#41;</span><span class="sxs-lookup"><span data-stu-id="54873-132">Selective XML Indexes &#40;SXI&#41;</span></span>](selective-xml-indexes-sxi.md)  
  
  
