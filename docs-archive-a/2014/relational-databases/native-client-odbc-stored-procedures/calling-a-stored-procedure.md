---
title: 저장 프로시저 호출 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- ODBC, stored procedures
- stored procedures [ODBC], calling
- SQL Server Native Client ODBC driver, stored procedures
- ODBC CALL escape sequence
- escape sequences [SQL Server]
- CALL statement
ms.assetid: d13737f4-f641-45bf-b56c-523e2ffc080f
author: rothja
ms.author: jroth
ms.openlocfilehash: c6fa704e45e4e85b479ae8a40a3e567bea1ec5e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741959"
---
# <a name="calling-a-stored-procedure"></a><span data-ttu-id="60243-102">저장 프로시저 호출</span><span class="sxs-lookup"><span data-stu-id="60243-102">Calling a Stored Procedure</span></span>
  <span data-ttu-id="60243-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT odbc 드라이버는 저장 프로시저를 실행 하기 위한 ODBC call 이스케이프 시퀀스와 EXECUTE 문을 모두 지원 합니다. [!INCLUDE[tsql](../../includes/tsql-md.md)] [EXECUTE](/sql/t-sql/language-elements/execute-transact-sql) odbc call 이스케이프 시퀀스는 선호 되는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="60243-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports both the ODBC CALL escape sequence and the [!INCLUDE[tsql](../../includes/tsql-md.md)][EXECUTE](/sql/t-sql/language-elements/execute-transact-sql) statement for executing stored procedures; the ODBC CALL escape sequence is the preferred method.</span></span> <span data-ttu-id="60243-104">ODBC 구문을 사용하면 애플리케이션에서는 저장 프로시저의 반환 코드를 검색할 수 있고 또한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 실행하는 컴퓨터 간 RPC(원격 프로시저 호출) 전송을 위해 원래 개발된 프로토콜을 사용하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버가 최적화됩니다.</span><span class="sxs-lookup"><span data-stu-id="60243-104">Using ODBC syntax enables an application to retrieve the return codes of stored procedures and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver is also optimized to use a protocol originally developed for sending remote procedure (RPC) calls between computers running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="60243-105">이 RPC 프로토콜은 서버에서 수행되는 매개 변수 처리와 문 구문 분석의 대부분을 제거하여 성능을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="60243-105">This RPC protocol increases performance by eliminating much of the parameter processing and statement parsing done on the server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60243-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ODBC를 사용 하 여 명명 된 매개 변수를 사용 하 여 저장 프로시저를 호출 하는 경우 (자세한 내용은 이름 매개 변수를 사용 하 여 매개 변수 [바인딩](https://go.microsoft.com/fwlink/?LinkID=209721)참조) 매개 변수 이름은 ' ' 문자로 시작 해야 합니다 \@ .</span><span class="sxs-lookup"><span data-stu-id="60243-106">When calling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures using named parameters with ODBC (for more information, see [Binding Parameters by Name (Named Parameters)](https://go.microsoft.com/fwlink/?LinkID=209721)), the parameter names must start with the '\@' character.</span></span> <span data-ttu-id="60243-107">이는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에만 적용되는 제한 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="60243-107">This is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specific restriction.</span></span> <span data-ttu-id="60243-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 MDAC(Microsoft Data Access Components)보다 이 제한 사항을 더욱 엄격하게 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="60243-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver enforces this restriction more strictly than the Microsoft Data Access Components (MDAC).</span></span>  
  
 <span data-ttu-id="60243-109">프로시저를 호출하는 ODBC CALL 이스케이프 시퀀스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="60243-109">The ODBC CALL escape sequence for calling a procedure is:</span></span>  
  
 <span data-ttu-id="60243-110">{[**? =**]**call**_procedure_name_[([*parameter*] [**,**[*parameter*]] ...)]}</span><span class="sxs-lookup"><span data-stu-id="60243-110">{[**?=**]**call**_procedure_name_[([*parameter*][**,**[*parameter*]]...)]}</span></span>  
  
 <span data-ttu-id="60243-111">여기서 *procedure_name* 는 프로시저의 이름을 지정 하 고 *매개 변수* 는 프로시저 매개 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60243-111">where *procedure_name* specifies the name of a procedure and *parameter* specifies a procedure parameter.</span></span> <span data-ttu-id="60243-112">명명된 매개 변수는 ODBC CALL 이스케이프 시퀀스를 사용하는 문에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="60243-112">Named parameters are only supported in statements using the ODBC CALL escape sequence.</span></span>  
  
 <span data-ttu-id="60243-113">프로시저는 0개 이상의 매개 변수를 가질 수 있고</span><span class="sxs-lookup"><span data-stu-id="60243-113">A procedure can have zero or more parameters.</span></span> <span data-ttu-id="60243-114">값(구문 시작에 나오는 선택적 매개 변수 표식인 ?=로 표시됨)을 반환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60243-114">It can also return a value (as indicated by the optional parameter marker ?= at the start of the syntax).</span></span> <span data-ttu-id="60243-115">매개 변수가 입력 또는 입/출력 매개 변수인 경우 리터럴 또는 매개 변수 표식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60243-115">If a parameter is an input or an input/output parameter, it can be a literal or a parameter marker.</span></span> <span data-ttu-id="60243-116">매개 변수가 출력 매개 변수인 경우에는 출력을 알 수 없기 때문에 매개 변수 표식을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="60243-116">If the parameter is an output parameter, it must be a parameter marker because the output is unknown.</span></span> <span data-ttu-id="60243-117">프로시저 호출 문이 실행 되기 전에 매개 변수 표식을 [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) 와 바인딩해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="60243-117">Parameter markers must be bound with [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) before the procedure call statement is executed.</span></span>  
  
 <span data-ttu-id="60243-118">입력 및 입/출력 매개 변수는 프로시저 호출에서 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60243-118">Input and input/output parameters can be omitted from procedure calls.</span></span> <span data-ttu-id="60243-119">매개 변수 없이 괄호만 지정하여 프로시저를 호출하면 드라이버는 첫 번째 매개 변수에 기본값을 사용하도록 데이터 원본에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="60243-119">If a procedure is called with parentheses but without any parameters, the driver instructs the data source to use the default value for the first parameter.</span></span> <span data-ttu-id="60243-120">예:</span><span class="sxs-lookup"><span data-stu-id="60243-120">For example:</span></span>  
  
 <span data-ttu-id="60243-121">{**call** _procedure_name_**()**}</span><span class="sxs-lookup"><span data-stu-id="60243-121">{**call** _procedure_name_**( )**}</span></span>  
  
 <span data-ttu-id="60243-122">프로시저에 매개 변수가 없으면 프로시저가 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60243-122">If the procedure does not have any parameters, the procedure can fail.</span></span> <span data-ttu-id="60243-123">괄호 없이 프로시저를 호출하면 드라이버는 아무 매개 변수 값도 보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="60243-123">If a procedure is called without parentheses, the driver does not send any parameter values.</span></span> <span data-ttu-id="60243-124">예:</span><span class="sxs-lookup"><span data-stu-id="60243-124">For example:</span></span>  
  
 <span data-ttu-id="60243-125">{**call** _procedure_name_}</span><span class="sxs-lookup"><span data-stu-id="60243-125">{**call** _procedure_name_}</span></span>  
  
 <span data-ttu-id="60243-126">프로시저 호출 시 리터럴을 입력 및 입/출력 매개 변수로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60243-126">Literals can be specified for input and input/output parameters in procedure calls.</span></span> <span data-ttu-id="60243-127">예를 들어 InsertOrder 프로시저에는 입력 매개 변수 다섯 개가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60243-127">For example, the procedure InsertOrder has five input parameters.</span></span> <span data-ttu-id="60243-128">InsertOrder에 대 한 다음 호출은 첫 번째 매개 변수를 생략 하 고 두 번째 매개 변수에 대 한 리터럴을 제공 하며 세 번째, 네 번째 및 다섯 번째 매개 변수에 대해 매개 변수 표식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="60243-128">The following call to InsertOrder omits the first parameter, provides a literal for the second parameter, and uses a parameter marker for the third, fourth, and fifth parameters.</span></span> <span data-ttu-id="60243-129">매개 변수는 1부터 차례대로 번호가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="60243-129">(Parameters are numbered sequentially, beginning with a value of 1.)</span></span>  
  
```  
{call InsertOrder(, 10, ?, ?, ?)}  
```  
  
 <span data-ttu-id="60243-130">매개 변수를 생략하더라도 다른 매개 변수와 구분하는 쉼표는 생략하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60243-130">Note that if a parameter is omitted, the comma delimiting it from other parameters must still appear.</span></span> <span data-ttu-id="60243-131">입력 또는 입/출력 매개 변수를 생략할 경우 프로시저는 매개 변수의 기본값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="60243-131">If an input or input/output parameter is omitted, the procedure uses the default value of the parameter.</span></span> <span data-ttu-id="60243-132">매개 변수에 바인딩된 길이/표시기 버퍼의 값을 SQL_DEFAULT_PARAM으로 설정하거나, DEFAULT 키워드를 사용하여 입력 또는 입/출력 매개 변수의 기본값을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60243-132">Other ways to specify the default value of an input or input/output parameter are to set the value of the length/indicator buffer bound to the parameter to SQL_DEFAULT_PARAM, or to use the DEFAULT keyword.</span></span>  
  
 <span data-ttu-id="60243-133">입/출력 매개 변수를 생략하거나, 매개 변수에 리터럴을 제공하면 드라이버는 출력 값을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="60243-133">If an input/output parameter is omitted, or if a literal is supplied for the parameter, the driver discards the output value.</span></span> <span data-ttu-id="60243-134">마찬가지로 프로시저의 반환 값에 대한 매개 변수 표식을 생략하면 드라이버는 반환 값을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="60243-134">Similarly, if the parameter marker for the return value of a procedure is omitted, the driver discards the return value.</span></span> <span data-ttu-id="60243-135">마지막으로, 애플리케이션에서 값을 반환하지 않는 프로시저에 대해 반환 값 매개 변수를 지정하면 드라이버는 매개 변수에 바인딩된 길이/표시기 버퍼의 값을 SQL_NULL_DATA로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="60243-135">Finally, if an application specifies a return value parameter for a procedure that does not return a value, the driver sets the value of the length/indicator buffer bound to the parameter to SQL_NULL_DATA.</span></span>  
  
## <a name="delimiters-in-call-statements"></a><span data-ttu-id="60243-136">CALL 문의 구분 기호</span><span class="sxs-lookup"><span data-stu-id="60243-136">Delimiters in CALL Statements</span></span>  
 <span data-ttu-id="60243-137">기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 ODBC { CALL } 이스케이프 시퀀스와 관련된 호환성 옵션도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="60243-137">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver by default also supports a compatibility option specific to the ODBC { CALL } escape sequence.</span></span> <span data-ttu-id="60243-138">드라이버는 다음과 같이 전체 저장 프로시저 이름을 구분하는 큰따옴표 쌍 하나만 사용하는 CALL 문을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="60243-138">The driver accepts CALL statements with only a single set of double quotation marks delimiting the entire stored procedure name:</span></span>  
  
```  
{ CALL "master.dbo.sp_who" }  
```  
  
 <span data-ttu-id="60243-139">기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 다음과 같이 ISO 규칙에 따라 각 식별자를 큰따옴표로 묶은 CALL 문도 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="60243-139">By default the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver also accepts CALL statements that follow the ISO rules and enclose each identifier in double quotation marks:</span></span>  
  
```  
{ CALL "master"."dbo"."sp_who" }  
```  
  
 <span data-ttu-id="60243-140">그러나 기본 설정을 사용하여 실행할 경우 적절한 ISO 표준으로 지정되지 않은 문자가 포함된 식별자를 사용하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 두 가지 따옴표 붙은 식별자 형식을 모두 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="60243-140">When running with the default settings, however, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver does not support using either form of quoted identifier with identifiers that contain characters not specified as legal in identifiers by the ISO standard.</span></span> <span data-ttu-id="60243-141">예를 들어 드라이버가 따옴표 붙은 식별자가 포함 된 CALL 문을 사용 하 여 **"My. Proc"** 라는 저장 프로시저에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="60243-141">For example, the driver cannot access a stored procedure named **"My.Proc"** using a CALL statement with quoted identifiers:</span></span>  
  
```  
{ CALL "MyDB"."MyOwner"."My.Proc" }  
```  
  
 <span data-ttu-id="60243-142">드라이버는 이 문을 다음과 같이 해석합니다.</span><span class="sxs-lookup"><span data-stu-id="60243-142">This statement is interpreted by the driver as:</span></span>  
  
```  
{ CALL MyDB.MyOwner.My.Proc }  
```  
  
 <span data-ttu-id="60243-143">서버에서 **MyDB** 라는 연결 된 서버가 존재 하지 않는다는 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="60243-143">The server raises an error that a linked server named **MyDB** does not exist.</span></span>  
  
 <span data-ttu-id="60243-144">다음과 같이 대괄호로 묶은 식별자를 사용할 경우에는 이 문제가 발생하지 않고 문이 제대로 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="60243-144">The issue does not exist when using bracketed identifiers, this statement is interpreted correctly:</span></span>  
  
```  
{ CALL [MyDB].[MyOwner].[My.Table] }  
```  
  
## <a name="see-also"></a><span data-ttu-id="60243-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="60243-145">See Also</span></span>  
 [<span data-ttu-id="60243-146">저장 프로시저 실행</span><span class="sxs-lookup"><span data-stu-id="60243-146">Running Stored Procedures</span></span>](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
