---
title: Oracle CDC 인스턴스 데이터 형식 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: eec13d8d-c15a-4542-bfc4-da66b1a6bfe0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 71d4ce02db89c1bfd11fe9a3a3535fc92fbc49fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728595"
---
# <a name="oracle-cdc-instance-data-types"></a><span data-ttu-id="b95ee-102">Oracle CDC 인스턴스 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="b95ee-102">Oracle CDC Instance Data Types</span></span>
  <span data-ttu-id="b95ee-103">Oracle CDC 인스턴스는 대부분의 Oracle 데이터 형식을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b95ee-103">The Oracle CDC Instance supports most Oracle data types.</span></span> <span data-ttu-id="b95ee-104">다음 섹션에서는 지원되는 데이터 형식과 지원되지 않는 데이터 형식에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b95ee-104">The following sections describe the supported data types and the non-supported data types.</span></span>  
  
## <a name="supported-data-types"></a><span data-ttu-id="b95ee-105">지원되는 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="b95ee-105">Supported Data Types</span></span>  
 <span data-ttu-id="b95ee-106">다음 표에서는 캡처할 수 있는 Oracle 데이터 형식과 변경 테이블의 SQL Server 데이터 형식에 대한 기본 매핑에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b95ee-106">The following table describes the Oracle data types that can be captured and their default mapping to SQL Server data types in the change tables.</span></span> <span data-ttu-id="b95ee-107">원본 Oracle 테이블에 대한 캡처 인스턴스를 추가할 때 이러한 매핑 중 일부를 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b95ee-107">When adding a capture instance for a source Oracle table, you can override some of these mappings.</span></span>  
  
|<span data-ttu-id="b95ee-108">Oracle 데이터베이스 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="b95ee-108">Oracle Database Data Type</span></span>|<span data-ttu-id="b95ee-109">SQL Server 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="b95ee-109">SQL Server Data Type</span></span>|  
|-------------------------------|--------------------------|  
|<span data-ttu-id="b95ee-110">BINARY_FLOAT</span><span class="sxs-lookup"><span data-stu-id="b95ee-110">BINARY_FLOAT</span></span>|<span data-ttu-id="b95ee-111">real</span><span class="sxs-lookup"><span data-stu-id="b95ee-111">REAL</span></span>|  
|<span data-ttu-id="b95ee-112">BINARY_DOUBLE</span><span class="sxs-lookup"><span data-stu-id="b95ee-112">BINARY_DOUBLE</span></span>|<span data-ttu-id="b95ee-113">FLOAT</span><span class="sxs-lookup"><span data-stu-id="b95ee-113">FLOAT</span></span>|  
|<span data-ttu-id="b95ee-114">CHAR</span><span class="sxs-lookup"><span data-stu-id="b95ee-114">CHAR</span></span>|<span data-ttu-id="b95ee-115">NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="b95ee-115">NVARCHAR</span></span>|  
|<span data-ttu-id="b95ee-116">DATE</span><span class="sxs-lookup"><span data-stu-id="b95ee-116">DATE</span></span>|<span data-ttu-id="b95ee-117">DATETIME</span><span class="sxs-lookup"><span data-stu-id="b95ee-117">DATETIME</span></span>|  
|<span data-ttu-id="b95ee-118">FLOAT</span><span class="sxs-lookup"><span data-stu-id="b95ee-118">FLOAT</span></span>|<span data-ttu-id="b95ee-119">FLOAT</span><span class="sxs-lookup"><span data-stu-id="b95ee-119">FLOAT</span></span>|  
|<span data-ttu-id="b95ee-120">INT</span><span class="sxs-lookup"><span data-stu-id="b95ee-120">INT</span></span>|<span data-ttu-id="b95ee-121">NUMERIC(38)</span><span class="sxs-lookup"><span data-stu-id="b95ee-121">NUMERIC (38)</span></span>|  
|<span data-ttu-id="b95ee-122">INTERVAL</span><span class="sxs-lookup"><span data-stu-id="b95ee-122">INTERVAL</span></span>|<span data-ttu-id="b95ee-123">DATETIME</span><span class="sxs-lookup"><span data-stu-id="b95ee-123">DATETIME</span></span>|  
|<span data-ttu-id="b95ee-124">NCHAR</span><span class="sxs-lookup"><span data-stu-id="b95ee-124">NCHAR</span></span>|<span data-ttu-id="b95ee-125">NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="b95ee-125">NVARCHAR</span></span>|  
|<span data-ttu-id="b95ee-126">NUMBER</span><span class="sxs-lookup"><span data-stu-id="b95ee-126">NUMBER</span></span>|<span data-ttu-id="b95ee-127">FLOAT</span><span class="sxs-lookup"><span data-stu-id="b95ee-127">FLOAT</span></span>|  
|<span data-ttu-id="b95ee-128">NAVARCHAR2</span><span class="sxs-lookup"><span data-stu-id="b95ee-128">NAVARCHAR2</span></span>|<span data-ttu-id="b95ee-129">NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="b95ee-129">NVARCHAR</span></span>|  
|<span data-ttu-id="b95ee-130">RAW</span><span class="sxs-lookup"><span data-stu-id="b95ee-130">RAW</span></span>|<span data-ttu-id="b95ee-131">VARBINARY</span><span class="sxs-lookup"><span data-stu-id="b95ee-131">VARBINARY</span></span>|  
|<span data-ttu-id="b95ee-132">real</span><span class="sxs-lookup"><span data-stu-id="b95ee-132">REAL</span></span>|<span data-ttu-id="b95ee-133">FLOAT</span><span class="sxs-lookup"><span data-stu-id="b95ee-133">FLOAT</span></span>|  
|<span data-ttu-id="b95ee-134">timestamp</span><span class="sxs-lookup"><span data-stu-id="b95ee-134">TIMESTAMP</span></span>|<span data-ttu-id="b95ee-135">DATETIME2</span><span class="sxs-lookup"><span data-stu-id="b95ee-135">DATETIME2</span></span>|  
|<span data-ttu-id="b95ee-136">TIMESTAMP WITH TIME ZONE</span><span class="sxs-lookup"><span data-stu-id="b95ee-136">TIMESTAMP WITH TIME ZONE</span></span>|<span data-ttu-id="b95ee-137">VARCHAR(37)</span><span class="sxs-lookup"><span data-stu-id="b95ee-137">VARCHAR (37)</span></span>|  
|<span data-ttu-id="b95ee-138">TIMESTAMP WITH LOCAL TIME ZONE</span><span class="sxs-lookup"><span data-stu-id="b95ee-138">TIMESTAMP WITH LOCAL TIME ZONE</span></span>|<span data-ttu-id="b95ee-139">VARCHAR(37)</span><span class="sxs-lookup"><span data-stu-id="b95ee-139">VARCHAR (37)</span></span>|  
|<span data-ttu-id="b95ee-140">VARCHAR2</span><span class="sxs-lookup"><span data-stu-id="b95ee-140">VARCHAR2</span></span>|<span data-ttu-id="b95ee-141">VARCHAR</span><span class="sxs-lookup"><span data-stu-id="b95ee-141">VARCHAR</span></span>|  
|<span data-ttu-id="b95ee-142">XMLTYPE</span><span class="sxs-lookup"><span data-stu-id="b95ee-142">XMLTYPE</span></span>|<span data-ttu-id="b95ee-143">NVARCHAR(MAX)</span><span class="sxs-lookup"><span data-stu-id="b95ee-143">NVARCHAR (MAX)</span></span>|  
  
## <a name="non-supported-data-types"></a><span data-ttu-id="b95ee-144">지원되지 않는 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="b95ee-144">Non-Supported Data Types</span></span>  
 <span data-ttu-id="b95ee-145">다음 Oracle 데이터 형식 열이 있는 원본 Oracle 테이블은 캡처할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b95ee-145">Source Oracle tables with columns of the following Oracle data types cannot be captured.</span></span> <span data-ttu-id="b95ee-146">이러한 데이터 형식을 가진 캡처된 열은 null로 표시되지만, 값 변경은 캡처된 테이블의 변경 마스크에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b95ee-146">Captured columns with these data types will show as null; however, a change in their value is indicated in the change mask of the captured tables.</span></span>  
  
-   <span data-ttu-id="b95ee-147">LONG</span><span class="sxs-lookup"><span data-stu-id="b95ee-147">LONG</span></span>  
  
-   <span data-ttu-id="b95ee-148">XMLTYPE</span><span class="sxs-lookup"><span data-stu-id="b95ee-148">XMLTYPE</span></span>  
  
-   <span data-ttu-id="b95ee-149">BLOB</span><span class="sxs-lookup"><span data-stu-id="b95ee-149">BLOB</span></span>  
  
-   <span data-ttu-id="b95ee-150">CLOB</span><span class="sxs-lookup"><span data-stu-id="b95ee-150">CLOB</span></span>  
  
 <span data-ttu-id="b95ee-151">다음 Oracle 데이터 형식 열이 있는 원본 Oracle 테이블은 캡처할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b95ee-151">Source Oracle tables with columns of the following Oracle data types cannot be captured.</span></span>  
  
-   <span data-ttu-id="b95ee-152">BFILE</span><span class="sxs-lookup"><span data-stu-id="b95ee-152">BFILE</span></span>  
  
-   <span data-ttu-id="b95ee-153">ROWID</span><span class="sxs-lookup"><span data-stu-id="b95ee-153">ROWID</span></span>  
  
-   <span data-ttu-id="b95ee-154">REF</span><span class="sxs-lookup"><span data-stu-id="b95ee-154">REF</span></span>  
  
-   <span data-ttu-id="b95ee-155">UROWID</span><span class="sxs-lookup"><span data-stu-id="b95ee-155">UROWID</span></span>  
  
-   <span data-ttu-id="b95ee-156">중첩 테이블</span><span class="sxs-lookup"><span data-stu-id="b95ee-156">Nested Table</span></span>  
  
 <span data-ttu-id="b95ee-157">다음 데이터 형식이 테이블에 있는 경우 LogMinder가 테이블 열에 대한 데이터를 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b95ee-157">If the following data types are present in a table they will prevent the LogMinder from getting any data for any column of the table:</span></span>  
  
-   <span data-ttu-id="b95ee-158">사용자 정의 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="b95ee-158">User-defined data types</span></span>  
  
-   <span data-ttu-id="b95ee-159">VARRAY</span><span class="sxs-lookup"><span data-stu-id="b95ee-159">VARRAY</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b95ee-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b95ee-160">See Also</span></span>  
 <span data-ttu-id="b95ee-161">[Change Data Capture Designer for Oracle by Attunity](change-data-capture-designer-for-oracle-by-attunity.md) </span><span class="sxs-lookup"><span data-stu-id="b95ee-161">[Change Data Capture Designer for Oracle by Attunity](change-data-capture-designer-for-oracle-by-attunity.md) </span></span>  
 [<span data-ttu-id="b95ee-162">Oracle CDC 인스턴스</span><span class="sxs-lookup"><span data-stu-id="b95ee-162">The Oracle CDC Instance</span></span>](the-oracle-cdc-instance.md)  
  
  
