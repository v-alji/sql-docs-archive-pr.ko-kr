---
title: 바인딩 및 변환(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- conversions [OLE DB]
- bindings [OLE DB]
- OLE DB, bindings and conversions
ms.assetid: c187df58-a8c8-4c74-a76f-663abbc5f0c1
author: rothja
ms.author: jroth
ms.openlocfilehash: 95c73bdad80b5f948a45235ad208ab307fcceff3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659972"
---
# <a name="bindings-and-conversions-ole-db"></a><span data-ttu-id="6bbb9-102">바인딩 및 변환(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="6bbb9-102">Bindings and Conversions (OLE DB)</span></span>
  <span data-ttu-id="6bbb9-103">이 섹션에서는 `datetime` 값과 `datetimeoffset` 값 사이의 변환 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6bbb9-103">This section discusses how to convert between `datetime` and `datetimeoffset` values.</span></span> <span data-ttu-id="6bbb9-104">이 섹션에 설명된 변환은 OLE DB에서 이미 제공하거나 OLE DB의 일관된 확장입니다.</span><span class="sxs-lookup"><span data-stu-id="6bbb9-104">The conversions described in this section are either already provided by OLE DB or are a consistent extension of OLE DB.</span></span>  
  
 <span data-ttu-id="6bbb9-105">OLE DB에서 날짜와 시간에 대한 리터럴 및 문자열 형식은 일반적으로 ISO를 따르며 클라이언트 로캘에 종속되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6bbb9-105">The format of literals and strings for dates and times in OLE DB generally follows ISO, and is not dependent on the client locale.</span></span> <span data-ttu-id="6bbb9-106">한 가지 예외는 OLE Automation이 표준인 DBTYPE_DATE이지만</span><span class="sxs-lookup"><span data-stu-id="6bbb9-106">One exception is DBTYPE_DATE, where the standard is OLE Automation.</span></span> <span data-ttu-id="6bbb9-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client에서는 클라이언트와의 사이에 데이터가 전송되는 경우에만 형식을 변환하기 때문에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client가 애플리케이션에 의해 강제로 DBTYPE_DATE와 문자열 형식 사이를 변환하는 경우는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6bbb9-107">However, because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client only converts between types when data is transmitted to or from the client, there is no way for an application to force [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client to convert between DBTYPE_DATE and string formats.</span></span> <span data-ttu-id="6bbb9-108">이러한 경우를 제외하면 문자열에는 다음과 같은 형식이 사용됩니다. 여기서 대괄호 안의 텍스트는 선택적 요소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6bbb9-108">Otherwise, strings use the following formats (text in brackets indicates an optional element):</span></span>  
  
-   <span data-ttu-id="6bbb9-109">`datetime` 및 `datetimeoffset` 문자열의 형식</span><span class="sxs-lookup"><span data-stu-id="6bbb9-109">The format of `datetime` and `datetimeoffset` strings is:</span></span>  
  
     <span data-ttu-id="6bbb9-110">*yyyy* - *mm* - *dd*[ *hh*:*mm*:*ss*[.\* 9999999\*] [??</span><span class="sxs-lookup"><span data-stu-id="6bbb9-110">*yyyy*-*mm*-*dd*[ *hh*:*mm*:*ss*[.*9999999*][ ??</span></span> <span data-ttu-id="6bbb9-111">*hh*:*mm*]]</span><span class="sxs-lookup"><span data-stu-id="6bbb9-111">*hh*:*mm*]]</span></span>  
  
-   <span data-ttu-id="6bbb9-112">`time` 문자열의 형식</span><span class="sxs-lookup"><span data-stu-id="6bbb9-112">The format of `time` strings is:</span></span>  
  
     <span data-ttu-id="6bbb9-113">*hh*:*mm*:*ss*[.*9999999*]</span><span class="sxs-lookup"><span data-stu-id="6bbb9-113">*hh*:*mm*:*ss*[.*9999999*]</span></span>  
  
-   <span data-ttu-id="6bbb9-114">`date` 문자열의 형식</span><span class="sxs-lookup"><span data-stu-id="6bbb9-114">The format of `date` strings is:</span></span>  
  
     <span data-ttu-id="6bbb9-115">*yyyy*-*mm*-*dd*</span><span class="sxs-lookup"><span data-stu-id="6bbb9-115">*yyyy*-*mm*-*dd*</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6bbb9-116">이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client와 SQLOLEDB에서는 OLE 변환을 구현했으며 이 경우 표준 변환은 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="6bbb9-116">Earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client and SQLOLEDB implemented OLE conversions, in case standard conversions failed.</span></span> <span data-ttu-id="6bbb9-117">그 결과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 10.0 이상에서 수행하는 변환 중 일부는 OLE DB 사양과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="6bbb9-117">As a result, some conversions performed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 10.0 and later differ from the OLE DB specification.</span></span>  
  
 <span data-ttu-id="6bbb9-118">문자열에서 변환을 시작하면 공백 및 필드 너비를 보다 융통성 있게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bbb9-118">Conversions from strings allow flexibility in white space and field width.</span></span> <span data-ttu-id="6bbb9-119">자세한 내용은 [OLE DB 날짜 및 시간 기능 향상을 위한 데이터 형식 지원](data-type-support-for-ole-db-date-and-time-improvements.md)의 "데이터 형식: 문자열 및 리터럴" 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6bbb9-119">For more information, see the "Data Formats: Strings and Literals" section in [Data Type Support for OLE DB Date and Time Improvements](data-type-support-for-ole-db-date-and-time-improvements.md).</span></span>  
  
 <span data-ttu-id="6bbb9-120">일반적인 변환 규칙은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6bbb9-120">The following are general conversion rules:</span></span>  
  
-   <span data-ttu-id="6bbb9-121">문자열을 날짜/시간 형식으로 변환하면 문자열이 먼저 ISO 리터럴로 구문 분석됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bbb9-121">When a string is converted to a date/time type, the string is first parsed as an ISO literal.</span></span> <span data-ttu-id="6bbb9-122">구문 분석이 실패하면 문자열은 시간 구성 요소가 있는 OLE 날짜 리터럴로 구문 분석됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bbb9-122">If this fails, the string is parsed as an OLE date literal, which has time components.</span></span>  
  
-   <span data-ttu-id="6bbb9-123">시간 구성 요소가 없지만 받는 사람이 시간을 저장할 수 있는 경우 시간이 0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bbb9-123">If no time is present but the receiver can store time, the time is set to zero.</span></span> <span data-ttu-id="6bbb9-124">날짜 구성 요소가 없지만 받는 사람이 날짜를 저장할 수 있는 경우, ISO 변환을 사용하면 날짜가 현재 날짜로 설정되고 OLE 변환을 사용하면 날짜가 1899-12-30으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bbb9-124">If no date is present but the receiver can store a date, the date is set to the current date when ISO conversions are used and to 1899-12-30 when OLE conversions are used.</span></span>  
  
-   <span data-ttu-id="6bbb9-125">클라이언트에서 사용하는 데이터 형식에는 표준 시간대가 없지만 서버에서 표준 시간대를 저장할 수 있는 경우 클라이언트의 데이터는 클라이언트 표준 시간대를 기준으로 하는 것으로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="6bbb9-125">If no timezone is present in the data type that the client is using, but the server can store timezone, the data on the client is assumed to be in the client timezone.</span></span>  
  
-   <span data-ttu-id="6bbb9-126">서버에는 표준 시간대가 없지만 클라이언트에 표준 시간대 정보가 있는 경우 UTC 표준 시간대가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bbb9-126">If no timezone is present at the server but the client has timezone information, the UTC timezone is assumed.</span></span> <span data-ttu-id="6bbb9-127">이는 서버 동작과는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="6bbb9-127">This differs from server behavior.</span></span>  
  
-   <span data-ttu-id="6bbb9-128">시간 구성 요소가 있지만 받는 사람이 시간을 저장할 수 없는 경우 시간 구성 요소는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bbb9-128">If the time is present but the receiver cannot store time, the time component is ignored.</span></span>  
  
-   <span data-ttu-id="6bbb9-129">날짜 구성 요소가 있지만 받는 사람이 날짜를 저장할 수 없는 경우 날짜 구성 요소는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bbb9-129">If the date is present but the receiver cannot store the date, the date component is ignored.</span></span>  
  
-   <span data-ttu-id="6bbb9-130">클라이언트에서 서버로 변환할 때 초 또는 소수 자릿수 초가 잘리는 경우 DB_E_ERRORSOCCURRED가 반환되고 DBSTATUS_E_DATAOVERFLOW 상태가 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bbb9-130">If truncation of seconds or fractional seconds occurs when converting from client to server, DB_E_ERRORSOCCURRED is returned and the status DBSTATUS_E_DATAOVERFLOW is set.</span></span>  
  
-   <span data-ttu-id="6bbb9-131">서버에서 클라이언트로 변환할 때 초 또는 소수 자릿수 초가 잘리는 경우 DBSTATUS_S_TRUNCATED가 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bbb9-131">If truncation of seconds or fractional seconds occurs when converting from server to client, DBSTATUS_S_TRUNCATED is set</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6bbb9-132">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="6bbb9-132">In This Section</span></span>  
 [<span data-ttu-id="6bbb9-133">클라이언트에서 서버로 수행되는 변환</span><span class="sxs-lookup"><span data-stu-id="6bbb9-133">Conversions Performed from Client to Server</span></span>](conversions-performed-from-client-to-server.md)  
 <span data-ttu-id="6bbb9-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB를 사용하여 작성된 클라이언트 애플리케이션과 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상 간에 수행되는 날짜/시간 변환에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6bbb9-134">Describes date/time conversions performed between a client application written with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (or later).</span></span>  
  
 [<span data-ttu-id="6bbb9-135">서버에서 클라이언트로 수행되는 변환</span><span class="sxs-lookup"><span data-stu-id="6bbb9-135">Conversions Performed from Server to Client</span></span>](conversions-performed-from-server-to-client.md)  
 <span data-ttu-id="6bbb9-136">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB를 사용하여 작성된 클라이언트 애플리케이션 간에 수행되는 날짜/시간 변환에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6bbb9-136">Describes date/time conversions performed between [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (or later) and a client application written with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bbb9-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6bbb9-137">See Also</span></span>  
 [<span data-ttu-id="6bbb9-138">날짜 및 시간 기능 향상&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="6bbb9-138">Date and Time Improvements &#40;OLE DB&#41;</span></span>](date-and-time-improvements-ole-db.md)  
  
  
