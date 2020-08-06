---
title: BINARY BASE64 옵션 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- AUTO FOR XML mode, BINARY BASE64 option
ms.assetid: 86a7bb85-7f83-412a-b775-d2c379702fe9
author: rothja
ms.author: jroth
ms.openlocfilehash: 090d6a91ee56707a4eb1d545aa5a05bc25999fab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738037"
---
# <a name="use-the-binary-base64-option"></a><span data-ttu-id="472de-102">BINARY BASE64 옵션 사용</span><span class="sxs-lookup"><span data-stu-id="472de-102">Use the BINARY BASE64 Option</span></span>
  <span data-ttu-id="472de-103">쿼리에서 BINARY BASE64 옵션을 지정하면 이진 데이터가 base64 인코딩 형식으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="472de-103">If the BINARY BASE64 option is specified in the query, the binary data is returned in base64 encoding format.</span></span> <span data-ttu-id="472de-104">기본적으로 BINARY BASE64 옵션이 지정되지 않은 경우 AUTO 모드는 이진 데이터의 URL 인코딩을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="472de-104">By default, if the BINARY BASE64 option is not specified, AUTO mode supports URL encoding of binary data.</span></span> <span data-ttu-id="472de-105">즉, 이진 데이터 대신 쿼리가 실행된 데이터베이스의 가상 루트의 상대 URL에 대한 참조가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="472de-105">That is, instead of binary data, a reference to a relative URL to the virtual root of the database where the query was executed is returned.</span></span> <span data-ttu-id="472de-106">이 참조를 사용하면 후속 작업에서 SQLXML ISAPI dbobject 쿼리를 사용하여 실제 이진 데이터를 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="472de-106">This reference can be used to access the actual binary data in subsequent operations by using the SQLXML ISAPI dbobject query.</span></span> <span data-ttu-id="472de-107">쿼리는 이미지를 식별하기 위해 기본 키 열과 같은 정보를 충분히 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="472de-107">The query must provide enough information, such as primary key columns, to identify the image.</span></span>  
  
 <span data-ttu-id="472de-108">쿼리를 지정할 때 뷰의 이진 열에 대해 별칭이 사용되는 경우 별칭은 이진 데이터의 URL 인코딩으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="472de-108">In specifying a query, if an alias is used for the binary column of the view, the alias is returned in the URL encoding of the binary data.</span></span> <span data-ttu-id="472de-109">후속 작업에서 별칭은 아무 의미도 없으며 URL 인코딩은 이미지를 검색하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="472de-109">In subsequent operations, the alias is meaningless, and the URL encoding cannot be used to retrieve the image.</span></span> <span data-ttu-id="472de-110">따라서 FOR XML AUTO 모드를 사용하여 뷰를 쿼리할 때는 별칭을 사용하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="472de-110">Therefore, do not use aliases when querying a view using FOR XML AUTO mode.</span></span>  
  
 <span data-ttu-id="472de-111">예를 들어 SELECT 쿼리에서 모든 열에 BLOB에 대한 캐스트를 지정하면 임시 엔터티가 되어 관련 테이블 이름과 열 이름이 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="472de-111">For example, in a SELECT query, casting any column to a binary large object (BLOB) makes it a temporary entity in that it loses its associated table name and column name.</span></span> <span data-ttu-id="472de-112">이것은 XML 계층 구조에서 이 값을 둘 위치를 알 수 없으므로, 이로 인해 AUTO 모드 쿼리에서 오류가 발생하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="472de-112">This causes AUTO mode queries to generate an error, because it does not know where to put this value in the XML hierarchy.</span></span> <span data-ttu-id="472de-113">예:</span><span class="sxs-lookup"><span data-stu-id="472de-113">For example:</span></span>  
  
```  
CREATE TABLE MyTable (Col1 int PRIMARY KEY, Col2 binary)  
INSERT INTO MyTable VALUES (1, 0x7);  
```  
  
 <span data-ttu-id="472de-114">다음 쿼리에서는 BLOB(Binary Large Object)으로 캐스팅하기 때문에 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="472de-114">This query produces an error, because of the casting to a binary large object (BLOB):</span></span>  
  
```  
SELECT Col1,  
CAST(Col2 as image) as Col2  
FROM MyTable  
FOR XML AUTO;  
```  
  
 <span data-ttu-id="472de-115">이 솔루션은 FOR XML 절에 BINARY BASE64 옵션을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="472de-115">The solution is to add the BINARY BASE64 option to the FOR XML clause.</span></span> <span data-ttu-id="472de-116">캐스트 지정을 없애면 예상대로 쿼리 결과가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="472de-116">If you remove the casting, the query produces the results as expected:</span></span>  
  
```  
SELECT Col1,  
CAST(Col2 as image) as Col2  
FROM MyTable  
FOR XML AUTO, BINARY BASE64;  
```  
  
 <span data-ttu-id="472de-117">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="472de-117">This is the result:</span></span>  
  
```  
<MyTable Col1="1" Col2="Bw==" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="472de-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="472de-118">See Also</span></span>  
 [<span data-ttu-id="472de-119">FOR XML에서 AUTO 모드 사용</span><span class="sxs-lookup"><span data-stu-id="472de-119">Use AUTO Mode with FOR XML</span></span>](use-auto-mode-with-for-xml.md)  
  
  
