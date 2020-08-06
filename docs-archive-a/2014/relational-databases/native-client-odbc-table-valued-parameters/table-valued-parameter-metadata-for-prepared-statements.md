---
title: 준비 된 문의 테이블 반환 매개 변수 메타 데이터 Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), metadata for prepared statements
ms.assetid: fd2fc705-2e98-4011-9822-c7e6cca4a535
author: rothja
ms.author: jroth
ms.openlocfilehash: ad1394bd5e5bedc69a98308ba67a98434559c146
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741944"
---
# <a name="table-valued-parameter-metadata-for-prepared-statements"></a><span data-ttu-id="0b75f-102">준비된 문의 테이블 반환 매개 변수 메타데이터</span><span class="sxs-lookup"><span data-stu-id="0b75f-102">Table-Valued Parameter Metadata for Prepared Statements</span></span>
  <span data-ttu-id="0b75f-103">응용 프로그램은 SQLNumParams 및 SQLDescribeParam을 통해 준비 된 프로시저 호출에 대 한 메타 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b75f-103">An application can obtain metadata for a prepared procedure call through SQLNumParams and SQLDescribeParam.</span></span> <span data-ttu-id="0b75f-104">테이블 반환 매개 변수의 경우 *DataTypePtr* 는 SQL_SS_TABLE로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b75f-104">For table-valued parameters, *DataTypePtr* is set to SQL_SS_TABLE.</span></span> <span data-ttu-id="0b75f-105">SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME 및 SQL_CA_SS_SCHEMA_NAME에 대 한 SQLGetDescField를 통해 추가 메타 데이터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b75f-105">Additional metadata is available through SQLGetDescField for SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME, and SQL_CA_SS_SCHEMA_NAME.</span></span>  
  
 <span data-ttu-id="0b75f-106">SQLColumns에서 SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME 및 SQL_CA_SS_SCHEMA_NAME를 사용 하 여 테이블 반환 매개 변수와 연결 된 테이블 형식에 대 한 열 메타 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b75f-106">SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME, and SQL_CA_SS_SCHEMA_NAME can be used with SQLColumns to obtain column metadata for table types associated with table-valued parameters.</span></span> <span data-ttu-id="0b75f-107">이 경우 SQLColumns를 호출 하기 전에 SQL_SOPT_SS_NAME_SCOPE을 SQL_SS_NAME_SCOPE_TABLE_TYPE로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b75f-107">In this case, SQL_SOPT_SS_NAME_SCOPE must be set to SQL_SS_NAME_SCOPE_TABLE_TYPE before SQLColumns is called.</span></span> <span data-ttu-id="0b75f-108">그리고 애플리케이션이 테이블 반환 매개 변수 열 메타데이터 검색을 마치면 SQL_SOPT_SS_NAME_SCOPE를 기본값인 SQL_SS_NAME_SCOPE_TABLE로 다시 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b75f-108">SQL_SOPT_SS_NAME_SCOPE should then be set back to the default value, SQL_SS_NAME_SCOPE_TABLE, when the application has finished retrieving table-valued parameter column metadata.</span></span>  
  
 <span data-ttu-id="0b75f-109">SQL_CA_SS_TYPE_NAME , SQL_CA_SS_CATALOG_NAME 및 SQL_CA_SS_SCHEMA_NAME을 CLR 사용자 정의 형식 매개 변수에 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b75f-109">SQL_CA_SS_TYPE_NAME , SQL_CA_SS_CATALOG_NAME, and SQL_CA_SS_SCHEMA_NAME can also be used with CLR user-defined type parameters.</span></span>  
  
 <span data-ttu-id="0b75f-110">저장 프로시저 호출이 아닌 준비된 문의 테이블 반환 매개 변수 메타데이터는 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0b75f-110">You cannot obtain table-valued parameter metadata for prepared statements that are not stored procedure calls.</span></span> <span data-ttu-id="0b75f-111">이렇게 하려고 하면 애플리케이션에서 SQLSTATE 42000이고 메시지가 &quot;구문 오류 또는 액세스 위반입니다.&quot;인 SQL_ERROR가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b75f-111">If you try to do this, the application returns SQL_ERROR with SQLSTATE 42000 and the message "Syntax error or access violation".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b75f-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0b75f-112">See Also</span></span>  
 [<span data-ttu-id="0b75f-113">ODBC&#41;&#40;테이블 반환 매개 변수</span><span class="sxs-lookup"><span data-stu-id="0b75f-113">Table-Valued Parameters &#40;ODBC&#41;</span></span>](table-valued-parameters-odbc.md)  
  
  
