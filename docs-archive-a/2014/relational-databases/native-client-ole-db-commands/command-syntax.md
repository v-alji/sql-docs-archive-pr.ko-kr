---
title: 명령 구문 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, commands
- commands [OLE DB]
- SQL Server Native Client OLE DB provider, stored procedures
- stored procedures [OLE DB], command syntax
ms.assetid: d463d3d7-e5cb-426d-8e92-aa29980356b6
author: rothja
ms.author: jroth
ms.openlocfilehash: da5ddb75a5c6fc10db031707b7d97ead71363e9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741908"
---
# <a name="command-syntax"></a><span data-ttu-id="3d602-102">명령 구문</span><span class="sxs-lookup"><span data-stu-id="3d602-102">Command Syntax</span></span>
  <span data-ttu-id="3d602-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 DBGUID_SQL 매크로에 지정 된 명령 구문을 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d602-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider recognizes command syntax specified by the DBGUID_SQL macro.</span></span> <span data-ttu-id="3d602-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자의 경우 지정자는 ODBC SQL, ISO 및의 amalgam [!INCLUDE[tsql](../../includes/tsql-md.md)] 가 유효한 구문 임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3d602-104">For the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, the specifier indicates that an amalgam of ODBC SQL, ISO, and [!INCLUDE[tsql](../../includes/tsql-md.md)] is valid syntax.</span></span> <span data-ttu-id="3d602-105">예를 들어 다음 SQL 문은 ODBC SQL 이스케이프 시퀀스를 사용하여 LCASE 문자열 함수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3d602-105">For example, the following SQL statement uses an ODBC SQL escape sequence to specify the LCASE string function:</span></span>  
  
```  
SELECT customerid={fn LCASE(CustomerID)} FROM Customers  
```  
  
 <span data-ttu-id="3d602-106">LCASE는 문자열을 반환하고 모든 대문자를 소문자로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="3d602-106">LCASE returns a character string, converting all uppercase characters to their lowercase equivalents.</span></span> <span data-ttu-id="3d602-107">ISO 문자열 함수 LOWER도 동일한 작업을 수행하기 때문에 다음 SQL 문은 바로 위에 있는 ODBC 문에 해당하는 ISO 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="3d602-107">The ISO string function LOWER performs the same operation, so the following SQL statement is a ISO equivalent to the ODBC statement presented above:</span></span>  
  
```  
SELECT customerid=LOWER(CustomerID) FROM Customers  
```  
  
 <span data-ttu-id="3d602-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 명령의 텍스트로 지정 된 경우 문 형식을 성공적으로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d602-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider processes either form of the statement successfully when specified as text for a command.</span></span>  
  
## <a name="stored-procedures"></a><span data-ttu-id="3d602-109">저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="3d602-109">Stored Procedures</span></span>  
 <span data-ttu-id="3d602-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자 명령을 사용 하 여 저장 프로시저를 실행 하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 명령 텍스트에서 ODBC CALL 이스케이프 시퀀스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d602-110">When executing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedure using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider command, use the ODBC CALL escape sequence in the command text.</span></span> <span data-ttu-id="3d602-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는의 원격 프로시저 호출 메커니즘을 사용 하 여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 명령 처리를 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d602-111">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider then uses the remote procedure call mechanism of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to optimize command processing.</span></span> <span data-ttu-id="3d602-112">예를 들어 다음 중 [!INCLUDE[tsql](../../includes/tsql-md.md)] 형식보다는 ODBC SQL 문을 명령 텍스트로 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3d602-112">For example, the following ODBC SQL statement is preferred command text over the [!INCLUDE[tsql](../../includes/tsql-md.md)] form:</span></span>  
  
-   <span data-ttu-id="3d602-113">ODBC SQL</span><span class="sxs-lookup"><span data-stu-id="3d602-113">ODBC SQL</span></span>  
  
    ```  
    {call SalesByCategory('Produce', '1995')}  
    ```  
  
-   <span data-ttu-id="3d602-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3d602-114">Transact-SQL</span></span>  
  
    ```  
    EXECUTE SalesByCategory 'Produce', '1995'  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3d602-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3d602-115">See Also</span></span>  
 [<span data-ttu-id="3d602-116">명령</span><span class="sxs-lookup"><span data-stu-id="3d602-116">Commands</span></span>](commands.md)  
  
  
