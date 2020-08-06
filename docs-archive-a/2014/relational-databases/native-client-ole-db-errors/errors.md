---
title: 오류 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- OLE/COM errors
- errors [OLE DB]
- OLE DB error handling, about error handling
- OLE DB error handling
ms.assetid: bd0612f4-96ef-4919-b0f9-b5447210fe93
author: rothja
ms.author: jroth
ms.openlocfilehash: 0560a31b60a10e278f621aa53f1c7fa038fe8039
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653844"
---
# <a name="errors"></a><span data-ttu-id="ae76b-102">오류</span><span class="sxs-lookup"><span data-stu-id="ae76b-102">Errors</span></span>
  <span data-ttu-id="ae76b-103">OLE/COM 개체는 개체 멤버 함수의 HRESULT 반환 코드를 통해 오류를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="ae76b-103">OLE/COM objects report errors through the HRESULT return code of object member functions.</span></span> <span data-ttu-id="ae76b-104">OLE/COM HRESULT는 비트 압축 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="ae76b-104">An OLE/COM HRESULT is a bit-packed structure.</span></span> <span data-ttu-id="ae76b-105">OLE는 구조 멤버를 역참조하는 매크로를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ae76b-105">OLE provides macros that dereference structure members.</span></span>  
  
 <span data-ttu-id="ae76b-106">OLE/COM은 **IErrorInfo** 인터페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ae76b-106">OLE/COM specifies the **IErrorInfo** interface.</span></span> <span data-ttu-id="ae76b-107">이 인터페이스는 **GetDescription**과 같은 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ae76b-107">The interface exposes methods such as **GetDescription**.</span></span> <span data-ttu-id="ae76b-108">이 인터페이스를 사용하여 클라이언트는 OLE/COM 서버에서 오류 정보를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="ae76b-108">This allows clients to extract error details from OLE/COM servers.</span></span> <span data-ttu-id="ae76b-109">OLE DB는 단일 멤버 함수 실행에 대해 여러 개의 오류 정보 패킷 반환을 지원하기 위해 **IErrorInfo**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ae76b-109">OLE DB extends **IErrorInfo** to support the return of multiple error information packets on a single-member function execution.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="ae76b-110">에서 여러 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ae76b-110">can return multiple errors.</span></span> <span data-ttu-id="ae76b-111">애플리케이션은 ISQLErrorInfo 및 IErrorRecords를 조합한 [IMultipleResults::GetResult](https://go.microsoft.com/fwlink/?LinkId=129630)를 호출하여 한 번에 하나씩 서버 오류를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae76b-111">An application can retrieve server errors one at a time by calling [IMultipleResults::GetResult](https://go.microsoft.com/fwlink/?LinkId=129630) combined with ISQLErrorInfo and IErrorRecords.</span></span>  
  
 <span data-ttu-id="ae76b-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 OLE DB 레코드 강화 **IErrorInfo**, 사용자 지정 `ISQLErrorInfo` 및 공급자별 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) error 개체 인터페이스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae76b-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the OLE DB record-enhanced **IErrorInfo**, the custom `ISQLErrorInfo`, and the provider-specific [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) error object interfaces.</span></span>  
  
 <span data-ttu-id="ae76b-113">오류 추적에 대한 자세한 내용은 [데이터 액세스 추적](https://go.microsoft.com/fwlink/?LinkId=125805)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ae76b-113">For information about tracing errors, see [Data Access Tracing](https://go.microsoft.com/fwlink/?LinkId=125805).</span></span> <span data-ttu-id="ae76b-114">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]에 추가된 오류 추적의 향상된 기능에 대한 자세한 내용은 [확장 이벤트 로그의 진단 정보 액세스](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ae76b-114">For information about enhancements to error tracing added in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], see [Accessing Diagnostic Information in the Extended Events Log](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ae76b-115">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="ae76b-115">In This Section</span></span>  
  
-   [<span data-ttu-id="ae76b-116">반환 코드</span><span class="sxs-lookup"><span data-stu-id="ae76b-116">Return Codes</span></span>](return-codes.md)  
  
-   [<span data-ttu-id="ae76b-117">오류 인터페이스의 정보</span><span class="sxs-lookup"><span data-stu-id="ae76b-117">Information in Error Interfaces</span></span>](information-in-error-interfaces.md)  
  
-   [<span data-ttu-id="ae76b-118">SQL Server 오류 세부 정보</span><span class="sxs-lookup"><span data-stu-id="ae76b-118">SQL Server Error Detail</span></span>](sql-server-error-detail.md)  
  
-   [<span data-ttu-id="ae76b-119">오류 정보 검색</span><span class="sxs-lookup"><span data-stu-id="ae76b-119">Retrieving Error Information</span></span>](retrieving-error-information.md)  
  
-   [<span data-ttu-id="ae76b-120">SQL Server 메시지 결과</span><span class="sxs-lookup"><span data-stu-id="ae76b-120">SQL Server Message Results</span></span>](sql-server-message-results.md)  
  
## <a name="see-also"></a><span data-ttu-id="ae76b-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ae76b-121">See Also</span></span>  
 [<span data-ttu-id="ae76b-122">SQL Server Native Client&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="ae76b-122">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
