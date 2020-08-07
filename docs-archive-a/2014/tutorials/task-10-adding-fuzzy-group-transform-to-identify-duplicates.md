---
title: '태스크 10: 중복 항목을 식별 하는 유사 항목 그룹 변환 추가 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 90b2b323-babd-464a-8914-9dc5e66aca74
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 086625197850fdfd6381e9c0a4a7deac8ce3ae45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731208"
---
# <a name="task-10-adding-fuzzy-group-transform-to-identify-duplicates"></a><span data-ttu-id="f760d-102">태스크 10: 유사 항목 그룹화 변환을 추가하여 중복 항목 식별</span><span class="sxs-lookup"><span data-stu-id="f760d-102">Task 10: Adding Fuzzy Group Transform to Identify Duplicates</span></span>
  <span data-ttu-id="f760d-103">이 작업에서는 유사 항목 그룹 변환을 데이터 흐름에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f760d-103">In this task, you add a Fuzzy Group Transform to the data flow.</span></span> <span data-ttu-id="f760d-104">유사 항목 그룹 변환은 원본 데이터에서 중복 항목을 식별하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f760d-104">The Fuzzy Group transformation can help identify duplicates in the source data.</span></span> <span data-ttu-id="f760d-105">자세한 내용은 [유사 항목 그룹화 변환](../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f760d-105">See [Fuzzy Grouping Transformation](../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md) for more details.</span></span>  
  
1.  <span data-ttu-id="f760d-106">**SSIS 도구 상자** 의 **기타 변환** 에서 **유사 항목 그룹** 변환을 **올바른 레코드와 수정 된 레코드 결합**아래의 **데이터 흐름** 탭으로 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="f760d-106">Drag-drop **Fuzzy Group** transform in **Other Transforms** on the **SSIS Toolbox** to the **Data Flow** tab under **Combine Correct and Corrected Records**.</span></span>  
  
2.  <span data-ttu-id="f760d-107">**데이터 흐름** 탭에서 **유사 항목 그룹** 변환을 마우스 오른쪽 단추로 클릭 하 고 **이름 바꾸기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f760d-107">Right-click **Fuzzy Group** Transform in the **Data Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="f760d-108">**Id가 일치 하는 그룹 공급자** 를 입력 하 고 **enter**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="f760d-108">Type **Group Suppliers with matching IDs** and press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="f760d-109">연결- **올바른 및 수정 된 레코드** 를 파란색 커넥터를 사용 하 여 **id가 일치 하는 그룹 공급자로** 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="f760d-109">Connect **Combine Correct and Corrected Records** to **Group Suppliers with matching IDs** using the blue connector.</span></span>  
  
     <span data-ttu-id="f760d-110">![일치하는 ID가 있는 그룹 공급자에 대한 연결](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-01.jpg "일치하는 ID가 있는 그룹 공급자에 대한 연결")</span><span class="sxs-lookup"><span data-stu-id="f760d-110">![Connection to Group Suppliers with Matching IDs](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-01.jpg "Connection to Group Suppliers with Matching IDs")</span></span>  
  
4.  <span data-ttu-id="f760d-111">**Id가 일치 하는 그룹 공급자를**두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f760d-111">Double-click **Group Suppliers with matching IDs**.</span></span>  
  
5.  <span data-ttu-id="f760d-112">**유사 항목 그룹 변환 편집기**에서 **OLE DB 연결 관리자 드롭다운 목록** 옆에 있는 **새로 만들기** 를 클릭 하 여 **연결 관리자 OLE DB 구성** 대화 상자를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f760d-112">In the **Fuzzy Group Transformation Editor**, click **New** next to **OLE DB Connection Manager drop-down list** to launch **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
6.  <span data-ttu-id="f760d-113">대화 상자에서 **새로 만들기** 를 클릭 하 여 **연결 관리자** 대화 상자를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f760d-113">In the dialog box, click **New** to launch **Connection Manager** dialog box.</span></span>  
  
7.  <span data-ttu-id="f760d-114">서버 이름으로 **(local)** 또는 **마침표** (.)를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f760d-114">Type **(local)** or **period** (.) for the Server name.</span></span>  
  
8.  <span data-ttu-id="f760d-115">**데이터베이스 이름 선택 또는 입력** 필드에 대해 **MDS** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f760d-115">Select **MDS** for **Select or enter a database name** field.</span></span> <span data-ttu-id="f760d-116">이 경우에는 MDS 데이터베이스를 **유사 항목 그룹 변환**의 임시 저장소로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f760d-116">You will use the MDS database as the temporary storage for the **Fuzzy Group Transform**.</span></span> <span data-ttu-id="f760d-117">**유사 항목 그룹화** 변환에서는 변환 알고리즘에서 작업을 수행 하는 데 필요한 임시 SQL Server 테이블을 만들기 위해 SQL Server 인스턴스에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f760d-117">The **Fuzzy Grouping** transformation requires a connection to an instance of SQL Server to create the temporary SQL Server tables that the transformation algorithm requires to do its work.</span></span> <span data-ttu-id="f760d-118">데이터베이스를 만들거나 다른 기존 데이터베이스를 이 목적에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f760d-118">You can create a database or use another existing database for this purpose.</span></span>  
  
9. <span data-ttu-id="f760d-119">연결 **테스트** 를 클릭 하 여 연결을 테스트 하 고 메시지 상자에서 **확인** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f760d-119">Click **Test Connection** to test the connection and click **OK** on the message box.</span></span>  
  
10. <span data-ttu-id="f760d-120">**연결 관리자** 대화 상자에서 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f760d-120">In the **Connection Manager** dialog box, click **OK**.</span></span>  
  
11. <span data-ttu-id="f760d-121">**(로컬)을 선택 합니다. MDS** (또는 **localhost) MDS** **)를 클릭 하 고** **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f760d-121">Select **(local).MDS** (or **localhost.MDS**) from the **list of Data Connections** and click **OK**.</span></span>  
  
12. <span data-ttu-id="f760d-122">**유사 항목 그룹화 변환 편집기**에서 **(local)을 확인 합니다. MDS** 또는 **localhost MDS** 는 **OLE DB 연결 관리자**에 대해 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f760d-122">In the **Fuzzy Grouping Transformation Editor**, confirm that **(local).MDS** or **localhost.MDS** is selected for the **OLE DB Connection Manager**.</span></span>  
  
13. <span data-ttu-id="f760d-123">**열** 탭으로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f760d-123">Switch to the **Columns** tab.</span></span>  
  
14. <span data-ttu-id="f760d-124">**사용 가능한 입력 열**목록에서 **SupplierID_Output** (확인란)을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f760d-124">Select (check box) **SupplierID_Output** from the list of **Available Input Columns**.</span></span> <span data-ttu-id="f760d-125">변환을 구성하려면 중복 항목을 식별할 때 사용할 입력 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f760d-125">To configure the transformation, select the input columns to use when identifying duplicates.</span></span> <span data-ttu-id="f760d-126">간단한 설명을 위해 이 단계에서는 SupplierID만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f760d-126">To keep it simple, you only use the SupplierID in this step.</span></span>  
  
     <span data-ttu-id="f760d-127">![유사 항목 그룹화 변환 편집기](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-02.jpg "유사 항목 그룹화 변환 편집기")</span><span class="sxs-lookup"><span data-stu-id="f760d-127">![Fuzzy Grouping Transformation Editor](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-02.jpg "Fuzzy Grouping Transformation Editor")</span></span>  
  
15. <span data-ttu-id="f760d-128">**확인** 을 클릭 하 여 **유사 항목 그룹 변환 편집기**를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="f760d-128">Click **OK** to close the **Fuzzy Group Transformation Editor**.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="f760d-129">다음 단계</span><span class="sxs-lookup"><span data-stu-id="f760d-129">Next Step</span></span>  
 [<span data-ttu-id="f760d-130">태스크 11: 조건부 분할 변환을 추가하여 중복 항목 필터링</span><span class="sxs-lookup"><span data-stu-id="f760d-130">Task 11: Adding Conditional Split Transform to Filter Duplicates</span></span>](../../2014/tutorials/task-11-adding-conditional-split-transform-to-filter-duplicates.md)  
  
  
