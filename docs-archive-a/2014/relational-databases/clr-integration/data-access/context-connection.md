---
title: 컨텍스트 연결 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context connections [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- context [CLR integration]
ms.assetid: 67dd1925-d672-4986-a85f-bce4fe832ef7
author: rothja
ms.author: jroth
ms.openlocfilehash: 82c739aa9c1952c71e9a16aaa68ec999851b3202
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650115"
---
# <a name="context-connection"></a><span data-ttu-id="3cc4c-102">컨텍스트 연결</span><span class="sxs-lookup"><span data-stu-id="3cc4c-102">Context Connection</span></span>
  <span data-ttu-id="3cc4c-103">내부 데이터 액세스 문제는 상당히 일반적인 시나리오입니다.</span><span class="sxs-lookup"><span data-stu-id="3cc4c-103">The problem of internal data access is a fairly common scenario.</span></span> <span data-ttu-id="3cc4c-104">즉, CLR(공용 언어 런타임) 저장 프로시저 또는 함수가 실행 중인 서버에 액세스하려는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="3cc4c-104">That is, you wish to access the same server on which your common language runtime (CLR) stored procedure or function is executing.</span></span> <span data-ttu-id="3cc4c-105">한 가지 방법은 `System.Data.SqlClient.SqlConnection`을 사용하여 연결을 만들고, 로컬 서버를 가리키는 연결 문자열을 지정하고, 연결을 여는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3cc4c-105">One option is to create a connection using `System.Data.SqlClient.SqlConnection`, specify a connection string that points to the local server, and open the connection.</span></span> <span data-ttu-id="3cc4c-106">이렇게 하려면 로그인에 사용할 자격 증명을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cc4c-106">This requires specifying credentials for logging in.</span></span> <span data-ttu-id="3cc4c-107">연결은 저장 프로시저 또는 함수와 다른 데이터베이스 세션에 있거나, 다른 `SET` 옵션을 가지거나, 별도의 트랜잭션에 있거나, 사용자의 임시 테이블을 볼 수 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cc4c-107">The connection is in a different database session than the stored procedure or function, it may have different `SET` options, it is in a separate transaction, it does not see your temporary tables, and so on.</span></span> <span data-ttu-id="3cc4c-108">사용자의 관리 저장 프로시저 또는 함수 코드가 SQL Server 서버 프로세스에서 실행되는 경우 다른 사용자가 해당 서버에 연결하고 SQL 문을 실행하여 이를 호출했기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="3cc4c-108">If your managed stored procedure or function code is executing in the SQL Server process, it is because someone connected to that server and executed a SQL statement to invoke it.</span></span> <span data-ttu-id="3cc4c-109">저장 프로시저 또는 함수를 이 연결의 트랜잭션, `SET` 옵션 등과 함께 이 연결의 컨텍스트에서 실행하려는 경우가 있는데</span><span class="sxs-lookup"><span data-stu-id="3cc4c-109">You probably want the stored procedure or function to execute in the context of that connection, along with its transaction, `SET` options, and so on.</span></span> <span data-ttu-id="3cc4c-110">이를 컨텍스트 연결이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cc4c-110">This is called the context connection.</span></span>  
  
 <span data-ttu-id="3cc4c-111">컨텍스트 연결을 사용하여 코드를 처음 호출한 컨텍스트에서 Transact-SQL 문을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cc4c-111">The context connection lets you execute Transact-SQL statements in the same context that your code was invoked in the first place.</span></span> <span data-ttu-id="3cc4c-112">컨텍스트 연결을 얻으려면 다음 예와 같이 "context connection" 연결 문자열 키워드를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cc4c-112">In order to obtain the context connection, you must use the "context connection" connection string keyword, as in the example below:</span></span>  
  
 <span data-ttu-id="3cc4c-113">[C#]</span><span class="sxs-lookup"><span data-stu-id="3cc4c-113">[C#]</span></span>  
  
```  
using(SqlConnection connection = new SqlConnection("context connection=true"))   
{  
    connection.Open();  
    // Use the connection  
}  
```  
  
 <span data-ttu-id="3cc4c-114">[Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="3cc4c-114">[Visual Basic]</span></span>  
  
```  
Using connection as new SqlConnection("context connection=true")  
    connection.Open()  
    ' Use the connection  
End Using  
  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="3cc4c-115">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="3cc4c-115">In This Section</span></span>  
 [<span data-ttu-id="3cc4c-116">일반 연결 및 컨텍스트 연결</span><span class="sxs-lookup"><span data-stu-id="3cc4c-116">Regular vs. Context Connections</span></span>](context-connections-vs-regular-connections.md)  
 <span data-ttu-id="3cc4c-117">일반 연결과 컨텍스트 연결의 차이를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3cc4c-117">Describes the differences between regular and context connections.</span></span>  
  
 [<span data-ttu-id="3cc4c-118">일반 연결 및 컨텍스트 연결에 대한 제한 사항</span><span class="sxs-lookup"><span data-stu-id="3cc4c-118">Restrictions on Regular and Context Connections</span></span>](context-connections-and-regular-connections-restrictions.md)  
 <span data-ttu-id="3cc4c-119">일반 연결 및 컨텍스트 연결에 대한 제한 사항을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3cc4c-119">Describes the restrictions on regular and context connections.</span></span>  
  
  
