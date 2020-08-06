---
title: ADO NET 원본 편집기 (오류 출력 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetsource.erroroutput.f1
ms.assetid: 4dd9d129-a95c-4d3a-bbbf-e84a39089950
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b9ee480caa8764d70b52b25a416f200f353d30c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740257"
---
# <a name="ado-net-source-editor-error-output-page"></a><span data-ttu-id="fb541-102">ADO NET 원본 편집기(오류 출력 페이지)</span><span class="sxs-lookup"><span data-stu-id="fb541-102">ADO NET Source Editor (Error Output Page)</span></span>
  <span data-ttu-id="fb541-103">**ADO NET 원본 편집기** 대화 상자의 **오류 출력** 페이지를 사용하여 오류 처리 옵션을 선택하고 오류 출력 열에 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb541-103">Use the **Error Output** page of the **ADO NET Source Editor** dialog box to select error handling options and to set properties on error output columns.</span></span>  
  
 <span data-ttu-id="fb541-104">ADO NET 원본에 대한 자세한 내용은 [ADO NET Source](data-flow/ado-net-source.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="fb541-104">To learn more about the ADO NET source, see [ADO NET Source](data-flow/ado-net-source.md).</span></span>  
  
 <span data-ttu-id="fb541-105">**오류 출력 페이지를 열려면**</span><span class="sxs-lookup"><span data-stu-id="fb541-105">**To open the Error Output page**</span></span>  
  
1.  <span data-ttu-id="fb541-106">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 ADO NET 원본이 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fb541-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET source.</span></span>  
  
2.  <span data-ttu-id="fb541-107">**데이터 흐름** 탭에서 ADO NET 원본을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fb541-107">On the **Data Flow** tab, double-click the ADO NET source.</span></span>  
  
3.  <span data-ttu-id="fb541-108">**ADO NET 원본 편집기**에서 **오류 출력**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fb541-108">In the **ADO NET Source Editor**, click **Error Output**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fb541-109">옵션</span><span class="sxs-lookup"><span data-stu-id="fb541-109">Options</span></span>  
 <span data-ttu-id="fb541-110">**입/출력**</span><span class="sxs-lookup"><span data-stu-id="fb541-110">**Input/Output**</span></span>  
 <span data-ttu-id="fb541-111">데이터 원본의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fb541-111">View the name of the data source.</span></span>  
  
 <span data-ttu-id="fb541-112">**열**</span><span class="sxs-lookup"><span data-stu-id="fb541-112">**Column**</span></span>  
 <span data-ttu-id="fb541-113">**ADO NET 원본 편집기** 대화 상자의 **연결 관리자** 페이지에서 선택한 외부(원본) 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fb541-113">View the external (source) columns that you selected on the **Connection Manager** page of the **ADO NET Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="fb541-114">**오류**</span><span class="sxs-lookup"><span data-stu-id="fb541-114">**Error**</span></span>  
 <span data-ttu-id="fb541-115">오류가 발생할 경우 수행할 동작을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb541-115">Specify what should happen when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="fb541-116">**관련 항목:** [데이터 오류 처리](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="fb541-116">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="fb541-117">**잘림**</span><span class="sxs-lookup"><span data-stu-id="fb541-117">**Truncation**</span></span>  
 <span data-ttu-id="fb541-118">잘림이 발생할 경우 수행할 동작을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb541-118">Specify what should happen when a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="fb541-119">**설명**</span><span class="sxs-lookup"><span data-stu-id="fb541-119">**Description**</span></span>  
 <span data-ttu-id="fb541-120">오류에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fb541-120">View the description of the error.</span></span>  
  
 <span data-ttu-id="fb541-121">**이 값을 선택한 셀에 설정**</span><span class="sxs-lookup"><span data-stu-id="fb541-121">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="fb541-122">오류나 잘림 발생 시 선택한 모든 셀에 수행할 동작을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb541-122">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="fb541-123">**적용**</span><span class="sxs-lookup"><span data-stu-id="fb541-123">**Apply**</span></span>  
 <span data-ttu-id="fb541-124">선택한 셀에 오류 처리 옵션을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="fb541-124">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb541-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fb541-125">See Also</span></span>  
 <span data-ttu-id="fb541-126">[ADO NET 원본 편집기 &#40;연결 관리자 페이지&#41;](../../2014/integration-services/ado-net-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="fb541-126">[ADO NET Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/ado-net-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="fb541-127">[ADO NET 원본 편집기 &#40;열 페이지&#41;](../../2014/integration-services/ado-net-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="fb541-127">[ADO NET Source Editor &#40;Columns Page&#41;](../../2014/integration-services/ado-net-source-editor-columns-page.md) </span></span>  
 [<span data-ttu-id="fb541-128">ADO.NET 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="fb541-128">ADO.NET Connection Manager</span></span>](connection-manager/ado-net-connection-manager.md)  
  
  
