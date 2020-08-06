---
title: rrRenderingError - Reporting Services 오류 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rrRenderingError
ms.assetid: 0751efc3-b81b-44ee-8aac-8560f86ca322
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b44b042c5f3c0cfdb9ffb99d3f45ed073beb972a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732300"
---
# <a name="rrrenderingerror---reporting-services-error"></a><span data-ttu-id="4ba20-102">rrRenderingError - Reporting Services 오류</span><span class="sxs-lookup"><span data-stu-id="4ba20-102">rrRenderingError - Reporting Services Error</span></span>
    
## <a name="details"></a><span data-ttu-id="4ba20-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="4ba20-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4ba20-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="4ba20-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="4ba20-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="4ba20-105">Event ID</span></span>|<span data-ttu-id="4ba20-106">rrRenderingError</span><span class="sxs-lookup"><span data-stu-id="4ba20-106">rrRenderingError</span></span>|  
|<span data-ttu-id="4ba20-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="4ba20-107">Event Source</span></span>|<span data-ttu-id="4ba20-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings.resources.Strings</span><span class="sxs-lookup"><span data-stu-id="4ba20-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings.resources.Strings</span></span>|  
|<span data-ttu-id="4ba20-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="4ba20-109">Component</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="4ba20-110">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="4ba20-110">Message Text</span></span>|<span data-ttu-id="4ba20-111">보고서를 렌더링하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="4ba20-111">An error occurred during rendering of the report.</span></span> <span data-ttu-id="4ba20-112">(rrRenderingError) %1</span><span class="sxs-lookup"><span data-stu-id="4ba20-112">(rrRenderingError) %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4ba20-113">설명</span><span class="sxs-lookup"><span data-stu-id="4ba20-113">Explanation</span></span>  
 <span data-ttu-id="4ba20-114">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 에서 보고서를 렌더링할 수 없거나 내보낼 수 없을 때 이 메시지가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ba20-114">This message is returned when [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] cannot render or export the report.</span></span>  
  
 <span data-ttu-id="4ba20-115">크기가 지원되지 않음을 나타내는 메시지는 지정된 RDL 페이지 크기가 유효하지 않을 때 일반적으로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba20-115">A message that indicates that the size is not supported is typically caused when the specified RDL page size is not valid.</span></span> <span data-ttu-id="4ba20-116">유효한 RDL 페이지 크기를 지정한 다음 다시 시도하세요.</span><span class="sxs-lookup"><span data-stu-id="4ba20-116">Specify a valid RDL page size and then try again.</span></span>  
  
 <span data-ttu-id="4ba20-117">RDL 크기 단위가 지원되지 않음을 나타내는 메시지는 지원되지 않는 단위 유형이 지정되었을 때 일반적으로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba20-117">A message that indicates that an RDL size measurement is not supported is typically caused when an unsupported unit type is specified.</span></span> <span data-ttu-id="4ba20-118">유효한 단위 유형은 cm, in, mm, pc 및 pt입니다.</span><span class="sxs-lookup"><span data-stu-id="4ba20-118">Valid unit types are cm, in, mm, pc, and pt.</span></span> <span data-ttu-id="4ba20-119">유효한 단위 유형을 지정한 다음 다시 시도하세요.</span><span class="sxs-lookup"><span data-stu-id="4ba20-119">Specify a valid unit type and then try again.</span></span>  
  
 <span data-ttu-id="4ba20-120">음수 크기가 지원되지 않음을 나타내는 메시지는 페이지 크기의 음수 단위(예: -5cm)가 지정되었을 때 일반적으로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba20-120">A message that indicates that a negative size is not supported is typically caused when a negative measurement for the page size, for example -5 cm, is specified.</span></span> <span data-ttu-id="4ba20-121">페이지 크기에 대해 양수를 지정한 다음 다시 시도하세요.</span><span class="sxs-lookup"><span data-stu-id="4ba20-121">Specify a positive number for the page size and then try again.</span></span>  
  
 <span data-ttu-id="4ba20-122">범위를 벗어난 RDL 크기가 지정되었음을 나타내는 메시지는 페이지 크기 단위가 유효한 페이지 여백 크기 범위를 벗어났을 때 일반적으로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba20-122">A message that indicates that an RDL size is specified out of range is typically caused when a measurement for the page size is outside of the valid page margin size.</span></span> <span data-ttu-id="4ba20-123">유효한 페이지 여백 크기 내에 있는 페이지 크기 단위를 지정하세요.</span><span class="sxs-lookup"><span data-stu-id="4ba20-123">Specify a measurement for the page size that is within the valid page margin sizes.</span></span>  
  
 <span data-ttu-id="4ba20-124">지정된 색이 지원되지 않음을 나타내는 메시지는 RDL에 지정된 색이 유효하지 않을 때 일반적으로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba20-124">A message that indicates that a color specified is not supported is typically caused when a color specified in the RDL is not valid.</span></span> <span data-ttu-id="4ba20-125">RDL에서 지원하는 색을 변경한 다음 다시 시도하세요.</span><span class="sxs-lookup"><span data-stu-id="4ba20-125">Choose a color supported by RDL and then try again.</span></span>  
  
 <span data-ttu-id="4ba20-126">단일 동작을 사용하는 경우에만 동작 레이블이 선택 사항이고 여러 동작을 추가하려면 각 동작마다 레이블이 필요함을 나타내는 메시지는 유효하지 않은 동작 레이블이 지정되었을 때 일반적으로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba20-126">A message that indicates that the action label is only optional when using a single action and that adding multiple actions requires labels for each action is typically caused when an action label is specified and it is not valid.</span></span> <span data-ttu-id="4ba20-127">각 동작마다 유효한 동작 레이블을 지정하세요.</span><span class="sxs-lookup"><span data-stu-id="4ba20-127">Specify a valid action label for each action.</span></span>  
  
 <span data-ttu-id="4ba20-128">스타일 인수가 특정 유형이어야 함을 나타내는 메시지는 데이터 형식에 대해 잘못된 스타일 값이 지정되었을 때 일반적으로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba20-128">A message that indicates the style argument has to be of a specific type is typically caused when an incorrect style value for the data type is specified.</span></span> <span data-ttu-id="4ba20-129">RDL 사양은 다른 RDL 요소의 스타일 값에서 사용할 수 있는 유효한 유형을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba20-129">The RDL specification identifies the valid types that you can use in the style values of different RDL elements.</span></span> <span data-ttu-id="4ba20-130">예를 들어 배경색에 대해 잘못된 스타일 값은 "2pt"이고 높이에 대해 잘못된 값은 "true"입니다.</span><span class="sxs-lookup"><span data-stu-id="4ba20-130">For example, an incorrect style value for background color is "2pt" and incorrect value for height is "true".</span></span> <span data-ttu-id="4ba20-131">올바른 값을 지정한 다음 다시 시도하세요.</span><span class="sxs-lookup"><span data-stu-id="4ba20-131">Specify a correct value and then try again.</span></span>  
  
 <span data-ttu-id="4ba20-132">테두리 스타일이 지원되지 않음을 나타내는 메시지는 지정된 테두리 스타일이 유효하지 않을 때 일반적으로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba20-132">A message that indicates that the border style is not supported is typically caused when the border style specified is not valid.</span></span> <span data-ttu-id="4ba20-133">지원되는 테두리 스타일을 지정한 다음 다시 시도하세요.</span><span class="sxs-lookup"><span data-stu-id="4ba20-133">Specify a supported border style and then try again.</span></span>  
  
 <span data-ttu-id="4ba20-134">이미지 MIME 형식이 지원되지 않음을 나타내는 메시지는 이미지 보고서 항목에 대해 지정된 MIME 형식이 유효하지 않을 때 일반적으로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba20-134">A message that indicates that the image mimetype is not supported is typically caused when the specified mimetype for an image report item is not valid.</span></span> <span data-ttu-id="4ba20-135">보고서 항목에 대해 지원되는 MIME 형식을 지정한 다음 다시 시도하세요.</span><span class="sxs-lookup"><span data-stu-id="4ba20-135">Specify a supported mimetype for the report item and then try again.</span></span>  
  
 <span data-ttu-id="4ba20-136">행 개수가 시트에서 허용되는 최대 행 개수를 초과했음을 나타내는 메시지는 Excel 워크시트의 행 개수를 초과했을 때 일반적으로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba20-136">A message that indicates that the number of rows exceeds the maximum possible rows per sheet is typically caused when the number of rows in an Excel worksheet is exceeded.</span></span> <span data-ttu-id="4ba20-137">Excel에서는 최대 65,000개의 행을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba20-137">Excel supports up to 65,000 rows.</span></span>  
  
 <span data-ttu-id="4ba20-138">열 개수가 시트에서 허용되는 최대 열 개수를 초과했음을 나타내는 메시지는 Excel 워크시트의 열 개수를 초과했을 때 일반적으로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba20-138">A message that indicates that the number of columns exceeds the maximum possible columns per sheet is typically caused when the number of columns in an Excel worksheet is exceeded.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4ba20-139">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="4ba20-139">User Action</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="4ba20-140">내부 전용</span><span class="sxs-lookup"><span data-stu-id="4ba20-140">Internal-Only</span></span>  
  
