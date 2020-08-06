---
title: 테이블 반환 매개 변수의 ODBC SQL 유형 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL_SS_TABLE
ms.assetid: 6725bfb9-5f10-4115-be09-fd9c9f5779ea
author: rothja
ms.author: jroth
ms.openlocfilehash: c8ed46bf117c9158ae5b60c10ebd89e3d348f77c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653853"
---
# <a name="odbc-sql-type-for-table-valued-parameters"></a><span data-ttu-id="491ed-102">테이블 반환 매개 변수의 ODBC SQL 유형</span><span class="sxs-lookup"><span data-stu-id="491ed-102">ODBC SQL Type for Table-Valued Parameters</span></span>
  <span data-ttu-id="491ed-103">새로운 ODBC SQL 형식인 SQL_SS_TABLE에서 테이블 반환 매개 변수에 대한 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="491ed-103">Support for table-valued parameters is provided by a new ODBC SQL type, SQL_SS_TABLE.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="491ed-104">설명</span><span class="sxs-lookup"><span data-stu-id="491ed-104">Remarks</span></span>  
 <span data-ttu-id="491ed-105">SQL_SS_TABLE은 다른 ODBC 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식으로 변환할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="491ed-105">SQL_SS_TABLE cannot be converted to any other ODBC or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span>  
  
 <span data-ttu-id="491ed-106">SQLBindParameter의 *ValueType* 매개 변수에서 SQL_SS_TABLE를 C 데이터 형식으로 사용 하거나 apd (응용 프로그램 매개 변수 설명자) 레코드의 SQL_DESC_TYPE를 SQL_SS_TABLE로 설정 하려고 하면 SQL_ERROR가 반환 되 고 SQLSTATE = HY003, "잘못 된 응용 프로그램 버퍼 형식"으로 진단 레코드가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="491ed-106">If SQL_SS_TABLE is used as a C data type in the *ValueType* parameter of SQLBindParameter, or an attempt is made to set SQL_DESC_TYPE in an application parameter descriptor (APD) record to SQL_SS_TABLE, SQL_ERROR is returned and a diagnostic record is generated with SQLSTATE=HY003, "Invalid application buffer type".</span></span>  
  
 <span data-ttu-id="491ed-107">IPD 레코드에 SQL_DESC_TYPE이 SQL_SS_TABLE로 설정되어 있고 해당 APD 레코드가 SQL_C_DEFAULT가 아닌 경우 SQL_ERROR가 반환되고 SQLSTATE=HY003, "잘못된 애플리케이션 버퍼 형식입니다"가 표시되며 진단 레코드가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="491ed-107">If SQL_DESC_TYPE is set to SQL_SS_TABLE in an IPD record and the corresponding application parameter descriptor record is not SQL_C_DEFAULT, SQL_ERROR is returned and a diagnostic record is generated with SQLSTATE=HY003, "Invalid application buffer type".</span></span> <span data-ttu-id="491ed-108">SQLSetDescField, SQLSetDescRec 또는 SQLBindParameter의 *ParameterType* 에서이 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="491ed-108">This can occur with the *ParameterType* of a SQLSetDescField, SQLSetDescRec or SQLBindParameter.</span></span>  
  
 <span data-ttu-id="491ed-109">SQLGetData를 호출할 때 *TargetType* 매개 변수가 SQL_SS_TABLE 된 경우 SQL_ERROR가 반환 되 고 SQLSTATE = HY003, "잘못 된 응용 프로그램 버퍼 형식"으로 진단 레코드가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="491ed-109">If the *TargetType* parameter is SQL_SS_TABLE when calling SQLGetData, SQL_ERROR is returned and a diagnostic record is generated with SQLSTATE=HY003, "Invalid application buffer type".</span></span>  
  
 <span data-ttu-id="491ed-110">테이블 반환 매개 변수 열은 SQL_SS_TABLE 형식으로 바인딩할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="491ed-110">A table-valued parameter column cannot be bound as type SQL_SS_TABLE.</span></span> <span data-ttu-id="491ed-111">`SQLBindParameter` *ParameterType* 를 SQL_SS_TABLE으로 설정 하 여를 호출 하면 SQL_ERROR가 반환 되 고 SQLSTATE = HY004, "잘못 된 SQL 데이터 형식"으로 진단 레코드가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="491ed-111">If `SQLBindParameter` is called with *ParameterType* set to SQL_SS_TABLE, SQL_ERROR is returned and a diagnostic record is generated with SQLSTATE=HY004, "Invalid SQL data type".</span></span> <span data-ttu-id="491ed-112">SQLSetDescField 및 SQLSetDescRec에도이 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="491ed-112">This can also occur with SQLSetDescField and SQLSetDescRec.</span></span>  
  
 <span data-ttu-id="491ed-113">테이블 반환 매개 변수 열 값에는 매개 변수 및 결과 열과 동일한 데이터 변환 옵션이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="491ed-113">Table-valued parameter column values have the same data conversion options as parameters and result columns.</span></span>  
  
 <span data-ttu-id="491ed-114">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상 버전에서는 테이블 반환 매개 변수를 입력 매개 변수로만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="491ed-114">A table-valued parameter can only be an input parameter in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later.</span></span> <span data-ttu-id="491ed-115">SQLBindParameter 또는 SQLSetDescField를 통해 SQL_DESC_PARAMETER_TYPE를 SQL_PARAM_INPUT 이외의 값으로 설정 하려고 하면 SQL_ERROR가 반환 되 고 SQLSTATE = HY105 및 "잘못 된 매개 변수 형식입니다." 라는 메시지가 포함 된 진단 레코드가 문에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="491ed-115">If an attempt is made to set SQL_DESC_PARAMETER_TYPE to a value other than SQL_PARAM_INPUT via SQLBindParameter or SQLSetDescField, SQL_ERROR is returned and a diagnostic record is added to the statement with SQLSTATE=HY105 and the message "Invalid parameter type".</span></span>  
  
 <span data-ttu-id="491ed-116">테이블 반환 매개 변수에는 행별 기본값이 지원되지 않으므로 테이블 반환 매개 변수 열의 *StrLen_or_IndPtr*에는 SQL_DEFAULT_PARAM을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="491ed-116">Table-valued parameter columns cannot use SQL_DEFAULT_PARAM in *StrLen_or_IndPtr*, because per-row default values are not supported with table-valued parameters.</span></span> <span data-ttu-id="491ed-117">대신 애플리케이션에서 열 특성 SQL_CA_SS_COL_HAS_DEFAULT_VALUE를 1로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="491ed-117">Instead, an application can set the column attribute SQL_CA_SS_COL_HAS_DEFAULT_VALUE to 1.</span></span> <span data-ttu-id="491ed-118">즉, 해당 열이 모든 행에 대해 기본값을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="491ed-118">This means that the column will have default values for all rows.</span></span> <span data-ttu-id="491ed-119">*StrLen_or_IndPtr* SQL_DEFAULT_PARAM로 설정 된 경우 sqlexecute 또는 SQLExecDirect는 SQL_ERROR를 반환 하 고 SQLSTATE = HY090 및 "잘못 된 문자열 또는 버퍼 길이" 라는 메시지와 함께 진단 레코드가 문에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="491ed-119">If *StrLen_or_IndPtr* is set to SQL_DEFAULT_PARAM, SQLExecute or SQLExecDirect will return SQL_ERROR, and a diagnostic record will be added to the statement with SQLSTATE=HY090 and the message "Invalid string or buffer length".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="491ed-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="491ed-120">See Also</span></span>  
 [<span data-ttu-id="491ed-121">ODBC&#41;&#40;테이블 반환 매개 변수</span><span class="sxs-lookup"><span data-stu-id="491ed-121">Table-Valued Parameters &#40;ODBC&#41;</span></span>](table-valued-parameters-odbc.md)  
  
  
