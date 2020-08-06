---
title: 데이터 마이닝 쿼리 태스크 편집기 (출력 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dmquerytask.output.f1
helpviewer_keywords:
- Data Mining Query Task Editor
ms.assetid: 62f9e015-6fe0-4396-ad90-3ad51bf00025
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1508972b0487daa90f52af723d58185944a19a58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738524"
---
# <a name="data-mining-query-task-editor-output-tab"></a><span data-ttu-id="bc943-102">데이터 마이닝 쿼리 태스크 편집기(출력 탭)</span><span class="sxs-lookup"><span data-stu-id="bc943-102">Data Mining Query Task Editor (Output Tab)</span></span>
  <span data-ttu-id="bc943-103">**데이터 마이닝 쿼리 태스크 편집기** 대화 상자의 **출력** 탭을 사용하여 예측 쿼리의 대상을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc943-103">Use the **Output** tab of the **Data Mining Query Task Editor** dialog box to specify the destination of the prediction query.</span></span>  
  
 <span data-ttu-id="bc943-104">패키지에서 데이터 마이닝을 구현하는 방법에 대한 자세한 내용은 [데이터 마이닝 쿼리 태스크](control-flow/data-mining-query-task.md) 및 [데이터 마이닝 솔루션](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bc943-104">To learn about implementing data mining in packages, see [Data Mining Query Task](control-flow/data-mining-query-task.md) and [Data Mining Solutions](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions).</span></span>  
  
## <a name="general-options"></a><span data-ttu-id="bc943-105">일반 옵션</span><span class="sxs-lookup"><span data-stu-id="bc943-105">General Options</span></span>  
 <span data-ttu-id="bc943-106">**이름**</span><span class="sxs-lookup"><span data-stu-id="bc943-106">**Name**</span></span>  
 <span data-ttu-id="bc943-107">데이터 마이닝 쿼리 태스크에 사용할 고유 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bc943-107">Provide a unique name for the Data Mining Query task.</span></span> <span data-ttu-id="bc943-108">이 이름은 태스크 아이콘에서 레이블로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc943-108">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bc943-109">태스크 이름은 패키지 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc943-109">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="bc943-110">**설명**</span><span class="sxs-lookup"><span data-stu-id="bc943-110">**Description**</span></span>  
 <span data-ttu-id="bc943-111">데이터 마이닝 쿼리 태스크에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bc943-111">Type a description of the Data Mining Query task.</span></span>  
  
## <a name="output-tab-options"></a><span data-ttu-id="bc943-112">출력 탭 옵션</span><span class="sxs-lookup"><span data-stu-id="bc943-112">Output Tab Options</span></span>  
 <span data-ttu-id="bc943-113">**연결**</span><span class="sxs-lookup"><span data-stu-id="bc943-113">**Connection**</span></span>  
 <span data-ttu-id="bc943-114">목록에서 연결 관리자를 선택하거나 **새로 만들기** 를 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bc943-114">Select a connection manager in the list or click **New** to create a new connection manager.</span></span>  
  
 <span data-ttu-id="bc943-115">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="bc943-115">**New**</span></span>  
 <span data-ttu-id="bc943-116">새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bc943-116">Create a new connection manager.</span></span> <span data-ttu-id="bc943-117">ADO.NET 및 OLE DB 연결 관리자 유형만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc943-117">Only the ADO.NET and OLE DB connection manager types can be used.</span></span>  
  
 <span data-ttu-id="bc943-118">**출력 테이블**</span><span class="sxs-lookup"><span data-stu-id="bc943-118">**Output table**</span></span>  
 <span data-ttu-id="bc943-119">예측 쿼리가 결과를 작성할 테이블을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bc943-119">Specify the table to which the prediction query writes its results.</span></span>  
  
 <span data-ttu-id="bc943-120">**출력 테이블을 삭제하고 다시 만들기**</span><span class="sxs-lookup"><span data-stu-id="bc943-120">**Drop and re-create the output table**</span></span>  
 <span data-ttu-id="bc943-121">테이블을 삭제한 다음 다시 만들어 예측 쿼리가 대상 테이블의 내용을 덮어쓸지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bc943-121">Indicate whether the prediction query should overwrite content in the destination table by dropping and then re-creating the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc943-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bc943-122">See Also</span></span>  
 <span data-ttu-id="bc943-123">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="bc943-123">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="bc943-124">[데이터 마이닝 쿼리 태스크 편집기 &#40;마이닝 모델 탭&#41;](../../2014/integration-services/data-mining-query-task-editor-mining-model-tab.md) </span><span class="sxs-lookup"><span data-stu-id="bc943-124">[Data Mining Query Task Editor &#40;Mining Model Tab&#41;](../../2014/integration-services/data-mining-query-task-editor-mining-model-tab.md) </span></span>  
 <span data-ttu-id="bc943-125">[데이터 마이닝 쿼리 태스크 편집기 &#40;쿼리 탭&#41;](../../2014/integration-services/data-mining-query-task-editor-query-tab.md) </span><span class="sxs-lookup"><span data-stu-id="bc943-125">[Data Mining Query Task Editor &#40;Query Tab&#41;](../../2014/integration-services/data-mining-query-task-editor-query-tab.md) </span></span>  
 [<span data-ttu-id="bc943-126">Data Mining Designer</span><span class="sxs-lookup"><span data-stu-id="bc943-126">Data Mining Designer</span></span>](https://docs.microsoft.com/analysis-services/data-mining/data-mining-designer)  
  
  
