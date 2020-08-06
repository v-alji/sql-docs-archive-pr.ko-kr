---
title: 대량 삽입 태스크 편집기 (연결 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.bulkinserttask.connection.f1
helpviewer_keywords:
- Bulk Insert Task Editor
ms.assetid: 51252c20-8865-4ede-a3fd-bd73a968f47d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b2cd722fd8520ff011c0d57040a55d624178e15e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738656"
---
# <a name="bulk-insert-task-editor-connection-page"></a><span data-ttu-id="8e648-102">대량 삽입 태스크 편집기(연결 페이지)</span><span class="sxs-lookup"><span data-stu-id="8e648-102">Bulk Insert Task Editor (Connection Page)</span></span>
  <span data-ttu-id="8e648-103">**대량 삽입 태스크 편집기** 대화 상자의 **연결** 페이지를 사용하여 대량 삽입 태스크의 원본 및 대상과 사용할 서식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e648-103">Use the **Connection** page of the **Bulk Insert Task Editor** dialog box to specify the source and destination of the bulk insert operation and the format to use.</span></span>  
  
 <span data-ttu-id="8e648-104">대량 삽입 작업에 대해 알아보려면 [대량 삽입 태스크](control-flow/bulk-insert-task.md) 및 [데이터를 가져오거나 내보내기 위한 서식 파일&#40;SQL Server&#41;](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8e648-104">To learn about working with bulk inserts, see [Bulk Insert Task](control-flow/bulk-insert-task.md) and [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8e648-105">옵션</span><span class="sxs-lookup"><span data-stu-id="8e648-105">Options</span></span>  
 <span data-ttu-id="8e648-106">**연결**</span><span class="sxs-lookup"><span data-stu-id="8e648-106">**Connection**</span></span>  
 <span data-ttu-id="8e648-107">목록에서 OLE DB 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8e648-107">Select an OLE DB connection manager in the list, or click \<**New connection...**> to create a new connection.</span></span>  
  
 <span data-ttu-id="8e648-108">**관련 항목:** [OLE DB 연결 관리자](connection-manager/ole-db-connection-manager.md), [OLE DB 연결 관리자 구성](../../2014/integration-services/configure-ole-db-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="8e648-108">**Related Topics:** [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md), [Configure OLE DB Connection Manager](../../2014/integration-services/configure-ole-db-connection-manager.md)</span></span>  
  
 <span data-ttu-id="8e648-109">**DestinationTable**</span><span class="sxs-lookup"><span data-stu-id="8e648-109">**DestinationTable**</span></span>  
 <span data-ttu-id="8e648-110">대상 테이블 또는 뷰의 이름을 입력하거나 목록에서 테이블 또는 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e648-110">Type the name of the destination table or view or select a table or view in the list.</span></span>  
  
 <span data-ttu-id="8e648-111">**형식**</span><span class="sxs-lookup"><span data-stu-id="8e648-111">**Format**</span></span>  
 <span data-ttu-id="8e648-112">대량 삽입을 위한 서식의 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e648-112">Select the source of the format for the bulk insert.</span></span> <span data-ttu-id="8e648-113">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e648-113">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="8e648-114">값</span><span class="sxs-lookup"><span data-stu-id="8e648-114">Value</span></span>|<span data-ttu-id="8e648-115">Description</span><span class="sxs-lookup"><span data-stu-id="8e648-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8e648-116">**파일 사용**</span><span class="sxs-lookup"><span data-stu-id="8e648-116">**Use File**</span></span>|<span data-ttu-id="8e648-117">서식 지정을 포함하는 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e648-117">Select a file containing the format specification.</span></span> <span data-ttu-id="8e648-118">이 옵션을 선택하면 동적 옵션 **FormatFile**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e648-118">Selecting this option displays the dynamic option, **FormatFile**.</span></span>|  
|<span data-ttu-id="8e648-119">**지정**</span><span class="sxs-lookup"><span data-stu-id="8e648-119">**Specify**</span></span>|<span data-ttu-id="8e648-120">서식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8e648-120">Specify the format.</span></span> <span data-ttu-id="8e648-121">이 옵션을 선택 하면 동적 옵션 및가 표시 됩니다 `RowDelimiter` `ColumnDelimiter` .</span><span class="sxs-lookup"><span data-stu-id="8e648-121">Selecting this option displays the dynamic options, `RowDelimiter` and `ColumnDelimiter`.</span></span>|  
  
 <span data-ttu-id="8e648-122">**최근에 사용한 파일**</span><span class="sxs-lookup"><span data-stu-id="8e648-122">**File**</span></span>  
 <span data-ttu-id="8e648-123">목록에서 파일 또는 플랫 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8e648-123">Select a File or Flat File connection manager in the list, or click \<**New connection...**> to create a new connection.</span></span>  
  
 <span data-ttu-id="8e648-124">파일 위치는 이 태스크를 위해 연결 관리자에 지정된 SQL Server 데이터베이스 엔진의 상대적 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="8e648-124">The file location is relative to the SQL Server Database Engine specified in the connection manager for this task.</span></span> <span data-ttu-id="8e648-125">텍스트 파일은 서버의 로컬 하드 드라이브에서 또는 SQL Server에 매핑된 드라이브 또는 공유 드라이브를 통해 SQL Server 데이터베이스 엔진이 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e648-125">The text file must be accessible by the SQL Server Database Engine either on a local hard drive on the server, or via a share or mapped drive to the SQL Server.</span></span> <span data-ttu-id="8e648-126">이 파일은 SSIS 런타임으로 액세스되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8e648-126">The file is not accessed by the SSIS Runtime.</span></span>  
  
 <span data-ttu-id="8e648-127">플랫 파일 연결 관리자를 사용하여 원본 파일에 액세스할 경우 대량 삽입 태스크에서는 플랫 파일 연결 관리자에서 지정한 서식을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8e648-127">If you access the source file by using a Flat File connection manager, the Bulk Insert task does not use the format specified in the Flat File connection manager.</span></span> <span data-ttu-id="8e648-128">대신 대량 삽입 태스크에서는 서식 파일에 지정된 서식이나 태스크의 RowDelimiter 및 ColumnDelimiter 속성 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8e648-128">Instead, the Bulk Insert task uses either the format specified in a format file or the values of the RowDelimiter and ColumnDelimiter properties of the task.</span></span>  
  
 <span data-ttu-id="8e648-129">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md), [플랫 파일 연결 관리자](connection-manager/flat-file-connection-manager.md), [플랫 파일 연결 관리자 편집기&#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md), [플랫 파일 연결 관리자 편집기&#40;열 페이지&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md), [플랫 파일 연결 관리자 편집기&#40;고급 페이지&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)</span><span class="sxs-lookup"><span data-stu-id="8e648-129">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md), [Flat File Connection Manager](connection-manager/flat-file-connection-manager.md), [Flat File Connection Manager Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md), [Flat File Connection Manager Editor &#40;Columns Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md), [Flat File Connection Manager Editor &#40;Advanced Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)</span></span>  
  
 <span data-ttu-id="8e648-130">**테이블 새로 고침**</span><span class="sxs-lookup"><span data-stu-id="8e648-130">**Refresh Tables**</span></span>  
 <span data-ttu-id="8e648-131">테이블 및 뷰 목록을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="8e648-131">Refresh the list of tables and views.</span></span>  
  
## <a name="format-dynamic-options"></a><span data-ttu-id="8e648-132">Format 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="8e648-132">Format Dynamic Options</span></span>  
  
### <a name="format--use-file"></a><span data-ttu-id="8e648-133">Format = 파일 사용</span><span class="sxs-lookup"><span data-stu-id="8e648-133">Format = Use File</span></span>  
 <span data-ttu-id="8e648-134">**FormatFile**</span><span class="sxs-lookup"><span data-stu-id="8e648-134">**FormatFile**</span></span>  
 <span data-ttu-id="8e648-135">서식 파일의 경로를 입력하거나 줄임표 단추 **(...)** 를 클릭하여 서식 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8e648-135">Type the path of the format file or click the ellipsis button **(...)** to locate the format file.</span></span>  
  
### <a name="format--specify"></a><span data-ttu-id="8e648-136">Format = 지정</span><span class="sxs-lookup"><span data-stu-id="8e648-136">Format = Specify</span></span>  
 `RowDelimiter`  
 <span data-ttu-id="8e648-137">원본 파일의 행 구분 기호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8e648-137">Specify the row delimiter in the source file.</span></span> <span data-ttu-id="8e648-138">기본값은 **{CR}{LF}** 입니다.</span><span class="sxs-lookup"><span data-stu-id="8e648-138">The default value is **{CR}{LF}**.</span></span>  
  
 `ColumnDelimiter`  
 <span data-ttu-id="8e648-139">원본 파일의 열 구분 기호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8e648-139">Specify the column delimiter in the source file.</span></span> <span data-ttu-id="8e648-140">기본값은 **탭**입니다.</span><span class="sxs-lookup"><span data-stu-id="8e648-140">The default is **Tab**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e648-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8e648-141">See Also</span></span>  
 <span data-ttu-id="8e648-142">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="8e648-142">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="8e648-143">[대량 삽입 태스크 편집기 &#40;일반 페이지&#41;](../../2014/integration-services/bulk-insert-task-editor-general-page.md) </span><span class="sxs-lookup"><span data-stu-id="8e648-143">[Bulk Insert Task Editor &#40;General Page&#41;](../../2014/integration-services/bulk-insert-task-editor-general-page.md) </span></span>  
 <span data-ttu-id="8e648-144">[대량 삽입 태스크 편집기 &#40;옵션 페이지&#41;](../../2014/integration-services/bulk-insert-task-editor-options-page.md) </span><span class="sxs-lookup"><span data-stu-id="8e648-144">[Bulk Insert Task Editor &#40;Options Page&#41;](../../2014/integration-services/bulk-insert-task-editor-options-page.md) </span></span>  
 <span data-ttu-id="8e648-145">[식 페이지](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="8e648-145">[Expressions Page](expressions/expressions-page.md) </span></span>  
 <span data-ttu-id="8e648-146">[BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8e648-146">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 [<span data-ttu-id="8e648-147">제어 흐름</span><span class="sxs-lookup"><span data-stu-id="8e648-147">Control Flow</span></span>](control-flow/control-flow.md)  
  
  
