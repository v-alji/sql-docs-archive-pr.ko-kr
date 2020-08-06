---
title: FILESTREAM 지원 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- FILESTREAM [SQL Server], SQL Server Native Client
- SQL Server Native Client [FILESTREAM support]
ms.assetid: 1ad3400d-7fcd-40c9-87ae-f5afc61e0374
author: rothja
ms.author: jroth
ms.openlocfilehash: 18e9a002bfb205e2c0807234550998fe48120d20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730600"
---
# <a name="filestream-support"></a><span data-ttu-id="8375c-102">FILESTREAM 지원</span><span class="sxs-lookup"><span data-stu-id="8375c-102">FILESTREAM Support</span></span>
  <span data-ttu-id="8375c-103">FILESTREAM은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 또는 Windows 파일 시스템에 대한 직접 액세스를 통해 큰 이진 값을 저장하고 액세스하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8375c-103">FILESTREAM provides a way to store and access large binary values, either through [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or by direct access to the Windows file system.</span></span> <span data-ttu-id="8375c-104">큰 이진 값은 2GB보다 큰 값입니다.</span><span class="sxs-lookup"><span data-stu-id="8375c-104">A large binary value is a value larger than 2 gigabytes (GB).</span></span> <span data-ttu-id="8375c-105">향상된 FILESTREAM 지원에 대한 자세한 내용은 [FILESTREAM &#40;SQL Server&#41;](../../blob/filestream-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8375c-105">For more information about enhanced FILESTREAM support, see [FILESTREAM &#40;SQL Server&#41;](../../blob/filestream-sql-server.md).</span></span>  
  
 <span data-ttu-id="8375c-106">데이터베이스 연결을 열면 `@@TEXTSIZE`가 기본적으로 -1("제한 없음")로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8375c-106">When a database connection is opened, `@@TEXTSIZE` will be set to -1 ("unlimited"), by default.</span></span>  
  
 <span data-ttu-id="8375c-107">Windows 파일 시스템 API를 사용하여 FILESTREAM 열에 액세스하고 업데이트할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8375c-107">It is also possible to access and update FILESTREAM columns using Windows file system APIs.</span></span>  
  
 <span data-ttu-id="8375c-108">자세한 내용은 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8375c-108">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="8375c-109">FILESTREAM Support &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="8375c-109">FILESTREAM Support &#40;OLE DB&#41;</span></span>](../ole-db/filestream-support-ole-db.md)  
  
-   [<span data-ttu-id="8375c-110">ODBC&#41;&#40;FILESTREAM 지원</span><span class="sxs-lookup"><span data-stu-id="8375c-110">FILESTREAM Support &#40;ODBC&#41;</span></span>](../odbc/filestream-support-odbc.md)  
  
-   [<span data-ttu-id="8375c-111">OpenSqlFilestream을 사용하여 FILESTREAM 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="8375c-111">Access FILESTREAM Data with OpenSqlFilestream</span></span>](../../blob/access-filestream-data-with-opensqlfilestream.md)  
  
## <a name="querying-for-filestream-columns"></a><span data-ttu-id="8375c-112">FILESTREAM 열 쿼리</span><span class="sxs-lookup"><span data-stu-id="8375c-112">Querying for FILESTREAM Columns</span></span>  
 <span data-ttu-id="8375c-113">OLE DB의 스키마 행 집합은 열이 FILESTREAM 열인지 여부를 보고하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8375c-113">Schema rowsets in OLE DB will not report whether a column is a FILESTREAM column.</span></span> <span data-ttu-id="8375c-114">OLE DB의 ITableDefinition을 사용하여 FILESTREAM 열을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8375c-114">ITableDefinition in OLE DB cannot be used to create a FILESTREAM column.</span></span>  
  
 <span data-ttu-id="8375c-115">ODBC의 SQLColumns와 같은 카탈로그 함수는 열이 FILESTREAM 열인지 여부를 보고 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8375c-115">Catalog functions such as SQLColumns in ODBC will not report whether a column is a FILESTREAM column.</span></span>  
  
 <span data-ttu-id="8375c-116">FILESTREAM 열을 만들거나 FILESTREAM 열이 있는 기존 열을 검색 하려면 `is_filestream` [sys. columns](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql) 카탈로그 뷰의 열을 사용 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8375c-116">To create FILESTREAM columns or to detect which existing columns are FILESTREAM columns, you can use the `is_filestream` column of the [sys.columns](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="8375c-117">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8375c-117">The following is an example:</span></span>  
  
```  
-- Create a table with a FILESTREAM column.  
CREATE TABLE Bob_01 (GuidCol1 uniqueidentifier ROWGUIDCOL NOT NULL UNIQUE DEFAULT NEWID(), IntCol2 int, varbinaryCol3 varbinary(max) FILESTREAM);  
  
-- Find FILESTREAM columns.  
SELECT name FROM sys.columns WHERE is_filestream=1;  
  
-- Determine whether a column is a FILESTREAM column.  
SELECT is_filestream FROM sys.columns WHERE name = 'varbinaryCol3' AND object_id IN (SELECT object_id FROM sys.tables WHERE name='Bob_01');  
```  
  
## <a name="down-level-compatibility"></a><span data-ttu-id="8375c-118">하위 수준과의 호환성</span><span class="sxs-lookup"><span data-stu-id="8375c-118">Down-Level Compatibility</span></span>  
 <span data-ttu-id="8375c-119">에 포함 된 Native Client 버전을 사용 하 여 클라이언트를 컴파일하면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssVersion2005](../../../includes/sscurrent-md.md)] `varbinary(max)` 동작이와 호환 됩니다 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="8375c-119">If your client was compiled using the version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client that was included with [!INCLUDE[ssVersion2005](../../../includes/sscurrent-md.md)], `varbinary(max)` behavior will be compatible with [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="8375c-120">즉, 반환되는 데이터의 최대 크기가 2GB로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="8375c-120">That is, the maximum size of returned data will be limited to 2 GB.</span></span> <span data-ttu-id="8375c-121">결과 값이 2GB보다 큰 경우 잘림이 발생하고 "문자열 데이터 오른쪽 잘림" 경고가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8375c-121">For result values larger that 2 GB, truncation will occur and a "string data right truncation" warning will be returned.</span></span>  
  
 <span data-ttu-id="8375c-122">데이터 형식 호환성을 80으로 설정하면 클라이언트 동작이 하위 수준 클라이언트 동작과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="8375c-122">When data-type compatibility is set to 80, client behavior will be consistent with down-level client behavior.</span></span>  
  
 <span data-ttu-id="8375c-123">SQLOLEDB 또는 Native Client 이전에 릴리스된 다른 공급자를 사용 하는 클라이언트의 [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] 경우 `varbinary(max)` 는 이미지에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="8375c-123">For clients that use SQLOLEDB or other providers that were released before the [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] Native Client, `varbinary(max)` will be mapped to image.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8375c-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8375c-124">See Also</span></span>  
 [<span data-ttu-id="8375c-125">SQL Server Native Client 기능</span><span class="sxs-lookup"><span data-stu-id="8375c-125">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
