---
title: XML 데이터(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XML [SQL Server]
- XML [SQL Server], about XML
ms.assetid: 6a1793c9-9856-485c-aac5-88fda62f61a8
author: rothja
ms.author: jroth
ms.openlocfilehash: 48ddec1de8492c86aecfd80ea960c4a01673c24f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647546"
---
# <a name="xml-data-sql-server"></a><span data-ttu-id="28035-102">XML 데이터(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="28035-102">XML Data (SQL Server)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="28035-103">에서는 반구조화된 데이터 관리를 위한 다양한 애플리케이션을 개발할 수 있는 강력한 플랫폼을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="28035-103">provides a powerful platform for developing rich applications for semi-structured data management.</span></span> <span data-ttu-id="28035-104">XML에 대한 지원은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 모든 구성 요소에 통합되어 있고 해당되는 지원은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="28035-104">Support for XML is integrated into all the components in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and includes the following:</span></span>  
  
-   <span data-ttu-id="28035-105">`xml` 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="28035-105">The `xml` data type.</span></span> <span data-ttu-id="28035-106">XML 값은 XML 스키마의 컬렉션에 따라 형식화되거나 형식화되지 않은 상태로 유지될 수 있는 `xml` 데이터 형식의 열에 기본적으로 저장될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28035-106">XML values can be stored natively in an `xml` data type column that can be typed according to a collection of XML schemas, or left untyped.</span></span> <span data-ttu-id="28035-107">XML 열을 인덱싱할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28035-107">You can index the XML column.</span></span>  
  
-   <span data-ttu-id="28035-108">`xml` 유형의 변수와 열에 저장된 XML 데이터에 대해 XQuery 쿼리를 지정할 수 있는 기능</span><span class="sxs-lookup"><span data-stu-id="28035-108">The ability to specify an XQuery query against XML data stored in columns and variables of the `xml` type.</span></span>  
  
-   <span data-ttu-id="28035-109">XML 데이터를 대량으로 로드할 수 있는 OPENROWSET의 향상</span><span class="sxs-lookup"><span data-stu-id="28035-109">Enhancements to OPENROWSET to allow bulk loading of XML data.</span></span>  
  
-   <span data-ttu-id="28035-110">XML 형식의 관계형 데이터를 검색할 수 있는 FOR XML 절</span><span class="sxs-lookup"><span data-stu-id="28035-110">The FOR XML clause, to retrieve relational data in XML format.</span></span>  
  
-   <span data-ttu-id="28035-111">관계형 형식의 XML 데이터를 검색할 수 있는 OPENXML 함수</span><span class="sxs-lookup"><span data-stu-id="28035-111">The OPENXML function, to retrieve XML data in relational format.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="28035-112">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="28035-112">In This Section</span></span>  
 [<span data-ttu-id="28035-113">XML 데이터 형식 및 열&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="28035-113">XML Data Type and Columns &#40;SQL Server&#41;</span></span>](xml-data-type-and-columns-sql-server.md)  
 [<span data-ttu-id="28035-114">XML 인덱스&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="28035-114">XML Indexes &#40;SQL Server&#41;</span></span>](xml-indexes-sql-server.md)  
 [<span data-ttu-id="28035-115">XML 스키마 컬렉션&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="28035-115">XML Schema Collections &#40;SQL Server&#41;</span></span>](xml-schema-collections-sql-server.md)  
 [<span data-ttu-id="28035-116">FOR XML&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="28035-116">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
 [<span data-ttu-id="28035-117">OPENXML&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="28035-117">OPENXML &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/openxml-transact-sql)  
  
## <a name="related-content"></a><span data-ttu-id="28035-118">관련 내용</span><span class="sxs-lookup"><span data-stu-id="28035-118">Related Content</span></span>  
 [<span data-ttu-id="28035-119">XML 문서 대량 가져오기 및 내보내기 예제&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="28035-119">Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;</span></span>](../import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
 [<span data-ttu-id="28035-120">XQuery 언어 참조&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="28035-120">XQuery Language Reference &#40;SQL Server&#41;</span></span>](/sql/xquery/xquery-language-reference-sql-server)  
  
