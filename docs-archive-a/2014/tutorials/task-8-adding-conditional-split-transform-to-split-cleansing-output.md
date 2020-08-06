---
title: '작업 8: 분할 정리 출력에 조건부 분할 변환 추가 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: d4ebe420-a4a9-4076-89d3-41abe726fc5c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9be7ea6f5330382ad0417df99e18bcba5b59a4e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639140"
---
# <a name="task-8-adding-conditional-split-transform-to-split-cleansing-output"></a><span data-ttu-id="d3d7d-102">태스크 8: 분할 정리 출력에 조건부 분할 변환 추가</span><span class="sxs-lookup"><span data-stu-id="d3d7d-102">Task 8: Adding Conditional Split Transform to Split Cleansing Output</span></span>
  <span data-ttu-id="d3d7d-103">이 변환에서는 데이터 흐름에 조건부 분할 변환을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d3d7d-103">In this transform, you add a Conditional Split Transform to the data flow.</span></span> <span data-ttu-id="d3d7d-104">조건부 분할 변환은 데이터 내용에 따라 각 행을 서로 다른 출력으로 라우팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3d7d-104">The Conditional Split transformation can route rows to different outputs based on the content of the data.</span></span> <span data-ttu-id="d3d7d-105">이 자습서에서는 DQS 정리 변환의 **레코드 상태** 출력 열을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3d7d-105">For this tutorial, you use the **Record Status** output column from the DQS Cleansing transform.</span></span> <span data-ttu-id="d3d7d-106">이 자습서에서는 수정 레코드 또는 수정된 레코드만 MDS 서버에 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="d3d7d-106">You will upload only correct or corrected records to MDS server in this tutorial.</span></span> <span data-ttu-id="d3d7d-107">따라서 레코드 **상태가** **올바른지** 또는 **수정**되었는지 확인 하 고 레코드를 MDS에 업로드 하기 전에 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3d7d-107">Therefore you check if the **Record Status** is **Correct** or **Corrected**, and combine the records before uploading the records to MDS.</span></span>  
  
1.  <span data-ttu-id="d3d7d-108">**SSIS 도구 상자** 의 **일반** 섹션에서 **공급자 데이터 정리**의 **데이터 흐름** 탭으로 **조건부 분할 변환** 을 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="d3d7d-108">Drag-drop **Conditional Split Transform** from **Common** section in the **SSIS Toolbox** to the **Data Flow** tab under **Cleanse Supplier Data**.</span></span>  
  
2.  <span data-ttu-id="d3d7d-109">**조건부 분할**을 마우스 오른쪽 단추로 클릭 하 고 **이름 바꾸기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3d7d-109">Right-click **Conditional Split**, and click **Rename**.</span></span> <span data-ttu-id="d3d7d-110">**선택 수정 및 수정 된 레코드** 를 입력 하 고 **enter**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="d3d7d-110">Type **Pick Correct and Corrected Records** and press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="d3d7d-111">**정리 공급자 데이터** 를 연결 하 고 파란색 커넥터를 사용 하 여 **수정 및** 수정 된 레코드를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3d7d-111">Connect **Cleanse Supplier Data** and **Pick Correct and Corrected Records** using the blue connector.</span></span>  
  
     <span data-ttu-id="d3d7d-112">![공급자 데이터 정리-> 수정 & 수정 됨](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-01.jpg "공급자 데이터 정리 -> 올바른 데이터 및 수정된 데이터 선택")</span><span class="sxs-lookup"><span data-stu-id="d3d7d-112">![Cleanse Supplier Data -> Pick Correct & Corrected](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-01.jpg "Cleanse Supplier Data -> Pick Correct & Corrected")</span></span>  
  
4.  <span data-ttu-id="d3d7d-113">**데이터 흐름** 탭에서 **수정 및 수정 된 레코드 선택** 을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3d7d-113">Double-click **Pick Correct and Corrected Records** in the **Data Flow** tab.</span></span>  
  
5.  <span data-ttu-id="d3d7d-114">화면 맨 아래에 있는 **기본 출력 이름을** **수정**합니다.</span><span class="sxs-lookup"><span data-stu-id="d3d7d-114">Change the **Default Output Name** at the bottom of the screen to **Correct**.</span></span>  
  
6.  <span data-ttu-id="d3d7d-115">**왼쪽 위 창**에서 **열** 을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3d7d-115">Expand **Columns** in the **top-left pane**.</span></span>  
  
     <span data-ttu-id="d3d7d-116">![조건부 분할 변환 편집기](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-02.jpg "조건부 분할 변환 편집기")</span><span class="sxs-lookup"><span data-stu-id="d3d7d-116">![Conditional Split Transformation Editor](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-02.jpg "Conditional Split Transformation Editor")</span></span>  
  
7.  <span data-ttu-id="d3d7d-117">**레코드 상태** 를 **조건** 열로 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="d3d7d-117">Drag-drop **Record Status** to the **Condition** column.</span></span>  
  
8.  <span data-ttu-id="d3d7d-118">**조건** 열의 **[레코드 상태]** 옆에 **= = "수정 됨"** 을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3d7d-118">Type **=="Corrected"** next to **[Record Status]** for the **Condition** column.</span></span>  
  
9. <span data-ttu-id="d3d7d-119">**출력 이름 열**에서 **Case 1** 을 클릭 하 고 이름을 **수정**됨으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3d7d-119">Click **Case 1** in the **Output Name Column**, and change the name to **Corrected**.</span></span>  
  
10. <span data-ttu-id="d3d7d-120">**확인** 을 클릭 하 여 **조건부 분할 변환 편집기** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="d3d7d-120">Click **OK** to close the **Conditional Split Transformation Editor** dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="d3d7d-121">다음 단계</span><span class="sxs-lookup"><span data-stu-id="d3d7d-121">Next Step</span></span>  
 [<span data-ttu-id="d3d7d-122">태스크 9: Union All 변환을 추가하여 수정 및 수정된 레코드 결합</span><span class="sxs-lookup"><span data-stu-id="d3d7d-122">Task 9: Adding Union All Transform to Combine Correct and Corrected Records</span></span>](../../2014/tutorials/task-9-adding-union-all-transform-to-combine-correct-and-corrected-records.md)  
  
  
