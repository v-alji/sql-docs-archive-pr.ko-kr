---
title: 오류 인터페이스의 정보 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error interfaces
- ISQLErrorInfo interface
- errors [OLE DB], error interfaces
ms.assetid: 4620f03f-1193-43e7-ba19-ad022737d300
author: rothja
ms.author: jroth
ms.openlocfilehash: e9859ccbd804ba15685d84b98cbe74d4b096d98c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653840"
---
# <a name="information-in-error-interfaces"></a><span data-ttu-id="d7ca6-102">오류 인터페이스의 정보</span><span class="sxs-lookup"><span data-stu-id="d7ca6-102">Information in Error Interfaces</span></span>
  <span data-ttu-id="d7ca6-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 OLE DB 정의 오류 인터페이스 **IErrorInfo**, **Ierrorrecords**및 **ISQLErrorInfo**에 일부 오류 및 상태 정보를 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ca6-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider reports some error and status information in the OLE DB-defined error interfaces **IErrorInfo**, **IErrorRecords**, and **ISQLErrorInfo**.</span></span>  
  
 <span data-ttu-id="d7ca6-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 다음과 같이 **IErrorInfo** 멤버 함수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ca6-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports **IErrorInfo** member functions as follows.</span></span>  
  
|<span data-ttu-id="d7ca6-105">멤버 함수</span><span class="sxs-lookup"><span data-stu-id="d7ca6-105">Member function</span></span>|<span data-ttu-id="d7ca6-106">Description</span><span class="sxs-lookup"><span data-stu-id="d7ca6-106">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="d7ca6-107">**GetDescription**</span><span class="sxs-lookup"><span data-stu-id="d7ca6-107">**GetDescription**</span></span>|<span data-ttu-id="d7ca6-108">설명적인 오류 메시지 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="d7ca6-108">Descriptive error message string.</span></span>|  
|<span data-ttu-id="d7ca6-109">**GetGUID**</span><span class="sxs-lookup"><span data-stu-id="d7ca6-109">**GetGUID**</span></span>|<span data-ttu-id="d7ca6-110">오류를 정의한 인터페이스의 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="d7ca6-110">GUID of the interface that defined the error.</span></span>|  
|<span data-ttu-id="d7ca6-111">**GetHelpContext**</span><span class="sxs-lookup"><span data-stu-id="d7ca6-111">**GetHelpContext**</span></span>|<span data-ttu-id="d7ca6-112">지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ca6-112">Not supported.</span></span> <span data-ttu-id="d7ca6-113">항상 0을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ca6-113">Always returns zero.</span></span>|  
|<span data-ttu-id="d7ca6-114">**GetHelpFile**</span><span class="sxs-lookup"><span data-stu-id="d7ca6-114">**GetHelpFile**</span></span>|<span data-ttu-id="d7ca6-115">지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ca6-115">Not supported.</span></span> <span data-ttu-id="d7ca6-116">항상 NULL을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ca6-116">Always returns NULL.</span></span>|  
|<span data-ttu-id="d7ca6-117">**GetSource**</span><span class="sxs-lookup"><span data-stu-id="d7ca6-117">**GetSource**</span></span>|<span data-ttu-id="d7ca6-118">"Microsoft SQL Server Native Client" 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="d7ca6-118">String "Microsoft SQL Server Native Client".</span></span>|  
  
 <span data-ttu-id="d7ca6-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 다음과 같이 소비자가 사용할 수 있는 **Ierrorrecords** 멤버 함수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ca6-119">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports consumer-available **IErrorRecords** member functions as follows.</span></span>  
  
|<span data-ttu-id="d7ca6-120">멤버 함수</span><span class="sxs-lookup"><span data-stu-id="d7ca6-120">Member function</span></span>|<span data-ttu-id="d7ca6-121">Description</span><span class="sxs-lookup"><span data-stu-id="d7ca6-121">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="d7ca6-122">**GetBasicErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="d7ca6-122">**GetBasicErrorInfo**</span></span>|<span data-ttu-id="d7ca6-123">ERRORINFO 구조에 오류에 대한 기본 정보를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="d7ca6-123">Fills an ERRORINFO structure with basic information about an error.</span></span> <span data-ttu-id="d7ca6-124">ERRORINFO 구조에는 오류에 대한 HRESULT 반환 값을 식별하는 멤버와 오류가 적용되는 공급자 및 인터페이스가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7ca6-124">An ERRORINFO structure contains members that identify the HRESULT return value for the error, and the provider and interface to which the error applies.</span></span>|  
|<span data-ttu-id="d7ca6-125">**GetCustomErrorObject**</span><span class="sxs-lookup"><span data-stu-id="d7ca6-125">**GetCustomErrorObject**</span></span>|<span data-ttu-id="d7ca6-126">**ISQLErrorInfo** 및 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) 인터페이스에 대한 참조를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ca6-126">Returns a reference on interfaces **ISQLErrorInfo,** and [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md).</span></span>|  
|<span data-ttu-id="d7ca6-127">**GetErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="d7ca6-127">**GetErrorInfo**</span></span>|<span data-ttu-id="d7ca6-128">**IErrorInfo** 인터페이스에 대한 참조를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ca6-128">Returns a reference on an **IErrorInfo** interface.</span></span>|  
|<span data-ttu-id="d7ca6-129">**GetErrorParameters**</span><span class="sxs-lookup"><span data-stu-id="d7ca6-129">**GetErrorParameters**</span></span>|<span data-ttu-id="d7ca6-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 **geterrorparameters**를 통해 소비자에 게 매개 변수를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ca6-130">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not return parameters to the consumer through **GetErrorParameters**.</span></span>|  
|<span data-ttu-id="d7ca6-131">**GetRecordCount**</span><span class="sxs-lookup"><span data-stu-id="d7ca6-131">**GetRecordCount**</span></span>|<span data-ttu-id="d7ca6-132">사용할 수 있는 오류 레코드 수입니다.</span><span class="sxs-lookup"><span data-stu-id="d7ca6-132">Count of error records available.</span></span>|  
  
 <span data-ttu-id="d7ca6-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 다음과 같이 **ISQLErrorInfo:: GetSQLInfo** 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ca6-133">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports **ISQLErrorInfo::GetSQLInfo** parameters as follows.</span></span>  
  
|<span data-ttu-id="d7ca6-134">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d7ca6-134">Parameter</span></span>|<span data-ttu-id="d7ca6-135">Description</span><span class="sxs-lookup"><span data-stu-id="d7ca6-135">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d7ca6-136">*pbstrSQLState*</span><span class="sxs-lookup"><span data-stu-id="d7ca6-136">*pbstrSQLState*</span></span>|<span data-ttu-id="d7ca6-137">오류의 SQLSTATE 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ca6-137">Returns a SQLSTATE value for the error.</span></span> <span data-ttu-id="d7ca6-138">SQLSTATE 값은 SQL-92, ODBC 및 ISO SQL, API 사양에서 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7ca6-138">SQLSTATE values are defined in the SQL-92, ODBC and ISO SQL, and API specifications.</span></span> <span data-ttu-id="d7ca6-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 구현 별 SQLSTATE 값을 정의 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ca6-139">Neither [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nor the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defined implementation-specific SQLSTATE values.</span></span>|  
|<span data-ttu-id="d7ca6-140">*plNativeError*</span><span class="sxs-lookup"><span data-stu-id="d7ca6-140">*plNativeError*</span></span>|<span data-ttu-id="d7ca6-141">사용 가능한 경우 **master.dbo.sysmessages**의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 번호를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ca6-141">Returns the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error number from **master.dbo.sysmessages** when available.</span></span> <span data-ttu-id="d7ca6-142">Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB 공급자 데이터 원본을 성공적으로 초기화 한 후 네이티브 오류를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ca6-142">Native errors are available after a successful attempt to initialize a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider data source.</span></span> <span data-ttu-id="d7ca6-143">시도 전에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 항상 0을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ca6-143">Prior to the attempt, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider always returns zero.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d7ca6-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d7ca6-144">See Also</span></span>  
 [<span data-ttu-id="d7ca6-145">Errors</span><span class="sxs-lookup"><span data-stu-id="d7ca6-145">Errors</span></span>](errors.md)  
  
  
