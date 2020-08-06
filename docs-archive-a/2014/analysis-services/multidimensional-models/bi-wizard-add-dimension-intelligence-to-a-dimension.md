---
title: 차원에 차원 인텔리전스 추가 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Business Intelligence enhancements [Analysis Services], dimension intelligence
- dimensions [Analysis Services], Business Intelligence enhancements
- dimension intelligence [Analysis Services]
- Type property
ms.assetid: b64fa386-eac2-4286-a320-0631a1887aac
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5cad591d3e89dc306571efa9aeef9d81a235c9fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648659"
---
# <a name="add-dimension-intelligence-to-a-dimension"></a><span data-ttu-id="e52cb-102">차원에 차원 인텔리전스 추가</span><span class="sxs-lookup"><span data-stu-id="e52cb-102">Add Dimension Intelligence to a Dimension</span></span>
  <span data-ttu-id="e52cb-103">큐브나 차원에 차원 인텔리전스 기능을 추가하여 차원에 대한 표준 비즈니스 유형을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e52cb-103">Add the dimension intelligence enhancement to a cube or a dimension to specify a standard business type for a dimension.</span></span> <span data-ttu-id="e52cb-104">이 기능은 차원 특성에 해당하는 유형도 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e52cb-104">This enhancement also specifies the corresponding types for dimension attributes.</span></span> <span data-ttu-id="e52cb-105">클라이언트 애플리케이션은 데이터를 분석할 때 이러한 유형 지정을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e52cb-105">Client applications can use these type specifications when analyzing data.</span></span>  
  
 <span data-ttu-id="e52cb-106">차원 인텔리전스를 추가하려면 비즈니스 인텔리전스 마법사의 **기능 선택** 페이지에서 **차원 인텔리전스 정의** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e52cb-106">To add dimension intelligence, you use the Business Intelligence Wizard, and select the **Define dimension intelligence** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="e52cb-107">그런 다음 마법사의 안내를 따라 차원 인텔리전스를 적용할 차원을 선택하고 선택한 차원에 대한 특성을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="e52cb-107">This wizard then guides you through the steps of selecting a dimension to which you want to apply dimension intelligence and identifying the attributes for the selected dimension.</span></span>  
  
## <a name="selecting-a-dimension"></a><span data-ttu-id="e52cb-108">차원 선택</span><span class="sxs-lookup"><span data-stu-id="e52cb-108">Selecting a Dimension</span></span>  
 <span data-ttu-id="e52cb-109">마법사의 첫 번째 **차원 인텔리전스 옵션 설정** 페이지에서 차원 인텔리전스를 적용할 차원을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e52cb-109">On the first **Set Dimension Intelligence Options** page of the wizard, you specify the dimension to which you want to apply dimension intelligence.</span></span> <span data-ttu-id="e52cb-110">선택한 차원에 차원 인텔리전스 기능을 추가하면 차원이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="e52cb-110">The dimension intelligence enhancement added to this selected dimension will result in changes to the dimension.</span></span> <span data-ttu-id="e52cb-111">이러한 변경 내용은 선택된 차원을 포함하는 모든 큐브에 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="e52cb-111">These changes will be inherited by all cubes that include the selected dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e52cb-112">차원으로 **계정** 을 선택한 경우 차원에 대한 계정 인텔리전스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e52cb-112">If you select **Account** as the dimension, you will be specifying account intelligence for the dimension.</span></span> <span data-ttu-id="e52cb-113">자세한 내용은 [차원에 계정 인텔리전스 추가](bi-wizard-add-account-intelligence-to-a-dimension.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e52cb-113">For more information, see [Add Account Intelligence to a Dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).</span></span>  
  
## <a name="specifying-dimension-attributes"></a><span data-ttu-id="e52cb-114">차원 특성 지정</span><span class="sxs-lookup"><span data-stu-id="e52cb-114">Specifying Dimension Attributes</span></span>  
 <span data-ttu-id="e52cb-115">차원 **인텔리전스 정의** 페이지의 **차원 유형** 목록에서 선택한 항목은 차원의 속성을 설정 합니다 `Type` .</span><span class="sxs-lookup"><span data-stu-id="e52cb-115">On the **Define Dimension Intelligence** page, in **Dimension Type** list, the selection that you make sets the dimension's `Type` property.</span></span> <span data-ttu-id="e52cb-116">`Type` 속성을 설정하는 것은 서버와 클라이언트 애플리케이션에 차원 내용에 대한 정보를 제공하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e52cb-116">The `Type` property setting provides information to servers and client applications about the contents of a dimension.</span></span> <span data-ttu-id="e52cb-117">일부 설정은 클라이언트 애플리케이션에서 안내 역할만 합니다. 이러한 설정은 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="e52cb-117">Some settings only provide guidance for client applications; these settings are optional.</span></span> <span data-ttu-id="e52cb-118">그러나 계정, 시간 등의 설정은 특정 동작을 결정하며 특정 비즈니스 인텔리전스 기능을 구현하기 위해 반드시 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e52cb-118">Other settings, such as Accounts or Time, determine specific behaviors and may be required to implement particular business intelligence enhancements.</span></span> <span data-ttu-id="e52cb-119">예를 들어 SQL Server Management Studio에서 차원 유형을 사용하여 통화 차원을 식별하고 해당 통화 변환 규칙을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e52cb-119">For example, the SQL Server Management Studio uses the dimension type to identify a Currency dimension and set the appropriate currency conversion rules.</span></span> <span data-ttu-id="e52cb-120">**차원 유형** 의 기본 설정은 **일반**이며 차원 내용에 대해 어떠한 가정도 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e52cb-120">The default setting for the **Dimension Type** is **Regular**, which makes no assumptions about the contents of the dimension.</span></span>  
  
 <span data-ttu-id="e52cb-121">차원 유형을 선택한 후에는 **차원 특성**의 **포함** 열에서 차원의 해당 특성이 있는 각 표준 특성 유형 옆의 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e52cb-121">After selecting the dimension type, in **Dimension attributes**, in the **Include** column, select the check box next to each standard attribute type for which there is a corresponding attribute in the dimension.</span></span> <span data-ttu-id="e52cb-122">마지막으로 **차원 특성** 열에서 드롭다운 목록을 확장하고 선택한 특성 유형에 해당하는 차원의 특성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e52cb-122">Finally, in the **Dimension Attribute** column, expand the drop-down list, and select the attribute in the dimension that corresponds to the selected attribute type.</span></span> <span data-ttu-id="e52cb-123">이 목록에서 특성을 선택하면 해당 특성의 `Type` 속성이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e52cb-123">Selecting the attribute from the list sets the attribute `Type` property for the attributes.</span></span>  
  
 <span data-ttu-id="e52cb-124">예를 들어 계정 차원에 차원 인텔리전스를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="e52cb-124">For example, you want to add dimension intelligence to an Accounts dimension.</span></span> <span data-ttu-id="e52cb-125">**차원 유형**에서 **계정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e52cb-125">In **Dimension Type**, you select **Accounts**.</span></span> <span data-ttu-id="e52cb-126">차원에 **계정 유형** 및 **계정 설명** 특성이 있는 경우 **포함** 열에서 **계정 이름** 및 **계정 유형** 계정 유형에 대한 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e52cb-126">Then, if the dimension has **Account Type** and **Account Description** attributes, in the **Include** column, you select the check boxes for the **Account Name** and **Account Type** account types.</span></span> <span data-ttu-id="e52cb-127">그런 다음 **차원 특성** 열에서 이러한 계정 유형을 차원의 **계정 설명** 및 **계정 유형** 특성에 각각 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e52cb-127">In the **Dimension Attribute** column, you then associate these account types with the **Account Description** and **Account Type** attributes, respectively, in the dimension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e52cb-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e52cb-128">See Also</span></span>  
 [<span data-ttu-id="e52cb-129">비즈니스 인텔리전스 마법사를 사용하여 시간 인텔리전스 계산 정의</span><span class="sxs-lookup"><span data-stu-id="e52cb-129">Define Time Intelligence Calculations using the Business Intelligence Wizard</span></span>](define-time-intelligence-calculations-using-the-business-intelligence-wizard.md)  
  
  
