---
title: 여러 행 집합 결과를 생성하는 명령 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- SQL Server Native Client OLE DB provider, commands
- SQL Server Native Client OLE DB provider, multiple rowsets
- commands [OLE DB]
- multiple-rowset results
ms.assetid: 4567668d-35fd-4162-b61f-f7536862cdcb
author: rothja
ms.author: jroth
ms.openlocfilehash: 8b42a89c0b043e4c72e8b5634cf70e16b435167a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728232"
---
# <a name="commands-generating-multiple-rowset-results"></a><span data-ttu-id="692dd-102">여러 행 집합 결과를 생성하는 명령</span><span class="sxs-lookup"><span data-stu-id="692dd-102">Commands Generating Multiple-Rowset Results</span></span>
  <span data-ttu-id="692dd-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 문에서 여러 행 집합을 반환할 수 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="692dd-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider can return multiple rowsets from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] statements.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="692dd-104">문은 다음과 같은 조건에서 여러 행 집합 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="692dd-104">statements return multiple-rowset results under the following conditions:</span></span>  
  
-   <span data-ttu-id="692dd-105">일괄 처리되는 SQL 문이 단일 명령으로 제출된 경우</span><span class="sxs-lookup"><span data-stu-id="692dd-105">Batched SQL statements are submitted as a single command.</span></span>  
  
-   <span data-ttu-id="692dd-106">저장 프로시저가 SQL 문의 일괄 처리를 구현하는 경우</span><span class="sxs-lookup"><span data-stu-id="692dd-106">Stored procedures implement a batch of SQL statements.</span></span>  
  
## <a name="batches"></a><span data-ttu-id="692dd-107">Batch</span><span class="sxs-lookup"><span data-stu-id="692dd-107">Batches</span></span>  
 <span data-ttu-id="692dd-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 세미콜론 문자를 SQL 문에 대 한 일괄 처리 구분 기호로 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="692dd-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider recognizes the semicolon character as a batch delimiter for SQL statements:</span></span>  
  
```  
WCHAR*       wSQLString = L"SELECT * FROM Categories; "  
                          L"SELECT * FROM Products";  
```  
  
 <span data-ttu-id="692dd-109">여러 SQL 문을 하나의 일괄 처리로 보내는 것이 각 SQL 문을 별도로 실행하는 것보다 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="692dd-109">Sending multiple SQL statements in one batch is more efficient than executing each SQL statement separately.</span></span> <span data-ttu-id="692dd-110">하나의 일괄 처리를 보내는 경우 클라이언트에서 서버로의 네트워크 왕복 수가 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="692dd-110">Sending one batch reduces the network round trips from the client to the server.</span></span>  
  
## <a name="stored-procedures"></a><span data-ttu-id="692dd-111">저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="692dd-111">Stored Procedures</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="692dd-112">는 저장 프로시저의 각 문에 대해 하나의 결과 집합을 반환하므로 대부분의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 저장 프로시저는 여러 결과 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="692dd-112">returns a result set for each statement in a stored procedure, so most [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures return multiple result sets.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="692dd-113">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="692dd-113">In This Section</span></span>  
  
-   [<span data-ttu-id="692dd-114">IMultipleResults를 사용하여 여러 결과 집합 처리</span><span class="sxs-lookup"><span data-stu-id="692dd-114">Using IMultipleResults to Process Multiple Result Sets</span></span>](using-imultipleresults-to-process-multiple-result-sets.md)  
  
## <a name="see-also"></a><span data-ttu-id="692dd-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="692dd-115">See Also</span></span>  
 [<span data-ttu-id="692dd-116">명령</span><span class="sxs-lookup"><span data-stu-id="692dd-116">Commands</span></span>](commands.md)  
  
  
