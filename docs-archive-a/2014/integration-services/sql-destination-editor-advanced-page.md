---
title: SQL 대상 편집기 (고급 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlserverdestadapter.advanced.f1
helpviewer_keywords:
- SQL Server Destination Editor
ms.assetid: 9b46bcf8-ddaf-4d7d-90a6-80bc19517e9b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ccf25ad888c93f694678a152417affe5c0e16091
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647748"
---
# <a name="sql-destination-editor-advanced-page"></a><span data-ttu-id="3412b-102">SQL 대상 편집기(고급 페이지)</span><span class="sxs-lookup"><span data-stu-id="3412b-102">SQL Destination Editor (Advanced Page)</span></span>
  <span data-ttu-id="3412b-103">**SQL 대상 편집기** 대화 상자의 **고급** 페이지를 사용하여 고급 대량 삽입 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-103">Use the **Advanced** page of the **SQL Destination Editor** dialog box to specify advanced bulk insert options.</span></span>  
  
 <span data-ttu-id="3412b-104">SQL Server 대상에 대한 자세한 내용은 [SQL Server Destination](data-flow/sql-server-destination.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3412b-104">To learn more about the SQL Server destination, see [SQL Server Destination](data-flow/sql-server-destination.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="3412b-105">옵션</span><span class="sxs-lookup"><span data-stu-id="3412b-105">Options</span></span>  
 <span data-ttu-id="3412b-106">**ID 유지**</span><span class="sxs-lookup"><span data-stu-id="3412b-106">**Keep identity**</span></span>  
 <span data-ttu-id="3412b-107">태스크에서 ID 열에 값을 삽입할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-107">Specify whether the task should insert values into identity columns.</span></span> <span data-ttu-id="3412b-108">이 속성의 기본값은 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-108">The default value of this property is `False`.</span></span>  
  
 <span data-ttu-id="3412b-109">**Null 유지**</span><span class="sxs-lookup"><span data-stu-id="3412b-109">**Keep nulls**</span></span>  
 <span data-ttu-id="3412b-110">태스크에서 Null 값을 유지할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-110">Specify whether the task should keep null values.</span></span> <span data-ttu-id="3412b-111">이 속성의 기본값은 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-111">The default value of this property is `False`.</span></span>  
  
 <span data-ttu-id="3412b-112">**테이블 잠금**</span><span class="sxs-lookup"><span data-stu-id="3412b-112">**Table lock**</span></span>  
 <span data-ttu-id="3412b-113">데이터를 로드할 때 테이블을 잠글지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-113">Specify whether the table is locked when the data is loaded.</span></span> <span data-ttu-id="3412b-114">이 속성의 기본값은 `True`입니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-114">The default value of this property is `True`.</span></span>  
  
 <span data-ttu-id="3412b-115">**CHECK 제약 조건**</span><span class="sxs-lookup"><span data-stu-id="3412b-115">**Check constraints**</span></span>  
 <span data-ttu-id="3412b-116">태스크에서 제약 조건을 확인할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-116">Specify whether the task should check constraints.</span></span> <span data-ttu-id="3412b-117">이 속성의 기본값은 `True`입니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-117">The default value of this property is `True`.</span></span>  
  
 <span data-ttu-id="3412b-118">**트리거 실행**</span><span class="sxs-lookup"><span data-stu-id="3412b-118">**Fire triggers**</span></span>  
 <span data-ttu-id="3412b-119">대량 삽입에서 테이블에 대해 트리거를 실행할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-119">Specify whether the bulk insert should fire triggers on tables.</span></span> <span data-ttu-id="3412b-120">이 속성의 기본값은 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-120">The default value of this property is `False`.</span></span>  
  
 <span data-ttu-id="3412b-121">**첫 번째 행**</span><span class="sxs-lookup"><span data-stu-id="3412b-121">**First Row**</span></span>  
 <span data-ttu-id="3412b-122">삽입할 첫 번째 행을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-122">Specify the first row to insert.</span></span> <span data-ttu-id="3412b-123">이 속성의 기본값은 값이 할당 되지 않음을 나타내는 **-1**입니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-123">The default value of this property is **-1**, indicating that no value has been assigned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3412b-124">이 속성에 값을 할당하지 않으려면 **SQL 대상 편집기** 에서 해당 입력란의 내용을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-124">Clear the text box in the **SQL Destination Editor** to indicate that you do not want to assign a value for this property.</span></span> <span data-ttu-id="3412b-125">**속성** 창, **고급 편집기**및 개체 모델에 -1을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-125">Use -1 in the **Properties** window, the **Advanced Editor**, and the object model.</span></span>  
  
 <span data-ttu-id="3412b-126">**마지막 행**</span><span class="sxs-lookup"><span data-stu-id="3412b-126">**Last Row**</span></span>  
 <span data-ttu-id="3412b-127">삽입할 마지막 행을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-127">Specify the last row to insert.</span></span> <span data-ttu-id="3412b-128">이 속성의 기본값은 값이 할당 되지 않음을 나타내는 **-1**입니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-128">The default value of this property is **-1**, indicating that no value has been assigned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3412b-129">이 속성에 값을 할당하지 않으려면 **SQL 대상 편집기** 에서 해당 입력란의 내용을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-129">Clear the text box in the **SQL Destination Editor** to indicate that you do not want to assign a value for this property.</span></span> <span data-ttu-id="3412b-130">**속성** 창, **고급 편집기**및 개체 모델에 -1을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-130">Use -1 in the **Properties** window, the **Advanced Editor**, and the object model.</span></span>  
  
 <span data-ttu-id="3412b-131">**최대 오류 수**</span><span class="sxs-lookup"><span data-stu-id="3412b-131">**Maximum number of errors**</span></span>  
 <span data-ttu-id="3412b-132">대량 삽입이 중지되기 전에 발생할 수 있는 오류 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-132">Specify the number of errors that can occur before the bulk insert stops.</span></span> <span data-ttu-id="3412b-133">이 속성의 기본값은 값이 할당 되지 않음을 나타내는 **-1**입니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-133">The default value of this property is **-1**, indicating that no value has been assigned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3412b-134">이 속성에 값을 할당하지 않으려면 **SQL 대상 편집기** 에서 해당 입력란의 내용을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-134">Clear the text box in the **SQL Destination Editor** to indicate that you do not want to assign a value for this property.</span></span> <span data-ttu-id="3412b-135">**속성** 창, **고급 편집기**및 개체 모델에 -1을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-135">Use -1 in the **Properties** window, the **Advanced Editor**, and the object model.</span></span>  
  
 <span data-ttu-id="3412b-136">**Timeout**</span><span class="sxs-lookup"><span data-stu-id="3412b-136">**Timeout**</span></span>  
 <span data-ttu-id="3412b-137">시간이 초과되어 대량 삽입이 중지되기까지 기다리는 시간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-137">Specify the number of seconds to wait before the bulk insert stops because of a time-out.</span></span>  
  
 <span data-ttu-id="3412b-138">**열 순서 지정**</span><span class="sxs-lookup"><span data-stu-id="3412b-138">**Order columns**</span></span>  
 <span data-ttu-id="3412b-139">정렬 열의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-139">Type the names of the sort columns.</span></span> <span data-ttu-id="3412b-140">각 열을 오름차순이나 내림차순으로 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-140">Each column can be sorted in ascending or descending order.</span></span> <span data-ttu-id="3412b-141">여러 정렬 열을 사용하는 경우 쉼표로 목록을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="3412b-141">If you use multiple sort columns, delimit the list with commas.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3412b-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3412b-142">See Also</span></span>  
 <span data-ttu-id="3412b-143">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3412b-143">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="3412b-144">[SQL 대상 편집기 &#40;연결 관리자 페이지&#41;](../../2014/integration-services/sql-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="3412b-144">[SQL Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/sql-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="3412b-145">[SQL 대상 편집기 &#40;매핑 페이지&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="3412b-145">[SQL Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md) </span></span>  
 [<span data-ttu-id="3412b-146">SQL Server 대상을 사용하여 데이터 대량 로드</span><span class="sxs-lookup"><span data-stu-id="3412b-146">Bulk Load Data by Using the SQL Server Destination</span></span>](data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  
