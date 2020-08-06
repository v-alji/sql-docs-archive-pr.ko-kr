---
title: SQLXMLOLEDB 공급자 사용 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sample applications [SQLXML]
- SQLXMLOLEDB Provider, samples
- ClientSideXML property
ms.assetid: fbcefac5-29c9-478b-b0e0-d510b593f446
author: rothja
ms.author: jroth
ms.openlocfilehash: 74e3c53eecd657d610c2fe90e108e0290e9b05b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651600"
---
# <a name="using-the-sqlxmloledb-provider-sqlxml-40"></a><span data-ttu-id="9ff00-102">SQLXMLOLEDB 공급자 사용(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="9ff00-102">Using the SQLXMLOLEDB Provider (SQLXML 4.0)</span></span>
  <span data-ttu-id="9ff00-103">이 섹션의 항목에서는 SQLXMLOLEDB 공급자 고유 속성의 사용 방법을 보여 주는 ADO 예제 애플리케이션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff00-103">The topics in this section provide ADO sample applications that illustrate the use of SQLXMLOLEDB Provider-specific properties.</span></span>  
  
## <a name="application-requirements-for-sqlxmloledb-40-provider"></a><span data-ttu-id="9ff00-104">SQLXMLOLEDB 4.0 공급자의 애플리케이션 요구 사항</span><span class="sxs-lookup"><span data-stu-id="9ff00-104">Application Requirements for SQLXMLOLEDB 4.0 Provider</span></span>  
 <span data-ttu-id="9ff00-105">SQLXMLOLEDB 4.0을 사용하는 작업 예제를 만들려면 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff00-105">To create working samples that use SQLXMLOLEDB 4.0, you must do the following:</span></span>  
  
1.  <span data-ttu-id="9ff00-106">Microsoft Visual Basic .exe 애플리케이션을 만들고 다음 참조 중 하나를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff00-106">Create a Microsoft Visual Basic .exe application and add one of the following references:</span></span>  
  
    -   <span data-ttu-id="9ff00-107">Microsoft ADO(ActiveX Data Objects) 2.6 라이브러리</span><span class="sxs-lookup"><span data-stu-id="9ff00-107">Microsoft ActiveX Data Objects 2.6 Library</span></span>  
  
    -   <span data-ttu-id="9ff00-108">Microsoft ADO(ActiveX Data Objects) 2.7 라이브러리</span><span class="sxs-lookup"><span data-stu-id="9ff00-108">Microsoft ActiveX Data Objects 2.7 Library</span></span>  
  
    -   <span data-ttu-id="9ff00-109">Microsoft ActiveX Data Objects 2.8 라이브러리</span><span class="sxs-lookup"><span data-stu-id="9ff00-109">Microsoft ActiveX Data Objects 2.8 Library</span></span>  
  
2.  <span data-ttu-id="9ff00-110">SQLXML 4.0과 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client를 배포 및 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff00-110">Deploy and install SQLXML 4.0 and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
     <span data-ttu-id="9ff00-111">자세한 내용은 [SQLXML 4.0 프로그래밍 개념](../../sqlxml/sqlxml-4-0-programming-concepts.md) 및 [SQL Server Native Client 설치](../../native-client/applications/installing-sql-server-native-client.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ff00-111">For more information, see on [SQLXML 4.0 Programming Concepts](../../sqlxml/sqlxml-4-0-programming-concepts.md) and [Installing SQL Server Native Client](../../native-client/applications/installing-sql-server-native-client.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9ff00-112">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="9ff00-112">In This Section</span></span>  
 [<span data-ttu-id="9ff00-113">SQLXMLOLEDB 공급자&#41;&#40;SQL 쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="9ff00-113">Executing SQL Queries &#40;SQLXMLOLEDB Provider&#41;</span></span>](executing-sql-queries-sqlxmloledb-provider.md)  
 <span data-ttu-id="9ff00-114">ClientSideXML 및 xml 루트 속성을 사용 하 여 SQL 쿼리를 실행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ff00-114">Illustrates the use of the ClientSideXML and xml root properties to execute SQL queries.</span></span>  
  
 [<span data-ttu-id="9ff00-115">SQLXMLOLEDB Provider &#40;SQL 쿼리를 포함 하는 템플릿 실행&#41;</span><span class="sxs-lookup"><span data-stu-id="9ff00-115">Executing Templates That Contain SQL Queries &#40;SQLXMLOLEDB Provider&#41;</span></span>](executing-templates-that-contain-sql-queries-sqlxmloledb-provider.md)  
 <span data-ttu-id="9ff00-116">ClientSideXML 속성을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ff00-116">Illustrates the use of the ClientSideXML property.</span></span>  
  
 [<span data-ttu-id="9ff00-117">SQLXMLOLEDB 공급자를 &#40;XPath 쿼리 실행&#41;</span><span class="sxs-lookup"><span data-stu-id="9ff00-117">Executing XPath Queries &#40;SQLXMLOLEDB Provider&#41;</span></span>](executing-xpath-queries-sqlxmloledb-provider.md)  
 <span data-ttu-id="9ff00-118">ClientSideXML, 기본 경로 및 매핑 스키마 속성을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ff00-118">Illustrates the use of the ClientSideXML, Base Path, and Mapping Schema properties.</span></span>  
  
 [<span data-ttu-id="9ff00-119">SQLXMLOLEDB 공급자를 사용 하 &#40;네임 스페이스가 있는 XPath 쿼리 실행&#41;</span><span class="sxs-lookup"><span data-stu-id="9ff00-119">Executing XPath Queries with Namespaces &#40;SQLXMLOLEDB Provider&#41;</span></span>](executing-xpath-queries-with-namespaces-sqlxmloledb-provider.md)  
 <span data-ttu-id="9ff00-120">네임스페이스로 한정된 스키마에 대해 쿼리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff00-120">Illustrates how to query against namespace-qualified schemas.</span></span>  
  
 [<span data-ttu-id="9ff00-121">SQLXMLOLEDB Provider &#40;XPath 쿼리를 포함 하는 템플릿 실행&#41;</span><span class="sxs-lookup"><span data-stu-id="9ff00-121">Executing Templates That Contain XPath Queries &#40;SQLXMLOLEDB Provider&#41;</span></span>](executing-templates-that-contain-xpath-queries-sqlxmloledb-provider.md)  
 <span data-ttu-id="9ff00-122">ClientSideXML, 기본 경로 및 매핑 스키마 속성을 사용 하 여 SQL 쿼리를 사용 하 여 템플릿을 실행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ff00-122">Illustrates how to execute templates with SQL queries using the ClientSideXML, Base Path, and Mapping Schema properties.</span></span>  
  
 [<span data-ttu-id="9ff00-123">SQLXMLOLEDB 공급자&#41;&#40;XSL 변환 적용</span><span class="sxs-lookup"><span data-stu-id="9ff00-123">Applying an XSL Transformation &#40;SQLXMLOLEDB Provider&#41;</span></span>](applying-an-xsl-transformation-sqlxmloledb-provider.md)  
 <span data-ttu-id="9ff00-124">Xml 및 xsl 속성을 사용 하 여 XSL 변환을 적용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ff00-124">Illustrates the use of the ClientSideXML and xsl properties in applying an XSL transformation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ff00-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9ff00-125">See Also</span></span>  
 [<span data-ttu-id="9ff00-126">SQL Server Native Client의 시스템 요구 사항</span><span class="sxs-lookup"><span data-stu-id="9ff00-126">System Requirements for SQL Server Native Client</span></span>](../../native-client/system-requirements-for-sql-server-native-client.md)  
  
  
