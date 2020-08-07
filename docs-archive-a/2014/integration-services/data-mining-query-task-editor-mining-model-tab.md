---
title: 데이터 마이닝 쿼리 태스크 편집기 (마이닝 모델 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dmquerytask.miningmodel.f1
helpviewer_keywords:
- Data Mining Query Task Editor
ms.assetid: 0ede9b86-be27-471e-b012-22a65adce579
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 794365c8d15ff9725fc385bb43d51e70ffa529b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734392"
---
# <a name="data-mining-query-task-editor-mining-model-tab"></a><span data-ttu-id="105fc-102">데이터 마이닝 쿼리 태스크 편집기(마이닝 모델 탭)</span><span class="sxs-lookup"><span data-stu-id="105fc-102">Data Mining Query Task Editor (Mining Model Tab)</span></span>
  <span data-ttu-id="105fc-103">**데이터 마이닝 쿼리 태스크** 대화 상자의 **마이닝 모델** 탭을 사용하여 사용할 마이닝 구조와 마이닝 모델을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="105fc-103">Use the **Mining Model** tab of the **Data Mining Query Task** dialog box to specify the mining structure and mining model to use.</span></span>  
  
 <span data-ttu-id="105fc-104">패키지에서 데이터 마이닝을 구현하는 방법에 대한 자세한 내용은 [데이터 마이닝 쿼리 태스크](control-flow/data-mining-query-task.md) 및 [데이터 마이닝 솔루션](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="105fc-104">To learn about implementing data mining in packages, see [Data Mining Query Task](control-flow/data-mining-query-task.md) and [Data Mining Solutions](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions).</span></span>  
  
## <a name="general-options"></a><span data-ttu-id="105fc-105">일반 옵션</span><span class="sxs-lookup"><span data-stu-id="105fc-105">General Options</span></span>  
 <span data-ttu-id="105fc-106">**이름**</span><span class="sxs-lookup"><span data-stu-id="105fc-106">**Name**</span></span>  
 <span data-ttu-id="105fc-107">데이터 마이닝 쿼리 태스크에 사용할 고유 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="105fc-107">Provide a unique name for the Data Mining Query task.</span></span> <span data-ttu-id="105fc-108">이 이름은 태스크 아이콘에서 레이블로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="105fc-108">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="105fc-109">태스크 이름은 패키지 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="105fc-109">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="105fc-110">**설명**</span><span class="sxs-lookup"><span data-stu-id="105fc-110">**Description**</span></span>  
 <span data-ttu-id="105fc-111">데이터 마이닝 쿼리 태스크에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="105fc-111">Type a description of the Data Mining Query task.</span></span>  
  
## <a name="mining-model-tab-options"></a><span data-ttu-id="105fc-112">마이닝 모델 탭 옵션</span><span class="sxs-lookup"><span data-stu-id="105fc-112">Mining Model Tab Options</span></span>  
 <span data-ttu-id="105fc-113">**연결**</span><span class="sxs-lookup"><span data-stu-id="105fc-113">**Connection**</span></span>  
 <span data-ttu-id="105fc-114">목록에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 연결 관리자를 선택하거나 **새로 만들기** 를 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="105fc-114">Select an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] connection manager in the list or click **New** to create a new connection manager.</span></span>  
  
 <span data-ttu-id="105fc-115">**관련 항목:**  [Analysis Services 연결 관리자](connection-manager/analysis-services-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="105fc-115">**Related Topics:**  [Analysis Services Connection Manager](connection-manager/analysis-services-connection-manager.md)</span></span>  
  
 <span data-ttu-id="105fc-116">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="105fc-116">**New**</span></span>  
 <span data-ttu-id="105fc-117">새로운 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="105fc-117">Create a new [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] connection manager.</span></span>  
  
 <span data-ttu-id="105fc-118">**관련 항목:** [Analysis Services 연결 관리자 추가 대화 상자 UI 참조](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)</span><span class="sxs-lookup"><span data-stu-id="105fc-118">**Related Topics:** [Add Analysis Services Connection Manager Dialog Box UI Reference](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)</span></span>  
  
 <span data-ttu-id="105fc-119">**마이닝 구조**</span><span class="sxs-lookup"><span data-stu-id="105fc-119">**Mining structure**</span></span>  
 <span data-ttu-id="105fc-120">목록에서 마이닝 구조를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="105fc-120">Select a mining structure in the list.</span></span>  
  
 <span data-ttu-id="105fc-121">**마이닝 모델**</span><span class="sxs-lookup"><span data-stu-id="105fc-121">**Mining models**</span></span>  
 <span data-ttu-id="105fc-122">선택한 마이닝 구조를 기반으로 하는 마이닝 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="105fc-122">Select a mining model built on the selected mining structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="105fc-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="105fc-123">See Also</span></span>  
 <span data-ttu-id="105fc-124">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="105fc-124">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="105fc-125">[데이터 마이닝 쿼리 태스크 편집기 &#40;쿼리 탭&#41;](../../2014/integration-services/data-mining-query-task-editor-query-tab.md) </span><span class="sxs-lookup"><span data-stu-id="105fc-125">[Data Mining Query Task Editor &#40;Query Tab&#41;](../../2014/integration-services/data-mining-query-task-editor-query-tab.md) </span></span>  
 <span data-ttu-id="105fc-126">[데이터 마이닝 쿼리 태스크 편집기 &#40;출력 탭&#41;](../../2014/integration-services/data-mining-query-task-editor-output-tab.md) </span><span class="sxs-lookup"><span data-stu-id="105fc-126">[Data Mining Query Task Editor &#40;Output Tab&#41;](../../2014/integration-services/data-mining-query-task-editor-output-tab.md) </span></span>  
 [<span data-ttu-id="105fc-127">Data Mining Designer</span><span class="sxs-lookup"><span data-stu-id="105fc-127">Data Mining Designer</span></span>](https://docs.microsoft.com/analysis-services/data-mining/data-mining-designer)  
  
  
