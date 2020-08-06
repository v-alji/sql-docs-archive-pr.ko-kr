---
title: 명령 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- parameters [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, parameters
- SQL Server Native Client OLE DB provider, commands
- parameters [SQL Server Native Client], OLE DB
- commands [OLE DB]
ms.assetid: 072ead49-ebaf-41eb-9a0f-613e9d990f26
author: rothja
ms.author: jroth
ms.openlocfilehash: 6c00250bac3504ffb06b37aeb8c4e7eaf583c987
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661651"
---
# <a name="command-parameters"></a><span data-ttu-id="0bb25-102">명령 매개 변수</span><span class="sxs-lookup"><span data-stu-id="0bb25-102">Command Parameters</span></span>
  <span data-ttu-id="0bb25-103">매개 변수는 명령 텍스트에서 물음표(?) 문자로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0bb25-103">Parameters are marked in command text with the question mark character.</span></span> <span data-ttu-id="0bb25-104">예를 들어 다음 SQL 문은 한 개의 입력 매개 변수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb25-104">For example, the following SQL statement is marked for a single input parameter:</span></span>  
  
```  
{call SalesByCategory('Produce', ?)}  
```  
  
 <span data-ttu-id="0bb25-105">네트워크 트래픽을 줄여 성능을 향상 시키기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 명령을 실행 하기 전에 **ICommandWithParameters:: GetParameterInfo** 또는 **ICommandPrepare::P repare** 를 호출 하지 않으면 Native Client OLE DB 공급자가 자동으로 매개 변수 정보를 파생 시 키 지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0bb25-105">To improve performance by reducing network traffic, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not automatically derive parameter information unless **ICommandWithParameters::GetParameterInfo** or **ICommandPrepare::Prepare** is called before executing a command.</span></span> <span data-ttu-id="0bb25-106">즉, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 다음을 자동으로 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0bb25-106">This means that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not automatically:</span></span>  
  
-   <span data-ttu-id="0bb25-107">**ICommandWithParameters::SetParameterInfo**에 지정된 데이터 형식이 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb25-107">Verify the correctness of the data type specified with **ICommandWithParameters::SetParameterInfo**.</span></span>  
  
-   <span data-ttu-id="0bb25-108">접근자 바인딩 정보에 지정된 DBTYPE에서 매개 변수의 올바른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식으로 매핑</span><span class="sxs-lookup"><span data-stu-id="0bb25-108">Map from the DBTYPE specified in the accessor binding information to the correct [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type for the parameter.</span></span>  
  
 <span data-ttu-id="0bb25-109">애플리케이션에서 매개 변수의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식과 호환되지 않는 데이터 형식을 지정하면 이러한 방법 중 하나에서 오류나 전체 자릿수 손실이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bb25-109">Applications will receive possible errors or loss of precision with either of these methods if they specify data types that are not compatible with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type of the parameter.</span></span>  
  
 <span data-ttu-id="0bb25-110">이 문제가 발생하지 않게 하려면 애플리케이션에서 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb25-110">To ensure this does not happen, the application should:</span></span>  
  
-   <span data-ttu-id="0bb25-111">**ICommandWithParameters::SetParameterInfo**를 하드 코딩할 경우 *pwszDataSourceType*이 매개 변수의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식과 일치하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb25-111">Ensure that *pwszDataSourceType* matches the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type for the parameter if hard-coding **ICommandWithParameters::SetParameterInfo**.</span></span>  
  
-   <span data-ttu-id="0bb25-112">접근자를 하드 코딩할 경우 매개 변수에 바인딩되는 DBTYPE 값이 매개 변수의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식과 같은 형식인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb25-112">Ensure that the DBTYPE value being bound to the parameter is of the same type as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type for the parameter if hard-coding an accessor.</span></span>  
  
-   <span data-ttu-id="0bb25-113">공급자가 매개 변수의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 동적으로 얻을 수 있도록 **ICommandWithParameters::GetParameterInfo**를 호출하는 애플리케이션을 코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb25-113">Code the application to call **ICommandWithParameters::GetParameterInfo** so that the provider can obtain the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types of the parameters dynamically.</span></span> <span data-ttu-id="0bb25-114">이로 인해 서버로의 네트워크 왕복이 추가로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb25-114">Note that this causes an extra network round trip to the server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0bb25-115">공급자에서는 FROM 절이 포함된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UPDATE 또는 DELETE 문, 매개 변수를 포함하는 하위 쿼리에 종속된 SQL 문, 비교, like 또는 한정된 조건자의 두 식이나 매개 변수 중 하나가 함수의 매개 변수인 쿼리에 매개 변수 표식이 포함된 SQL 문에 대해 **ICommandWithParameters::GetParameterInfo**를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0bb25-115">The provider does not support calling **ICommandWithParameters::GetParameterInfo** for any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UPDATE or DELETE statement containing a FROM clause; for any SQL statement depending on a subquery containing parameters; for SQL statements containing parameter markers in both expressions of a comparison, like, or quantified predicate; or queries where one of the parameters is a parameter to a function.</span></span> <span data-ttu-id="0bb25-116">또한 SQL 문을 일괄 처리할 경우 공급자에서는 일괄 처리의 첫 번째 문 다음에 나오는 문의 매개 변수 표식에 대해 **ICommandWithParameters::GetParameterInfo**를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0bb25-116">When processing a batch of SQL statements, the provider also does not support calling **ICommandWithParameters::GetParameterInfo** for parameter markers in statements after the first statement in the batch.</span></span> <span data-ttu-id="0bb25-117">주석(/\* \*/)이 [!INCLUDE[tsql](../../includes/tsql-md.md)] 명령에 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0bb25-117">Comments (/\* \*/) are not allowed in the [!INCLUDE[tsql](../../includes/tsql-md.md)] command.</span></span>  
  
 <span data-ttu-id="0bb25-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 SQL 문 명령에서 입력 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb25-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports input parameters in SQL statement commands.</span></span> <span data-ttu-id="0bb25-119">프로시저 호출 명령에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 입력, 출력 및 입/출력 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb25-119">On procedure-call commands, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports input, output, and input/output parameters.</span></span> <span data-ttu-id="0bb25-120">실행 시(반환되는 행 집합이 없는 경우에만 해당) 또는 반환된 행 집합이 애플리케이션에서 모두 사용된 경우에 출력 매개 변수 값이 애플리케이션에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="0bb25-120">Output parameter values are returned to the application either on execution (only if there are no rowsets returned) or when all returned rowsets are exhausted by the application.</span></span> <span data-ttu-id="0bb25-121">반환된 값이 유효한지 확인하려면 **IMultipleResults**를 사용하여 행 집합을 강제로 소비합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb25-121">To ensure that returned values are valid, use **IMultipleResults** to force rowset consumption.</span></span>  
  
 <span data-ttu-id="0bb25-122">저장 프로시저 매개 변수의 이름은 DBPARAMBINDINFO 구조에서 지정하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0bb25-122">The names of stored procedure parameters need not be specified in a DBPARAMBINDINFO structure.</span></span> <span data-ttu-id="0bb25-123">*PwszName* 멤버의 값에 NULL을 사용 하 여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자가 매개 변수 이름을 무시 하 고 **ICommandWithParameters:: SetParameterInfo**의 *rgParamOrdinals* 멤버에 지정 된 서 수만 사용 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb25-123">Use NULL for the value of the *pwszName* member to indicate that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider should ignore the parameter name and use only the ordinal specified in the *rgParamOrdinals* member of **ICommandWithParameters::SetParameterInfo**.</span></span> <span data-ttu-id="0bb25-124">명령 텍스트에 명명된 매개 변수와 명명되지 않은 매개 변수가 모두 포함된 경우 모든 명명되지 않은 매개 변수를 명명된 매개 변수보다 먼저 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb25-124">If the command text contains both named and unnamed parameters, all of the unnamed parameters must be specified before any named parameters.</span></span>  
  
 <span data-ttu-id="0bb25-125">저장 프로시저 매개 변수의 이름이 지정 된 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 이름을 확인 하 여 유효한 지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb25-125">If the name of a stored procedure parameter is specified, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider checks the name to ensure that it is valid.</span></span> <span data-ttu-id="0bb25-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 소비자 로부터 잘못 된 매개 변수 이름을 받을 때 오류를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb25-126">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns an error when it receives an erroneous parameter name from the consumer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0bb25-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]XML 및 UDT (사용자 정의 형식)에 대 한 지원을 노출 하기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 새 [ISSCommandWithParameters](../native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md) 인터페이스를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb25-127">To expose support for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML and user-defined types (UDT), the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements a new [ISSCommandWithParameters](../native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md) interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bb25-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0bb25-128">See Also</span></span>  
 [<span data-ttu-id="0bb25-129">명령</span><span class="sxs-lookup"><span data-stu-id="0bb25-129">Commands</span></span>](commands.md)  
  
  
