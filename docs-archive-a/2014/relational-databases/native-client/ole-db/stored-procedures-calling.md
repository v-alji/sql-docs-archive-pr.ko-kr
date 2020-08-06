---
title: 저장 프로시저 호출(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- RPC escape sequence
- OLE DB, stored procedures
- parameters [SQL Server Native Client], OLE DB
- ODBC CALL escape sequence
- stored procedures [OLE DB], calling
- SQL Server Native Client OLE DB provider, stored procedures
ms.assetid: 8e5738e5-4bbe-4f34-bd69-0c0633290bdd
author: rothja
ms.author: jroth
ms.openlocfilehash: 695848c8633d310f5e8ee21e9e738749d1550e4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738194"
---
# <a name="calling-a-stored-procedure-ole-db"></a><span data-ttu-id="1bfeb-102">저장 프로시저 호출(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="1bfeb-102">Calling a Stored Procedure (OLE DB)</span></span>
  <span data-ttu-id="1bfeb-103">저장 프로시저는 0개 이상의 매개 변수를 가질 수 있으며</span><span class="sxs-lookup"><span data-stu-id="1bfeb-103">A stored procedure can have zero or more parameters.</span></span> <span data-ttu-id="1bfeb-104">값을 반환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-104">It can also return a value.</span></span> <span data-ttu-id="1bfeb-105">Native Client OLE DB 공급자를 사용 하는 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 저장 프로시저에 대 한 매개 변수를 다음으로 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-105">When using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider, parameters to a stored procedure can be passed by:</span></span>  
  
-   <span data-ttu-id="1bfeb-106">데이터 값을 하드 코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-106">Hard-coding the data value.</span></span>  
  
-   <span data-ttu-id="1bfeb-107">매개 변수 표식(?)을 사용하여 매개 변수를 지정하고, 프로그램 변수를 매개 변수 표식에 바인딩한 후 데이터 값을 프로그램 변수에 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-107">Using a parameter marker (?) to specify parameters, bind a program variable to the parameter marker, and then place the data value in the program variable.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1bfeb-108">OLE DB로 명명된 매개 변수를 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 저장 프로시저를 호출할 때 매개 변수 이름은 '\@' 문자로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-108">When calling [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stored procedures using named parameters with OLE DB, the parameter names must start with the '\@' character.</span></span> <span data-ttu-id="1bfeb-109">이는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에만 적용되는 제한 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-109">This is a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] specific restriction.</span></span> <span data-ttu-id="1bfeb-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 MDAC보다 더 엄격하게 이 제한 사항을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-110">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider enforces this restriction more strictly than MDAC.</span></span>  
  
 <span data-ttu-id="1bfeb-111">매개 변수 지원을 위해 **ICommandWithParameters** 인터페이스가 명령 개체에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-111">To support parameters, the **ICommandWithParameters** interface is exposed on the command object.</span></span> <span data-ttu-id="1bfeb-112">매개 변수를 사용하려면 소비자는 먼저 **ICommandWithParameters::SetParameterInfo** 메서드를 호출하거나 **GetParameterInfo** 메서드를 호출하는 호출 문을 통해 공급자에게 매개 변수를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-112">To use parameters, the consumer first describes the parameters to the provider by calling the **ICommandWithParameters::SetParameterInfo** method (or optionally prepares a calling statement that calls the **GetParameterInfo** method).</span></span> <span data-ttu-id="1bfeb-113">그런 다음 소비자는 버퍼의 구조를 지정하는 접근자를 만들고 매개 변수 값을 이 버퍼에 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-113">The consumer then creates an accessor that specifies the structure of a buffer and places parameter values in this buffer.</span></span> <span data-ttu-id="1bfeb-114">마지막으로 소비자는 접근자의 핸들과 버퍼에 대한 포인터를 **Execute**로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-114">Finally, it passes the handle of the accessor and a pointer to the buffer to **Execute**.</span></span> <span data-ttu-id="1bfeb-115">이후의 **Execute**에 대한 호출에서 소비자는 버퍼에 새 매개 변수 값을 넣고 접근자 핸들과 버퍼 포인터를 사용하여 **Execute**를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-115">On later calls to **Execute**, the consumer places new parameter values in the buffer and calls **Execute** with the accessor handle and buffer pointer.</span></span>  
  
 <span data-ttu-id="1bfeb-116">매개 변수를 사용하여 임시 저장 프로시저를 호출하는 명령은 먼저 **ICommandWithParameters::SetParameterInfo**를 호출하여 매개 변수 정보를 정의해야 명령을 성공적으로 준비할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-116">A command that calls a temporary stored procedure using parameters must first call **ICommandWithParameters::SetParameterInfo** to define the parameter information, before the command can be successfully prepared.</span></span> <span data-ttu-id="1bfeb-117">이는 임시 저장 프로시저의 내부 이름이 클라이언트에서 사용하는 외부 이름과 다르고, SQLOLEDB는 임시 저장 프로시저에 대한 매개 변수 정보를 확인하기 위해 시스템 테이블을 쿼리할 수 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-117">This is because the internal name for a temporary stored procedure differs from the external name used by a client and SQLOLEDB cannot query the system tables to determine the parameter information for a temporary stored procedure.</span></span>  
  
 <span data-ttu-id="1bfeb-118">다음은 매개 변수 바인딩 프로세스의 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-118">These are the steps in the parameter binding process:</span></span>  
  
1.  <span data-ttu-id="1bfeb-119">DBPARAMBINDINFO 구조의 배열에 매개 변수 정보, 즉 매개 변수 이름, 매개 변수의 데이터 형식에 대한 공급자별 이름 또는 표준 데이터 형식 이름 등을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-119">Fill in the parameter information in an array of DBPARAMBINDINFO structures; that is, parameter name, provider-specific name for the data type of the parameter or a standard data type name, and so on.</span></span> <span data-ttu-id="1bfeb-120">배열의 각 구조는 하나의 매개 변수를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-120">Each structure in the array describes one parameter.</span></span> <span data-ttu-id="1bfeb-121">이 배열은 **SetParameterInfo** 메서드로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-121">This array is then passed to the **SetParameterInfo** method.</span></span>  
  
2.  <span data-ttu-id="1bfeb-122">**ICommandWithParameters::SetParameterInfo** 메서드를 호출하여 공급자에게 매개 변수를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-122">Call the **ICommandWithParameters::SetParameterInfo** method to describe parameters to the provider.</span></span> <span data-ttu-id="1bfeb-123">**SetParameterInfo**는 각 매개 변수의 네이티브 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-123">**SetParameterInfo** specifies the native data type of each parameter.</span></span> <span data-ttu-id="1bfeb-124">**SetParameterInfo** 인수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-124">**SetParameterInfo** arguments are:</span></span>  
  
    -   <span data-ttu-id="1bfeb-125">형식 정보를 설정할 매개 변수의 수</span><span class="sxs-lookup"><span data-stu-id="1bfeb-125">The number of parameters for which to set type information.</span></span>  
  
    -   <span data-ttu-id="1bfeb-126">형식 정보를 설정할 매개 변수 서수의 배열</span><span class="sxs-lookup"><span data-stu-id="1bfeb-126">An array of parameter ordinals for which to set type information.</span></span>  
  
    -   <span data-ttu-id="1bfeb-127">DBPARAMBINDINFO 구조의 배열</span><span class="sxs-lookup"><span data-stu-id="1bfeb-127">An array of DBPARAMBINDINFO structures.</span></span>  
  
3.  <span data-ttu-id="1bfeb-128">**IAccessor::CreateAccessor** 명령을 사용하여 매개 변수 접근자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-128">Create a parameter accessor by using the **IAccessor::CreateAccessor** command.</span></span> <span data-ttu-id="1bfeb-129">이 접근자는 버퍼의 구조를 지정하고 매개 변수 값을 버퍼에 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-129">The accessor specifies the structure of a buffer and places parameter values in the buffer.</span></span> <span data-ttu-id="1bfeb-130">**CreateAccessor** 명령은 바인딩 집합으로부터 접근자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-130">The **CreateAccessor** command creates an accessor from a set of bindings.</span></span> <span data-ttu-id="1bfeb-131">이러한 바인딩은 소비자가 DBBINDING 구조의 배열을 사용하여 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-131">These bindings are described by the consumer by using an array of DBBINDING structures.</span></span> <span data-ttu-id="1bfeb-132">각 바인딩은 단일 매개 변수를 소비자의 버퍼에 연결하며 다음과 같은 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-132">Each binding associates a single parameter to the buffer of the consumer and contains information such as:</span></span>  
  
    -   <span data-ttu-id="1bfeb-133">바인딩이 적용되는 매개 변수의 서수</span><span class="sxs-lookup"><span data-stu-id="1bfeb-133">The ordinal of the parameter to which the binding applies.</span></span>  
  
    -   <span data-ttu-id="1bfeb-134">바인딩 대상(데이터 형식, 길이 및 상태)</span><span class="sxs-lookup"><span data-stu-id="1bfeb-134">What is bound (the data value, its length, and its status).</span></span>  
  
    -   <span data-ttu-id="1bfeb-135">이러한 각 부분에 대한 버퍼의 오프셋</span><span class="sxs-lookup"><span data-stu-id="1bfeb-135">The offset in the buffer to each of these parts.</span></span>  
  
    -   <span data-ttu-id="1bfeb-136">소비자의 버퍼에 존재하는 데이터 값의 길이와 형식</span><span class="sxs-lookup"><span data-stu-id="1bfeb-136">The length and type of the data value as it exists in the buffer of the consumer.</span></span>  
  
     <span data-ttu-id="1bfeb-137">접근자는 해당 핸들로 식별되며, 핸들은 HACCESSOR 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-137">An accessor is identified by its handle, which is of type HACCESSOR.</span></span> <span data-ttu-id="1bfeb-138">이 핸들은 **CreateAccessor** 메서드에 의해 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-138">This handle is returned by the **CreateAccessor** method.</span></span> <span data-ttu-id="1bfeb-139">소비자는 접근자 사용을 마칠 때마다 **ReleaseAccessor** 메서드를 호출하여 점유한 메모리를 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-139">Whenever the consumer finishes using an accessor, the consumer must call the **ReleaseAccessor** method to release the memory it holds.</span></span>  
  
     <span data-ttu-id="1bfeb-140">소비자는 **ICommand::Execute**와 같은 메서드를 호출할 때 접근자에 대한 핸들과 버퍼 자체에 대한 포인터를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-140">When the consumer calls a method, such as **ICommand::Execute**, it passes the handle to an accessor and a pointer to a buffer itself.</span></span> <span data-ttu-id="1bfeb-141">공급자는 이 접근자를 사용하여 버퍼에 포함된 데이터를 전송할 방법을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-141">The provider uses this accessor to determine how to transfer the data contained in the buffer.</span></span>  
  
4.  <span data-ttu-id="1bfeb-142">DBPARAMS 구조를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-142">Fill in the DBPARAMS structure.</span></span> <span data-ttu-id="1bfeb-143">입력 매개 변수 값이 읽히고 출력 매개 변수 값이 기록되는 소비자 변수는 런타임에 DBPARAMS 구조로 **ICommand::Execute**에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-143">The consumer variables from which input parameter values are taken and to which output parameter values are written are passed at run time to **ICommand::Execute** in the DBPARAMS structure.</span></span> <span data-ttu-id="1bfeb-144">DBPARAMS 구조에는 다음 3개의 요소가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-144">The DBPARAMS structure includes three elements:</span></span>  
  
    -   <span data-ttu-id="1bfeb-145">접근자 핸들에 의해 지정된 바인딩에 따라 공급자가 입력 매개 변수 데이터를 가져오고 출력 매개 변수 데이터를 반환하는 버퍼에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="1bfeb-145">A pointer to the buffer from which the provider retrieves input parameter data and to which the provider returns output parameter data, according to the bindings specified by the accessor handle.</span></span>  
  
    -   <span data-ttu-id="1bfeb-146">버퍼에 있는 매개 변수 집합의 수</span><span class="sxs-lookup"><span data-stu-id="1bfeb-146">The number of sets of parameters in the buffer.</span></span>  
  
    -   <span data-ttu-id="1bfeb-147">3단계에서 만든 접근자 핸들</span><span class="sxs-lookup"><span data-stu-id="1bfeb-147">The accessor handle created in Step 3.</span></span>  
  
5.  <span data-ttu-id="1bfeb-148">**ICommand::Execute**를 사용하여 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-148">Execute the command by using **ICommand::Execute**.</span></span>  
  
## <a name="methods-of-calling-a-stored-procedure"></a><span data-ttu-id="1bfeb-149">저장 프로시저 호출 방법</span><span class="sxs-lookup"><span data-stu-id="1bfeb-149">Methods of Calling a Stored Procedure</span></span>  
 <span data-ttu-id="1bfeb-150">에서 저장 프로시저를 실행할 때 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 다음을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-150">When executing a stored procedure in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports the:</span></span>  
  
-   <span data-ttu-id="1bfeb-151">ODBC CALL 이스케이프 시퀀스</span><span class="sxs-lookup"><span data-stu-id="1bfeb-151">ODBC CALL escape sequence.</span></span>  
  
-   <span data-ttu-id="1bfeb-152">RPC(원격 프로시저 호출) 이스케이프 시퀀스</span><span class="sxs-lookup"><span data-stu-id="1bfeb-152">Remote procedure call (RPC) escape sequence.</span></span>  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="1bfeb-153">EXECUTE 문</span><span class="sxs-lookup"><span data-stu-id="1bfeb-153">EXECUTE statement.</span></span>  
  
### <a name="odbc-call-escape-sequence"></a><span data-ttu-id="1bfeb-154">ODBC CALL 이스케이프 시퀀스</span><span class="sxs-lookup"><span data-stu-id="1bfeb-154">ODBC CALL Escape Sequence</span></span>  
 <span data-ttu-id="1bfeb-155">매개 변수 정보를 알 경우 **ICommandWithParameters::SetParameterInfo** 메서드를 호출하여 공급자에게 매개 변수를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-155">If you know parameter information, call **ICommandWithParameters::SetParameterInfo** method to describe the parameters to the provider.</span></span> <span data-ttu-id="1bfeb-156">그렇지 않은 경우 저장 프로시저 호출에 ODBC CALL 구문을 사용하면 공급자는 도우미 함수를 호출하여 저장 프로시저 매개 변수 정보를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-156">Otherwise, when the ODBC CALL syntax is used in calling a stored procedure, the provider calls a helper function to find the stored procedure parameter information.</span></span>  
  
 <span data-ttu-id="1bfeb-157">매개 변수 정보(매개 변수 메타데이터)가 확실하지 않을 경우에는 ODBC CALL 구문을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-157">If you are not sure about the parameter information (parameter metadata), ODBC CALL syntax is recommended.</span></span>  
  
 <span data-ttu-id="1bfeb-158">ODBC CALL 이스케이프 시퀀스를 사용한 프로시저 호출의 일반적인 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-158">The general syntax for calling a procedure by using the ODBC CALL escape sequence is:</span></span>  
  
 <span data-ttu-id="1bfeb-159">{[**? =**]**call**_procedure_name_[**(**[*parameter*] [**,**[*parameter*]] ... **)**]}</span><span class="sxs-lookup"><span data-stu-id="1bfeb-159">{[**?=**]**call**_procedure_name_[**(**[*parameter*][**,**[*parameter*]]...**)**]}</span></span>  
  
 <span data-ttu-id="1bfeb-160">예:</span><span class="sxs-lookup"><span data-stu-id="1bfeb-160">For example:</span></span>  
  
```  
{call SalesByCategory('Produce', '1995')}  
```  
  
### <a name="rpc-escape-sequence"></a><span data-ttu-id="1bfeb-161">RPC 이스케이프 시퀀스</span><span class="sxs-lookup"><span data-stu-id="1bfeb-161">RPC Escape Sequence</span></span>  
 <span data-ttu-id="1bfeb-162">RPC 이스케이프 시퀀스는 ODBC CALL의 저장 프로시저 호출 구문과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-162">The RPC escape sequence is similar to the ODBC CALL syntax of calling a stored procedure.</span></span> <span data-ttu-id="1bfeb-163">프로시저를 여러 번 호출한다면 저장 프로시저를 호출하는 3가지 방법 중 RPC 이스케이프 시퀀스가 가장 높은 성능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-163">If you will call the procedure multiple times, the RPC escape sequence provides most optimal performance among the three methods of calling a stored procedure.</span></span>  
  
 <span data-ttu-id="1bfeb-164">RPC 이스케이프 시퀀스를 사용하여 저장 프로시저를 실행할 경우 공급자는 ODBC CALL 구문에서와는 달리 매개 변수 정보를 확인하기 위한 어떠한 도우미 함수도 호출하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-164">When the RPC escape sequence is used to execute a stored procedure, the provider does not call any helper function to determine the parameter information (as it does in the case of ODBC CALL syntax).</span></span> <span data-ttu-id="1bfeb-165">RPC 구문은 ODBC CALL 구문보다 간단하므로 명령이 구문 분석되는 시간이 더 빠르고 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-165">The RPC syntax is simpler than the ODBC CALL syntax, so the command is parsed faster, improving performance.</span></span> <span data-ttu-id="1bfeb-166">이 경우 **ICommandWithParameters::SetParameterInfo**를 실행하여 매개 변수 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-166">In this case, you need to provide the parameter information by executing **ICommandWithParameters::SetParameterInfo**.</span></span>  
  
 <span data-ttu-id="1bfeb-167">RPC 이스케이프 시퀀스에서는 반환 값이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-167">The RPC escape sequence requires you to have a return value.</span></span> <span data-ttu-id="1bfeb-168">저장 프로시저가 값을 반환하지 않으면 서버는 기본적으로 0을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-168">If the stored procedure does not return a value, the server returns a 0 by default.</span></span> <span data-ttu-id="1bfeb-169">또한 저장 프로시저에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 커서를 열 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-169">In addition, you cannot open a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cursor on the stored procedure.</span></span> <span data-ttu-id="1bfeb-170">저장 프로시저는 암시적으로 준비되며 **ICommandPrepare::Prepare**에 대한 호출은 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-170">The stored procedure is prepared implicitly and the call to **ICommandPrepare::Prepare** will fail.</span></span> <span data-ttu-id="1bfeb-171">RPC 호출을 준비할 수 없기 때문에 열 메타데이터를 쿼리할 수 없습니다. 따라서 IColumnsInfo::GetColumnInfo 및 IColumnsRowset::GetColumnsRowset에서 DB_E_NOTPREPARED를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-171">Because of the inability to prepare an RPC call, you can not query column metadata; IColumnsInfo::GetColumnInfo and IColumnsRowset::GetColumnsRowset will return DB_E_NOTPREPARED.</span></span>  
  
 <span data-ttu-id="1bfeb-172">모든 매개 변수 메타데이터를 알고 있다면 RPC 이스케이프 시퀀스를 사용하여 저장 프로시저를 실행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-172">If you know all the parameter metadata, RPC escape sequence is the recommended way to execute stored procedures.</span></span>  
  
 <span data-ttu-id="1bfeb-173">다음은 RPC 이스케이프 시퀀스를 사용한 저장 프로시저 호출의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-173">This is an example of RPC escape sequence for calling a stored procedure:</span></span>  
  
```  
{rpc SalesByCategory}  
```  
  
 <span data-ttu-id="1bfeb-174">RPC 이스케이프 시퀀스를 보여주는 샘플 애플리케이션은 [&#40;RPC 구문을 사용하여&#41; 저장 프로시저를 실행하고 반환 코드 및 출력 매개 변수를 처리&#40;OLE DB&#41;](../../native-client-ole-db-how-to/results/execute-stored-procedure-with-rpc-and-process-output.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-174">For a sample application that demonstrates an RPC escape sequence, see [Execute a Stored Procedure &#40;Using RPC Syntax&#41; and Process Return Codes and Output Parameters &#40;OLE DB&#41;](../../native-client-ole-db-how-to/results/execute-stored-procedure-with-rpc-and-process-output.md).</span></span>  
  
### <a name="transact-sql-execute-statement"></a><span data-ttu-id="1bfeb-175">Transact-SQL EXECUTE 문</span><span class="sxs-lookup"><span data-stu-id="1bfeb-175">Transact-SQL EXECUTE Statement</span></span>  
 <span data-ttu-id="1bfeb-176">저장 프로시저를 호출할 때는 [EXECUTE](/sql/t-sql/language-elements/execute-transact-sql) 문보다 ODBC CALL 이스케이프 시퀀스와 RPC 이스케이프 시퀀스가 더 일반적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-176">The ODBC CALL escape sequence and the RPC escape sequence are the preferred methods for calling a stored procedure rather than the [EXECUTE](/sql/t-sql/language-elements/execute-transact-sql) statement.</span></span> <span data-ttu-id="1bfeb-177">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는의 RPC 메커니즘을 사용 하 여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 명령 처리를 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-177">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider uses the RPC mechanism of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to optimize command processing.</span></span> <span data-ttu-id="1bfeb-178">이 RPC 프로토콜은 서버에서 수행되는 매개 변수 처리와 문 구문 분석의 대부분을 제거하여 성능을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-178">This RPC protocol increases performance by eliminating much of the parameter processing and statement parsing done on the server.</span></span>  
  
 <span data-ttu-id="1bfeb-179">다음은 [!INCLUDE[tsql](../../../includes/tsql-md.md)] **EXECUTE** 문의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="1bfeb-179">This is an example of the [!INCLUDE[tsql](../../../includes/tsql-md.md)] **EXECUTE** statement:</span></span>  
  
```  
EXECUTE SalesByCategory 'Produce', '1995'  
```  
  
## <a name="see-also"></a><span data-ttu-id="1bfeb-180">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1bfeb-180">See Also</span></span>  
 [<span data-ttu-id="1bfeb-181">저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="1bfeb-181">Stored Procedures</span></span>](stored-procedures.md)  
  
  
