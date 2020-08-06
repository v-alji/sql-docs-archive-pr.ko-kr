---
title: '태스크 7: 데이터 흐름에 DQS 정리 변환 추가 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 0b749c71-dfb6-493a-804f-600290d46eef
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 887bc361a51b61e9137404e054bd52e2b630ca5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647374"
---
# <a name="task-7-adding-dqs-cleansing-transform-to-the-data-flow"></a><span data-ttu-id="557f4-102">태스크 7: Data Flow에 DQS 정리 변환 추가</span><span class="sxs-lookup"><span data-stu-id="557f4-102">Task 7: Adding DQS Cleansing Transform to the Data Flow</span></span>
  <span data-ttu-id="557f4-103">이 작업에서는 데이터 흐름에 DQS 정리 변환을 추가하여 DQS를 사용해서 입력 공급자 데이터를 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="557f4-103">In this task, you add DQS Cleansing Transform to the data flow to cleanse the input supplier data by using DQS.</span></span> <span data-ttu-id="557f4-104">변환에 대 한 자세한 내용은 **[Dqs 정리 변환](https://msdn.microsoft.com/library/ee677619.aspx)** 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="557f4-104">See **[DQS Cleansing Transform](https://msdn.microsoft.com/library/ee677619.aspx)** for more details about the transform.</span></span>  
  
1.  <span data-ttu-id="557f4-105">**데이터 흐름** 탭에서 **DQS 정리** 를 마우스 오른쪽 단추로 클릭 하 고 **이름 바꾸기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="557f4-105">Right-click **DQS Cleansing** in the **Data Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="557f4-106">**정리 공급자 데이터**를 입력 하 고 **enter**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="557f4-106">Type **Cleanse Supplier Data**, and press **ENTER**.</span></span>  
  
2.  <span data-ttu-id="557f4-107">**Excel 파일에서 공급자 데이터 읽기를**선택 합니다. 파란색 커넥터를 끌어 **공급자 데이터를 정리**합니다.</span><span class="sxs-lookup"><span data-stu-id="557f4-107">Select **Read Supplier Data from Excel File**; drag the blue connector to **Cleanse Supplier Data**.</span></span> <span data-ttu-id="557f4-108">구성 요소가 이제 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="557f4-108">The components are now connected.</span></span>  
  
     <span data-ttu-id="557f4-109">![공급자 데이터 읽기-공급자 데이터 > 정리](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-01.jpg "공급자 데이터 읽기 -> 공급자 데이터 정리")</span><span class="sxs-lookup"><span data-stu-id="557f4-109">![Read Supplier Data -> Cleanse Supplier Data](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-01.jpg "Read Supplier Data -> Cleanse Supplier Data")</span></span>  
  
3.  <span data-ttu-id="557f4-110">**공급자 데이터 정리**를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="557f4-110">Double-click **Cleanse Supplier Data**.</span></span>  
  
4.  <span data-ttu-id="557f4-111">**Dqs 정리 변환 편집기**에서 **데이터 품질 연결 관리자 드롭다운 목록**옆에 있는 **새로 만들기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="557f4-111">In the **DQS Cleansing Transformation Editor**, click **New** next to the **Data Quality Connection Manager drop-down list**.</span></span>  
  
5.  <span data-ttu-id="557f4-112">**Dqs 정리 연결 관리자** 대화 상자에서 **(local)** 또는 **마침표** (.)를 입력 하 여 로컬 서버에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="557f4-112">In the **DQS Cleansing Connection Manager** dialog box, type **(local)** or **period** (.) to connect to the local server.</span></span> <span data-ttu-id="557f4-113">이 단원에서는 DQS가 로컬 서버에 설치되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="557f4-113">This lesson assumes that you have DQS installed on a local server.</span></span>  
  
6.  <span data-ttu-id="557f4-114">**연결 테스트** 를 클릭 하 여 DQS 서버에 대 한 연결을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="557f4-114">Click **Test Connection** to test the connection to DQS server.</span></span>  
  
7.  <span data-ttu-id="557f4-115">**확인** 을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="557f4-115">Click **OK** to close the dialog box.</span></span>  
  
8.  <span data-ttu-id="557f4-116">**데이터 품질 기술 자료**에 대해 **Suppliers** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="557f4-116">Select **Suppliers** for the **Data Quality Knowledge Base**.</span></span>  
  
     <span data-ttu-id="557f4-117">![DQS 정리 변환 편집기 - 공급자 KB](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-02.jpg "DQS 정리 변환 편집기 - 공급자 KB")</span><span class="sxs-lookup"><span data-stu-id="557f4-117">![DQS Cleansing Transformation Editor - Suppliers KB](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-02.jpg "DQS Cleansing Transformation Editor - Suppliers KB")</span></span>  
  
9. <span data-ttu-id="557f4-118">위쪽의 **매핑** 탭으로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="557f4-118">Switch to the **Mapping** tab at the top.</span></span>  
  
10. <span data-ttu-id="557f4-119">**사용 가능한 입력 열**에서 확인란을 선택 하 여 **공급자 이름**, **ContactEmailAddress**, **주소 줄**, **구/군/시** **, 시**/도, **국가**및 **우편** 번호를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="557f4-119">From **Available Input Columns**, select **Supplier Name**, **ContactEmailAddress**, **Address Line**, **City**, **State**, **Country**, and **Zip Code** by selecting the check boxes.</span></span>  
  
     <span data-ttu-id="557f4-120">![DQS 정리 변환 편집기 - 매핑](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-03.jpg "DQS 정리 변환 편집기 - 매핑")</span><span class="sxs-lookup"><span data-stu-id="557f4-120">![DQS Cleansing Transformation Editor - Mappings](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-03.jpg "DQS Cleansing Transformation Editor - Mappings")</span></span>  
  
11. <span data-ttu-id="557f4-121">아래쪽 창에서 **도메인** 열의 드롭다운 목록을 사용 하 여 이러한 열을 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="557f4-121">In the bottom pane, map these columns by using drop-down lists in the **Domain** column:</span></span>  
  
    |<span data-ttu-id="557f4-122">열</span><span class="sxs-lookup"><span data-stu-id="557f4-122">Column</span></span>|<span data-ttu-id="557f4-123">도메인</span><span class="sxs-lookup"><span data-stu-id="557f4-123">Domain</span></span>|  
    |------------|------------|  
    |<span data-ttu-id="557f4-124">Supplier Name</span><span class="sxs-lookup"><span data-stu-id="557f4-124">Supplier Name</span></span>|<span data-ttu-id="557f4-125">Supplier Name</span><span class="sxs-lookup"><span data-stu-id="557f4-125">Supplier Name</span></span>|  
    |<span data-ttu-id="557f4-126">ContactEmailAddress</span><span class="sxs-lookup"><span data-stu-id="557f4-126">ContactEmailAddress</span></span>|<span data-ttu-id="557f4-127">담당자 이메일</span><span class="sxs-lookup"><span data-stu-id="557f4-127">Contact Email</span></span>|  
    |<span data-ttu-id="557f4-128">Address Line</span><span class="sxs-lookup"><span data-stu-id="557f4-128">Address Line</span></span>|<span data-ttu-id="557f4-129">Address Line</span><span class="sxs-lookup"><span data-stu-id="557f4-129">Address Line</span></span>|  
    |<span data-ttu-id="557f4-130">도시</span><span class="sxs-lookup"><span data-stu-id="557f4-130">City</span></span>|<span data-ttu-id="557f4-131">도시</span><span class="sxs-lookup"><span data-stu-id="557f4-131">City</span></span>|  
    |<span data-ttu-id="557f4-132">주</span><span class="sxs-lookup"><span data-stu-id="557f4-132">State</span></span>|<span data-ttu-id="557f4-133">주</span><span class="sxs-lookup"><span data-stu-id="557f4-133">State</span></span>|  
    |<span data-ttu-id="557f4-134">국가</span><span class="sxs-lookup"><span data-stu-id="557f4-134">Country</span></span>|<span data-ttu-id="557f4-135">국가</span><span class="sxs-lookup"><span data-stu-id="557f4-135">Country</span></span>|  
    |<span data-ttu-id="557f4-136">Zip Code</span><span class="sxs-lookup"><span data-stu-id="557f4-136">Zip Code</span></span>|<span data-ttu-id="557f4-137">Zip</span><span class="sxs-lookup"><span data-stu-id="557f4-137">Zip</span></span>|  
  
12. <span data-ttu-id="557f4-138">**확인** 을 클릭 하 여 **DQS 정리 변환 편집기** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="557f4-138">Click **OK** to close the **DQS Cleansing Transformation Editor** dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="557f4-139">다음 단계</span><span class="sxs-lookup"><span data-stu-id="557f4-139">Next Step</span></span>  
 [<span data-ttu-id="557f4-140">태스크 8: 분할 정리 출력에 조건부 분할 변환 추가</span><span class="sxs-lookup"><span data-stu-id="557f4-140">Task 8: Adding Conditional Split Transform to Split Cleansing Output</span></span>](../../2014/tutorials/task-8-adding-conditional-split-transform-to-split-cleansing-output.md)  
  
  
