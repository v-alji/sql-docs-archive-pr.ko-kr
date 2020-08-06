---
title: 대량 삽입 태스크 편집기 (옵션 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.bulkinserttask.options.f1
helpviewer_keywords:
- Bulk Insert Task Editor
ms.assetid: b3702811-3eb8-4b28-9190-5ae7a1a7bb6f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1751d1e0ac01d5459a8c76e6a48626c2ad6deafd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738643"
---
# <a name="bulk-insert-task-editor-options-page"></a><span data-ttu-id="da508-102">대량 삽입 태스크 편집기(옵션 페이지)</span><span class="sxs-lookup"><span data-stu-id="da508-102">Bulk Insert Task Editor (Options Page)</span></span>
  <span data-ttu-id="da508-103">**대량 삽입 태스크 편집기** 대화 상자의 **옵션** 페이지를 사용하여 대량 삽입 작업에 대한 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da508-103">Use the **Options** page of the **Bulk Insert Task Editor** dialog box to set properties for the bulk insert operation.</span></span> <span data-ttu-id="da508-104">대량 삽입 태스크는 대량의 데이터를 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 테이블 또는 뷰로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="da508-104">The Bulk Insert task copies large amounts of data into a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] table or view.</span></span>  
  
 <span data-ttu-id="da508-105">대량 삽입 작업에 대한 자세한 내용은 [대량 삽입 태스크](control-flow/bulk-insert-task.md) 및 [BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="da508-105">To learn about working with bulk inserts, see [Bulk Insert Task](control-flow/bulk-insert-task.md) and [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
## <a name="options"></a><span data-ttu-id="da508-106">옵션</span><span class="sxs-lookup"><span data-stu-id="da508-106">Options</span></span>  
 <span data-ttu-id="da508-107">**CodePage**</span><span class="sxs-lookup"><span data-stu-id="da508-107">**CodePage**</span></span>  
 <span data-ttu-id="da508-108">데이터 파일에서 데이터의 코드 페이지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="da508-108">Specify the code page of the data in the data file.</span></span>  
  
 <span data-ttu-id="da508-109">**DataFileType**</span><span class="sxs-lookup"><span data-stu-id="da508-109">**DataFileType**</span></span>  
 <span data-ttu-id="da508-110">로드 작업에 사용할 데이터 형식 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="da508-110">Specify the data-type value to use in the load operation.</span></span>  
  
 <span data-ttu-id="da508-111">**BatchSize**</span><span class="sxs-lookup"><span data-stu-id="da508-111">**BatchSize**</span></span>  
 <span data-ttu-id="da508-112">일괄 처리의 행 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="da508-112">Specify the number of rows in a batch.</span></span> <span data-ttu-id="da508-113">전체 데이터 파일이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="da508-113">The default is the entire data file.</span></span> <span data-ttu-id="da508-114">**BatchSize** 를 0으로 설정하면 데이터가 단일 일괄 처리로 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="da508-114">If you set **BatchSize** to zero, the data is loaded in a single batch.</span></span>  
  
 <span data-ttu-id="da508-115">**LastRow**</span><span class="sxs-lookup"><span data-stu-id="da508-115">**LastRow**</span></span>  
 <span data-ttu-id="da508-116">복사할 마지막 행을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="da508-116">Specify the last row to copy.</span></span>  
  
 <span data-ttu-id="da508-117">**FirstRow**</span><span class="sxs-lookup"><span data-stu-id="da508-117">**FirstRow**</span></span>  
 <span data-ttu-id="da508-118">복사를 시작할 처음 행을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="da508-118">Specify the first row from which to start copying.</span></span>  
  
 <span data-ttu-id="da508-119">**옵션**</span><span class="sxs-lookup"><span data-stu-id="da508-119">**Options**</span></span>  
 |<span data-ttu-id="da508-120">용어</span><span class="sxs-lookup"><span data-stu-id="da508-120">Term</span></span>|<span data-ttu-id="da508-121">정의</span><span class="sxs-lookup"><span data-stu-id="da508-121">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="da508-122">**CHECK 제약 조건**</span><span class="sxs-lookup"><span data-stu-id="da508-122">**Check constraints**</span></span>|<span data-ttu-id="da508-123">테이블 및 열 제약 조건을 확인하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="da508-123">Select to check the table and column constraints.</span></span>|  
|<span data-ttu-id="da508-124">**Null 유지**</span><span class="sxs-lookup"><span data-stu-id="da508-124">**Keep nulls**</span></span>|<span data-ttu-id="da508-125">대량 삽입 작업 중에 빈 열에 기본값을 삽입하는 대신 Null 값을 유지하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="da508-125">Select to retain null values during the bulk insert operation, instead of inserting any default values for empty columns.</span></span>|  
|<span data-ttu-id="da508-126">**ID 삽입 가능**</span><span class="sxs-lookup"><span data-stu-id="da508-126">**Enable identity insert**</span></span>|<span data-ttu-id="da508-127">기존 값을 ID 열에 삽입하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="da508-127">Select to insert existing values into an identity column.</span></span>|  
|<span data-ttu-id="da508-128">**테이블 잠금**</span><span class="sxs-lookup"><span data-stu-id="da508-128">**Table lock**</span></span>|<span data-ttu-id="da508-129">대량 삽입 중에 테이블을 잠그려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="da508-129">Select to lock the table during the bulk insert.</span></span>|  
|<span data-ttu-id="da508-130">**트리거 실행**</span><span class="sxs-lookup"><span data-stu-id="da508-130">**Fire triggers**</span></span>|<span data-ttu-id="da508-131">테이블에 삽입, 업데이트 또는 삭제 트리거를 발생시키려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="da508-131">Select to fire any insert, update, or delete triggers on the table.</span></span>|  
  
 <span data-ttu-id="da508-132">**SortedData**</span><span class="sxs-lookup"><span data-stu-id="da508-132">**SortedData**</span></span>  
 <span data-ttu-id="da508-133">대량 삽입 문에 ORDER BY 절을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="da508-133">Specify the ORDER BY clause in the bulk insert statement.</span></span> <span data-ttu-id="da508-134">사용자가 제공한 열 이름은 대상 테이블에서 유효한 열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da508-134">The column name that you supply must be a valid column in the destination table.</span></span> <span data-ttu-id="da508-135">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="da508-135">The default is `false`.</span></span> <span data-ttu-id="da508-136">즉, 데이터는 ORDER BY 절로 정렬되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="da508-136">This means that the data is not sorted by an ORDER BY clause.</span></span>  
  
 <span data-ttu-id="da508-137">**MaxErrors**</span><span class="sxs-lookup"><span data-stu-id="da508-137">**MaxErrors**</span></span>  
 <span data-ttu-id="da508-138">대량 삽입 작업이 취소되는 최대 오류 발생 횟수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="da508-138">Specify the maximum number of errors that can occur before the bulk insert operation is canceled.</span></span> <span data-ttu-id="da508-139">값을 0으로 지정하면 오류가 무한으로 발생해도 작업이 취소되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="da508-139">A value of 0 indicates that an infinite number of errors are allowed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="da508-140">대량 로드 작업으로 가져올 수 없는 각 행은 하나의 오류로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="da508-140">Each row that cannot be imported by the bulk load operation is counted as one error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da508-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="da508-141">See Also</span></span>  
 <span data-ttu-id="da508-142">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="da508-142">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="da508-143">[대량 삽입 태스크 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="da508-143">[Bulk Insert Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="da508-144">[대량 삽입 태스크 편집기 &#40;연결 페이지&#41;](../../2014/integration-services/bulk-insert-task-editor-connection-page.md) </span><span class="sxs-lookup"><span data-stu-id="da508-144">[Bulk Insert Task Editor &#40;Connection Page&#41;](../../2014/integration-services/bulk-insert-task-editor-connection-page.md) </span></span>  
 <span data-ttu-id="da508-145">[식 페이지](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="da508-145">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="da508-146">제어 흐름</span><span class="sxs-lookup"><span data-stu-id="da508-146">Control Flow</span></span>](control-flow/control-flow.md)  
  
  
