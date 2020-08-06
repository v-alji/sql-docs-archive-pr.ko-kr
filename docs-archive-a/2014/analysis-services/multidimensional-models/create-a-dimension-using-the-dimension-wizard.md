---
title: 차원 마법사를 사용 하 여 차원 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], creating
ms.assetid: d84f66ae-7551-49bf-99d0-88368ca2dd0e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9ec38dc7170b915dce0cedea60c93385560e11f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737054"
---
# <a name="create-a-dimension-using-the-dimension-wizard"></a><span data-ttu-id="2f78d-102">차원 마법사를 사용하여 차원 만들기</span><span class="sxs-lookup"><span data-stu-id="2f78d-102">Create a Dimension Using the Dimension Wizard</span></span>
  <span data-ttu-id="2f78d-103">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 차원 마법사를 사용하여 새 차원을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-103">You can create a new dimension by using the Dimension Wizard in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
### <a name="to-create-a-new-dimension"></a><span data-ttu-id="2f78d-104">새 차원을 만들려면</span><span class="sxs-lookup"><span data-stu-id="2f78d-104">To create a new dimension</span></span>  
  
1.  <span data-ttu-id="2f78d-105">**솔루션 탐색기**에서 **차원**을 마우스 오른쪽 단추로 클릭 한 다음 **새 차원**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-105">In **Solution Explorer**, right-click **Dimensions**, and then click **New Dimension**.</span></span>  
  
2.  <span data-ttu-id="2f78d-106">차원 마법사의 **생성 방법 선택** 페이지에서 **기존 테이블 사용**을 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-106">On the **Select Creation Method** page of the Dimension Wizard, select **Use an existing table**, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f78d-107">기존 테이블 없이 차원을 만들어야 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-107">You might occasionally have to create a dimension without using an existing table.</span></span> <span data-ttu-id="2f78d-108">자세한 내용은 [데이터 원본에 시간이 아닌 테이블을 생성하여 차원 만들기](create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md) 및 [시간 테이블을 생성하여 시간 차원 만들기](create-a-time-dimension-by-generating-a-time-table.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2f78d-108">For more information, see [Create a Dimension by Generating a Non-Time Table in the Data Source](create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md) and [Create a Time Dimension by Generating a Time Table](create-a-time-dimension-by-generating-a-time-table.md).</span></span>  
  
3.  <span data-ttu-id="2f78d-109">**원본 정보 지정** 페이지에서 다음 절차를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-109">On the **Specify Source Information** page, do the following procedures:</span></span>  
  
    1.  <span data-ttu-id="2f78d-110">**데이터 원본 뷰** 목록에서 데이터 원본 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-110">In the **Data source view** list, select a data source view.</span></span>  
  
    2.  <span data-ttu-id="2f78d-111">**주 테이블** 목록에서 주 차원 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-111">In the **Main table** list, select the main dimension table.</span></span>  
  
    3.  <span data-ttu-id="2f78d-112">**키 열** 목록에서 주 차원 테이블에 정의된 기본 키에 따라 자동으로 선택된 키 열을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-112">In the **Key columns** list, review the key columns that the wizard has automatically selected based on the primary key that is defined in the main dimension table.</span></span> <span data-ttu-id="2f78d-113">이 기본 설정을 변경하려면 차원 테이블을 팩트 테이블에 연결하는 키 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-113">To change this default setting, specify the key columns that link the dimension table to the fact table.</span></span>  
  
    4.  <span data-ttu-id="2f78d-114">**이름 열** 드롭다운 목록에서 자동으로 선택된 이름 열을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-114">In the **Name column** drop-down list, review the name column that the wizard has automatically selected.</span></span>  
  
         <span data-ttu-id="2f78d-115">이 기본 이름은 열에 설명 정보가 포함된 경우에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-115">This default name is appropriate when the column contains descriptive information.</span></span> <span data-ttu-id="2f78d-116">그러나 최종 사용자에게 보다 의미 있는 가치를 포함하는 이름을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-116">However, you might want to specify a name that contains values that are more meaningful for the end user.</span></span> <span data-ttu-id="2f78d-117">예를 들어 Products 차원에 있는 제품 범주 특성의 키 열로 **ProductCategoryKey** 열이 사용되면 **ProductCategoryName** 열을 해당 이름 열로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-117">For example, if a product category attribute in a Products dimension uses the **ProductCategoryKey** column as its key column, you can specify the **ProductCategoryName** column as its name column.</span></span>  
  
         <span data-ttu-id="2f78d-118">**키 열** 목록에 키 열이 여러 개 있는 경우 키 특성에 대한 멤버 값을 제공하는 이름 열을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-118">If the **Key columns** list contains multiple key columns, you must specify a name column that provides the member values for the key attribute.</span></span> <span data-ttu-id="2f78d-119">이를 위해 데이터 원본 뷰에서 명명된 계산을 만들고 이를 이름 열로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-119">To do this, you can create a named calculation in the data source view and use that as the name column.</span></span>  
  
    5.  <span data-ttu-id="2f78d-120">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-120">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="2f78d-121">**관련 테이블 선택** 페이지에서 차원에 포함시킬 관련 테이블을 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-121">On the **Select Related Tables** page, select the related tables that you want to include in your dimension, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f78d-122"> 지정된 주 차원 테이블에 다른 차원 테이블에 대한 관계가 있을 경우 **관련 테이블 선택** 페이지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-122">The **Select Related Tables** page appears if the main dimension table that you specified has relationships to other dimension tables.</span></span>  
  
5.  <span data-ttu-id="2f78d-123">**차원 특성 선택** 페이지에서 차원에 포함시킬 특성을 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-123">On the **Select Dimension Attributes** page, select the attributes that you want to include in the dimension, and then click **Next**.</span></span>  
  
     <span data-ttu-id="2f78d-124">필요에 따라 특성 이름을 변경하고 찾아보기를 설정 또는 해제하며 특성 유형을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-124">Optionally, you can change the attribute names, enable or disable browsing, and specify the attribute type.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f78d-125"> 특성의 **찾아보기 사용** 및 **특성 유형** 필드를 활성화하려면 차원에 포함시킬 특성 이름을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-125">To make the **Enable Browsing** and **Attribute Type** fields of an attribute active, the attribute must be selected for inclusion in the dimension.</span></span>  
  
6.  <span data-ttu-id="2f78d-126">**계정 인텔리전스 정의** 페이지의 **기본 제공 계정 유형** 열에서 계정 유형을 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-126">On the **Define Account Intelligence** page, in the **Built-In Account Types** column, select the account type, and then click **Next**.</span></span>  
  
     <span data-ttu-id="2f78d-127">계정 유형은 **원본 테이블 계정 유형** 열에 나열된 원본 테이블의 계정 유형에 대응해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-127">The account type must correspond to the account type of the source table that is listed in the **Source Table Account Types** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f78d-128">**계정 인텔리전스 정의** 페이지는 마법사의 **차원 특성 선택** 페이지에서 **계정 유형** 차원 특성을 정의한 경우에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-128">The **Define Account Intelligence** page appears if you defined an **Account Type** dimension attribute on the **Select Dimension Attributes** page of the wizard.</span></span>  
  
7.  <span data-ttu-id="2f78d-129">**마법사 완료** 페이지에서 새 차원의 이름을 입력하고 차원 구조를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-129">On the **Completing the Wizard** page, enter a name for the new dimension and review the dimension structure.</span></span> <span data-ttu-id="2f78d-130">변경하려면 **뒤로**를 클릭하고 변경하지 않으려면 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-130">If you want to make changes, click **Back**; otherwise, click **Finish**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f78d-131">차원 마법사를 완료한 후에는 차원 디자이너를 사용하여 차원의 특성과 계층을 추가, 제거 및 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f78d-131">You can use Dimension Designer after you complete the Dimension Wizard to add, remove, and configure attributes and hierarchies in the dimension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f78d-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2f78d-132">See Also</span></span>  
 [<span data-ttu-id="2f78d-133">기존 테이블을 사용하여 차원 만들기</span><span class="sxs-lookup"><span data-stu-id="2f78d-133">Create a Dimension by Using an Existing Table</span></span>](create-a-dimension-by-using-an-existing-table.md)  
  
  
