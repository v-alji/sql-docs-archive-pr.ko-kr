---
title: 조회 변환 편집기 (일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.general.f1
ms.assetid: 4bd15e48-0feb-4f95-be91-5df58105dbfb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aa178118f7e090b6a3c15c7ab9347f322461f07b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729623"
---
# <a name="lookup-transformation-editor-general-page"></a><span data-ttu-id="0632a-102">조회 변환 편집기(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="0632a-102">Lookup Transformation Editor (General Page)</span></span>
  <span data-ttu-id="0632a-103">조회 변환 편집기 대화 상자의 **일반** 페이지를 사용하여 캐시 모드와 연결 형식을 선택하고 일치하는 항목이 없는 행의 처리 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0632a-103">Use the **General** page of the Lookup Transformation Editor dialog box to select the cache mode, select the connection type, and specify how to handle rows with no matching entries.</span></span>  
  
 <span data-ttu-id="0632a-104">조회 변환에 대한 자세한 내용은 [Lookup Transformation](data-flow/transformations/lookup-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0632a-104">To learn more about the Lookup transformation, see [Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="0632a-105">옵션</span><span class="sxs-lookup"><span data-stu-id="0632a-105">Options</span></span>  
 <span data-ttu-id="0632a-106">**전체 캐시**</span><span class="sxs-lookup"><span data-stu-id="0632a-106">**Full cache**</span></span>  
 <span data-ttu-id="0632a-107">조회 변환이 실행되기 전에 참조 데이터 세트를 생성하고 캐시에 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="0632a-107">Generate and load the reference dataset into cache before the Lookup transformation is executed.</span></span>  
  
 <span data-ttu-id="0632a-108">**부분 캐시**</span><span class="sxs-lookup"><span data-stu-id="0632a-108">**Partial cache**</span></span>  
 <span data-ttu-id="0632a-109">조회 변환이 실행되는 동안 참조 데이터 세트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="0632a-109">Generate the reference dataset during the execution of the Lookup transformation.</span></span> <span data-ttu-id="0632a-110">참조 데이터 세트에서 일치하는 항목이 있는 행 및 일치하는 항목이 없는 행을 캐시에 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="0632a-110">Load the rows with matching entries in the reference dataset and the rows with no matching entries in the dataset into cache.</span></span>  
  
 <span data-ttu-id="0632a-111">**캐시 없음**</span><span class="sxs-lookup"><span data-stu-id="0632a-111">**No cache**</span></span>  
 <span data-ttu-id="0632a-112">조회 변환이 실행되는 동안 참조 데이터 세트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="0632a-112">Generate the reference dataset during the execution of the Lookup transformation.</span></span> <span data-ttu-id="0632a-113">캐시에 로드되는 데이터가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0632a-113">No data is loaded into cache.</span></span>  
  
 <span data-ttu-id="0632a-114">**캐시 연결 관리자**</span><span class="sxs-lookup"><span data-stu-id="0632a-114">**Cache connection manager**</span></span>  
 <span data-ttu-id="0632a-115">조회 변환이 캐시 연결 관리자를 사용하도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="0632a-115">Configure the Lookup transformation to use a Cache connection manager.</span></span> <span data-ttu-id="0632a-116">이 옵션은 전체 캐시 옵션을 선택하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0632a-116">This option is available only if the Full cache option is selected.</span></span>  
  
 <span data-ttu-id="0632a-117">**캐시 없음**</span><span class="sxs-lookup"><span data-stu-id="0632a-117">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="0632a-118">조회 변환이 OLE DB 연결 관리자를 사용하도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="0632a-118">Configure the Lookup transformation to use an OLE DB connection manager.</span></span>  
  
 <span data-ttu-id="0632a-119">**일치하는 항목이 없는 행 처리 방법 지정**</span><span class="sxs-lookup"><span data-stu-id="0632a-119">**Specify how to handle rows with no matching entries**</span></span>  
 <span data-ttu-id="0632a-120">참조 데이터 세트에서 하나 이상의 항목과 일치하지 않는 행을 처리하기 위한 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0632a-120">Select an option for handling rows that do not match at least one entry in the reference dataset.</span></span>  
  
 <span data-ttu-id="0632a-121">**일치하는 항목이 없는 출력으로 행 리디렉션**을 선택하면 행이 일치하는 항목이 없는 출력으로 리디렉션되고 오류로 처리되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0632a-121">When you select **Redirect rows to no match output**, the rows are redirected to a no match output and are not handled as errors.</span></span> <span data-ttu-id="0632a-122">이 경우 **조회 변환 편집기** 대화 상자의 **오류 출력** 페이지에 있는 **오류** 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0632a-122">The **Error** option on the **Error Output** page of the **Lookup Transformation Editor** dialog box is not available.</span></span>  
  
 <span data-ttu-id="0632a-123">**일치하는 항목이 없는 행 처리 방법 지정** 목록 상자에서 다른 옵션을 선택하면 행이 오류로 처리되며</span><span class="sxs-lookup"><span data-stu-id="0632a-123">When you select any other option in the **Specify how to handle rows with no matching entries** list box, the rows are handled as errors.</span></span> <span data-ttu-id="0632a-124">**오류 출력** 페이지에 있는 **오류** 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0632a-124">The **Error** option on the **Error Output** page is available.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="0632a-125">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="0632a-125">External Resources</span></span>  
 <span data-ttu-id="0632a-126">blogs.msdn.com의 블로그 항목 - [조회 캐시 모드](https://go.microsoft.com/fwlink/?LinkId=219518)</span><span class="sxs-lookup"><span data-stu-id="0632a-126">Blog entry, [Lookup cache modes](https://go.microsoft.com/fwlink/?LinkId=219518) on blogs.msdn.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0632a-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0632a-127">See Also</span></span>  
 <span data-ttu-id="0632a-128">[캐시 연결 관리자](connection-manager/cache-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="0632a-128">[Cache Connection Manager](connection-manager/cache-connection-manager.md) </span></span>  
 <span data-ttu-id="0632a-129">[조회 변환 편집기 &#40;연결 페이지&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md) </span><span class="sxs-lookup"><span data-stu-id="0632a-129">[Lookup Transformation Editor &#40;Connection Page&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md) </span></span>  
 <span data-ttu-id="0632a-130">[조회 변환 편집기 &#40;열 페이지&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="0632a-130">[Lookup Transformation Editor &#40;Columns Page&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md) </span></span>  
 <span data-ttu-id="0632a-131">[조회 변환 편집기 &#40;고급 페이지&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="0632a-131">[Lookup Transformation Editor &#40;Advanced Page&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="0632a-132">조회 변환 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="0632a-132">Lookup Transformation Editor &#40;Error Output Page&#41;</span></span>](../../2014/integration-services/lookup-transformation-editor-error-output-page.md)  
  
  
