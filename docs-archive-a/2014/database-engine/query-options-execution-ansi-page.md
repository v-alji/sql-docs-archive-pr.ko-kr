---
title: 쿼리 옵션 실행 (ANSI 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.ansi.f1
ms.assetid: c90d7cdf-3309-46f4-b900-220521bb9552
author: rothja
ms.author: jroth
ms.openlocfilehash: 013a7a318ed7f8db9156700f789ae64cf3e4e017
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735539"
---
# <a name="query-options-execution-ansi-page"></a><span data-ttu-id="b12c3-102">쿼리 옵션 실행(ANSI 페이지)</span><span class="sxs-lookup"><span data-stu-id="b12c3-102">Query Options Execution (ANSI Page)</span></span>
  <span data-ttu-id="b12c3-103">이 페이지를 사용 하 여에서 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ISO (ANSI) 표준에 지정 된 설정의 일부 또는 전부를 사용 하 여 쿼리를 실행 하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-103">Use this page to specify that [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will run the queries using all or a portion of the settings specified in the ISO (ANSI) standard.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="b12c3-104">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="b12c3-104">UI element list</span></span>  
 <span data-ttu-id="b12c3-105">**SET ANSI_DEFAULTS**</span><span class="sxs-lookup"><span data-stu-id="b12c3-105">**SET ANSI_DEFAULTS**</span></span>  
 <span data-ttu-id="b12c3-106">기본 ISO 설정을 모두 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-106">Select all of the default ISO settings.</span></span> <span data-ttu-id="b12c3-107">일부 ISO 설정만 구성되어 있으므로 이 상자는 기본적으로 비활성화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-107">This box is unavailable by default, because only some of the ISO settings are configured.</span></span>  
  
 <span data-ttu-id="b12c3-108">**SET QUOTED_IDENTIFIER**</span><span class="sxs-lookup"><span data-stu-id="b12c3-108">**SET QUOTED_IDENTIFIER**</span></span>  
 <span data-ttu-id="b12c3-109">개체 식별자 앞뒤에 따옴표를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-109">Surround object identifiers with quotation marks.</span></span> <span data-ttu-id="b12c3-110">이 옵션은 기본적으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-110">This option is selected by default.</span></span>  
  
 <span data-ttu-id="b12c3-111">**SET ANSI_NULL_DFLT_ON**</span><span class="sxs-lookup"><span data-stu-id="b12c3-111">**SET ANSI_NULL_DFLT_ON**</span></span>  
 <span data-ttu-id="b12c3-112">CREATE TABLE 또는 ALTER TABLE 문(기본 상태)을 실행하는 동안 NOT NULL로 명시적으로 정의되지 않은 모든 사용자 정의 데이터 형식 또는 열에서 Null 값을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-112">Allow null values for all user-defined data types or columns that are not explicitly defined as NOTNULL during a CREATE TABLE or ALTER TABLE statement (the default state).</span></span> <span data-ttu-id="b12c3-113">이 옵션은 기본적으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-113">This option is selected by default.</span></span>  
  
 <span data-ttu-id="b12c3-114">**SET IMPLICIT_TRANSACTIONS**</span><span class="sxs-lookup"><span data-stu-id="b12c3-114">**SET IMPLICIT_TRANSACTIONS**</span></span>  
 <span data-ttu-id="b12c3-115">이 옵션은 기본적으로 선택되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-115">This option is not selected by default.</span></span>  
  
 <span data-ttu-id="b12c3-116">**SET CURSOR_CLOSE_ON_COMMIT**</span><span class="sxs-lookup"><span data-stu-id="b12c3-116">**SET CURSOR_CLOSE_ON_COMMIT**</span></span>  
 <span data-ttu-id="b12c3-117">트랜잭션이 커밋되면 ISO에 따라 열려 있는 모든 커서를 자동으로 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-117">Close any open cursors automatically (in compliance with ISO) when a transaction is committed.</span></span> <span data-ttu-id="b12c3-118">이 옵션의 선택을 취소(OFF로 설정)하면 커서는 트랜잭션이 바뀌어도 계속 열려 있으며 연결이 닫히거나 커서를 명시적으로 닫아야만 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-118">When cleared (set to OFF), cursors remain open across transaction boundaries, closing only when the connection is closed or when they are explicitly closed.</span></span> <span data-ttu-id="b12c3-119">이 옵션은 기본적으로 선택되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-119">This option is not selected by default.</span></span>  
  
 <span data-ttu-id="b12c3-120">**SET ANSI_PADDING**</span><span class="sxs-lookup"><span data-stu-id="b12c3-120">**SET ANSI_PADDING**</span></span>  
 <span data-ttu-id="b12c3-121">열이 정의 된 열 크기 보다 짧은 값을 저장 하는 방법과 **char**, **varchar**, **binary**및 **varbinary** 데이터에 후행 공백이 있는 값을 저장 하는 방법을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-121">Controls the way the column stores values shorter than the defined size of the column, and the way the column stores values that have trailing blanks in **char**, **varchar**, **binary**, and **varbinary** data.</span></span> <span data-ttu-id="b12c3-122">이 설정은 새 열의 정의에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-122">This setting affects only the definition of new columns.</span></span> <span data-ttu-id="b12c3-123">열이 생성된 다음에는 열을 만들 때의 설정에 따라 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서 값을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-123">After the column is created, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] stores the values based on the setting when the column was created.</span></span> <span data-ttu-id="b12c3-124">나중에 이 설정을 변경해도 기존의 열은 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-124">Existing columns are not affected by a later change to this setting.</span></span> <span data-ttu-id="b12c3-125">이 확인란은 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-125">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="b12c3-126">**SET ANSI_WARNINGS**</span><span class="sxs-lookup"><span data-stu-id="b12c3-126">**SET ANSI_WARNINGS**</span></span>  
 <span data-ttu-id="b12c3-127">여러 오류 상황에 대한 ISO 표준 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-127">Specifies ISO standard behavior for several error conditions:</span></span>  
  
-   <span data-ttu-id="b12c3-128">이 확인란을 선택하면 SUM, AVG, MAX, MIN, STDEV, STDEVP, VAR, VARP 또는 COUNT와 같은 집계 함수에 Null 값이 나타나는 경우에 경고 메시지가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-128">When this check box is selected, if null values appear in aggregate functions (such as SUM, AVG, MAX, MIN, STDEV, STDEVP, VAR, VARP, or COUNT), a warning message is generated.</span></span> <span data-ttu-id="b12c3-129">**OFF**인 경우 경고가 발생 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-129">When **OFF**, no warning is issued.</span></span>  
  
-   <span data-ttu-id="b12c3-130">이 확인란의 선택을 취소한 경우 0으로 나누기 및 산술 오버플로 오류가 발생하면 문이 롤백되고 오류 메시지가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-130">When this check box is cleared, divide-by-zero and arithmetic overflow errors cause the statement to be rolled back and an error message is generated.</span></span> <span data-ttu-id="b12c3-131">OFF로 설정한 경우 0으로 나누기 및 산술 오버플로 오류가 발생하면 Null 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-131">When OFF, divide-by-zero and arithmetic overflow errors cause null values to be returned.</span></span> <span data-ttu-id="b12c3-132">새 값의 길이가 열의 최대 크기를 초과하는 character, Unicode 또는 binary 열에 INSERT나 UPDATE 작업을 하려고 하면 0으로 나누기 또는 산술 오버플로 오류로 인해 Null 값이 반환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-132">The behavior in which a divide-by-zero or arithmetic overflow error causes null values to be returned occurs if an INSERTor UPDATEoperation is attempted on a character, Unicode, or binary column in which the length of a new value exceeds the maximum size of the column.</span></span> <span data-ttu-id="b12c3-133">**SET ANSI_WARNINGS** ON 이면 ISO 표준에 지정 된 대로 삽입 또는 업데이트 작업이 취소 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-133">If **SET ANSI_WARNINGS** is ON, the INSERT or UPDATE operation is canceled as specified by the ISO standard.</span></span> <span data-ttu-id="b12c3-134">문자 열에 대해서는 후행 공백이, 이진 열에 대해서는 후행 Null 값이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-134">Trailing blanks are ignored for character columns, and trailing nulls are ignored for binary columns.</span></span> <span data-ttu-id="b12c3-135">이 옵션이 OFF이면 열의 크기에 맞게 데이터가 잘리고 문이 성공적으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-135">When OFF, data is truncated to the size of the column and the statement succeeds.</span></span>  
  
 <span data-ttu-id="b12c3-136">이 옵션은 기본적으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-136">This option is selected by default.</span></span>  
  
 <span data-ttu-id="b12c3-137">**SET ANSI_NULLS**</span><span class="sxs-lookup"><span data-stu-id="b12c3-137">**SET ANSI_NULLS**</span></span>  
 <span data-ttu-id="b12c3-138">같음(`=`)과 같지 않음(`<>`) 비교 연산자를 Null 값과 함께 사용할 경우의 ISO 호환 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-138">Specifies ISO compliant behavior of the Equal (`=`) and Not Equal to (`<>`) comparison operators when used with null values.</span></span> <span data-ttu-id="b12c3-139">**SET ANSI_NULLS** 를 선택하면 데이터와 Null 값을 비교한 결과가 ISO 호환 동작에 따라 UNKNOWN이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-139">When **SET ANSI_NULLS** is selected, all comparisons against a null value evaluate to UNKNOWN, the ISO compliant behavior.</span></span> <span data-ttu-id="b12c3-140">**SET ANSI_NULLS** 를 선택하지 않으면 데이터 값이 NULL일 때 Null 값에 대한 모든 데이터 비교의 결과가 TRUE가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-140">When **SET ANSI_NULLS** is not selected, comparisons of all data against a null value evaluate to TRUE if the data value is NULL.</span></span> <span data-ttu-id="b12c3-141">이 옵션은 기본적으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-141">This option is selected by default.</span></span>  
  
 <span data-ttu-id="b12c3-142">**기본값으로 다시 설정**</span><span class="sxs-lookup"><span data-stu-id="b12c3-142">**Reset to Default**</span></span>  
 <span data-ttu-id="b12c3-143">이 페이지의 모든 값을 원래 기본값으로 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b12c3-143">Resets all values on this page to the original default values.</span></span>  
  
  
