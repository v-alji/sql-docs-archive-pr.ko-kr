---
title: 느린 변경 차원 마법사를 사용하여 출력 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Slowly Changing Dimension transformation
- slowly changing dimensions
- Slowly Changing Dimension Wizard
ms.assetid: da111731-1ffa-49b9-bcaa-3c93fd0eb619
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f6ec3dfb34de8eb7e20b255ce485ee506f070749
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652240"
---
# <a name="configure-outputs-using-the-slowly-changing-dimension-wizard"></a><span data-ttu-id="0104b-102">느린 변경 차원 마법사를 사용하여 출력 구성</span><span class="sxs-lookup"><span data-stu-id="0104b-102">Configure Outputs Using the Slowly Changing Dimension Wizard</span></span>
  <span data-ttu-id="0104b-103">느린 변경 차원 마법사는 느린 변경 차원 변환에 대한 편집기 역할을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-103">The Slowly Changing Dimension Wizard functions as the editor for the Slowly Changing Dimension transformation.</span></span> <span data-ttu-id="0104b-104">느린 변경 차원 데이터에 대한 데이터 흐름의 작성 및 구성은 복잡한 태스크일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-104">Building and configuring the data flow for slowly changing dimension data can be a complex task.</span></span> <span data-ttu-id="0104b-105">느린 변경 차원 마법사를 사용하면 열을 매핑하고, 비즈니스 키 열을 선택하고, 열 변경 특성을 설정하고, 유추 차원 멤버에 대한 지원을 구성하는 단계별 안내에 따라 가장 쉬운 방법으로 느린 변경 차원 변환 출력에 대한 데이터 흐름을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-105">The Slowly Changing Dimension Wizard offers the simplest method of building the data flow for the Slowly Changing Dimension transformation outputs by guiding you through the steps of mapping columns, selecting business key columns, setting column change attributes, and configuring support for inferred dimension members.</span></span>

 <span data-ttu-id="0104b-106">차원 테이블에 있는 적어도 하나 이상의 비즈니스 키 열을 선택하고 이를 입력 열에 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-106">You must choose at least one business key column in the dimension table and map it to an input column.</span></span> <span data-ttu-id="0104b-107">비즈니스 키의 값은 원본의 레코드를 차원 테이블의 레코드로 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-107">The value of the business key links a record in the source to a record in the dimension table.</span></span> <span data-ttu-id="0104b-108">이 매핑은 변환에서 차원 테이블의 레코드를 찾고 레코드가 새로운 것인지 변경되는 것인지 확인하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-108">The transformation uses this mapping to locate the record in the dimension table and to determine whether a record is new or changing.</span></span> <span data-ttu-id="0104b-109">비즈니스 키는 일반적으로 원본의 기본 키이지만 레코드를 고유하게 식별하고 해당 값이 변경되지 않는 한 대체 키로 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-109">The business key is typically the primary key in the source, but it can be an alternate key as long as it uniquely identifies a record and its value does not change.</span></span> <span data-ttu-id="0104b-110">또한 비즈니스 키는 여러 개의 열로 구성된 복합 키로 사용될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-110">The business key can also be a composite key, consisting of multiple columns.</span></span> <span data-ttu-id="0104b-111">차원 테이블의 기본 키는 일반적으로 서로게이트 키입니다. 즉, ID 열 또는 스크립트와 같은 사용자 지정 솔루션을 통해 자동으로 생성되는 숫자 값입니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-111">The primary key in the dimension table is usually a surrogate key, which means a numeric value generated automatically by an identity column or by a custom solution such as a script.</span></span>

 <span data-ttu-id="0104b-112">느린 변경 차원 마법사를 실행하려면 데이터 흐름에 원본과 느린 변경 차원 변환을 추가한 다음 원본의 출력을 느린 변경 차원 변환의 입력에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-112">Before you can run the Slowly Changing Dimension Wizard, you must add a source and a Slowly Changing Dimension transformation to the data flow, and then connect the output from the source to the input of the Slowly Changing Dimension transformation.</span></span> <span data-ttu-id="0104b-113">선택적으로 데이터 흐름에는 데이터 원본과 느린 변경 차원 변환 사이의 다른 변환이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-113">Optionally, the data flow can include other transformations between the data source and the Slowly Changing Dimension transformation.</span></span>

 <span data-ttu-id="0104b-114">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 느린 변경 차원 마법사를 열려면 느린 변경 차원 변환을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-114">To open the Slowly Changing Dimension Wizard in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, double-click the Slowly Changing Dimension transformation.</span></span>

## <a name="creating-slowly-changing-dimension-outputs"></a><span data-ttu-id="0104b-115">느린 변경 차원 출력 만들기</span><span class="sxs-lookup"><span data-stu-id="0104b-115">Creating Slowly Changing Dimension Outputs</span></span>

#### <a name="to-create-slowly-changing-dimension-transformation-outputs"></a><span data-ttu-id="0104b-116">느린 변경 차원 변환 출력을 만들려면</span><span class="sxs-lookup"><span data-stu-id="0104b-116">To create Slowly Changing Dimension transformation outputs</span></span>

1.  <span data-ttu-id="0104b-117">업데이트하려는 차원 테이블이 포함된 데이터 원본에 액세스할 연결 관리자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-117">Choose the connection manager to access the data source that contains the dimension table that you want to update.</span></span>

     <span data-ttu-id="0104b-118">패키지에 포함된 연결 관리자 목록에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-118">You can select from a list of connection managers that the package includes.</span></span>

2.  <span data-ttu-id="0104b-119">업데이트하려는 차원 테이블 또는 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-119">Choose the dimension table or view you want to update.</span></span>

     <span data-ttu-id="0104b-120">연결 관리자를 선택한 후에는 데이터 원본의 테이블 또는 뷰를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-120">After you select the connection manager, you can select the table or view from the data source.</span></span>

3.  <span data-ttu-id="0104b-121">열에 키 특성을 설정하고 입력 열을 차원 테이블의 열로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-121">Set key attributes on columns and map input columns to columns in the dimension table.</span></span>

     <span data-ttu-id="0104b-122">차원 테이블에 있는 적어도 하나 이상의 비즈니스 키 열을 선택하고 이를 입력 열에 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-122">You must choose at least one business key column in the dimension table and map it to an input column.</span></span> <span data-ttu-id="0104b-123">다른 입력 열은 키가 아닌 매핑으로 차원 테이블의 열에 매핑될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-123">Other input columns can be mapped to columns in the dimension table as non-key mappings.</span></span>

4.  <span data-ttu-id="0104b-124">각 열에 대한 변경 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-124">Choose the change type for each column.</span></span>

    -   <span data-ttu-id="0104b-125">**변경 특성** 은 레코드의 기존 값을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-125">**Changing attribute** overwrites existing values in records.</span></span>

    -   <span data-ttu-id="0104b-126">**기록 특성** 은 기존 레코드를 업데이트하는 대신 새 레코드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-126">**Historical attribute** creates new records instead of updating existing records.</span></span>

    -   <span data-ttu-id="0104b-127">**고정 특성** 은 열 값이 변경되지 않도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-127">**Fixed attribute** indicates that the column value must not change.</span></span>

5.  <span data-ttu-id="0104b-128">고정 특성 및 변경 특성 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-128">Set fixed and changing attribute options.</span></span>

     <span data-ttu-id="0104b-129">**고정 특성** 변경 유형을 사용하도록 열을 구성한 경우에는 해당 열에서 변경 내용이 발견될 때 느린 변경 차원 변환이 실패할지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-129">If you configure columns to use the **Fixed attribute** change type, you can specify whether the Slowly Changing Dimension transformation fails when changes are detected in these columns.</span></span> <span data-ttu-id="0104b-130">**변경 특성** 변경 유형을 사용하도록 열을 구성한 경우에는 오래된 레코드를 포함하여 모든 일치하는 레코드가 업데이트되는지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-130">If you configure columns to use the **Changing attribute** change type, you can specify whether all matching records, including outdated records, are updated.</span></span>

6.  <span data-ttu-id="0104b-131">기록 특성 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-131">Set historical attribute options.</span></span>

     <span data-ttu-id="0104b-132">**기록 특성** 변경 유형을 사용하도록 열을 구성한 경우에는 현재 레코드와 만료된 레코드를 구분하는 방법을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-132">If you configure columns to use the **Historical attribute** change type, you must choose how to distinguish between current and expired records.</span></span> <span data-ttu-id="0104b-133">현재 레코드와 만료된 레코드를 구분하기 위해서는 현재 행 표시 열이나 두 개의 날짜 열을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-133">You can use a current row indicator column or two date columns to identify current and expired rows.</span></span> <span data-ttu-id="0104b-134">현재 행 표시 열을 사용할 때는 현재 행인 경우 **Current**또는 **True** 로 설정하고 만료된 행인 경우에는 **Expired** 또는 **False** 로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-134">If you use the current row indicator column, you can set it to **Current**, **True** when current and **Expired,** or **False** when expired.</span></span> <span data-ttu-id="0104b-135">또한 사용자 지정 값을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-135">You can also enter custom values.</span></span> <span data-ttu-id="0104b-136">시작 날짜와 종료 날짜의 두 날짜 열을 사용하는 경우에는 날짜 열 값을 설정할 때 시스템 변수를 선택하여 해당 값을 사용하거나 날짜를 입력하여 사용할 날짜를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-136">If you use two date columns, a start date and an end date, you can specify the date to use when setting the date column values by typing a date or by selecting a system variable and then using its value.</span></span>

7.  <span data-ttu-id="0104b-137">유추 멤버 지원을 지정하고 유추 멤버 레코드에 포함되는 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-137">Specify support for inferred members and choose the columns that the inferred member record contains.</span></span>

     <span data-ttu-id="0104b-138">측정값을 팩트 테이블로 로드할 때에는 존재하지 않는 유추 멤버에 대한 최소한의 레코드를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-138">When loading measures into a fact table, you can create minimal records for inferred members that do not yet exist.</span></span> <span data-ttu-id="0104b-139">그런 다음 실제 데이터를 사용할 수 있게 되면 차원 레코드를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-139">Later, when meaningful data is available, the dimension records can be updated.</span></span> <span data-ttu-id="0104b-140">다음과 같은 유형의 최소한의 레코드를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-140">The following types of minimal records can be created:</span></span>

    -   <span data-ttu-id="0104b-141">변경 유형이 포함된 모든 열이 Null인 레코드</span><span class="sxs-lookup"><span data-stu-id="0104b-141">A record in which all columns with change types are null.</span></span>

    -   <span data-ttu-id="0104b-142">부울 열에 유추 멤버로 표시되는 레코드</span><span class="sxs-lookup"><span data-stu-id="0104b-142">A record in which a Boolean column indicates the record is an inferred member.</span></span>

8.  <span data-ttu-id="0104b-143">느린 변경 차원 마법사에서 작성하는 구성을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-143">Review the configurations that the Slowly Changing Dimension Wizard builds.</span></span> <span data-ttu-id="0104b-144">지원되는 변경 유형에 따라 다른 데이터 흐름 구성 요소가 패키지에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-144">Depending on which change types are supported, different sets of data flow components are added to the package.</span></span>

     <span data-ttu-id="0104b-145">다음 다이어그램에서는 고정 특성, 변경 특성, 기록 특성 변경 내용, 유추 멤버 및 일치하는 레코드에 대한 변경 내용을 지원하는 데이터 흐름 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-145">The following diagram shows an example of a data flow that supports fixed attribute, changing attribute, and historical attribute changes, inferred members, and changes to matching records.</span></span>

     <span data-ttu-id="0104b-146">![느린 변경 차원 마법사의 데이터 흐름](../../media/dimensionwizard.gif "느린 변경 차원 마법사의 데이터 흐름")</span><span class="sxs-lookup"><span data-stu-id="0104b-146">![Data flow from Slowly Changing Dimension Wizard](../../media/dimensionwizard.gif "Data flow from Slowly Changing Dimension Wizard")</span></span>

## <a name="updating-slowly-changing-dimension-outputs"></a><span data-ttu-id="0104b-147">느린 변경 차원 출력 업데이트</span><span class="sxs-lookup"><span data-stu-id="0104b-147">Updating Slowly Changing Dimension Outputs</span></span>
 <span data-ttu-id="0104b-148">느린 변경 차원 변환 출력의 구성을 업데이트하는 가장 쉬운 방법은 느린 변경 차원 마법사를 다시 실행하고 마법사 페이지에서 속성을 수정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-148">The simplest way to update the configuration of the Slowly Changing Dimension transformation outputs is to rerun the Slowly Changing Dimension Wizard and modify properties from the wizard pages.</span></span> <span data-ttu-id="0104b-149">또한 **고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 느린 변경 차원 변환을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0104b-149">You can also update the Slowly Changing Dimension transformation using the **Advanced Editor** dialog box or programmatically.</span></span>

## <a name="see-also"></a><span data-ttu-id="0104b-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0104b-150">See Also</span></span>
 [<span data-ttu-id="0104b-151">느린 변경 차원 변환</span><span class="sxs-lookup"><span data-stu-id="0104b-151">Slowly Changing Dimension Transformation</span></span>](slowly-changing-dimension-transformation.md)


