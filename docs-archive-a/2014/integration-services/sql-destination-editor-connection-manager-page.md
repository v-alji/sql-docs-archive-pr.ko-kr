---
title: SQL 대상 편집기 (연결 관리자 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlserverdestadapter.connection.f1
helpviewer_keywords:
- SQL Server Destination Editor
ms.assetid: 423e1654-54af-47c6-ab6f-98670534557d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4f3a552968cb297de337e1f0c406b444d95dc5a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649591"
---
# <a name="sql-destination-editor-connection-manager-page"></a><span data-ttu-id="9337b-102">SQL 대상 편집기(연결 관리자 페이지)</span><span class="sxs-lookup"><span data-stu-id="9337b-102">SQL Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="9337b-103">**SQL 대상 편집기** 대화 상자의 **연결 관리자** 페이지를 사용하여 데이터 원본 정보를 지정하고 결과를 미리 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9337b-103">Use the **Connection Manager** page of the **SQL Destination Editor** dialog box to specify data source information, and to preview the results.</span></span> <span data-ttu-id="9337b-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]대상은 데이터베이스의 테이블 또는 뷰로 데이터를 로드 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="9337b-104">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] destination loads data into tables or views in a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="9337b-105">SQL Server 대상에 대한 자세한 내용은 [SQL Server Destination](data-flow/sql-server-destination.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9337b-105">To learn more about the SQL Server destination, see [SQL Server Destination](data-flow/sql-server-destination.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="9337b-106">옵션</span><span class="sxs-lookup"><span data-stu-id="9337b-106">Options</span></span>  
 <span data-ttu-id="9337b-107">**캐시 없음**</span><span class="sxs-lookup"><span data-stu-id="9337b-107">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="9337b-108">목록에서 기존 연결을 선택하거나 **새로 만들기**를 클릭하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9337b-108">Select an existing connection from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="9337b-109">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="9337b-109">**New**</span></span>  
 <span data-ttu-id="9337b-110">**OLE DB 연결 관리자 구성** 대화 상자를 사용하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9337b-110">Create a new connection by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="9337b-111">**테이블 또는 뷰 사용**</span><span class="sxs-lookup"><span data-stu-id="9337b-111">**Use a table or view**</span></span>  
 <span data-ttu-id="9337b-112">목록에서 기존 테이블 또는 뷰를 선택하거나 **새로 만들기**를 클릭하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9337b-112">Select an existing table or view from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="9337b-113">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="9337b-113">**New**</span></span>  
 <span data-ttu-id="9337b-114">**테이블 만들기** 대화 상자를 사용하여 새 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9337b-114">Create a new table by using the **Create Table** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9337b-115">**새로 만들기**를 클릭하면 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 연결된 데이터 원본에 따라 기본 CREATE TABLE 문을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="9337b-115">When you click **New**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="9337b-116">원본 테이블에 선언된 FILESTREAM 특성이 포함된 열이 있어도 기본 CREATE TABLE 문은 FILESTREAM 특성을 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9337b-116">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="9337b-117">FILESTREAM 특성이 포함된 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 구성 요소를 실행하려면 먼저 대상 데이터베이스에서 FILESTREAM 스토리지를 구현하십시오.</span><span class="sxs-lookup"><span data-stu-id="9337b-117">To run an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="9337b-118">그런 다음 **테이블 만들기** 대화 상자에서 FILESTREAM 특성을 CREATE TABLE 문에 추가하십시오.</span><span class="sxs-lookup"><span data-stu-id="9337b-118">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="9337b-119">자세한 내용은 [Blob&#40;Binary Large Object&#41; 데이터&#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9337b-119">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="9337b-120">**미리 보기**</span><span class="sxs-lookup"><span data-stu-id="9337b-120">**Preview**</span></span>  
 <span data-ttu-id="9337b-121">**쿼리 결과 미리 보기** 대화 상자를 사용하여 결과를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="9337b-121">Preview results by using the **Preview Query Results** dialog box.</span></span> <span data-ttu-id="9337b-122">미리 보기에는 최대 200개의 행이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9337b-122">Preview can display up to 200 rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9337b-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9337b-123">See Also</span></span>  
 <span data-ttu-id="9337b-124">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9337b-124">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="9337b-125">[SQL 대상 편집기 &#40;매핑 페이지&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="9337b-125">[SQL Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="9337b-126">[SQL 대상 편집기 &#40;고급 페이지&#41;](../../2014/integration-services/sql-destination-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="9337b-126">[SQL Destination Editor &#40;Advanced Page&#41;](../../2014/integration-services/sql-destination-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="9337b-127">SQL Server 대상을 사용하여 데이터 대량 로드</span><span class="sxs-lookup"><span data-stu-id="9337b-127">Bulk Load Data by Using the SQL Server Destination</span></span>](data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  
