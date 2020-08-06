---
title: SQL Server 오류 세부 정보 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], error details
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error details
- ISQLServerErrorInfo interface
ms.assetid: 51500ee3-3d78-47ec-b90f-ebfc55642e06
author: rothja
ms.author: jroth
ms.openlocfilehash: 4c03cf62dd274f9bcca213d33fb8969b26c9d980
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653835"
---
# <a name="sql-server-error-detail"></a><span data-ttu-id="d1728-102">SQL Server 오류 세부 정보</span><span class="sxs-lookup"><span data-stu-id="d1728-102">SQL Server Error Detail</span></span>
  <span data-ttu-id="d1728-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 공급자별 오류 인터페이스 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1728-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the provider-specific error interface [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md).</span></span> <span data-ttu-id="d1728-104">이 인터페이스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류에 대한 세부 정보를 반환하며 명령 실행이나 행 집합 작업이 실패할 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="d1728-104">The interface returns more detail about a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error and is valuable when command execution or rowset operations fail.</span></span>  
  
 <span data-ttu-id="d1728-105">**ISQLServerErrorInfo** 인터페이스에 액세스하는 두 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1728-105">There are two ways to obtain access to **ISQLServerErrorInfo** interface.</span></span>  
  
 <span data-ttu-id="d1728-106">소비자는 다음 코드 예제와 같이 **IErrorRecords::GetCustomerErrorObject**를 호출하여 **ISQLServerErrorInfo** 포인터를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1728-106">The consumer may call **IErrorRecords::GetCustomerErrorObject** to obtain an **ISQLServerErrorInfo** pointer, as shown in the following code sample.</span></span> <span data-ttu-id="d1728-107">(**ISQLErrorInfo**를 얻을 필요는 없습니다.) **ISQLErrorInfo** 및 **ISQLServerErrorInfo**는 모두 사용자 지정 OLE DB 오류 개체이고, **ISQLServerErrorInfo**는 프로시저 이름 및 줄 번호와 같은 세부 정보를 비롯하여 서버 오류 정보를 얻기 위해 사용하는 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="d1728-107">(There is no need to obtain **ISQLErrorInfo.**) Both **ISQLErrorInfo** and **ISQLServerErrorInfo** are custom OLE DB error objects, with **ISQLServerErrorInfo** being the interface to use to obtain information of server errors, including such details as procedure name and line numbers.</span></span>  
  
```  
// Get the SQL Server custom error object.  
if(FAILED(hr=pIErrorRecords->GetCustomErrorObject(  
   nRec, IID_ISQLServerErrorInfo,  
   (IUnknown**)&pISQLServerErrorErrorInfo)))  
```  
  
 <span data-ttu-id="d1728-108">**ISQLServerErrorInfo** 포인터를 가져오는 다른 방법은 이미 얻은 **ISQLErrorInfo** 포인터에서 **QueryInterface** 메서드를 호출하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d1728-108">Another way to get an **ISQLServerErrorInfo** pointer is to call the **QueryInterface** method on an already-obtained **ISQLErrorInfo** pointer.</span></span> <span data-ttu-id="d1728-109">**ISQLServerErrorInfo**에는 **ISQLErrorInfo**에서 사용할 수 있는 정보의 상위 집합이 포함되어 있으므로 **GetCustomerErrorObject**를 통해 **ISQLServerErrorInfo**로 직접 이동하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d1728-109">Note that because **ISQLServerErrorInfo** contains a superset of the information available from **ISQLErrorInfo**, it makes sense to go directly to **ISQLServerErrorInfo** through **GetCustomerErrorObject**.</span></span>  
  
 <span data-ttu-id="d1728-110">**ISQLServerErrorInfo** 인터페이스는 멤버 함수 [ISQLServerErrorInfo::GetErrorInfo](../native-client-ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md)를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="d1728-110">The **ISQLServerErrorInfo** interface exposes one member function, [ISQLServerErrorInfo::GetErrorInfo](../native-client-ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md).</span></span> <span data-ttu-id="d1728-111">이 함수는 SSERRORINFO 구조에 대한 포인터와 문자열 버퍼에 대한 포인터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d1728-111">The function returns a pointer to an SSERRORINFO structure and a pointer to a string buffer.</span></span> <span data-ttu-id="d1728-112">두 포인터는 모두 소비자가 **IMalloc::Free** 메서드를 사용하여 할당 취소해야 하는 메모리를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="d1728-112">Both pointers reference memory the consumer must deallocate by using the **IMalloc::Free** method.</span></span>  
  
 <span data-ttu-id="d1728-113">SSERRORINFO 구조 멤버는 소비자에 의해 다음과 같이 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1728-113">SSERRORINFO structure members are interpreted by the consumer as follows.</span></span>  
  
|<span data-ttu-id="d1728-114">멤버</span><span class="sxs-lookup"><span data-stu-id="d1728-114">Member</span></span>|<span data-ttu-id="d1728-115">설명</span><span class="sxs-lookup"><span data-stu-id="d1728-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="d1728-116">*pwszMessage*</span><span class="sxs-lookup"><span data-stu-id="d1728-116">*pwszMessage*</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d1728-117">오류 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="d1728-117">error message.</span></span> <span data-ttu-id="d1728-118">**IErrorInfo::GetDescription**에 반환된 문자열과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d1728-118">Identical to the string returned in **IErrorInfo::GetDescription**.</span></span>|  
|<span data-ttu-id="d1728-119">*pwszServer*</span><span class="sxs-lookup"><span data-stu-id="d1728-119">*pwszServer*</span></span>|<span data-ttu-id="d1728-120">세션에 대한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="d1728-120">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the session.</span></span>|  
|<span data-ttu-id="d1728-121">*pwszProcedure*</span><span class="sxs-lookup"><span data-stu-id="d1728-121">*pwszProcedure*</span></span>|<span data-ttu-id="d1728-122">해당되는 경우 오류가 발생한 프로시저의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="d1728-122">If appropriate, the name of the procedure in which the error originated.</span></span> <span data-ttu-id="d1728-123">그렇지 않으면 빈 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="d1728-123">An empty string otherwise.</span></span>|  
|<span data-ttu-id="d1728-124">*lNative*</span><span class="sxs-lookup"><span data-stu-id="d1728-124">*lNative*</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="d1728-125">원시 오류 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="d1728-125">native error number.</span></span> <span data-ttu-id="d1728-126">**ISQLErrorInfo::GetSQLInfo**의 *plNativeError* 매개 변수에 반환된 값과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d1728-126">Identical to the value returned in the *plNativeError* parameter of **ISQLErrorInfo::GetSQLInfo**.</span></span>|  
|<span data-ttu-id="d1728-127">*bState*</span><span class="sxs-lookup"><span data-stu-id="d1728-127">*bState*</span></span>|<span data-ttu-id="d1728-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 메시지의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="d1728-128">State of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error message.</span></span>|  
|<span data-ttu-id="d1728-129">*bClass*</span><span class="sxs-lookup"><span data-stu-id="d1728-129">*bClass*</span></span>|<span data-ttu-id="d1728-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 메시지의 심각도입니다.</span><span class="sxs-lookup"><span data-stu-id="d1728-130">Severity of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error message.</span></span>|  
|<span data-ttu-id="d1728-131">*wLineNumber*</span><span class="sxs-lookup"><span data-stu-id="d1728-131">*wLineNumber*</span></span>|<span data-ttu-id="d1728-132">해당되는 경우 오류가 발생한 저장 프로시저의 줄 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="d1728-132">When applicable, the line number of a stored procedure on which the error occurred.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1728-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d1728-133">See Also</span></span>  
 <span data-ttu-id="d1728-134">[오류](errors.md) </span><span class="sxs-lookup"><span data-stu-id="d1728-134">[Errors](errors.md) </span></span>  
 [<span data-ttu-id="d1728-135">RAISERROR&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d1728-135">RAISERROR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  
