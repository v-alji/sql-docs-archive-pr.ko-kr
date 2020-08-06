---
title: XML 데이터 검색 및 쿼리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XML data [SQL Server], retrieving
- XML instance retrieval
ms.assetid: 24a28760-1225-42b3-9c89-c9c0332d9c51
author: rothja
ms.author: jroth
ms.openlocfilehash: d387d1b96a57dcc7100368779f8ec6078fad5c7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730231"
---
# <a name="retrieve-and-query-xml-data"></a><span data-ttu-id="7ccc3-102">XML 데이터 검색 및 쿼리</span><span class="sxs-lookup"><span data-stu-id="7ccc3-102">Retrieve and Query XML Data</span></span>
  <span data-ttu-id="7ccc3-103">이 항목에서는 XML 데이터를 쿼리할 때 지정해야 하는 쿼리 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccc3-103">This topic describes the query options that you have to specify to query XML data.</span></span> <span data-ttu-id="7ccc3-104">또한 XML 인스턴스가 데이터베이스에 저장될 때 보존되지 않는 인스턴스의 일부분에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccc3-104">It also describes the parts of XML instances that are not preserved when they are stored in databases.</span></span>  
  
##  <a name="features-of-an-xml-instance-that-are-not-preserved"></a><a name="features"></a> <span data-ttu-id="7ccc3-105">보존되지 않는 XML 인스턴스 기능</span><span class="sxs-lookup"><span data-stu-id="7ccc3-105">Features of an XML Instance That Are Not Preserved</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7ccc3-106">에서는 XML 인스턴스의 내용을 보존하지만 XML 데이터 모델에서 중요하다고 간주되지 않는 XML 인스턴스의 측면은 보존하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ccc3-106">preserves the content of the XML instance, but does not preserve aspects of the XML instance that are not considered to be significant in the XML data model.</span></span> <span data-ttu-id="7ccc3-107">즉, 검색된 XML 인스턴스는 서버에 저장된 인스턴스와 다를 수 있지만 동일한 정보를 포함한다는 의미입니다.</span><span class="sxs-lookup"><span data-stu-id="7ccc3-107">This means that a retrieved XML instance might not be identical to the instance that was stored in the server, but will contain the same information.</span></span>  
  
### <a name="xml-declaration"></a><span data-ttu-id="7ccc3-108">XML 선언</span><span class="sxs-lookup"><span data-stu-id="7ccc3-108">XML Declaration</span></span>  
 <span data-ttu-id="7ccc3-109">인스턴스가 데이터베이스에 저장될 때 인스턴스에 있는 XML 선언이 보존되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ccc3-109">The XML declaration in an instance is not preserved when the instance is stored in the database.</span></span> <span data-ttu-id="7ccc3-110">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7ccc3-110">For example:</span></span>  
  
```  
CREATE TABLE T1 (Col1 int primary key, Col2 xml)  
GO  
INSERT INTO T1 values (1, '<?xml version="1.0" encoding="windows-1252" ?><doc></doc>')  
GO  
SELECT Col2  
FROM T1  
```  
  
 <span data-ttu-id="7ccc3-111">결과는 `<doc/>`입니다.</span><span class="sxs-lookup"><span data-stu-id="7ccc3-111">The result is `<doc/>`.</span></span>  
  
 <span data-ttu-id="7ccc3-112">XML 데이터가 `xml` 데이터 형식 인스턴스에 저장될 때 `<?xml version='1.0'?>`과 같은 XML 선언이 보존되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ccc3-112">The XML declaration, such as `<?xml version='1.0'?>`, is not preserved when storing XML data in an `xml` data type instance.</span></span> <span data-ttu-id="7ccc3-113">이것은 의도적인 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7ccc3-113">This is by design.</span></span> <span data-ttu-id="7ccc3-114">XML 선언 () 및 해당 특성 (버전/인코딩/독립 실행형)은 데이터가 형식으로 변환 된 후 손실 됩니다 `xml` .</span><span class="sxs-lookup"><span data-stu-id="7ccc3-114">The XML declaration () and its attributes (version/encoding/stand-alone) are lost after data is converted to type `xml`.</span></span> <span data-ttu-id="7ccc3-115">XML 선언은 XML 파서에 대한 지시어로 취급됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ccc3-115">The XML declaration is treated as a directive to the XML parser.</span></span> <span data-ttu-id="7ccc3-116">XML 데이터는 내부적으로 ucs-2로 저장되며</span><span class="sxs-lookup"><span data-stu-id="7ccc3-116">The XML data is stored internally as ucs-2.</span></span> <span data-ttu-id="7ccc3-117">XML 인스턴스의 다른 모든 PI는 보존됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ccc3-117">All other PIs in the XML instance are preserved.</span></span>  
  
  
### <a name="order-of-attributes"></a><span data-ttu-id="7ccc3-118">특성 순서</span><span class="sxs-lookup"><span data-stu-id="7ccc3-118">Order of Attributes</span></span>  
 <span data-ttu-id="7ccc3-119">XML 인스턴스의 특성 순서는 보존되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ccc3-119">The order of attributes in an XML instance is not preserved.</span></span> <span data-ttu-id="7ccc3-120">`xml` 유형의 열에 저장된 XML 인스턴스를 쿼리할 때 결과 XML의 특성 순서는 원래 XML 인스턴스와 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ccc3-120">When you query the XML instance stored in the `xml` type column, the order of attributes in the resulting XML may be different from the original XML instance.</span></span>  
  
  
### <a name="quotation-marks-around-attribute-values"></a><span data-ttu-id="7ccc3-121">따옴표로 묶는 특성 값</span><span class="sxs-lookup"><span data-stu-id="7ccc3-121">Quotation Marks Around Attribute Values</span></span>  
 <span data-ttu-id="7ccc3-122">특성 값에 표시된 작은따옴표와 큰따옴표는 보존되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ccc3-122">Single quotation marks and double quotations marks around attribute values are not preserved.</span></span> <span data-ttu-id="7ccc3-123">특성 값은 이름 및 값의 쌍으로 데이터베이스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ccc3-123">The attribute values are stored in the database as a name and value pair.</span></span> <span data-ttu-id="7ccc3-124">물음표는 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ccc3-124">The quotation marks are not stored.</span></span> <span data-ttu-id="7ccc3-125">XML 인스턴스에 대해 XQuery가 실행되는 경우 결과 XML은 특성 값이 큰따옴표로 묶여서 직렬화됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ccc3-125">When an XQuery is executed against an XML instance, the resulting XML is serialized with double quotation marks around the attribute values.</span></span>  
  
```  
DECLARE @x xml  
-- Use double quotation marks.  
SET @x = '<root a="1" />'  
SELECT @x  
GO  
DECLARE @x xml  
-- Use single quotation marks.  
SET @x = '<root a=''1'' />'  
SELECT @x  
GO  
```  
  
 <span data-ttu-id="7ccc3-126">두 쿼리 모두 = `<root a="1" />`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccc3-126">Both queries return = `<root a="1" />`.</span></span>  
  
  
### <a name="namespace-prefixes"></a><span data-ttu-id="7ccc3-127">네임스페이스 접두사</span><span class="sxs-lookup"><span data-stu-id="7ccc3-127">Namespace Prefixes</span></span>  
 <span data-ttu-id="7ccc3-128">네임스페이스 접두사는 유지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ccc3-128">Namespace prefixes are not preserved.</span></span> <span data-ttu-id="7ccc3-129">`xml` 유형의 열에 대해 XQuery를 지정하는 경우 직렬화된 XML 결과는 다른 네임스페이스 접두사를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ccc3-129">When you specify XQuery against an `xml` type column, the serialized XML result may return different namespace prefixes.</span></span>  
  
```  
DECLARE @x xml  
SET @x = '<ns1:root xmlns:ns1="abc" xmlns:ns2="abc">  
            <ns2:SomeElement/>  
          </ns1:root>'  
SELECT @x  
SELECT @x.query('/*')  
GO  
```  
  
 <span data-ttu-id="7ccc3-130">결과의 네임스페이스 접두사는 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ccc3-130">The namespace prefix in the result may be different.</span></span> <span data-ttu-id="7ccc3-131">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7ccc3-131">For example:</span></span>  
  
```  
<p1:root xmlns:p1="abc"><p1:SomeElement/></p1:root>  
```  
  
  
##  <a name="setting-required-query-options"></a><a name="query"></a> <span data-ttu-id="7ccc3-132">필수 쿼리 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="7ccc3-132">Setting Required Query Options</span></span>  
 <span data-ttu-id="7ccc3-133">`xml`데이터 형식 메서드를 사용 하 여 형식 열 또는 변수를 쿼리할 때는 `xml` 다음 옵션을 표시 된 대로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccc3-133">When querying `xml` type columns or variables using `xml` data type methods, the following options must be set as shown.</span></span>  
  
|<span data-ttu-id="7ccc3-134">SET 옵션</span><span class="sxs-lookup"><span data-stu-id="7ccc3-134">SET Options</span></span>|<span data-ttu-id="7ccc3-135">필요한 값</span><span class="sxs-lookup"><span data-stu-id="7ccc3-135">Required Values</span></span>|  
|-----------------|---------------------|  
|<span data-ttu-id="7ccc3-136">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="7ccc3-136">ANSI_NULLS</span></span>|<span data-ttu-id="7ccc3-137">켜기</span><span class="sxs-lookup"><span data-stu-id="7ccc3-137">ON</span></span>|  
|<span data-ttu-id="7ccc3-138">ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="7ccc3-138">ANSI_PADDING</span></span>|<span data-ttu-id="7ccc3-139">켜기</span><span class="sxs-lookup"><span data-stu-id="7ccc3-139">ON</span></span>|  
|<span data-ttu-id="7ccc3-140">ANSI_WARNINGS</span><span class="sxs-lookup"><span data-stu-id="7ccc3-140">ANSI_WARNINGS</span></span>|<span data-ttu-id="7ccc3-141">켜기</span><span class="sxs-lookup"><span data-stu-id="7ccc3-141">ON</span></span>|  
|<span data-ttu-id="7ccc3-142">ARITHABORT</span><span class="sxs-lookup"><span data-stu-id="7ccc3-142">ARITHABORT</span></span>|<span data-ttu-id="7ccc3-143">켜기</span><span class="sxs-lookup"><span data-stu-id="7ccc3-143">ON</span></span>|  
|<span data-ttu-id="7ccc3-144">CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="7ccc3-144">CONCAT_NULL_YIELDS_NULL</span></span>|<span data-ttu-id="7ccc3-145">켜기</span><span class="sxs-lookup"><span data-stu-id="7ccc3-145">ON</span></span>|  
|<span data-ttu-id="7ccc3-146">NUMERIC_ROUNDABORT</span><span class="sxs-lookup"><span data-stu-id="7ccc3-146">NUMERIC_ROUNDABORT</span></span>|<span data-ttu-id="7ccc3-147">OFF</span><span class="sxs-lookup"><span data-stu-id="7ccc3-147">OFF</span></span>|  
|<span data-ttu-id="7ccc3-148">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="7ccc3-148">QUOTED_IDENTIFIER</span></span>|<span data-ttu-id="7ccc3-149">켜기</span><span class="sxs-lookup"><span data-stu-id="7ccc3-149">ON</span></span>|  
  
 <span data-ttu-id="7ccc3-150">옵션이 표시 된 대로 설정 되어 있지 않으면 데이터 형식 메서드에 대 한 쿼리 및 수정 `xml` 이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccc3-150">If the options are not set as shown, queries and modifications on `xml` data type methods will fail.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="7ccc3-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ccc3-151">See Also</span></span>  
 [<span data-ttu-id="7ccc3-152">XML 데이터 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="7ccc3-152">Create Instances of XML Data</span></span>](create-instances-of-xml-data.md)  
  
  
