---
title: 프로시저 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC]
- stored procedures [ODBC], about ODBC stored procedures
- ODBC applications, statements
- statements [ODBC], stored procedures
- ODBC applications, stored procedures
ms.assetid: c64d5f3a-376b-48ef-84f3-b6148ac8600a
author: rothja
ms.author: jroth
ms.openlocfilehash: a7ae4678d324ba7d07ae429793b1f75b57bb15e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646400"
---
# <a name="procedures"></a><span data-ttu-id="d2f45-102">프로시저</span><span class="sxs-lookup"><span data-stu-id="d2f45-102">Procedures</span></span>
  <span data-ttu-id="d2f45-103">저장 프로시저란 하나 이상의 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문을 포함하는 미리 컴파일된 실행 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="d2f45-103">A stored procedure is a precompiled executable object that contains one or more [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="d2f45-104">저장 프로시저는 입/출력 매개 변수를 가질 수 있으며 정수 반환 코드를 반환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2f45-104">Stored procedures can have input and output parameters and can also put out an integer return code.</span></span> <span data-ttu-id="d2f45-105">애플리케이션에서는 카탈로그 함수를 사용하여 사용 가능한 저장 프로시저를 열거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2f45-105">An application can enumerate available stored procedures by using catalog functions.</span></span>  
  
 <span data-ttu-id="d2f45-106">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]를 대상으로 하는 ODBC 애플리케이션은 직접 실행 방식으로만 저장 프로시저를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2f45-106">ODBC applications that target [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] should only use direct execution to call a stored procedure.</span></span> <span data-ttu-id="d2f45-107">이전 버전의에 연결 된 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE Client ODBC 드라이버는 임시 저장 프로시저를 만들어 [sqlprepare 함수](https://go.microsoft.com/fwlink/?LinkId=59360) 를 구현 합니다 .이 프로시저는 **sqlprepare**에서 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2f45-107">When connected to earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver implements [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360) by creating a temporary stored procedure, which is then called on **SQLExecute**.</span></span> <span data-ttu-id="d2f45-108">대상 저장 프로시저만 호출 하 고 대상 저장 프로시저를 직접 실행 하는 임시 저장 프로시저를 만들도록 **Sqlprepare** 를 추가 하는 오버 헤드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2f45-108">It adds overhead to have **SQLPrepare** create a temporary stored procedure that only calls the target stored procedure versus directly executing the target stored procedure.</span></span> <span data-ttu-id="d2f45-109">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 인스턴스에 연결된 경우에도 호출을 준비하려면 추가 네트워크 왕복이 필요하고 저장 프로시저 실행 계획만 호출하는 실행 계획을 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2f45-109">Even when connected to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], preparing a call requires an extra round trip across the network and the building of an execution plan that just calls the stored procedure execution plan.</span></span>  
  
 <span data-ttu-id="d2f45-110">ODBC 애플리케이션에서는 저장 프로시저를 실행할 때 ODBC CALL 구문을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2f45-110">ODBC applications should use the ODBC CALL syntax when executing a stored procedure.</span></span> <span data-ttu-id="d2f45-111">ODBC CALL 구문을 사용하면 드라이버는 원격 프로시저 호출 메커니즘을 사용하여 프로시저를 호출하도록 최적화됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2f45-111">The driver is optimized to use a remote procedure call mechanism to call the procedure when the ODBC CALL syntax is used.</span></span> <span data-ttu-id="d2f45-112">이 방법은 서버에 [!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE 문을 보내는 데 사용되는 메커니즘에 비해 훨씬 효과적입니다.</span><span class="sxs-lookup"><span data-stu-id="d2f45-112">This is more efficient than the mechanism used to send a [!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE statement to the server.</span></span>  
  
 <span data-ttu-id="d2f45-113">자세한 내용은 [저장 프로시저 실행](../../native-client-odbc-stored-procedures/running-stored-procedures.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2f45-113">For more information, see [Running Stored Procedures](../../native-client-odbc-stored-procedures/running-stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2f45-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d2f45-114">See Also</span></span>  
 [<span data-ttu-id="d2f45-115">ODBC&#41;&#40;문을 실행 하는 중</span><span class="sxs-lookup"><span data-stu-id="d2f45-115">Executing Statements &#40;ODBC&#41;</span></span>](executing-statements-odbc.md)  
  
  
