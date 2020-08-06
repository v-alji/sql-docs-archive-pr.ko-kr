---
title: datetime 데이터 형식 변환 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- conversions [ODBC]
- bindings [ODBC]
- ODBC, bindings and conversions
ms.assetid: 66b9d282-c88d-40e5-93c2-fd5499a74458
author: rothja
ms.author: jroth
ms.openlocfilehash: 142e4388cb87055ddbc6faa7d5b1a92a627738c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653329"
---
# <a name="datetime-data-type-conversions-odbc"></a><span data-ttu-id="2b16d-102">datetime 데이터 형식 변환(ODBC)</span><span class="sxs-lookup"><span data-stu-id="2b16d-102">datetime Data Type Conversions (ODBC)</span></span>
  <span data-ttu-id="2b16d-103">다음 변환은 OLE DB에서 이미 정의되었거나 OLE DB의 지속적인 확장에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b16d-103">The following conversions are either already defined by ODBC or are a consistent extension of ODBC.</span></span> <span data-ttu-id="2b16d-104">각 공급자가 제공하는 변환은 공급자가 제공하는 커뮤니티에 의해 결정되며, 그 결과 공급자 간에 일치하지 않는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="2b16d-104">The conversions supplied by each provider are determined by the community served by the provider, and there are often inconsistencies between providers as a result.</span></span> <span data-ttu-id="2b16d-105">대괄호 안에 있는 값은 선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="2b16d-105">Values in square brackets are optional.</span></span>  
  
-   <span data-ttu-id="2b16d-106">datetime 문자열의 형식은 'yyyy-mm-dd[ hh:mm:ss[.9999999][ plus/minus hh:mm]]'입니다.</span><span class="sxs-lookup"><span data-stu-id="2b16d-106">The format of datetime strings is 'yyyy-mm-dd[ hh:mm:ss[.9999999][ plus/minus hh:mm]]'</span></span>  
  
-   <span data-ttu-id="2b16d-107">시간 문자열의 형식은 'hh:mm:ss[.9999999]'입니다.</span><span class="sxs-lookup"><span data-stu-id="2b16d-107">The format of time strings is 'hh:mm:ss[.9999999]'</span></span>  
  
-   <span data-ttu-id="2b16d-108">날짜 문자열의 형식은 'yyyy-mm-dd'입니다.</span><span class="sxs-lookup"><span data-stu-id="2b16d-108">The format of date strings is 'yyyy-mm-dd'</span></span>  
  
 <span data-ttu-id="2b16d-109">문자열에서 변환을 시작하면 공백 및 필드 너비를 보다 융통성 있게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b16d-109">Conversions from strings allow flexibility in white space and field width.</span></span> <span data-ttu-id="2b16d-110">자세한 내용은 [ODBC 날짜 및 시간 향상을 위한 데이터 형식 지원](data-type-support-for-odbc-date-and-time-improvements.md)의 "데이터 형식: 문자열 및 리터럴" 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2b16d-110">For more information, see the "Data Formats: Strings and Literals" section of [Data Type Support for ODBC Date and Time Improvements](data-type-support-for-odbc-date-and-time-improvements.md).</span></span>  
  
 <span data-ttu-id="2b16d-111">일반적인 변환 규칙은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2b16d-111">The following are general conversion rules:</span></span>  
  
-   <span data-ttu-id="2b16d-112">시간 구성 요소가 없지만 받는 사람이 시간을 저장할 수 있는 경우 시간이 0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b16d-112">If no time is present but the receiver can store time, the time is set to zero.</span></span>  
  
-   <span data-ttu-id="2b16d-113">날짜 구성 요소가 없지만 받는 사람이 날짜를 저장할 수 있는 경우 현재 날짜가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b16d-113">If no date is present but the receiver can store date, the current date is used.</span></span>  
  
-   <span data-ttu-id="2b16d-114">클라이언트에서 사용하는 데이터 형식에는 표준 시간대 구성 요소가 없지만 서버에서 표준 시간대를 저장할 수 있는 경우 날짜가 클라이언트 표준 시간대로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b16d-114">If no timezone is present in the data type that the client is using but the server can store timezone, the date is stored in the client timezone.</span></span> <span data-ttu-id="2b16d-115">이 동작은 서버 동작과는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="2b16d-115">Note that this differs from the server behavior.</span></span>  
  
-   <span data-ttu-id="2b16d-116">서버 유형에는 표준 시간대 구성 요소가 없지만 클라이언트 유형에 표준 시간대 구성 요소가 있는 경우 시간이 서버에 저장되기 전에 UTC로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b16d-116">If no timezone is present in the server type but the client type has a timezone, time is converted to UTC before being stored on the server.</span></span>  
  
-   <span data-ttu-id="2b16d-117">시간 구성 요소가 있지만 받는 사람이 시간을 저장할 수 없는 경우 시간 구성 요소가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b16d-117">If time is present but the receiver cannot store time, the time component is ignored.</span></span>  
  
-   <span data-ttu-id="2b16d-118">날짜 구성 요소가 있지만 받는 사람이 날짜를 저장할 수 없는 경우 날짜 구성 요소가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b16d-118">If a date is present but the receiver cannot store the date, the date component is ignored.</span></span>  
  
-   <span data-ttu-id="2b16d-119">C에서 SQL로 변환할 때 초 또는 소수 자릿수 초의 잘림이 발생하는 경우 SQLSTATE 22008 및 "Datetime 필드 오버플로" 메시지가 포함된 진단 레코드가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b16d-119">If truncation of seconds or fractional seconds occurs when converting from C to SQL, a diagnostic record is generated with SQLSTATE 22008 and the message "Datetime field overflow".</span></span>  
  
-   <span data-ttu-id="2b16d-120">SQL에서 C로 변환할 때 초 또는 소수 자릿수 초의 잘림이 발생하는 경우 SQLSTATE 01S07 및 "일부가 잘렸습니다" 메시지가 포함된 진단 레코드가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b16d-120">If truncation of seconds or fractional seconds occurs when converting from SQL to C, a diagnostic record is generated with SQLSTATE 01S07 and the message "Fractional truncation".</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2b16d-121">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="2b16d-121">In This Section</span></span>  
 [<span data-ttu-id="2b16d-122">C에서 SQL로의 변환</span><span class="sxs-lookup"><span data-stu-id="2b16d-122">Conversions from C to SQL</span></span>](datetime-data-type-conversions-from-c-to-sql.md)  
 <span data-ttu-id="2b16d-123">C 형식을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 날짜/시간 형식으로 변환할 때 고려해야 할 문제를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2b16d-123">Lists issues to consider when you convert from C types to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data/time types.</span></span>  
  
 [<span data-ttu-id="2b16d-124">SQL에서 C로 변환</span><span class="sxs-lookup"><span data-stu-id="2b16d-124">Conversions from SQL to C</span></span>](datetime-data-type-conversions-from-sql-to-c.md)  
 <span data-ttu-id="2b16d-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 날짜/시간 형식을 C 형식으로 변환할 때 고려해야 할 문제를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2b16d-125">Lists issues to consider when you convert from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data/time types to C types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b16d-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2b16d-126">See Also</span></span>  
 [<span data-ttu-id="2b16d-127">ODBC&#41;&#40;날짜 및 시간 기능 향상</span><span class="sxs-lookup"><span data-stu-id="2b16d-127">Date and Time Improvements &#40;ODBC&#41;</span></span>](date-and-time-improvements-odbc.md)  
  
  
