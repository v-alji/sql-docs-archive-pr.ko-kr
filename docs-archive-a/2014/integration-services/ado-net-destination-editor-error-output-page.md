---
title: ADO NET 대상 편집기 (오류 출력 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetdest.erroroutput.f1
ms.assetid: 1a56c3cf-fb6a-416d-a62c-bb19fe441ae5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b9cfd69d3adec2aa617f5e9d3add35a1a6923804
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651232"
---
# <a name="ado-net-destination-editor-error-output-page"></a><span data-ttu-id="93dc0-102">ADO NET 대상 편집기(오류 출력 페이지)</span><span class="sxs-lookup"><span data-stu-id="93dc0-102">ADO NET Destination Editor (Error Output Page)</span></span>
  <span data-ttu-id="93dc0-103">**ADO NET 대상 편집기** 대화 상자의 **오류 출력** 페이지를 사용하여 오류 처리 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93dc0-103">Use the **Error Output** page of the **ADO NET Destination Editor** dialog box to specify error handling options.</span></span>  
  
 <span data-ttu-id="93dc0-104">ADO NET 대상에 대한 자세한 내용은 [ADO NET Destination](data-flow/ado-net-destination.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="93dc0-104">To learn more about the ADO NET destination, see [ADO NET Destination](data-flow/ado-net-destination.md).</span></span>  
  
 <span data-ttu-id="93dc0-105">**오류 출력 페이지를 열려면**</span><span class="sxs-lookup"><span data-stu-id="93dc0-105">**To open the Error Output page**</span></span>  
  
1.  <span data-ttu-id="93dc0-106">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 ADO NET 대상이 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="93dc0-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET destination.</span></span>  
  
2.  <span data-ttu-id="93dc0-107">**데이터 흐름** 탭에서 ADO NET 대상을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93dc0-107">On the **Data Flow** tab, double-click the ADO NET destination.</span></span>  
  
3.  <span data-ttu-id="93dc0-108">**ADO NET 대상 편집기**에서 **오류 출력**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93dc0-108">In the **ADO NET Destination Editor**, click **Error Output**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="93dc0-109">옵션</span><span class="sxs-lookup"><span data-stu-id="93dc0-109">Options</span></span>  
 <span data-ttu-id="93dc0-110">**입력 또는 출력**</span><span class="sxs-lookup"><span data-stu-id="93dc0-110">**Input or Output**</span></span>  
 <span data-ttu-id="93dc0-111">입력 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="93dc0-111">View the name of the input.</span></span>  
  
 <span data-ttu-id="93dc0-112">**열**</span><span class="sxs-lookup"><span data-stu-id="93dc0-112">**Column**</span></span>  
 <span data-ttu-id="93dc0-113">사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93dc0-113">Not used.</span></span>  
  
 <span data-ttu-id="93dc0-114">**오류**</span><span class="sxs-lookup"><span data-stu-id="93dc0-114">**Error**</span></span>  
 <span data-ttu-id="93dc0-115">오류가 발생할 경우 수행할 동작을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93dc0-115">Specify what should happen when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="93dc0-116">**관련 항목:** [데이터 오류 처리](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="93dc0-116">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="93dc0-117">**잘림**</span><span class="sxs-lookup"><span data-stu-id="93dc0-117">**Truncation**</span></span>  
 <span data-ttu-id="93dc0-118">사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93dc0-118">Not used.</span></span>  
  
 <span data-ttu-id="93dc0-119">**설명**</span><span class="sxs-lookup"><span data-stu-id="93dc0-119">**Description**</span></span>  
 <span data-ttu-id="93dc0-120">작업에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="93dc0-120">View the description of the operation.</span></span>  
  
 <span data-ttu-id="93dc0-121">**이 값을 선택한 셀에 설정**</span><span class="sxs-lookup"><span data-stu-id="93dc0-121">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="93dc0-122">오류나 잘림 발생 시 선택한 모든 셀에 수행할 동작을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93dc0-122">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="93dc0-123">**적용**</span><span class="sxs-lookup"><span data-stu-id="93dc0-123">**Apply**</span></span>  
 <span data-ttu-id="93dc0-124">선택한 셀에 오류 처리 옵션을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="93dc0-124">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93dc0-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="93dc0-125">See Also</span></span>  
 <span data-ttu-id="93dc0-126">[ADO NET 대상 편집기 &#40;연결 관리자 페이지&#41;](../../2014/integration-services/ado-net-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="93dc0-126">[ADO NET Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/ado-net-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="93dc0-127">ADO NET 대상 편집기&#40;매핑 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="93dc0-127">ADO NET Destination Editor &#40;Mappings Page&#41;</span></span>](../../2014/integration-services/ado-net-destination-editor-mappings-page.md)  
  
  
