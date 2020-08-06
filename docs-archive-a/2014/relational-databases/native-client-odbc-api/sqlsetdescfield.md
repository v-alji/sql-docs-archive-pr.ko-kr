---
title: SQLSetDescField | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetDescField function
ms.assetid: de4bed15-15be-4825-994c-1046255e725a
author: rothja
ms.author: jroth
ms.openlocfilehash: 1b8290fd90c0c9bb91f08d94e119689d38fbc04e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660512"
---
# <a name="sqlsetdescfield"></a><span data-ttu-id="70d66-102">SQLSetDescField</span><span class="sxs-lookup"><span data-stu-id="70d66-102">SQLSetDescField</span></span>
  <span data-ttu-id="70d66-103">SQLSetDescField를 사용 하 여 테이블 반환 매개 변수 및 테이블 반환 매개 변수 열의 설명자 필드를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70d66-103">SQLSetDescField can be used to set descriptor fields for table-valued parameters and table-valued parameter columns.</span></span> <span data-ttu-id="70d66-104">사용할 수 있는 필드에 대 한 자세한 내용은 테이블 반환 매개 변수 [설명자 필드](../native-client-odbc-table-valued-parameters/table-valued-parameter-descriptor-fields.md) 및 [테이블 반환 매개 변수 구성 열의 설명자 필드](../native-client-odbc-table-valued-parameters/descriptor-fields-for-table-valued-parameter-constituent-columns.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="70d66-104">For information about the available fields, see [Table-Valued Parameter Descriptor Fields](../native-client-odbc-table-valued-parameters/table-valued-parameter-descriptor-fields.md) and [Descriptor Fields for Table-Valued Parameter Constituent Columns](../native-client-odbc-table-valued-parameters/descriptor-fields-for-table-valued-parameter-constituent-columns.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70d66-105">설명</span><span class="sxs-lookup"><span data-stu-id="70d66-105">Remarks</span></span>  
 <span data-ttu-id="70d66-106">테이블 반환 매개 변수 열은 설명자 헤더 필드 SQL_SOPT_SS_PARAM_FOCUS가 SQL_DESC_TYPE이 SQL_SS_TABLE로 설정된 레코드의 서수로 설정된 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70d66-106">Table-valued parameter columns are only available when the descriptor header field SQL_SOPT_SS_PARAM_FOCUS is set to the ordinal of a record that has SQL_DESC_TYPE set to SQL_SS_TABLE.</span></span> <span data-ttu-id="70d66-107">SQL_SOPT_SS_PARAM_FOCUS에 대한 자세한 내용은 [SQLSetStmtAttr](sqlsetstmtattr.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="70d66-107">For more information about SQL_SOPT_SS_PARAM_FOCUS, see [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span>  
  
 <span data-ttu-id="70d66-108">SQL_SOPT_SS_PARAM_FOCUS를 테이블 반환 매개 변수가 아닌 매개 변수의 서 수로 설정 하려고 하면 SQLSetStmtAttr가 SQL_ERROR를 반환 하 고 SQLSTATE = HY024 및 "잘못 된 특성 값입니다." 라는 메시지가 포함 된 진단 레코드가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="70d66-108">If an attempt is made to set SQL_SOPT_SS_PARAM_FOCUS to the ordinal of a parameter that is not a table-valued parameter, SQLSetStmtAttr returns SQL_ERROR, and a diagnostic record is created with SQLSTATE = HY024 and the message "Invalid attribute value".</span></span> <span data-ttu-id="70d66-109">SQL_SOPT_SS_PARAM_FOCUS는 SQL_ERROR가 반환될 때 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70d66-109">SQL_SOPT_SS_PARAM_FOCUS is not changed when SQL_ERROR is returned.</span></span>  
  
 <span data-ttu-id="70d66-110">SQL_SOPT_SS_PARAM_FOCUS를 0으로 설정하면 매개 변수의 설명자 레코드에 대한 액세스가 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="70d66-110">Setting SQL_SOPT_SS_PARAM_FOCUS to 0 restores access to descriptor records for parameters.</span></span>  
  
 <span data-ttu-id="70d66-111">테이블 반환 매개 변수에 대 한 자세한 내용은 [ODBC&#41;&#40;테이블 반환 매개 변수 ](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="70d66-111">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="sqlsetdescfield-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="70d66-112">향상된 날짜 및 시간 기능에 대한 SQLSetDescField 지원</span><span class="sxs-lookup"><span data-stu-id="70d66-112">SQLSetDescField Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="70d66-113">ODBC에서 날짜/시간 기능이 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="70d66-113">Date/time features have been enhanced in ODBC.</span></span> <span data-ttu-id="70d66-114">새로운 날짜/시간 형식에 제공되는 설명자 필드에 대한 자세한 내용은 [Parameter and Result Metadata](../native-client-odbc-date-time/metadata-parameter-and-result.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="70d66-114">For information about the descriptor field provided for the new date/time types, see [Parameter and Result Metadata](../native-client-odbc-date-time/metadata-parameter-and-result.md).</span></span>  
  
 <span data-ttu-id="70d66-115">자세한 내용은 [ODBC&#41;&#40;날짜 및 시간 향상 ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="70d66-115">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlsetdescfield-support-for-large-clr-udts"></a><span data-ttu-id="70d66-116">큰 CLR UDT에 대한 SQLSetDescField 지원</span><span class="sxs-lookup"><span data-stu-id="70d66-116">SQLSetDescField Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="70d66-117">SQLSetDescField는 많은 CLR Udt (사용자 정의 형식)를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="70d66-117">SQLSetDescField supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="70d66-118">자세한 내용은 [ODBC&#41;&#40;LARGE CLR 사용자 정의 형식 ](../native-client/odbc/large-clr-user-defined-types-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="70d66-118">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="sqlsetdescfield-support-for-sparse-columns"></a><span data-ttu-id="70d66-119">스파스 열에 대한 SQLSetDescField 지원</span><span class="sxs-lookup"><span data-stu-id="70d66-119">SQLSetDescField Support for Sparse Columns</span></span>  
 <span data-ttu-id="70d66-120">SQLSetDecField를 사용 하 여 APD (응용 프로그램 매개 변수 설명자)의 SQL_SOPT_SS_NAME_SCOPE SQL_SS_NAME_SCOPE_EXTENDED 값으로 설정 하 고 SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70d66-120">SQLSetDecField can be used to set SQL_SOPT_SS_NAME_SCOPE in the application parameter descriptor (APD) to the values SQL_SS_NAME_SCOPE_EXTENDED and SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET.</span></span>  
  
 <span data-ttu-id="70d66-121">자세한 내용은 [스파스 열 지원 &#40;ODBC&#41;](../native-client/odbc/sparse-columns-support-odbc.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="70d66-121">For more information, see [Sparse Columns Support &#40;ODBC&#41;](../native-client/odbc/sparse-columns-support-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70d66-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="70d66-122">See Also</span></span>  
 <span data-ttu-id="70d66-123">[SQLSetDescField](https://go.microsoft.com/fwlink/?LinkId=80705) </span><span class="sxs-lookup"><span data-stu-id="70d66-123">[SQLSetDescField](https://go.microsoft.com/fwlink/?LinkId=80705) </span></span>  
 [<span data-ttu-id="70d66-124">ODBC API 구현 정보</span><span class="sxs-lookup"><span data-stu-id="70d66-124">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
