---
title: XSD 데이터 형식을 XPath 데이터 형식에 매핑 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping data types [SQLXML]
- data types [SQLXML], converting
- annotated XSD schemas, mapping data types
- XPath queries [SQLXML], mapping data types
- converting data types [SQLXML]
- data types [SQLXML], mapping data types
- XPath data types [SQLXML]
- XSD schemas [SQLXML], mapping data types
ms.assetid: ced1a95e-18d4-4a5a-8da8-dbb6d58bbd45
author: rothja
ms.author: jroth
ms.openlocfilehash: a4a3bd0b100dd935b5cea0d9ee4565633a9cb80e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659898"
---
# <a name="mapping-xsd-data-types-to-xpath-data-types-sqlxml-40"></a><span data-ttu-id="668c5-102">XSD 데이터 형식을 XPath 데이터 형식에 매핑(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="668c5-102">Mapping XSD Data Types to XPath Data Types (SQLXML 4.0)</span></span>
  <span data-ttu-id="668c5-103">XSD 스키마에 대해 XPath 쿼리를 실행할 경우 XSD 형식이 `xsd:type` 특성에 지정되어 있으면 XPath는 쿼리를 처리할 때 지정된 데이터 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="668c5-103">When an XPath query is executed against an XSD schema and the XSD type is specified in the `xsd:type` attribute, XPath uses the data type specified when it processes the query.</span></span>  
  
 <span data-ttu-id="668c5-104">다음 표에서 볼 수 있는 것처럼 노드의 XPath 데이터 형식은 스키마의 XSD 데이터 형식에서 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="668c5-104">The XPath data type of a node is derived from the XSD data type in the schema, as shown in the following table.</span></span> <span data-ttu-id="668c5-105">EmployeeID 노드는 설명을 위해 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="668c5-105">(The EmployeeID node is used for the purpose of illustration.)</span></span>  
  
|<span data-ttu-id="668c5-106">XSD 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="668c5-106">XSD data type</span></span>|<span data-ttu-id="668c5-107">XDR 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="668c5-107">XDR data type</span></span>|<span data-ttu-id="668c5-108">해당</span><span class="sxs-lookup"><span data-stu-id="668c5-108">Equivalent</span></span><br /><br /> <span data-ttu-id="668c5-109">XPath 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="668c5-109">XPath data type</span></span>|<span data-ttu-id="668c5-110">SQL Server</span><span class="sxs-lookup"><span data-stu-id="668c5-110">SQL Server</span></span><br /><br /> <span data-ttu-id="668c5-111">변환</span><span class="sxs-lookup"><span data-stu-id="668c5-111">conversion that is used</span></span>|  
|-------------------|-------------------|------------------------------------|--------------------------------------------|  
|`Base64Binary`<br /><br /> `HexBinary`|`None`<br /><br /> `bin.base64bin.hex`|`Not applicable`|<span data-ttu-id="668c5-112">없음</span><span class="sxs-lookup"><span data-stu-id="668c5-112">None</span></span><br /><br /> <span data-ttu-id="668c5-113">EmployeeID</span><span class="sxs-lookup"><span data-stu-id="668c5-113">EmployeeID</span></span>|  
|`Boolean`|`boolean`|`boolean`|<span data-ttu-id="668c5-114">CONVERT(bit, EmployeeID)</span><span class="sxs-lookup"><span data-stu-id="668c5-114">CONVERT(bit, EmployeeID)</span></span>|  
|`Decimal, integer, float, byte, short, int, long, float, double, unsignedByte, unsignedShort, unsignedInt, unsignedLong`|`number, int, float,i1, i2, i4, i8,r4, r8ui1, ui2, ui4, ui8`|`number`|<span data-ttu-id="668c5-115">CONVERT(float(53), EmployeeID)</span><span class="sxs-lookup"><span data-stu-id="668c5-115">CONVERT(float(53), EmployeeID)</span></span>|  
|`id, idref, idrefsentity, entities, notation, nmtoken, nmtokens, DateTime, string, AnyURI`|`id, idref, idrefsentity, entities, enumeration, notation, nmtoken, nmtokens, char, dateTime, dateTime.tz, string, uri, uuid`|`string`|<span data-ttu-id="668c5-116">CONVERT(nvarchar(4000), EmployeeID, 126)</span><span class="sxs-lookup"><span data-stu-id="668c5-116">CONVERT(nvarchar(4000), EmployeeID, 126)</span></span>|  
|`decimal`|`fixed14.4`|`Not applicable (There is no data type in XPath that is equivalent to the fixed14.4 XDR data type.)`|<span data-ttu-id="668c5-117">CONVERT(money, EmployeeID)</span><span class="sxs-lookup"><span data-stu-id="668c5-117">CONVERT(money, EmployeeID)</span></span>|  
|`date`|`date`|`string`|<span data-ttu-id="668c5-118">LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)</span><span class="sxs-lookup"><span data-stu-id="668c5-118">LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)</span></span>|  
|`time`|`time`<br /><br /> `time.tz`|`string`|<span data-ttu-id="668c5-119">SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)</span><span class="sxs-lookup"><span data-stu-id="668c5-119">SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)</span></span>|  
  
  
