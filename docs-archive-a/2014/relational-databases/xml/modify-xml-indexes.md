---
title: XML 인덱스 수정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XML indexes [SQL Server], modifying
- modifying indexes
ms.assetid: 24d50fe1-c6ec-49e6-91a3-9791851ba53d
author: rothja
ms.author: jroth
ms.openlocfilehash: c5c67470fc9aaaeefe49e5ccb1a8602e082c4054
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729155"
---
# <a name="modify-xml-indexes"></a><span data-ttu-id="05c00-102">XML 인덱스 수정</span><span class="sxs-lookup"><span data-stu-id="05c00-102">Modify XML Indexes</span></span>
  <span data-ttu-id="05c00-103">[ALTER INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL 문은 기존의 XML 인덱스와 비 XML 인덱스를 수정하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="05c00-103">The [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL statement can be used to modify existing XML and non-XML indexes.</span></span> <span data-ttu-id="05c00-104">그러나 모든 ALTER INDEX 옵션을 XML 인덱스에 사용할 수 있는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="05c00-104">However, not all the ALTER INDEX options are available to XML indexes.</span></span> <span data-ttu-id="05c00-105">XML 인덱스를 수정할 때 다음 옵션은 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05c00-105">The following options are not valid when modifying XML indexes:</span></span>  
  
-   <span data-ttu-id="05c00-106">다시 작성 및 설정 옵션인 IGNORE_DUP_KEY는 XML 인덱스에 대해 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05c00-106">The rebuild and set option IGNORE_DUP_KEY is not valid for XML indexes.</span></span> <span data-ttu-id="05c00-107">다시 작성 옵션 ONLINE은 보조 XML 인덱스에 대해 OFF로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05c00-107">The rebuild option ONLINE must be set to OFF for secondary XML indexes.</span></span> <span data-ttu-id="05c00-108">DROP_EXISTING 옵션은 ALTER INDEX 문에서 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05c00-108">The option DROP_EXISTING is not permitted in the ALTER INDEX statement.</span></span>  
  
-   <span data-ttu-id="05c00-109">사용자 테이블에서 PRIMARY KEY 제약 조건을 수정하면 자동으로 XML 인덱스에 전파되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05c00-109">The modifications of the primary key constraint in the user table are not automatically propagated to XML indexes.</span></span> <span data-ttu-id="05c00-110">사용자는 먼저 XML 인덱스를 삭제한 다음 다시 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05c00-110">The user must drop the XML indexes first and then re-create them.</span></span>  
  
-   <span data-ttu-id="05c00-111">ALTER INDEX ALL이 지정되면 비-XML 인덱스 및 XML 인덱스 모두에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="05c00-111">If ALTER INDEX ALL is specified, it applies to both non-XML and XML indexes.</span></span> <span data-ttu-id="05c00-112">인덱싱 옵션은 두 가지 인덱스 유형에 모두 유효하지 않도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05c00-112">Indexing options may be specified that are not valid for both types of indexes.</span></span> <span data-ttu-id="05c00-113">이 경우 전체 문이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="05c00-113">In this case, the whole statement fails.</span></span>  
  
## <a name="example-modifying-an-xml-index"></a><span data-ttu-id="05c00-114">예제: XML 인덱스 수정</span><span class="sxs-lookup"><span data-stu-id="05c00-114">Example: Modifying an XML Index</span></span>  
 <span data-ttu-id="05c00-115">다음 예에서는 XML 인덱스가 생성되고 `ALLOW_ROW_LOCKS` 옵션을 `OFF`로 설정하여 수정됩니다.</span><span class="sxs-lookup"><span data-stu-id="05c00-115">In the following example, an XML index is created and then modified by setting the option `ALLOW_ROW_LOCKS` to `OFF`.</span></span> <span data-ttu-id="05c00-116">`ALLOW_ROW_LOCKS` 가 `OFF`일 때는 행이 잠기지 않고 페이지 수준 및 테이블 수준의 잠금을 사용하여 지정된 인덱스에 대한 액세스가 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="05c00-116">When `ALLOW_ROW_LOCKS` is `OFF`, rows are not locked and access to the specified indexes is obtained by using page-and table-level locks.</span></span>  
  
```  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML)  
GO  
-- Create primary XML index.   
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlCol)  
GO  
-- Note the type 3 is index on XML type.  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T')  
AND name='PIdx_T_XmlCol'  
  
-- Modify and set an index option.  
ALTER INDEX PIdx_T_XmlCol on T   
SET (ALLOW_ROW_LOCKS = OFF)  
```  
  
## <a name="example-disabling-and-enabling-an-xml-index"></a><span data-ttu-id="05c00-117">예제: XML 인덱스 사용 및 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="05c00-117">Example: Disabling and Enabling an XML Index</span></span>  
 <span data-ttu-id="05c00-118">기본적으로 XML 인덱스는 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="05c00-118">By default, an XML index is enabled.</span></span> <span data-ttu-id="05c00-119">XML 인덱스가 비활성화되어 있는 경우 XML 열에 대해 실행되는 쿼리에서는 해당 XML 인덱스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="05c00-119">If an XML index is disabled, the queries running against the XML column do not use the XML index.</span></span> <span data-ttu-id="05c00-120">XML 인덱스를 활성화하려면 `ALTER INDEX` 옵션과 함께 `REBUILD` 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="05c00-120">To enable an XML index, use `ALTER INDEX` with the `REBUILD` option.</span></span>  
  
```  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML)  
GO  
CREATE PRIMARY XML INDEX PIdx_T_XmlCol ON T(XmlCol)  
GO  
ALTER INDEX PIdx_T_XmlCol on T DISABLE  
Go  
-- Verify index is disabled.  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T')  
AND name='PIdx_T_XmlCol'  
-- Rebuild the index.  
ALTER INDEX PIdx_T_XmlCol on T REBUILD  
Go  
```  
  
## <a name="see-also"></a><span data-ttu-id="05c00-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="05c00-121">See Also</span></span>  
 [<span data-ttu-id="05c00-122">XML 인덱스&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="05c00-122">XML Indexes &#40;SQL Server&#41;</span></span>](xml-indexes-sql-server.md)  
  
  
