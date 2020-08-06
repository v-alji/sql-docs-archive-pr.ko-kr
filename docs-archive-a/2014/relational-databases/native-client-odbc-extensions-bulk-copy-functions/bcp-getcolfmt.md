---
title: bcp_getcolfmt | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_getcolfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_getcolfmt function
ms.assetid: f8bdada5-7b2d-4475-8c98-f93e9d77b130
author: rothja
ms.author: jroth
ms.openlocfilehash: aabc811a5aa0babe5119c4ef0ed0e649586d73cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649057"
---
# <a name="bcp_getcolfmt"></a><span data-ttu-id="cfb88-102">bcp_getcolfmt</span><span class="sxs-lookup"><span data-stu-id="cfb88-102">bcp_getcolfmt</span></span>
  <span data-ttu-id="cfb88-103">열 형식 속성 값을 찾는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cfb88-103">Used to find the column format property value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfb88-104">구문</span><span class="sxs-lookup"><span data-stu-id="cfb88-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_getcolfmt (  
HDBC   
hdbc  
,  
INT   
field  
,  
INT   
property  
,  
void*   
pValue  
,  
INT   
cbvalue,  
INT*   
pcbLen  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="cfb88-105">인수</span><span class="sxs-lookup"><span data-stu-id="cfb88-105">Arguments</span></span>  
 <span data-ttu-id="cfb88-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="cfb88-106">*hdbc*</span></span>  
 <span data-ttu-id="cfb88-107">대량 복사가 가능한 ODBC 연결 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="cfb88-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="cfb88-108">*필드가*</span><span class="sxs-lookup"><span data-stu-id="cfb88-108">*field*</span></span>  
 <span data-ttu-id="cfb88-109">속성을 검색할 열 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="cfb88-109">Is the column number for which the property is retrieved.</span></span>  
  
 <span data-ttu-id="cfb88-110">*property*</span><span class="sxs-lookup"><span data-stu-id="cfb88-110">*property*</span></span>  
 <span data-ttu-id="cfb88-111">속성 상수 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="cfb88-111">Is one of the property constants.</span></span>  
  
 <span data-ttu-id="cfb88-112">*pValue*</span><span class="sxs-lookup"><span data-stu-id="cfb88-112">*pValue*</span></span>  
 <span data-ttu-id="cfb88-113">검색할 속성 값이 있는 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="cfb88-113">Is the pointer to the buffer from which to retrieve the property value.</span></span>  
  
 <span data-ttu-id="cfb88-114">*cbValue*</span><span class="sxs-lookup"><span data-stu-id="cfb88-114">*cbValue*</span></span>  
 <span data-ttu-id="cfb88-115">속성 버퍼의 길이(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="cfb88-115">Is the length of the property buffer in bytes.</span></span>  
  
 <span data-ttu-id="cfb88-116">*pcbLen*</span><span class="sxs-lookup"><span data-stu-id="cfb88-116">*pcbLen*</span></span>  
 <span data-ttu-id="cfb88-117">속성 버퍼에서 반환되는 데이터의 길이에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="cfb88-117">Pointer to length of the data that is being returned in the property buffer.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="cfb88-118">반환</span><span class="sxs-lookup"><span data-stu-id="cfb88-118">Returns</span></span>  
 <span data-ttu-id="cfb88-119">SUCCEED 또는 FAIL</span><span class="sxs-lookup"><span data-stu-id="cfb88-119">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfb88-120">설명</span><span class="sxs-lookup"><span data-stu-id="cfb88-120">Remarks</span></span>  
 <span data-ttu-id="cfb88-121">열 형식 속성 값은 [bcp_setcolfmt](bcp-setcolfmt.md) 항목에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfb88-121">Column format property values are listed in the [bcp_setcolfmt](bcp-setcolfmt.md) topic.</span></span> <span data-ttu-id="cfb88-122">열 형식 속성 값은 **bcp_setcolfmt** 함수를 호출하여 설정되고 **bcp_getcolfmt** 함수는 열 형식 속성 값을 찾는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cfb88-122">The column format property values are set by calling the **bcp_setcolfmt** function, and the **bcp_getcolfmt** function is used to find the column format property value.</span></span>  
  
 <span data-ttu-id="cfb88-123">이전 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 버전과 비교해서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이상 버전의 서버 컴퓨터에 연결할 때 동작 변경 내용이 관찰될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfb88-123">Behavior changes may be observed when connecting to a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (or later) server computer, compared to earlier [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions.</span></span> <span data-ttu-id="cfb88-124">자세한 내용은 [메타데이터 검색](../native-client/features/metadata-discovery.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cfb88-124">For more information, see [Metadata Discovery](../native-client/features/metadata-discovery.md).</span></span>  
  
## <a name="bcp_getcolfmt-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="cfb88-125">향상된 날짜 및 시간 기능에 대한 bcp_getcolfmt 지원</span><span class="sxs-lookup"><span data-stu-id="cfb88-125">bcp_getcolfmt Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="cfb88-126">`BCP_FMT_TYPE`날짜/시간 형식의 속성에 사용 되는 형식은 [OLE DB 및 ODBC&#41;&#40;향상 된 날짜 및 시간 형식에 대 한 대량 복사 변경 내용 ](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)에 지정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfb88-126">The types used with the `BCP_FMT_TYPE` property for date/time types are as specified in [Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).</span></span>  
  
 <span data-ttu-id="cfb88-127">자세한 내용은 [ODBC&#41;&#40;날짜 및 시간 향상 ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cfb88-127">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfb88-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cfb88-128">See Also</span></span>  
 [<span data-ttu-id="cfb88-129">Bulk Copy Functions</span><span class="sxs-lookup"><span data-stu-id="cfb88-129">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
