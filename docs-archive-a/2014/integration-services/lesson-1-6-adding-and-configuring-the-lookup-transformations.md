---
title: '6단계: 조회 변환 추가 및 구성 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5c59f723-9707-4407-80ae-f05f483cf65f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 96b0a848508c19eb24cf1538244a39fcec57361a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651123"
---
# <a name="step-6-adding-and-configuring-the-lookup-transformations"></a><span data-ttu-id="6b50a-102">6단계: 조회 변환 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="6b50a-102">Step 6: Adding and Configuring the Lookup Transformations</span></span>
  <span data-ttu-id="6b50a-103">원본 파일에서 데이터를 추출하도록 플랫 파일 원본을 구성한 후에 다음 태스크에서는 **CurrencyKey** 및 **DateKey**값을 얻는 데 필요한 조회 변환을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-103">After you have configured the Flat File source to extract data from the source file, the next task is to define the Lookup transformations needed to obtain the values for the **CurrencyKey** and **DateKey**.</span></span> <span data-ttu-id="6b50a-104">조회 변환에서는 지정한 입력 열의 데이터를 참조 데이터 세트의 열로 조인하여 조회를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-104">A Lookup transformation performs a lookup by joining data in the specified input column to a column in a reference dataset.</span></span> <span data-ttu-id="6b50a-105">참조 데이터 세트는 기존 테이블, 기존 뷰, 새 테이블 또는 SQL 문의 결과일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-105">The reference dataset can be an existing table or view, a new table, or the result of an SQL statement.</span></span> <span data-ttu-id="6b50a-106">이 자습서에서 조회 변환은 OLE DB 연결 관리자를 사용하여 참조 데이터 세트의 원본인 데이터가 포함된 데이터베이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-106">In this tutorial, the Lookup transformation uses an OLE DB connection manager to connect to the database that contains the data that is the source of the reference dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6b50a-107">또한 참조 데이터 세트가 포함된 캐시에 연결되도록 조회 변환을 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-107">You can also configure the Lookup transformation to connect to a cache that contains the reference dataset.</span></span> <span data-ttu-id="6b50a-108">자세한 내용은 [Lookup Transformation](data-flow/transformations/lookup-transformation.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6b50a-108">For more information, see [Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
 <span data-ttu-id="6b50a-109">이 자습서에서는 다음과 같은 두 가지 조회 변환 구성 요소를 패키지에 추가하고 구성하는 과정을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-109">For this tutorial, you will add and configure the following two Lookup transformation components to the package:</span></span>  
  
-   <span data-ttu-id="6b50a-110">플랫 파일의 일치하는 **CurrencyID** 열 값에 따라 **DimCurrency** 차원 테이블의 **CurrencyKey** 열에서 값을 조회하는 하나의 변환</span><span class="sxs-lookup"><span data-stu-id="6b50a-110">One transformation to perform a lookup of values from the **CurrencyKey** column of the **DimCurrency** dimension table based on matching **CurrencyID** column values from the flat file.</span></span>  
  
-   <span data-ttu-id="6b50a-111">플랫 파일의 일치하는 **CurrencyDate** 열 값에 따라 **DimDate** 차원 테이블의 **DateKey** 열에서 값을 조회하는 하나의 변환</span><span class="sxs-lookup"><span data-stu-id="6b50a-111">One transformation to perform a lookup of values from the **DateKey** column of the **DimDate** dimension table based on matching **CurrencyDate** column values from the flat file.</span></span>  
  
 <span data-ttu-id="6b50a-112">두 경우 모두 조회 변환에는 이전에 작성한 OLE DB 연결 관리자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-112">In both cases, the Lookup transformation will utilize the OLE DB connection manager that you previously created.</span></span>  
  
### <a name="to-add-and-configure-the-lookup-currency-key-transformation"></a><span data-ttu-id="6b50a-113">Lookup Currency Key 변환을 추가하고 구성하려면</span><span class="sxs-lookup"><span data-stu-id="6b50a-113">To add and configure the Lookup Currency Key transformation</span></span>  
  
1.  <span data-ttu-id="6b50a-114">**SSIS 도구 상자**에서 **일반**을 확장 한 다음 **조회** 를 **데이터 흐름** 탭의 디자인 화면으로 끌어다 놓습니다. lookup을 **Extract Sample Currency 데이터** 원본 바로 아래에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-114">In the **SSIS Toolbox**, expand **Common**, and then drag **Lookup** onto the design surface of the **Data Flow** tab. Place Lookup directly below the **Extract Sample Currency Data** source.</span></span>  
  
2.  <span data-ttu-id="6b50a-115">**Extract Sample Currency Data** 플랫 파일 원본을 클릭하고 녹색 화살표를 새로 추가한 **조회** 변환으로 끌어다 놓아서 두 구성 요소를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-115">Click the **Extract Sample Currency Data** flat file source and drag the green arrow onto the newly added **Lookup** transformation to connect the two components.</span></span>  
  
3.  <span data-ttu-id="6b50a-116">**데이터 흐름** 디자인 화면에서 **조회** 변환의 **조회** 를 클릭하고 이름을 **Lookup Currency Key**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-116">On the **Data Flow** design surface, click **Lookup** in the **Lookup** transformation, and change the name to **Lookup Currency Key**.</span></span>  
  
4.  <span data-ttu-id="6b50a-117">**Lookup CurrencyKey** 변환을 두 번 클릭하여 조회 변환 편집기를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-117">Double-click the **Lookup CurrencyKey** transformation to display the Lookup Transformation Editor.</span></span>  
  
5.  <span data-ttu-id="6b50a-118">**일반** 페이지에서 다음을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-118">On the **General** page, make the following selections:</span></span>  
  
    1.  <span data-ttu-id="6b50a-119">**전체 캐시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-119">Select **Full cache**.</span></span>  
  
    2.  <span data-ttu-id="6b50a-120">**연결 형식** 영역에서 **OLE DB 연결 관리자**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-120">In the **Connection type** area, select **OLE DB connection manager**.</span></span>  
  
6.  <span data-ttu-id="6b50a-121">**연결** 페이지에서 다음을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-121">On the **Connection** page, make the following selections:</span></span>  
  
    1.  <span data-ttu-id="6b50a-122">**OLE DB 연결 관리자** 상자에 **localhost.AdventureWorksDW2012** 가 표시되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-122">In the **OLE DB connection manager** dialog box, ensure that **localhost.AdventureWorksDW2012** is displayed.</span></span>  
  
    2.  <span data-ttu-id="6b50a-123">**SQL 쿼리 결과 사용**을 선택하고 다음 SQL 문을 입력하거나 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-123">Select **Use results of an SQL query**, and then type or copy the following SQL statement:</span></span>  
  
        ```  
        select * from (select * from [dbo].[DimCurrency]) as refTable  
        where [refTable].[CurrencyAlternateKey] = 'ARS'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'AUD'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'BRL'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'CAD'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'CNY'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'DEM'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'EUR'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'FRF'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'GBP'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'JPY'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'MXN'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'SAR'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'USD'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'VEB'  
        ```  
  
7.  <span data-ttu-id="6b50a-124">**열** 페이지에서 다음을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-124">On the **Columns** page, make the following selections:</span></span>  
  
    1.  <span data-ttu-id="6b50a-125">**사용 가능한 입력 열** 패널에서 **CurrencyID** 를 **사용 가능한 조회 열** 패널로 끌어다 **CurrencyAlternateKey**에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-125">In the **Available Input Columns** panel, drag **CurrencyID** to the **Available Lookup Columns** panel and drop it on **CurrencyAlternateKey**.</span></span>  
  
    2.  <span data-ttu-id="6b50a-126">**사용 가능한 조회 열** 목록에서 **CurrencyKey**왼쪽에 있는 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-126">In the **Available Lookup Columns** list, select the check box to the left of **CurrencyKey**.</span></span>  
  
8.  <span data-ttu-id="6b50a-127">**확인** 을 클릭하여 **데이터 흐름** 디자인 화면으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-127">Click **OK** to return to the **Data Flow** design surface.</span></span>  
  
9. <span data-ttu-id="6b50a-128">Lookup Currency Key 변환을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-128">Right-click the Lookup Currency Key transformation, click **Properties**.</span></span>  
  
10. <span data-ttu-id="6b50a-129">속성 창에서 `LocaleID` 속성이 **영어 (미국)** 로 설정 되어 있고 **defaultcodepage** 속성이 **1252**로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-129">In the Properties window, verify that the `LocaleID` property is set to **English (United States)** and the **DefaultCodePage** property is set to **1252**.</span></span>  
  
### <a name="to-add-and-configure-the--lookup-datekey-transformation"></a><span data-ttu-id="6b50a-130">Lookup DateKey 변환을 추가하고 구성하려면</span><span class="sxs-lookup"><span data-stu-id="6b50a-130">To add and configure the  Lookup DateKey transformation</span></span>  
  
1.  <span data-ttu-id="6b50a-131">**SSIS 도구 상자**에서 **조회** 를 **데이터 흐름** 디자인 화면으로 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-131">In the **SSIS Toolbox**, drag **Lookup** onto the **Data Flow** design surface.</span></span> <span data-ttu-id="6b50a-132">조회를 **Lookup Currency Key** 변환 바로 아래에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-132">Place Lookup directly below the **Lookup Currency Key** transformation.</span></span>  
  
2.  <span data-ttu-id="6b50a-133">**Lookup Currency Key** 변환을 클릭하고 녹색 화살표를 새로 추가한 **조회** 변환으로 끌어다 놓아서 두 구성 요소를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-133">Click the **Lookup Currency Key** transformation and drag the green arrow onto the newly added **Lookup** transformation to connect the two components.</span></span>  
  
3.  <span data-ttu-id="6b50a-134">**입/출력 선택** 대화 상자에서 **출력** 목록 상자의 **조회 일치 항목 출력** 을 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-134">In the **Input Output Selection** dialog box, click **Lookup Match Output** in the **Output** list box, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="6b50a-135">**데이터 흐름** 디자인 화면에서 새로 추가한 **Lookup** 변환의 **조회** 를 클릭하고 이름을 **Lookup Date Key**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-135">On the **Data Flow** design surface, click **Lookup** in the newly added **Lookup** transformation, and change the name to **Lookup Date Key**.</span></span>  
  
5.  <span data-ttu-id="6b50a-136">**Lookup Date Key** 변환을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-136">Double-click the **Lookup Date Key** transformation.</span></span>  
  
6.  <span data-ttu-id="6b50a-137">**일반** 페이지에서 **부분 캐시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-137">On the **General** page, select **Partial cache**.</span></span>  
  
7.  <span data-ttu-id="6b50a-138">**연결** 페이지에서 다음을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-138">On the **Connection** page, make the following selections:</span></span>  
  
    1.  <span data-ttu-id="6b50a-139">**OLEDB 연결 관리자** 대화 상자에서 **localhost.AdventureWorksDW2012** 가 표시되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-139">In the **OLEDB connection manager** dialog box, ensure that **localhost.AdventureWorksDW2012** is displayed.</span></span>  
  
    2.  <span data-ttu-id="6b50a-140">**테이블 또는 뷰 사용** 상자에서 **[dbo].[DimDate]** 를 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-140">In the **Use a table or view** box, type or select **[dbo].[DimDate]**.</span></span>  
  
8.  <span data-ttu-id="6b50a-141">**열** 페이지에서 다음을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-141">On the **Columns** page, make the following selections:</span></span>  
  
    1.  <span data-ttu-id="6b50a-142">**사용 가능한 입력 열** 패널에서 **CurrencyDate** 를 **사용 가능한 조회 열** 패널로 끌어다 **FullDateAlternateKey**에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-142">In the **Available Input Columns** panel, drag **CurrencyDate** to the **Available Lookup Columns** panel and drop it on **FullDateAlternateKey**.</span></span>  
  
    2.  <span data-ttu-id="6b50a-143">**사용 가능한 조회 열** 목록에서 **DateKey**왼쪽에 있는 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-143">In the **Available Lookup Columns** list, select the check box to the left of **DateKey**.</span></span>  
  
9. <span data-ttu-id="6b50a-144">**고급** 페이지에서 캐싱 옵션을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-144">On the **Advanced** page, review the caching options.</span></span>  
  
10. <span data-ttu-id="6b50a-145">**확인** 을 클릭하여 **데이터 흐름** 디자인 화면으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-145">Click **OK** to return to the **Data Flow** design surface.</span></span>  
  
11. <span data-ttu-id="6b50a-146">Lookup Date Key 변환을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-146">Right-click the Lookup Date Key transformation and click **Properties.**</span></span>  
  
12. <span data-ttu-id="6b50a-147">속성 창에서 `LocaleID` 속성이 **영어 (미국)** 로 설정 되어 있고 **defaultcodepage** 속성이 **1252**로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b50a-147">In the Properties window, verify that the `LocaleID` property is set to **English (United States)** and the **DefaultCodePage** property is set to **1252**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="6b50a-148">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="6b50a-148">Next Task in Lesson</span></span>  
 [<span data-ttu-id="6b50a-149">7단계: OLE DB 대상 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="6b50a-149">Step 7: Adding and Configuring the OLE DB Destination</span></span>](lesson-1-7-adding-and-configuring-the-ole-db-destination.md)  
  
## <a name="see-also"></a><span data-ttu-id="6b50a-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6b50a-150">See Also</span></span>  
 [<span data-ttu-id="6b50a-151">조회 변환</span><span class="sxs-lookup"><span data-stu-id="6b50a-151">Lookup Transformation</span></span>](data-flow/transformations/lookup-transformation.md)  
  
  
