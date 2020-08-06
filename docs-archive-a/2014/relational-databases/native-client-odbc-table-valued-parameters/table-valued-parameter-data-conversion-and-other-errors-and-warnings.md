---
title: 테이블 반환 매개 변수 데이터 변환 및 기타 오류 및 경고 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), data conversion
- table-valued parameters (ODBC), error messages
ms.assetid: edd45234-59dc-4338-94fc-330e820cc248
author: rothja
ms.author: jroth
ms.openlocfilehash: 45b9ba7f91b54548e096bbe47da6e01ba562f59d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646392"
---
# <a name="table-valued-parameter-data-conversion-and-other-errors-and-warnings"></a><span data-ttu-id="ec920-102">테이블 반환 매개 변수 데이터 변환과 기타 오류 및 경고</span><span class="sxs-lookup"><span data-stu-id="ec920-102">Table-Valued Parameter Data Conversion and Other Errors and Warnings</span></span>
  <span data-ttu-id="ec920-103">다른 열 및 매개 변수 값과 동일한 방식으로 클라이언트와 서버 데이터 형식 간에 테이블 반환 매개 변수 열 값을 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec920-103">Table-valued parameter column values can be converted between client and server data types in the same way as other column and parameter values.</span></span> <span data-ttu-id="ec920-104">하지만 테이블 반환 매개 변수에는 다중 열과 다중 행이 포함될 수 있으므로 오류가 발생한 실제 값을 확인하는 것이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ec920-104">But because a table-valued parameter can contain multiple columns and multiple rows, it is important to be able to identify the actual value where the error occurred.</span></span>  
  
 <span data-ttu-id="ec920-105">테이블 반환 매개 변수 열에서 오류나 경고가 검색된 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client는 진단 레코드를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="ec920-105">When an error or warning is detected in a table-valued parameter column, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client will generate a diagnostic record.</span></span> <span data-ttu-id="ec920-106">오류 메시지에는 테이블 반환 매개 변수의 매개 변수 번호와 열 서수 및 행 번호가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec920-106">The error message will contain the parameter number of the table-valued parameter, plus the column ordinal and row number.</span></span> <span data-ttu-id="ec920-107">애플리케이션에서는 진단 레코드의 진단 필드 SQL_DIAG_SS_TABLE_COLUMN_NUMBER 및 SQL_DIAG_SS_TABLE_ROW_NUMBER를 사용하여 오류 및 경고와 연관된 값을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec920-107">An application can also use the diagnostic fields SQL_DIAG_SS_TABLE_COLUMN_NUMBER and SQL_DIAG_SS_TABLE_ROW_NUMBER within diagnostic records to determine which values are associated with errors and warnings.</span></span> <span data-ttu-id="ec920-108">이러한 진단 필드는 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상 버전에서 사용 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="ec920-108">These diagnostic fields are available in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions.</span></span>  
  
 <span data-ttu-id="ec920-109">진단 레코드의 SQLSTATE 및 메시지 구성 요소는 모든 측면에서 기존 ODBC 동작을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="ec920-109">The SQLSTATE and message components of diagnostic records will conform to existing ODBC behavior in all other respects.</span></span> <span data-ttu-id="ec920-110">즉, 매개 변수, 행 및 열 식별 정보를 제외 하면 테이블 반환 매개 변수에 대 한 오류 메시지의 값은 테이블 반환 매개 변수가 아닌 매개 변수와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec920-110">That is, except for the parameter, row, and column identification information, error messages have the same values for table-valued parameters as they would for non-table-valued parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec920-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ec920-111">See Also</span></span>  
 [<span data-ttu-id="ec920-112">ODBC&#41;&#40;테이블 반환 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ec920-112">Table-Valued Parameters &#40;ODBC&#41;</span></span>](table-valued-parameters-odbc.md)  
  
  
