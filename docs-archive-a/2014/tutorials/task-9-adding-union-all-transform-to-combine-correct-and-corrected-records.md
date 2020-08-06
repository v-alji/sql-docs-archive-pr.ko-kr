---
title: '작업 9: Union All 변환을 추가 하 여 올바른 레코드와 수정 된 레코드 결합 | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 24ba466d-a7d3-49e7-9111-b348399c9e58
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 83afb5ea9367660048fe36d00ab59d808da17b81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742683"
---
# <a name="task-9-adding-union-all-transform-to-combine-correct-and-corrected-records"></a><span data-ttu-id="dbc29-102">태스크 9: Union All 변환을 추가하여 수정 및 수정된 레코드 결합</span><span class="sxs-lookup"><span data-stu-id="dbc29-102">Task 9: Adding Union All Transform to Combine Correct and Corrected Records</span></span>
  <span data-ttu-id="dbc29-103">이 작업에서는 UNION ALL 변환을 데이터 흐름에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc29-103">In this task, you add the Union All Transform to the data flow.</span></span> <span data-ttu-id="dbc29-104">UNION ALL 변환은 여러 개의 입력을 하나의 출력으로 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc29-104">The Union All transformation combines multiple inputs into one output.</span></span> <span data-ttu-id="dbc29-105">이 시나리오에서는 Correct 및 Corrected 레코드를 모두 하나의 스트림에 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc29-105">In your scenario, it combine both Correct and Corrected records into one stream.</span></span>  
  
1.  <span data-ttu-id="dbc29-106">**Union All** 변환을 **SSIS 도구 상자** 의 **일반** 섹션에서 **데이터 흐름** 탭으로 끌어서 놓고 **올바른 레코드 및 수정 된 레코드를 선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc29-106">Drag-drop **Union All** Transform from **Common** section of the **SSIS Toolbox** to the **Data Flow** tab and place it under **Pick Correct and Corrected Records**.</span></span>  
  
2.  <span data-ttu-id="dbc29-107">**데이터 흐름** 탭에서 **Union All** 변환을 마우스 오른쪽 단추로 클릭 하 고 **이름 바꾸기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc29-107">Right-click **Union All** Transform in the **Data Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="dbc29-108">**올바른 레코드와 수정 된 레코드 결합**을 입력 하 고 **enter**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="dbc29-108">Type **Combine Correct and Corrected Records**, and press **ENTER**.</span></span>  
  
     <span data-ttu-id="dbc29-109">![올바른 레코드 및 수정된 레코드 결합](../../2014/tutorials/media/et-addinguattocombinecacrecords-01.jpg "올바른 레코드 및 수정된 레코드 결합")</span><span class="sxs-lookup"><span data-stu-id="dbc29-109">![Combine Correct and Corrected Reocrds](../../2014/tutorials/media/et-addinguattocombinecacrecords-01.jpg "Combine Correct and Corrected Reocrds")</span></span>  
  
3.  <span data-ttu-id="dbc29-110">연결을 **선택 하 고** 수정 된 레코드를 수정 하 여 **데이터 흐름** 탭에서 파란색 커넥터를 사용 하 여 수정 된 레코드와 수정 된 **레코드를 결합** 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc29-110">Connect **Pick Correct and Corrected Records** to **Combine Correct and Corrected Records** in the **Data Flow** tab by using the blue connector.</span></span> <span data-ttu-id="dbc29-111">**입력 출력 선택** 대화 상자가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbc29-111">You should see the **Input Output Selection** dialog box.</span></span>  
  
4.  <span data-ttu-id="dbc29-112">**입력 출력** 대화 상자에서 **출력** 에 대해 **수정** 을 선택 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc29-112">In the **Input Output** dialog box, select **Correct** for **Output** and click **OK**.</span></span>  
  
     <span data-ttu-id="dbc29-113">![입/출력 선택 대화 상자](../../2014/tutorials/media/et-addinguattocombinecacrecords-02.jpg "입/출력 선택 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="dbc29-113">![Input Output Selection Dialog Box](../../2014/tutorials/media/et-addinguattocombinecacrecords-02.jpg "Input Output Selection Dialog Box")</span></span>  
  
5.  <span data-ttu-id="dbc29-114">커넥터 끝의 점을 왼쪽으로 끌어서 놓아 왼쪽으로 **올바른** 제목의 연결선을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc29-114">Move the connector titled **Correct** to the left by dragging and dropping the dot at the end of the connector to left.</span></span>  
  
     <span data-ttu-id="dbc29-115">![올바른 레코드를 연결하여 올바른 데이터 및 수정된 레코드 결합](../../2014/tutorials/media/et-addinguattocombinecacrecords-03.jpg "올바른 레코드를 연결하여 올바른 데이터 및 수정된 레코드 결합")</span><span class="sxs-lookup"><span data-stu-id="dbc29-115">![Connect Correct to Combine Correct and Corrected](../../2014/tutorials/media/et-addinguattocombinecacrecords-03.jpg "Connect Correct to Combine Correct and Corrected")</span></span>  
  
6.  <span data-ttu-id="dbc29-116">**올바른 레코드 및 수정 된 레코드** 변환을 선택 하면 다른 파란색 커넥터가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbc29-116">If you select **Pick Correct and Corrected Records** transform, you should see another blue connector.</span></span> <span data-ttu-id="dbc29-117">해당 파란색 커넥터를 끌어 **올바른 레코드와 수정 된 레코드를 결합**합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc29-117">Drag that blue connector to **Combine Correct and Corrected Records**.</span></span>  
  
     <span data-ttu-id="dbc29-118">![수정된 레코드를 연결하여 올바른 데이터 및 수정된 레코드 결합](../../2014/tutorials/media/et-addinguattocombinecacrecords-04.jpg "수정된 레코드를 연결하여 올바른 데이터 및 수정된 레코드 결합")</span><span class="sxs-lookup"><span data-stu-id="dbc29-118">![Connect Corrected to Combine Correct and Corrected](../../2014/tutorials/media/et-addinguattocombinecacrecords-04.jpg "Connect Corrected to Combine Correct and Corrected")</span></span>  
  
7.  <span data-ttu-id="dbc29-119">이 **커넥터** 는 **수정**된 제목 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc29-119">This **connector** should be titled **Corrected**.</span></span> <span data-ttu-id="dbc29-120">두 조건만 **정확** 하 고 **수정**되었으며 한 개의 조건이 이미 사용 되었으므로이 시간에는 **입력 출력 선택** 대화 상자가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dbc29-120">Since you have only two conditions **Correct** and **Corrected**, and one condition was already used, the **Input Output Selection** dialog box is not displayed this time.</span></span> <span data-ttu-id="dbc29-121">커넥터가 겹치면 커넥터를 왼쪽 또는 오른쪽으로 끌어서 왼쪽과 오른쪽으로 각각 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc29-121">If the connectors overlap, move one to left and the other one to right by dragging the connector to left or right.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="dbc29-122">다음 단계</span><span class="sxs-lookup"><span data-stu-id="dbc29-122">Next Step</span></span>  
 [<span data-ttu-id="dbc29-123">태스크 10: 유사 항목 그룹화 변환을 추가하여 중복 항목 식별</span><span class="sxs-lookup"><span data-stu-id="dbc29-123">Task 10: Adding Fuzzy Group Transform to Identify Duplicates</span></span>](../../2014/tutorials/task-10-adding-fuzzy-group-transform-to-identify-duplicates.md)  
  
  
