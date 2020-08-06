---
title: 대량 복사 작업 수행 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC]
- ODBC, bulk copy operations
- minimally logged operations [SQL Server Native Client]
- bulk copy [ODBC], about bulk copy
ms.assetid: 5c793405-487c-4f52-88b8-0091d529afb3
author: rothja
ms.author: jroth
ms.openlocfilehash: f2647ebca703eab46d7be0e1cfc2490a65384ee6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740927"
---
# <a name="performing-bulk-copy-operations-odbc"></a><span data-ttu-id="57451-102">대량 복사 작업 수행(ODBC)</span><span class="sxs-lookup"><span data-stu-id="57451-102">Performing Bulk Copy Operations (ODBC)</span></span>
  <span data-ttu-id="57451-103">ODBC 표준에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대량 복사 작업을 직접 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="57451-103">The ODBC standard does not directly support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bulk copy operations.</span></span> <span data-ttu-id="57451-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 이상 버전의 인스턴스에 연결되어 있으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대량 복사 작업을 수행하는 DB-Library 함수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="57451-104">When connected to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 or later, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports the DB-Library functions that perform [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bulk copy operations.</span></span> <span data-ttu-id="57451-105">이 드라이버 관련 확장은 대량 복사 함수를 사용하는 기존 DB-Library 애플리케이션에 대해 편리한 업그레이드 경로를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="57451-105">This driver-specific extension provides an easy upgrade path for existing DB-Library applications that use bulk copy functions.</span></span> <span data-ttu-id="57451-106">특별한 대량 복사 지원은 다음 파일에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57451-106">The specialized bulk copy support is in the following files:</span></span>  
  
-   <span data-ttu-id="57451-107">sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="57451-107">sqlncli.h</span></span>  
  
     <span data-ttu-id="57451-108">대량 복사 함수를 위한 함수 프로토타입 및 상수 정의를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="57451-108">Includes function prototypes and constant definitions for bulk copy functions.</span></span> <span data-ttu-id="57451-109">sqlncli.h는 대량 복사 작업을 수행하는 ODBC 애플리케이션에 포함되어야 하며 애플리케이션을 컴파일할 때 애플리케이션의 포함 경로에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57451-109">sqlncli.h must be included in the ODBC application performing bulk copy operations and must be in the application's include path when it is compiled.</span></span>  
  
-   <span data-ttu-id="57451-110">sqlncli11.lib</span><span class="sxs-lookup"><span data-stu-id="57451-110">sqlncli11.lib</span></span>  
  
     <span data-ttu-id="57451-111">링커의 라이브러리 경로에 있어야 하며 링크할 파일로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57451-111">Must be in the library path of the linker and specified as a file to be linked.</span></span> <span data-ttu-id="57451-112">sqlncli11.lib는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버와 함께 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="57451-112">sqlncli11.lib is distributed with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
-   <span data-ttu-id="57451-113">sqlncli11.dll</span><span class="sxs-lookup"><span data-stu-id="57451-113">sqlncli11.dll</span></span>  
  
     <span data-ttu-id="57451-114">실행 단계에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57451-114">Must be present at execution time.</span></span> <span data-ttu-id="57451-115">sqlncli11.dll은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버와 함께 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="57451-115">sqlncli11.dll is distributed with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="57451-116">ODBC **SQLBulkOperations** 함수는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대량 복사 함수와 관계가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="57451-116">The ODBC **SQLBulkOperations** function has no relationship to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bulk copy functions.</span></span> <span data-ttu-id="57451-117">애플리케이션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 관련된 대량 복사 함수를 사용하여 대량 복사 작업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57451-117">Applications must use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific bulk-copy functions to perform bulk copy operations.</span></span>  
  
## <a name="minimally-logging-bulk-copies"></a><span data-ttu-id="57451-118">최소로 기록된 대량 복사</span><span class="sxs-lookup"><span data-stu-id="57451-118">Minimally Logging Bulk Copies</span></span>  
 <span data-ttu-id="57451-119">전체 복구 모델을 사용하면 대량 로드로 수행되는 모든 행 삽입 작업이 트랜잭션 로그에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="57451-119">With the Full Recovery model, all row-insert operations performed by bulk load are fully logged in the transaction log.</span></span> <span data-ttu-id="57451-120">많은 양의 데이터를 로드하는 경우 트랜잭션 로그가 빠르게 채워질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57451-120">For large data loads, this can cause the transaction log to fill rapidly.</span></span> <span data-ttu-id="57451-121">특정 조건에서 최소 로깅을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57451-121">Under certain conditions, minimally logging is possible.</span></span> <span data-ttu-id="57451-122">최소 로깅은 대량 로드 작업으로 인해 로그 공간이 채워질 가능성을 줄이며 전체 로깅보다 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="57451-122">Minimal logging reduces the possibility of a bulk load operation filling the log space and is also more efficient than full logging.</span></span>  
  
 <span data-ttu-id="57451-123">최소 로깅을 사용 하는 방법에 대 한 자세한 내용은 [대량 가져오기의 최소 로깅을 위한 필수 조건](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="57451-123">For information on using minimal logging, see [Prerequisites for Minimal Logging in Bulk Import](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57451-124">설명</span><span class="sxs-lookup"><span data-stu-id="57451-124">Remarks</span></span>  
 <span data-ttu-id="57451-125">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에서 bcp.exe를 사용하는 경우 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이전에는 오류가 발생하지 않았던 상황에서 오류가 표시될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57451-125">When using bcp.exe in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later, you might see errors in situations where there were no errors prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="57451-126">이는 이후 버전에서 bcp.exe가 더 이상 암시적 데이터 형식 변환을 수행하지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="57451-126">This is because in the later versions, bcp.exe no longer performs implicit data type conversion.</span></span> <span data-ttu-id="57451-127">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이전에는 대상 테이블에 money 데이터 형식이 있을 경우 bcp.exe에서 숫자 데이터를 money 데이터 형식으로 변환했습니다.</span><span class="sxs-lookup"><span data-stu-id="57451-127">Prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], bcp.exe converted numeric data to a money data type, if the target table had a money data type.</span></span> <span data-ttu-id="57451-128">하지만 이 경우 bcp.exe에서 단순히 추가 필드를 자르기만 했습니다.</span><span class="sxs-lookup"><span data-stu-id="57451-128">However, in that situation, bcp.exe simply truncated extra fields.</span></span> <span data-ttu-id="57451-129">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]부터는 파일과 대상 테이블의 데이터 형식이 일치하지 않을 경우 대상 테이블에 맞게 잘라야 하는 데이터가 있으면 bcp.exe에서 오류를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="57451-129">Beginning in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], if data types do not match between the file and the target table, bcp.exe will raise an error if there is any data that would have to be truncated to fit into the target table.</span></span> <span data-ttu-id="57451-130">이 오류를 해결하려면 대상 데이터 형식과 일치하도록 데이터를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="57451-130">To resolve this error, fix the data to match the target data type.</span></span> <span data-ttu-id="57451-131">필요에 따라 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이전 릴리스의 bcp.exe를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="57451-131">Optionally, use bcp.exe from a release prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="57451-132">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="57451-132">In This Section</span></span>  
  
-   [<span data-ttu-id="57451-133">데이터 파일 및 서식 파일 사용</span><span class="sxs-lookup"><span data-stu-id="57451-133">Using Data Files and Format Files</span></span>](using-data-files-and-format-files.md)  
  
-   [<span data-ttu-id="57451-134">프로그램 변수에서 대량 복사</span><span class="sxs-lookup"><span data-stu-id="57451-134">Bulk Copying from Program Variables</span></span>](bulk-copying-from-program-variables.md)  
  
-   [<span data-ttu-id="57451-135">대량 복사 일괄 처리 크기 관리</span><span class="sxs-lookup"><span data-stu-id="57451-135">Managing Bulk Copy Batch Sizes</span></span>](managing-bulk-copy-batch-sizes.md)  
  
-   [<span data-ttu-id="57451-136">텍스트 및 이미지 데이터 대량 복사</span><span class="sxs-lookup"><span data-stu-id="57451-136">Bulk Copying Text and Image Data</span></span>](bulk-copying-text-and-image-data.md)  
  
-   [<span data-ttu-id="57451-137">DB-Library에서 ODBC 대량 복사로 변환</span><span class="sxs-lookup"><span data-stu-id="57451-137">Converting from DB-Library to ODBC Bulk Copy</span></span>](converting-from-db-library-to-odbc-bulk-copy.md)  
  
## <a name="see-also"></a><span data-ttu-id="57451-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="57451-138">See Also</span></span>  
 <span data-ttu-id="57451-139">[ODBC&#41;SQL Server Native Client &#40;](../native-client/odbc/sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="57451-139">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span></span>  
 [<span data-ttu-id="57451-140">데이터 대량 가져오기 및 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="57451-140">Bulk Import and Export of Data &#40;SQL Server&#41;</span></span>](../import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  
