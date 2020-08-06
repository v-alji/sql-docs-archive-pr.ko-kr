---
title: 저장 프로시저 결과 처리 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], results
ms.assetid: 788ef2a4-17de-4526-960b-46bf29aafc9f
author: rothja
ms.author: jroth
ms.openlocfilehash: 5f37a6d8beff88748fa944293bd67f449d29eff2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741956"
---
# <a name="processing-stored-procedure-results"></a><span data-ttu-id="cba3b-102">저장 프로시저 결과 처리</span><span class="sxs-lookup"><span data-stu-id="cba3b-102">Processing Stored Procedure Results</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cba3b-103">저장 프로시저는 데이터를 반환하기 위해 네 가지 메커니즘을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cba3b-103">stored procedures have four mechanisms used to return data:</span></span>  
  
-   <span data-ttu-id="cba3b-104">프로시저의 각 SELECT 문은 결과 집합을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="cba3b-104">Each SELECT statement in the procedure generates a result set.</span></span>  
  
-   <span data-ttu-id="cba3b-105">프로시저는 출력 매개 변수를 통해 데이터를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cba3b-105">The procedure can return data through output parameters.</span></span>  
  
-   <span data-ttu-id="cba3b-106">커서 출력 매개 변수는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 서버 커서를 다시 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cba3b-106">A cursor output parameter can pass back a [!INCLUDE[tsql](../../includes/tsql-md.md)] server cursor.</span></span>  
  
-   <span data-ttu-id="cba3b-107">프로시저에는 정수 반환 코드가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cba3b-107">The procedure can have an integer return code.</span></span>  
  
 <span data-ttu-id="cba3b-108">애플리케이션은 저장 프로시저의 이러한 모든 출력을 처리할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cba3b-108">Applications must be able to handle all these outputs from stored procedures.</span></span> <span data-ttu-id="cba3b-109">CALL 또는 EXECUTE 문에는 반환 코드 및 출력 매개 변수에 대한 매개 변수 표식이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cba3b-109">The CALL or EXECUTE statement should include parameter markers for the return code and output parameters.</span></span> <span data-ttu-id="cba3b-110">[SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) 를 사용 하 여 모두 출력 매개 변수로 바인딩하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 출력 값을 바인딩된 변수에 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="cba3b-110">Use [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) to bind them all as output parameters and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver will transfer the output values to the bound variables.</span></span> <span data-ttu-id="cba3b-111">출력 매개 변수 및 반환 코드는에서 클라이언트로 반환 되는 마지막 항목 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 입니다. [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) 가 SQL_NO_DATA를 반환할 때까지 응용 프로그램에 반환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cba3b-111">Output parameters and return codes are the last items returned to the client by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; they are not returned to the application until [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) returns SQL_NO_DATA.</span></span>  
  
 <span data-ttu-id="cba3b-112">ODBC는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 커서 매개 변수를 바인딩하는 기능을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cba3b-112">ODBC does not support binding [!INCLUDE[tsql](../../includes/tsql-md.md)] cursor parameters.</span></span> <span data-ttu-id="cba3b-113">출력 커서 매개 변수가 있는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저는 실행하기 전에 모든 출력 매개 변수를 바인딩해야 하므로 ODBC 애플리케이션은 이를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cba3b-113">Because all output parameters must be bound before executing a procedure, any [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure that contains an output cursor parameter cannot be called by ODBC applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cba3b-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cba3b-114">See Also</span></span>  
 [<span data-ttu-id="cba3b-115">저장 프로시저 실행</span><span class="sxs-lookup"><span data-stu-id="cba3b-115">Running Stored Procedures</span></span>](running-stored-procedures.md)  
  
  
