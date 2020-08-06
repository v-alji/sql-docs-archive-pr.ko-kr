---
title: '태스크 14: 제어 흐름에 SQL 실행 태스크를 추가 하 여 MDS에 대 한 저장 프로시저 실행 Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 9a5d1b52-d505-4e6f-8a89-569329c094e2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: da8e80b25706c40e749fc364baeb578681e76b42
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731160"
---
# <a name="task-14-adding-execute-sql-task-to-control-flow-to-run-the-stored-procedure-for-mds"></a><span data-ttu-id="dfdec-102">태스크 14: Control Flow에 SQL 실행 태스크를 추가하여 MDS에 대한 저장 프로시저 실행</span><span class="sxs-lookup"><span data-stu-id="dfdec-102">Task 14: Adding Execute SQL Task to Control Flow to Run the Stored Procedure for MDS</span></span>
  <span data-ttu-id="dfdec-103">데이터를 MDS의 준비 테이블에 로드한 다음에는 준비 테이블의 데이터를 MDS 데이터베이스의 적합한 테이블로 로드하기 위해 해당 테이블과 연관된 저장 프로시저를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdec-103">After loading data into the staging tables of MDS, you run a stored procedure associated with that table to load the data from staging into the appropriate tables in the MDS database.</span></span> <span data-ttu-id="dfdec-104">이 저장 프로시저에는 전달해야 하는 두 개의 필수 매개 변수(LogFlag 및 VersionName)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfdec-104">This stored procedure has two required parameters that you need to pass: LogFlag and VersionName.</span></span> <span data-ttu-id="dfdec-105">LogFlag는 준비 프로세스 중 트랜잭션을 기록할지 여부를 지정하고, VersionName은 모델의 버전을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dfdec-105">LogFlag specifies whether transactions are logged during the staging process and VersionName represents the version of the model.</span></span> <span data-ttu-id="dfdec-106">자세한 내용은 [준비 된 저장 프로시저](https://msdn.microsoft.com/library/hh231028.aspx) 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dfdec-106">See [Staged Stored Procedure](https://msdn.microsoft.com/library/hh231028.aspx) topic for more details.</span></span>

 <span data-ttu-id="dfdec-107">이 작업에서는 준비된 데이터를 적절한 MDS 테이블로 로드하기 위해 저장 프로시저를 호출하는 SQL 실행 태스크를 제어 흐름에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdec-107">In this task, you add the Execute SQL Task to the control flow to invoke the stored procedure to load the staged data into appropriate MDS tables.</span></span>

1.  <span data-ttu-id="dfdec-108">이제 **제어 흐름** 탭으로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdec-108">Now, switch to the **Control Flow** tab.</span></span>

2.  <span data-ttu-id="dfdec-109">**SQL 실행 태스크** 를 **SSIS 도구 상자** 에서 **제어 흐름** 탭으로 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="dfdec-109">Drag-drop **Execute SQL Task** from the **SSIS Toolbox** to the **Control Flow** tab.</span></span>

3.  <span data-ttu-id="dfdec-110">**제어 흐름** 탭에서 **SQL 실행 태스크** 를 마우스 오른쪽 단추로 클릭 하 고 **이름 바꾸기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdec-110">Right-click **Execute SQL Task** in the **Control Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="dfdec-111">**트리거 저장 프로시저를 입력 하 여 데이터를 MDS에 로드 하** 고 **enter**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="dfdec-111">Type **Trigger Stored Procedure to Load Data into MDS** and press **ENTER**.</span></span>

4.  <span data-ttu-id="dfdec-112">**수신, 정리, 일치 및 데이터 공급자 데이터** 를 연결 하 여 녹색 커넥터를 사용 하 여 **데이터를 로드 하는 트리거 저장 프로시저** 를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdec-112">Connect **Receive, Cleanse, Match, and Curate Supplier Data** to **Trigger Stored Procedure to Load Data** using the green connector.</span></span>

     <span data-ttu-id="dfdec-113">![SQL 실행 태스크에 연결](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-01.jpg "SQL 실행 태스크에 연결")</span><span class="sxs-lookup"><span data-stu-id="dfdec-113">![Connect to Execute SQL Task](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-01.jpg "Connect to Execute SQL Task")</span></span>

5.  <span data-ttu-id="dfdec-114">**변수** 창을 사용 하 여 다음 설정을 사용 하 여 두 개의 새 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdec-114">Using the **Variables** window, add two new variables with the following settings.</span></span> <span data-ttu-id="dfdec-115">**변수** 창이 표시 되지 않으면 메뉴 모음에서 **SSIS** 를 클릭 하 고 **변수**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdec-115">If you do not see the **Variables** window, click **SSIS** on the menu bar and click **Variables**.</span></span>

    |<span data-ttu-id="dfdec-116">Name</span><span class="sxs-lookup"><span data-stu-id="dfdec-116">Name</span></span>|<span data-ttu-id="dfdec-117">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="dfdec-117">Data Type</span></span>|<span data-ttu-id="dfdec-118">값</span><span class="sxs-lookup"><span data-stu-id="dfdec-118">Value</span></span>|
    |----------|---------------|-----------|
    |<span data-ttu-id="dfdec-119">LogFlag</span><span class="sxs-lookup"><span data-stu-id="dfdec-119">LogFlag</span></span>|<span data-ttu-id="dfdec-120">Int32</span><span class="sxs-lookup"><span data-stu-id="dfdec-120">Int32</span></span>|<span data-ttu-id="dfdec-121">1</span><span class="sxs-lookup"><span data-stu-id="dfdec-121">1</span></span>|
    |<span data-ttu-id="dfdec-122">VersionName</span><span class="sxs-lookup"><span data-stu-id="dfdec-122">VersionName</span></span>|<span data-ttu-id="dfdec-123">String</span><span class="sxs-lookup"><span data-stu-id="dfdec-123">String</span></span>|<span data-ttu-id="dfdec-124">VERSION_1</span><span class="sxs-lookup"><span data-stu-id="dfdec-124">VERSION_1</span></span>|

     <span data-ttu-id="dfdec-125">![SSIS 변수 창](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-02.jpg "SSIS 변수 창")</span><span class="sxs-lookup"><span data-stu-id="dfdec-125">![SSIS Variables Window](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-02.jpg "SSIS Variables Window")</span></span>

6.  <span data-ttu-id="dfdec-126">**트리거 저장 프로시저를 두 번 클릭 하 여 데이터를 MDS로 로드**합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdec-126">Double-click **Trigger Stored Procedure to Load Data into MDS**.</span></span>

7.  <span data-ttu-id="dfdec-127">**SQL 실행 태스크 편집기** 대화 상자에서 **(로컬)을 선택 합니다. MDS** (또는 **localhost) MDS**)를 **연결**합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdec-127">In the **Execute SQL Task Editor** dialog box, select **(local).MDS** (or **localhost.MDS**) for **Connection**.</span></span>

8.  <span data-ttu-id="dfdec-128">**EXEC [stg]. [를 입력 합니다. udp_Supplier_Leaf]?,?,?**</span><span class="sxs-lookup"><span data-stu-id="dfdec-128">Type **EXEC [stg].[udp_Supplier_Leaf] ?, ?, ?**</span></span> <span data-ttu-id="dfdec-129">**SQL 문**</span><span class="sxs-lookup"><span data-stu-id="dfdec-129">for **SQL Statement**.</span></span> <span data-ttu-id="dfdec-130">SQL Server Management Studio를 사용해서 이름을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfdec-130">You can verify the name by using SQL Server Management Studio.</span></span>

     <span data-ttu-id="dfdec-131">![SQL 편집기 실행 대화 상자 - 일반 설정](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-03.jpg "SQL 편집기 실행 대화 상자 - 일반 설정")</span><span class="sxs-lookup"><span data-stu-id="dfdec-131">![Execute SQL Editor Dialog Box - General Settings](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-03.jpg "Execute SQL Editor Dialog Box - General Settings")</span></span>

9. <span data-ttu-id="dfdec-132">왼쪽의 메뉴에서 **매개 변수 매핑** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdec-132">Click **Parameter Mapping** from the menu on left.</span></span>

10. <span data-ttu-id="dfdec-133">**매개 변수 매핑** 페이지에서 **추가** 를 클릭 하 여 매핑을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdec-133">In the **Parameter Mapping** page, click **Add** to add a mapping.</span></span> <span data-ttu-id="dfdec-134">드롭 다운 목록의 값이 올바르게 표시되도록 창을 최대화하고 열 크기를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdec-134">Maximize the window and resize columns so that you can see values in drop-down lists properly.</span></span>

11. <span data-ttu-id="dfdec-135">**변수 이름**에 대 한 드롭다운 목록에서 **User:: versionname** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdec-135">Select **User::VersionName** from the drop-down list for the **Variable Name**.</span></span>

12. <span data-ttu-id="dfdec-136">**데이터 형식**에 대해 **NVARCHAR** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdec-136">Select **NVARCHAR** for **Data Type**.</span></span>

13. <span data-ttu-id="dfdec-137">**매개 변수 이름**으로 **0** 을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdec-137">Type **0** (zero) for **Parameter Name**.</span></span>

14. <span data-ttu-id="dfdec-138">이전 4개 단계를 반복해서 변수를 두 개 더 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdec-138">Repeat the previous four steps to add two more variables.</span></span>

    |<span data-ttu-id="dfdec-139">변수 이름</span><span class="sxs-lookup"><span data-stu-id="dfdec-139">Variable Name</span></span>|<span data-ttu-id="dfdec-140">데이터 형식(중요)</span><span class="sxs-lookup"><span data-stu-id="dfdec-140">Data Type (important)</span></span>|<span data-ttu-id="dfdec-141">매개 변수 이름</span><span class="sxs-lookup"><span data-stu-id="dfdec-141">Parameter Name</span></span>|
    |-------------------|-----------------------------|--------------------|
    |<span data-ttu-id="dfdec-142">User::LogFlag</span><span class="sxs-lookup"><span data-stu-id="dfdec-142">User::LogFlag</span></span>|<span data-ttu-id="dfdec-143">LONG</span><span class="sxs-lookup"><span data-stu-id="dfdec-143">LONG</span></span>|<span data-ttu-id="dfdec-144">1</span><span class="sxs-lookup"><span data-stu-id="dfdec-144">1</span></span>|
    |<span data-ttu-id="dfdec-145">User::BatchTag</span><span class="sxs-lookup"><span data-stu-id="dfdec-145">User::BatchTag</span></span>|<span data-ttu-id="dfdec-146">NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="dfdec-146">NVARCHAR</span></span>|<span data-ttu-id="dfdec-147">2</span><span class="sxs-lookup"><span data-stu-id="dfdec-147">2</span></span>|

     <span data-ttu-id="dfdec-148">![SQL 실행 태스크 편집기 - 매개 변수 매핑](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-04.jpg "SQL 실행 태스크 편집기 - 매개 변수 매핑")</span><span class="sxs-lookup"><span data-stu-id="dfdec-148">![Execute SQL Task Editor - Parameter Mapping](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-04.jpg "Execute SQL Task Editor - Parameter Mapping")</span></span>

15. <span data-ttu-id="dfdec-149">**확인** 을 클릭 하 여 **SQL 편집기 실행** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="dfdec-149">Click **OK** to close the **Execute SQL Editor** dialog box.</span></span>

## <a name="next-step"></a><span data-ttu-id="dfdec-150">다음 단계</span><span class="sxs-lookup"><span data-stu-id="dfdec-150">Next Step</span></span>
 [<span data-ttu-id="dfdec-151">태스크 15: SSIS 프로젝트 빌드 및 실행</span><span class="sxs-lookup"><span data-stu-id="dfdec-151">Task 15: Building and Running the SSIS Project</span></span>](../../2014/tutorials/task-15-building-and-running-the-ssis-project.md)


