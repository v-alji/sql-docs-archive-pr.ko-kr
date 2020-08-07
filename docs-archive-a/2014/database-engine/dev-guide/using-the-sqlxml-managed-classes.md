---
title: SQLXML 관리 되는 클래스 사용 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- sample applications [SQLXML]
- SQLXML Managed Classes, sample applications
- examples [SQLXML], managed classes
- Managed Classes [SQLXML], samples
ms.assetid: 3f021290-00ee-44e1-af4b-33d3ba8c6302
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 634a0e4110b13931201edd026ee95028cb94e859
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732992"
---
# <a name="using-the-sqlxml-managed-classes"></a><span data-ttu-id="71eba-102">SQLXML 관리되는 클래스 사용</span><span class="sxs-lookup"><span data-stu-id="71eba-102">Using the SQLXML Managed Classes</span></span>
  <span data-ttu-id="71eba-103">이 섹션에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML 관리되는 클래스를 사용하는 방법을 보여 주는 예제 애플리케이션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="71eba-103">This section provides sample applications that demonstrate how to use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML Managed Classes.</span></span>  
  
 <span data-ttu-id="71eba-104">.NET Framework 내에서 데이터에 액세스 하 고 수정 하 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 방법 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 및 diffgram를 사용 하 여 테이블의 데이터를 업데이트 하는 방법에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [.Net 환경에서 SQLXML 기능에 액세스](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="71eba-104">For information about accessing and modifying data in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] within the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework, and about using DiffGrams to update data in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables, see [Accessing SQLXML Functionality in the .NET Environment](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="71eba-105">XML 대량 로드를 사용하여 XML 문서를 대량 로드하는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 애플리케이션을 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71eba-105">You can also write [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio applications to bulk load XML documents by using XML Bulk Load.</span></span> <span data-ttu-id="71eba-106">자세한 내용은 [SQLXML 4.0&#41;&#40;XML 데이터 대량 로드 수행 ](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="71eba-106">For more information, see [Performing Bulk Load of XML Data &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md).</span></span> <span data-ttu-id="71eba-107">애플리케이션에 XML 대량 로드 DLL(Xblkld4.dll)에 대한 참조를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71eba-107">You must add a reference to the XML Bulk Load DLL (Xblkld4.dll) in your application.</span></span> <span data-ttu-id="71eba-108">이 DLL은 Visual Studio .NET에서 자동으로 래퍼 라이브러리를 만드는 COM DLL입니다.</span><span class="sxs-lookup"><span data-stu-id="71eba-108">This is a COM DLL for which Visual Studio .NET automatically creates the wrapper library.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="71eba-109">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="71eba-109">In This Section</span></span>  
 [<span data-ttu-id="71eba-110">SQL 쿼리 실행 SQLXML 관리 되는 클래스 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="71eba-110">Executing SQL Queries &#40;SQLXML Managed Classes&#41;</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md)  
  [<span data-ttu-id="71eba-111">ExecuteXMLReader 메서드를 사용하여 SQL 쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="71eba-111">Executing SQL Queries by Using the ExecuteXMLReader Method</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-sql-queries-by-using-the-executexmlreader-method.md)  
  [<span data-ttu-id="71eba-112">클라이언트 쪽 &#40;SQLXML 관리 되는 클래스에서 XML 처리&#41;</span><span class="sxs-lookup"><span data-stu-id="71eba-112">Processing XML on the Client Side &#40;SQLXML Managed Classes&#41;</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/processing-xml-on-the-client-side-sqlxml-managed-classes.md)  
  [<span data-ttu-id="71eba-113">SQLXML 관리 되는 클래스 &#40;XPath 쿼리 실행&#41;</span><span class="sxs-lookup"><span data-stu-id="71eba-113">Executing XPath Queries &#40;SQLXML Managed Classes&#41;</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-xpath-queries-sqlxml-managed-classes.md)  
  [<span data-ttu-id="71eba-114">SQLXML 관리 되는 클래스 &#40;네임 스페이스를 사용 하 여 XPath 쿼리 실행&#41;</span><span class="sxs-lookup"><span data-stu-id="71eba-114">Executing XPath Queries with Namespaces &#40;SQLXML Managed Classes&#41;</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md)  
  [<span data-ttu-id="71eba-115">CommandText 속성을 사용하여 템플릿 파일 실행</span><span class="sxs-lookup"><span data-stu-id="71eba-115">Executing Template Files by Using the CommandText Property</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-template-files-by-using-the-commandtext-property.md)  
  [<span data-ttu-id="71eba-116">CommandStream 속성을 사용하여 템플릿 파일 실행</span><span class="sxs-lookup"><span data-stu-id="71eba-116">Executing Template Files by Using the CommandStream Property</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-template-files-by-using-the-commandstream-property.md)  
  [<span data-ttu-id="71eba-117">SQLXML 관리 되는 클래스 &#40;XSL 변환 적용&#41;</span><span class="sxs-lookup"><span data-stu-id="71eba-117">Applying an XSL Transformation &#40;SQLXML Managed Classes&#41;</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/applying-an-xsl-transformation-sqlxml-managed-classes.md)  
  
