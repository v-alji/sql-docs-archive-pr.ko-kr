---
title: 대량 복사 함수 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], functions
- ODBC, bulk copy operations
- functions [ODBC]
ms.assetid: 6526b892-1d58-4f55-8335-f09887f6ea02
author: rothja
ms.author: jroth
ms.openlocfilehash: 02dba8cf4d510d2ec5f20e600302bb692c749f97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652095"
---
# <a name="bulk-copy-functions"></a><span data-ttu-id="d308b-102">Bulk Copy Functions</span><span class="sxs-lookup"><span data-stu-id="d308b-102">Bulk Copy Functions</span></span>
  <span data-ttu-id="d308b-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관련 대량 복사 API 확장을 사용하면 클라이언트 애플리케이션에서 신속하게 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에 데이터 행을 추가하거나 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d308b-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific bulk-copy API extension of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver allows client applications to rapidly add data rows to, or extract data rows from, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="d308b-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client를 사용할 경우 SQLNCLI11.LIB 및 SQLNCLI.H에서 대량 복사 함수(BCP)를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d308b-104">When using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, you can reference the bulk copy functions (BCP) in SQLNCLI11.LIB and SQLNCLI.H.</span></span>  
  
 <span data-ttu-id="d308b-105">BCP API 함수 호출을 사용하는 애플리케이션은 애플리케이션에서 사용하는 드라이버(.dll)와 함께 제공되는 라이브러리(.lib)와 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d308b-105">An application that uses BCP API function calls should link with the library (.lib) that shipped with the driver (.dll) used by the application.</span></span> <span data-ttu-id="d308b-106">BCP 애플리케이션을 두 개 이상의 드라이버 라이브러리와 연결해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d308b-106">A BCP application should not link with more than one driver library.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d308b-107">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="d308b-107">In This Section</span></span>  
  
-   [<span data-ttu-id="d308b-108">bcp_batch</span><span class="sxs-lookup"><span data-stu-id="d308b-108">bcp_batch</span></span>](bcp-batch.md)  
  
-   [<span data-ttu-id="d308b-109">bcp_bind</span><span class="sxs-lookup"><span data-stu-id="d308b-109">bcp_bind</span></span>](bcp-bind.md)  
  
-   [<span data-ttu-id="d308b-110">bcp_colfmt</span><span class="sxs-lookup"><span data-stu-id="d308b-110">bcp_colfmt</span></span>](bcp-colfmt.md)  
  
-   [<span data-ttu-id="d308b-111">bcp_collen</span><span class="sxs-lookup"><span data-stu-id="d308b-111">bcp_collen</span></span>](bcp-collen.md)  
  
-   [<span data-ttu-id="d308b-112">bcp_colptr</span><span class="sxs-lookup"><span data-stu-id="d308b-112">bcp_colptr</span></span>](bcp-colptr.md)  
  
-   [<span data-ttu-id="d308b-113">bcp_columns</span><span class="sxs-lookup"><span data-stu-id="d308b-113">bcp_columns</span></span>](bcp-columns.md)  
  
-   [<span data-ttu-id="d308b-114">bcp_control</span><span class="sxs-lookup"><span data-stu-id="d308b-114">bcp_control</span></span>](bcp-control.md)  
  
-   [<span data-ttu-id="d308b-115">bcp_done</span><span class="sxs-lookup"><span data-stu-id="d308b-115">bcp_done</span></span>](bcp-done.md)  
  
-   [<span data-ttu-id="d308b-116">bcp_exec</span><span class="sxs-lookup"><span data-stu-id="d308b-116">bcp_exec</span></span>](bcp-exec.md)  
  
-   [<span data-ttu-id="d308b-117">bcp_getcolfmt</span><span class="sxs-lookup"><span data-stu-id="d308b-117">bcp_getcolfmt</span></span>](bcp-getcolfmt.md)  
  
-   [<span data-ttu-id="d308b-118">bcp_gettypename</span><span class="sxs-lookup"><span data-stu-id="d308b-118">bcp_gettypename</span></span>](bcp-gettypename.md)  
  
-   [<span data-ttu-id="d308b-119">bcp_init</span><span class="sxs-lookup"><span data-stu-id="d308b-119">bcp_init</span></span>](bcp-init.md)  
  
-   [<span data-ttu-id="d308b-120">bcp_moretext</span><span class="sxs-lookup"><span data-stu-id="d308b-120">bcp_moretext</span></span>](bcp-moretext.md)  
  
-   [<span data-ttu-id="d308b-121">bcp_readfmt</span><span class="sxs-lookup"><span data-stu-id="d308b-121">bcp_readfmt</span></span>](bcp-readfmt.md)  
  
-   [<span data-ttu-id="d308b-122">bcp_sendrow</span><span class="sxs-lookup"><span data-stu-id="d308b-122">bcp_sendrow</span></span>](bcp-sendrow.md)  
  
-   [<span data-ttu-id="d308b-123">bcp_setbulkmode</span><span class="sxs-lookup"><span data-stu-id="d308b-123">bcp_setbulkmode</span></span>](bcp-setbulkmode.md)  
  
-   [<span data-ttu-id="d308b-124">bcp_setcolfmt</span><span class="sxs-lookup"><span data-stu-id="d308b-124">bcp_setcolfmt</span></span>](bcp-setcolfmt.md)  
  
-   [<span data-ttu-id="d308b-125">bcp_writefmt</span><span class="sxs-lookup"><span data-stu-id="d308b-125">bcp_writefmt</span></span>](bcp-writefmt.md)  
  
## <a name="see-also"></a><span data-ttu-id="d308b-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d308b-126">See Also</span></span>  
 <span data-ttu-id="d308b-127">[SQL Server 드라이버 확장](../../database-engine/dev-guide/sql-server-driver-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="d308b-127">[SQL Server Driver Extensions](../../database-engine/dev-guide/sql-server-driver-extensions.md) </span></span>  
 [<span data-ttu-id="d308b-128">ODBC&#41;&#40;대량 복사 작업 수행</span><span class="sxs-lookup"><span data-stu-id="d308b-128">Performing Bulk Copy Operations &#40;ODBC&#41;</span></span>](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
