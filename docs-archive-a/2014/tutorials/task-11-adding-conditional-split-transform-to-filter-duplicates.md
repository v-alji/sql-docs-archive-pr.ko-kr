---
title: '작업 11: 조건부 분할 변환을 추가 하 여 중복 항목 필터링 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3094bd57-5cf4-4860-bf51-fadd1b309f94
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e8370563c4275df0d0513d5434a8b16efba728d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742687"
---
# <a name="task-11-adding-conditional-split-transform-to-filter-duplicates"></a><span data-ttu-id="7074e-102">태스크 11: 조건부 분할 변환을 추가하여 중복 항목 필터링</span><span class="sxs-lookup"><span data-stu-id="7074e-102">Task 11: Adding Conditional Split Transform to Filter Duplicates</span></span>
  <span data-ttu-id="7074e-103">이 작업에서는 조건부 분할 변환을 데이터 흐름에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7074e-103">In this task, you add the Conditional Split Transform to the data flow.</span></span> <span data-ttu-id="7074e-104">이 변환은 들어오는 레코드 집합에서 중복 항목을 필터링하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7074e-104">This transform helps you filter duplicates from the incoming record set.</span></span> <span data-ttu-id="7074e-105">유사 항목 그룹 변환은 일치하는 것으로 발견된 레코드를 그룹화하고 레코드 중 하나를 피벗 레코드로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7074e-105">The Fuzzy Group transform groups the records that it finds to be matches and picks one of the records as a pivot record.</span></span> <span data-ttu-id="7074e-106">그룹의 모든 레코드는 동일한 _key_out 값을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="7074e-106">All the records in a group have the same _key_out value.</span></span> <span data-ttu-id="7074e-107">그룹의 피벗 레코드는 _key_in 값이 _key_out 값과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="7074e-107">The pivot record in the group has _key_in same as the _key_out value.</span></span> <span data-ttu-id="7074e-108">그룹의 다른 레코드는 _key_in 및 _key_out 값이 서로 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="7074e-108">The other records in the group have different values for _key_in and _key_out.</span></span> <span data-ttu-id="7074e-109">따라서 _key_in==_key_out 조건을 사용해서 필터링하면 그룹의 피벗 행만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7074e-109">Therefore, when you filter using the condition _key_in==_key_out, you only get the pivot row in the group.</span></span>  
  
1.  <span data-ttu-id="7074e-110">**SSIS 도구 상자** 의 **공통** 섹션에서 **조건부 분할** 변환을 **데이터 흐름** 탭으로 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="7074e-110">Drag-drop **Conditional Split** Transform from **Common** section in the **SSIS Toolbox** to the **Data Flow** tab.</span></span>  
  
2.  <span data-ttu-id="7074e-111">**데이터 흐름** 탭에서 **조건부 분할 변환** 을 마우스 오른쪽 단추로 클릭 하 고 **이름 바꾸기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7074e-111">Right-click **Conditional Split Transform** in the **Data Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="7074e-112">**중복 필터** 를 입력 하 고 **enter**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="7074e-112">Type **Filter Duplicates** and press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="7074e-113">**Id가 일치 하는 그룹 공급자** 를 연결 하 여 **중복 항목을 필터링**합니다.</span><span class="sxs-lookup"><span data-stu-id="7074e-113">Connect **Group Suppliers with Matching IDs** to **Filter Duplicates**.</span></span>  
  
4.  <span data-ttu-id="7074e-114">**중복 필터** 를 두 번 클릭 하 여 **조건부 분할 변환 편집기** 대화 상자를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="7074e-114">Double-click **Filter Duplicates** to launch the **Conditional Split Transform Editor** dialog box.</span></span>  
  
5.  <span data-ttu-id="7074e-115">왼쪽 위 창에서 **열** 을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="7074e-115">Expand **Columns** in the top-left pane.</span></span>  
  
6.  <span data-ttu-id="7074e-116">**_Key_in** 를 **조건** 열로 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="7074e-116">Drag-drop **_key_in** to the **Condition** column.</span></span>  
  
7.  <span data-ttu-id="7074e-117">**_Key_in** 옆에 = = (같음)를 입력 하 고 **_key_out**을 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="7074e-117">Type == (equals to) next to **_key_in** and drag-drop **_key_out**.</span></span>  
  
8.  <span data-ttu-id="7074e-118">**출력 이름** 열에서 **Case 1** 을 클릭 하 고 **Unique Records**를 입력 한 다음 **enter**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="7074e-118">Click **Case 1** in the **Output Name** column, type **Unique Records**, and press **ENTER**.</span></span>  
  
     <span data-ttu-id="7074e-119">![조건부 분할 변환 편집기](../../2014/tutorials/media/et-addingconditionalsplittransformtofilterduplicates.jpg "조건부 분할 변환 편집기")</span><span class="sxs-lookup"><span data-stu-id="7074e-119">![Conditional Split Transformation Editor](../../2014/tutorials/media/et-addingconditionalsplittransformtofilterduplicates.jpg "Conditional Split Transformation Editor")</span></span>  
  
9. <span data-ttu-id="7074e-120">**확인** 을 클릭 하 여 **조건부 분할 변환 편집기** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="7074e-120">Click **OK** to close the **Conditional Split Transformation Editor** dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="7074e-121">다음 단계</span><span class="sxs-lookup"><span data-stu-id="7074e-121">Next Step</span></span>  
 [<span data-ttu-id="7074e-122">태스크 12: 파생 열 변환을 추가하여 MDS에 필요한 열 추가</span><span class="sxs-lookup"><span data-stu-id="7074e-122">Task 12: Adding Derived Column Transform to Add Columns Required by MDS</span></span>](../../2014/tutorials/task-12-adding-derived-column-transform-to-add-columns-required-by-mds.md)  
  
  
