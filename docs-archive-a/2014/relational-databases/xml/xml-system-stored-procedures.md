---
title: XML 시스템 저장 프로시저 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- system stored procedures [SQL Server], XML
- sp_xml_removedocument
- OPENXML statement, system stored procedures
- sp_xml_preparedocument
- XML [SQL Server], system stored procedures
ms.assetid: e60c7f85-6823-4d28-93d6-b053d08cc830
author: rothja
ms.author: jroth
ms.openlocfilehash: 2008294fe5bc532dfb6883656420b4189e4da7b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652668"
---
# <a name="xml-system-stored-procedures"></a><span data-ttu-id="1240d-102">XML 시스템 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="1240d-102">XML System Stored Procedures</span></span>
  <span data-ttu-id="1240d-103">SQL Server는 OPENXML과 함께 사용되는 다음 시스템 저장 프로시저를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1240d-103">SQL Server provides the following system stored procedures that are used together with OPENXML:</span></span>  
  
-   [<span data-ttu-id="1240d-104">sp_xml_preparedocument&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1240d-104">sp_xml_preparedocument &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql)  
  
-   [<span data-ttu-id="1240d-105">sp_xml_removedocument&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1240d-105">sp_xml_removedocument &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-xml-removedocument-transact-sql)  
  
 <span data-ttu-id="1240d-106">OPENXML을 사용하여 쿼리를 작성하려면 먼저 **sp_xml_preparedocument**를 호출하여 XML 문서의 내부 표현을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1240d-106">To write queries by using OPENXML, you must first create an internal representation of the XML document by calling **sp_xml_preparedocument**.</span></span> <span data-ttu-id="1240d-107">저장 프로시저는 XML 문서의 내부 표현에 대한 핸들을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1240d-107">The stored procedure returns a handle to the internal representation of the XML document.</span></span> <span data-ttu-id="1240d-108">그런 다음 이 핸들은 OPENXML에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="1240d-108">This handle is then passed to OPENXML.</span></span> <span data-ttu-id="1240d-109">OPENXML은 XPath를 기반으로 문서의 행 집합 뷰를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1240d-109">OPENXML provides rowset views of the document based on XPaths.</span></span> <span data-ttu-id="1240d-110">특히 OPENXML은 하나의 행 패턴과 하나 이상의 열 패턴입니다.</span><span class="sxs-lookup"><span data-stu-id="1240d-110">Specifically, this is one row pattern and one or more column patterns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1240d-111">**sp_xml_preparedocument** 가 반환한 문서 핸들은 세션 기간 동안 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="1240d-111">The document handle that is returned by **sp_xml_preparedocument** is valid for the duration of the session.</span></span>  
  
 <span data-ttu-id="1240d-112">**sp_xml_removedocument** 시스템 저장 프로시저를 호출하여 XML 문서의 내부 표현을 메모리에서 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1240d-112">The internal representation of an XML document can be removed from memory by calling the **sp_xml_removedocument** system stored procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1240d-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1240d-113">See Also</span></span>  
 <span data-ttu-id="1240d-114">[OPENXML&#40;Transact-SQL&#41;](/sql/t-sql/functions/openxml-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1240d-114">[OPENXML &#40;Transact-SQL&#41;](/sql/t-sql/functions/openxml-transact-sql) </span></span>  
 [<span data-ttu-id="1240d-115">OPENXML&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1240d-115">OPENXML &#40;SQL Server&#41;</span></span>](../xml/openxml-sql-server.md)  
  
  
