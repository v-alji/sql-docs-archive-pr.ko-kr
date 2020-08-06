---
title: 파워 뷰 보고서에 대 한 기본 필드 집합 구성 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- ql12.asvs.bidtoolset.deffieldset.f1
ms.assetid: 6836b42f-28b8-4a98-a86d-2c3c109f0189
author: minewiskan
ms.author: owend
ms.openlocfilehash: c66fbbacd0cc2efd7d379bcc8e68149551476869
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728792"
---
# <a name="configure-default-field-set-for-power-view-reports-ssas-tabular"></a><span data-ttu-id="001e5-102">파워 뷰 보고서의 기본 필드 집합 구성(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="001e5-102">Configure Default Field Set for Power View Reports (SSAS Tabular)</span></span>
  <span data-ttu-id="001e5-103">기본 필드 집합은 보고서 필드 목록에서 테이블을 선택할 때 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 보고서 캔버스에 자동으로 추가되는 미리 정의된 열 및 측정값 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="001e5-103">A default field set is a predefined list of columns and measures that are automatically added to a [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] report canvas when the table is selected in the report field list.</span></span> <span data-ttu-id="001e5-104">테이블 형식 모델 작성자는 보고서에 모델을 사용하는 보고서 작성자를 위해 기본 필드 집합을 만들어 중복된 단계를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="001e5-104">Tabular model authors can create a default field set to eliminate redundant steps for report authors who use the model for their reports.</span></span> <span data-ttu-id="001e5-105">예를 들어, 고객 연락처 정보를 사용하는 대부분의 보고서 작성자가 항상 연락처 이름, 기본 전화 번호, 전자 메일 주소 및 회사 이름을 보려고 하는 것으로 파악되는 경우 해당 열을 미리 선택하여 작성자가 Customer Contact 테이블을 클릭할 때 보고서 캔버스에 이러한 정보가 항상 추가되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="001e5-105">For example, if you know that most report authors who work with customer contact information always want to see a contact name, a primary phone number, an email address, and a company name, you can pre-select those columns so that they are always added to the report canvas when the author clicks the Customer Contact table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="001e5-106">기본 필드 집합은 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]에서 데이터 모델로 사용되는 테이블 형식 모델에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="001e5-106">A default field set applies only to a tabular model used as a data model in [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span> <span data-ttu-id="001e5-107">Excel 피벗 보고서에서는 기본 필드 집합이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="001e5-107">Default field sets are not supported in Excel pivot reports.</span></span>  
  
## <a name="creating-a-default-field-set"></a><span data-ttu-id="001e5-108">기본 필드 집합 만들기</span><span class="sxs-lookup"><span data-stu-id="001e5-108">Creating a Default Field Set</span></span>  
 <span data-ttu-id="001e5-109">[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]에서 특정 테이블이 선택될 때마다 기본적으로 포함되는 필드를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="001e5-109">You can determine which fields, if any, are included by default whenever a specific table is selected in [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span> <span data-ttu-id="001e5-110">목록에 필드가 나타나는 순서도 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="001e5-110">You can also determine the order in which fields appear in the list.</span></span> <span data-ttu-id="001e5-111">기본 필드 집합을 지정하려면 테이블 형식 모델 프로젝트에서 보고서 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="001e5-111">To specify a default field set, you set report properties in the tabular model project.</span></span>  
  
#### <a name="to-add-a-default-field-set"></a><span data-ttu-id="001e5-112">기본 필드 집합을 만들려면</span><span class="sxs-lookup"><span data-stu-id="001e5-112">To add a default field set</span></span>  
  
1.  <span data-ttu-id="001e5-113">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 기본 필드 목록을 구성 중인 테이블(탭)을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="001e5-113">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the table (tab) for which you are configuring a default field list.</span></span>  
  
2.  <span data-ttu-id="001e5-114">**속성** 창의 **기본 필드 집합** 속성에서 **편집하려면 클릭**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="001e5-114">In the **Properties** window, in the **Default Field Set** property, click **Click to edit**.</span></span>  
  
3.  <span data-ttu-id="001e5-115">기본 필드 집합 대화 상자에서 필드를 하나 이상 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="001e5-115">In the Default Field Set dialog, select one or more fields.</span></span> <span data-ttu-id="001e5-116">측정값을 비롯하여 테이블의 모든 필드를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="001e5-116">You can choose any field in the table, including measures.</span></span> <span data-ttu-id="001e5-117">Shift 키를 누른 채 범위를 선택하거나 Ctrl 키를 누른 채 개별 필드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="001e5-117">Hold down the Shift key to select a range, or the Ctrl key to select individual fields.</span></span>  
  
4.  <span data-ttu-id="001e5-118">**추가** 를 클릭하여 선택한 필드를 기본 필드 집합에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="001e5-118">Click **Add** to add them to the default field set.</span></span>  
  
5.  <span data-ttu-id="001e5-119">위쪽 및 아래쪽 단추를 사용하여 필드 목록의 필드 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="001e5-119">Use the Up and Down buttons to specify an order to the field list.</span></span> <span data-ttu-id="001e5-120">필드 집합에 대해 정의된 순서로 필드가 보고서에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="001e5-120">Fields will be added to the report in the order defined for the field set.</span></span>  
  
6.  <span data-ttu-id="001e5-121">통합 문서의 다른 테이블에 대해 이러한 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="001e5-121">Repeat these steps for other tables in your workbook.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="001e5-122">다음 단계</span><span class="sxs-lookup"><span data-stu-id="001e5-122">Next Step</span></span>  
 <span data-ttu-id="001e5-123">기본 필드 집합을 만든 후에는 기본 레이블, 기본 이미지, 기본 그룹 동작 또는 같은 값의 여러 행이 한 행에 함께 그룹화되는지 아니면 따로 나열되는지 지정하여 보고서 디자인 환경을 더 자세히 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="001e5-123">After you create a default field set, you can further influence the report design experience by specifying default labels, default images, default group behavior, or whether rows that contain the same value are grouped together in one row or listed individually.</span></span> <span data-ttu-id="001e5-124">자세한 내용은 [파워 뷰 보고서의 테이블 동작 속성 구성&#40;SSAS 테이블 형식&#41;](power-view-configure-table-behavior-properties-for-reports.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="001e5-124">For more information, see [Configure Table Behavior Properties for Power View Reports &#40;SSAS Tabular&#41;](power-view-configure-table-behavior-properties-for-reports.md).</span></span>  
  
  
