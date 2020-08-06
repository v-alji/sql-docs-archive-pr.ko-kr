---
title: 사용자 지정 보고서 항목 클래스 라이브러리 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, RDL
- RDL [Reporting Services], custom report items
ms.assetid: f18c5d8f-1d6b-4f0b-8657-c14896c2ce0d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 60f8cf912eb6ff3f5080e9cf757df40f37e65079
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639414"
---
# <a name="custom-report-item-class-libraries"></a><span data-ttu-id="fc3d6-102">사용자 지정 보고서 항목 클래스 라이브러리</span><span class="sxs-lookup"><span data-stu-id="fc3d6-102">Custom Report Item Class Libraries</span></span>
  <span data-ttu-id="fc3d6-103">사용자 지정 보고서 항목은 `Microsoft.ReportDesigner` 네임스페이스의 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-103">Custom report items use classes from the `Microsoft.ReportDesigner` namespace.</span></span> <span data-ttu-id="fc3d6-104">사용자 지정 보고서 항목 구현에 사용되는 클래스는 두 개의 기본 범주로 그룹화할 수 있습니다. 하나는 사용자 지정 보고서 항목 인프라를 지원하도록 설계된 고유 클래스이고, 다른 하나는 관련 RDL(Report Definition Language) 요소의 기능을 캡슐화하는 관리되는 래퍼 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-104">The classes used to implement a custom report item can be grouped into two main categories: unique classes designed to support custom report item infrastructure, and managed wrapper classes that encapsulate the functionality of relevant Report Definition Language (RDL) elements.</span></span> <span data-ttu-id="fc3d6-105">이러한 클래스 사용 방법에 대한 코드 예는 [SQL Server Reporting Services 제품 예제(SQL Server Reporting Services Product Samples)](https://go.microsoft.com/fwlink/?LinkId=177889)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-105">For a code sample on how to use these classes, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="custom-report-item-infrastructure-classes"></a><span data-ttu-id="fc3d6-106">사용자 지정 보고서 항목 인프라 클래스</span><span class="sxs-lookup"><span data-stu-id="fc3d6-106">Custom Report Item Infrastructure Classes</span></span>  
 <span data-ttu-id="fc3d6-107">다음 클래스는 사용자 지정 보고서 항목을 구현하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-107">The following classes are used to implement a custom report item.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fc3d6-108">다음 표는 전체 목록이 아니라 각 클래스에 가장 일반적으로 사용되는 속성 및 메서드를 나열한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-108">The following tables are not complete listings; they include only the most commonly used properties and methods for each class.</span></span>  
  
### <a name="microsoftreportdesignercustomreportitemdesigner"></a><span data-ttu-id="fc3d6-109">Microsoft.ReportDesigner.CustomReportItemDesigner</span><span class="sxs-lookup"><span data-stu-id="fc3d6-109">Microsoft.ReportDesigner.CustomReportItemDesigner</span></span>  
 <span data-ttu-id="fc3d6-110">주 사용자 지정 보고서 항목 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-110">This is the main custom report item class.</span></span> <span data-ttu-id="fc3d6-111">각 사용자 지정 보고서 항목 구현의 주 클래스는 이 클래스에서 상속되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-111">The main class of your custom report item implementation must inherit from this class.</span></span>  
  
#### <a name="public-properties"></a><span data-ttu-id="fc3d6-112">Public 속성</span><span class="sxs-lookup"><span data-stu-id="fc3d6-112">Public Properties</span></span>  
  
|||  
|-|-|  
|`Name`|<span data-ttu-id="fc3d6-113">사용자 지정 보고서 항목의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-113">The name of the custom report item.</span></span>|  
|`Type`|<span data-ttu-id="fc3d6-114">사용자 지정 보고서 항목의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-114">The type of the custom report item.</span></span>|  
|`CustomData`|<span data-ttu-id="fc3d6-115">디자인 타임에 지정된 사용자 지정 보고서 항목 데이터 속성을 캡슐화하는 <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-115">A <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> object that encapsulates the custom report item data properties specified at design time.</span></span>|  
|`CustomProperties`|<span data-ttu-id="fc3d6-116">사용자 지정 보고서 항목에 대한 사용자 지정 속성 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-116">A collection of custom properties for the custom report item.</span></span>|  
|`Height`|<span data-ttu-id="fc3d6-117">사용자 지정 보고서 항목 컨트롤의 높이입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-117">The height of the custom report item control.</span></span>|  
|`Width`|<span data-ttu-id="fc3d6-118">사용자 지정 보고서 항목 컨트롤의 너비입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-118">The width of the custom report item control.</span></span>|  
|`Report`|<span data-ttu-id="fc3d6-119">보고서의 데이터 세트 목록과 같은 보고서 수준 속성의 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-119">A container for the report-level properties, such as the list of datasets in the report.</span></span>|  
|`AltReportItem`|<span data-ttu-id="fc3d6-120">사용자 지정 보고서 항목 런타임 컨트롤이 지원되지 않는 곳에서 사용하는, 대체 보고서 항목 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-120">The alternate report item object, to be used where the custom report item run-time control is not supported.</span></span>|  
|`Style`|<span data-ttu-id="fc3d6-121">사용자 지정 보고서 항목의 스타일 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-121">The style properties for the custom report item.</span></span>|  
|`Adornment`|<span data-ttu-id="fc3d6-122">컨트롤의 대화형 편집에 사용되는 도구 영역 창입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-122">An adornment window used for interactive editing of the control.</span></span>|  
|`Site`|<span data-ttu-id="fc3d6-123">구성 요소의 `ISite`입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-123">The `ISite` of the component.</span></span>|  
|`DesignerVerbCollection`|<span data-ttu-id="fc3d6-124">컨트롤의 바로 가기 메뉴를 위한 사용자 지정 동사 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-124">An array of custom verbs for the control's shortcut menu.</span></span>|  
  
#### <a name="public-methods"></a><span data-ttu-id="fc3d6-125">Public 메서드</span><span class="sxs-lookup"><span data-stu-id="fc3d6-125">Public Methods</span></span>  
  
|||  
|-|-|  
|`BeginEdit`|<span data-ttu-id="fc3d6-126">컨트롤의 대화형 편집을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-126">Activates interactive editing for the control.</span></span>|  
|`DoDefaultAction`|<span data-ttu-id="fc3d6-127">컨트롤에서 마우스를 두 번 클릭하거나 Enter 키를 눌렀을 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-127">Called in response to double-clicking or pressing Return on the control.</span></span>|  
|`EndEdit`|<span data-ttu-id="fc3d6-128">컨트롤의 대화형 편집을 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-128">Deactivates interactive editing for the control.</span></span>|  
|`GetService`|<span data-ttu-id="fc3d6-129">서비스를 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-129">Returns an object which represents a service.</span></span>|  
|`InitializeNewComponent`|<span data-ttu-id="fc3d6-130">새 사용자 지정 보고서 항목이 만들어질 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-130">Called when a new custom report item is created.</span></span>|  
|`Invalidate`|<span data-ttu-id="fc3d6-131">컨트롤의 전체 화면을 다시 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-131">Repaints the entire surface of the control.</span></span>|  
|`OnDragEnter`<br /><br /> `OnDragDrop`|<span data-ttu-id="fc3d6-132">개체를 컨트롤로 끌어올 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-132">Called when an object is dragged onto the control.</span></span>|  
|`OnPaint`|<span data-ttu-id="fc3d6-133">`Paint` 이벤트에 대한 응답으로 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-133">Called in response to the `Paint` event.</span></span>|  
  
### <a name="microsoftreportdesignercustomreportitemattribute"></a><span data-ttu-id="fc3d6-134">Microsoft.ReportDesigner.CustomReportItemAttribute</span><span class="sxs-lookup"><span data-stu-id="fc3d6-134">Microsoft.ReportDesigner.CustomReportItemAttribute</span></span>  
 <span data-ttu-id="fc3d6-135">사용자 지정 보고서 항목의 유형을 식별하는 데 사용되는 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-135">This is the attribute used to identify the type of the custom report item.</span></span> <span data-ttu-id="fc3d6-136">이름은 `Name` `ReportItem` 보고서 디자이너 구성 파일에 있는 요소의 <> 특성 값과 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-136">The name must match the value of the <`Name`> attribute of the `ReportItem` element in the Report Designer configuration file.</span></span>  
  
#### <a name="public-methods"></a><span data-ttu-id="fc3d6-137">Public 메서드</span><span class="sxs-lookup"><span data-stu-id="fc3d6-137">Public Methods</span></span>  
  
|||  
|-|-|  
|`CustomReportItemAttribute`|<span data-ttu-id="fc3d6-138">CustomReportItemAttribute 개체를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-138">Constructs the CustomReportItemAttribute object.</span></span>|  
  
### <a name="microsoftreportdesignerlocalizednameattribute"></a><span data-ttu-id="fc3d6-139">Microsoft.ReportDesigner.LocalizedNameAttribute</span><span class="sxs-lookup"><span data-stu-id="fc3d6-139">Microsoft.ReportDesigner.LocalizedNameAttribute</span></span>  
 <span data-ttu-id="fc3d6-140">사용자 지정 보고서 항목 디자이너에 사용할 표시 이름을 지정하는 데 사용되는 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-140">This is the attribute used to specify display name to use for the custom report item designer.</span></span>  
  
#### <a name="public-methods"></a><span data-ttu-id="fc3d6-141">Public 메서드</span><span class="sxs-lookup"><span data-stu-id="fc3d6-141">Public Methods</span></span>  
  
|||  
|-|-|  
|`LocalizedNameAttribute`|<span data-ttu-id="fc3d6-142">LocalizedNameAttribute 개체를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-142">Constructs the LocalizedNameAttribute object.</span></span>|  
  
### <a name="microsoftreportdesigneradornment"></a><span data-ttu-id="fc3d6-143">Microsoft.ReportDesigner.Adornment</span><span class="sxs-lookup"><span data-stu-id="fc3d6-143">Microsoft.ReportDesigner.Adornment</span></span>  
 <span data-ttu-id="fc3d6-144">사용자 지정 보고서 항목 디자인 타임 구성 요소에서 `Adornment` 클래스를 사용하여 주 사각형 디자인 화면 바깥에 일정 영역을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-144">The `Adornment` class is used by the custom report item design-time component to provide areas outside of the main rectangle of the design surface.</span></span> <span data-ttu-id="fc3d6-145">이 영역은 마우스 클릭 및 끌어서 놓기 작업과 같은 사용자 인터페이스 이벤트를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-145">These areas can handle user interface events, such as mouse clicks and drag-and-drop operations.</span></span>  
  
#### <a name="public-methods"></a><span data-ttu-id="fc3d6-146">Public 메서드</span><span class="sxs-lookup"><span data-stu-id="fc3d6-146">Public Methods</span></span>  
  
|||  
|-|-|  
|`OnShow`|<span data-ttu-id="fc3d6-147">`Adornment`가 활성화될 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-147">Called when the `Adornment` is activated.</span></span>|  
|`OnHide`|<span data-ttu-id="fc3d6-148">`Adornment`가 비활성화될 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-148">Called when the `Adornment` is deactivated.</span></span>|  
|`Paint`|<span data-ttu-id="fc3d6-149">`Paint` 이벤트에 대한 응답으로 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-149">Called in response to the `Paint` event.</span></span>|  
|`OnDragEnter`<br /><br /> `OnDragOver`<br /><br /> `OnDragLeave`<br /><br /> `OnDragDrop`|<span data-ttu-id="fc3d6-150">개체를 `Adornment`로 끌어올 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-150">Called when an object is dragged into the `Adornment`.</span></span>|  
  
### <a name="microsoftreportdesigneradornerservice"></a><span data-ttu-id="fc3d6-151">Microsoft.ReportDesigner.AdornerService</span><span class="sxs-lookup"><span data-stu-id="fc3d6-151">Microsoft.ReportDesigner.AdornerService</span></span>  
 <span data-ttu-id="fc3d6-152">이 클래스는 사용자 지정 보고서 항목에서 사용자 지정 보고서 항목 디자인 타임 구성 요소에 `Adornment` 개체를 지원하기 위해 사용하는 표시 서비스 컬렉션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-152">This class is used to provide a collection of display services used by the custom report item to support `Adornment` objects for the custom report item design-time component.</span></span>  
  
#### <a name="public-properties"></a><span data-ttu-id="fc3d6-153">Public 속성</span><span class="sxs-lookup"><span data-stu-id="fc3d6-153">Public Properties</span></span>  
  
|||  
|-|-|  
|`AdornerWindowBounds`|<span data-ttu-id="fc3d6-154">Adorner 창의 경계입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-154">The bounds of the Adorner window.</span></span>|  
|`AdornerWindowRegion`|<span data-ttu-id="fc3d6-155">Adorner 창의 영역입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-155">The region of the Adorner window.</span></span>|  
|`AdornerWindowGraphics`|<span data-ttu-id="fc3d6-156">Adorner 창에 대한 그래픽 컨텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-156">A graphics context for the Adorner window.</span></span>|  
  
#### <a name="public-methods"></a><span data-ttu-id="fc3d6-157">Public 메서드</span><span class="sxs-lookup"><span data-stu-id="fc3d6-157">Public Methods</span></span>  
  
|||  
|-|-|  
|`ComponentRectInDesignerFrame`|<span data-ttu-id="fc3d6-158">디자이너 프레임 좌표로 변환된 구성 요소의 경계를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-158">Returns the bounds of the component translated into designer frame coordinates.</span></span>|  
|`InvalidateAdorner`|<span data-ttu-id="fc3d6-159">Adorner 창을 무효화합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-159">Invalidates the Adorner window.</span></span>|  
|`PointToAdorner`|<span data-ttu-id="fc3d6-160">Adorner 창 좌표로 변환된 화면 좌표 위치를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-160">Returns a point in screen coordinates translated to Adorner window coordinates.</span></span>|  
  
### <a name="microsoftreportdesignerexpressioneditor"></a><span data-ttu-id="fc3d6-161">Microsoft.ReportDesigner.ExpressionEditor</span><span class="sxs-lookup"><span data-stu-id="fc3d6-161">Microsoft.ReportDesigner.ExpressionEditor</span></span>  
 <span data-ttu-id="fc3d6-162">이 클래스를 사용하여 사용자 지정 보고서 항목 디자인 타임 컨트롤에서 식 편집기를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-162">This class can be used from your custom report item design-time control to invoke the Expression Editor.</span></span>  
  
#### <a name="public-methods"></a><span data-ttu-id="fc3d6-163">Public 메서드</span><span class="sxs-lookup"><span data-stu-id="fc3d6-163">Public Methods</span></span>  
  
|||  
|-|-|  
|`EditValue`|<span data-ttu-id="fc3d6-164">주어진 개체 값으로 초기화된 식 편집기를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-164">Invokes the Expression Editor, initialized with the given object value.</span></span>|  
  
### <a name="microsoftreportdesignerifieldsdataobject"></a><span data-ttu-id="fc3d6-165">Microsoft.ReportDesigner.IFieldsDataObject</span><span class="sxs-lookup"><span data-stu-id="fc3d6-165">Microsoft.ReportDesigner.IFieldsDataObject</span></span>  
 <span data-ttu-id="fc3d6-166">이 클래스는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 필드 컬렉션이며 디자인 환경에서 끌어서 놓기 이벤트를 지원하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-166">This class is a collection of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fields, and is used to support drag-and-drop events in the design environment.</span></span> <span data-ttu-id="fc3d6-167">`IReportItemDataObject`에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-167">Inherits from `IReportItemDataObject`.</span></span>  
  
#### <a name="public-properties"></a><span data-ttu-id="fc3d6-168">Public 속성</span><span class="sxs-lookup"><span data-stu-id="fc3d6-168">Public Properties</span></span>  
  
|||  
|-|-|  
|`DataSetName`|<span data-ttu-id="fc3d6-169">삭제할 필드를 포함하는 데이터 세트의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-169">The name of the dataset containing the fields to be dropped.</span></span>|  
|`Fields`|<span data-ttu-id="fc3d6-170">삭제할 필드(`Microsoft.ReportDesigner.Field`) 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3d6-170">The collection of fields (`Microsoft.ReportDesigner.Field`) to be dropped.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fc3d6-171">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fc3d6-171">See Also</span></span>  
 <span data-ttu-id="fc3d6-172">[SSRS&#41;&#40;보고서 정의 언어](../reports/report-definition-language-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fc3d6-172">[Report Definition Language &#40;SSRS&#41;](../reports/report-definition-language-ssrs.md) </span></span>  
 <span data-ttu-id="fc3d6-173">[사용자 지정 보고서 항목 런타임 구성 요소 만들기](creating-a-custom-report-item-run-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="fc3d6-173">[Creating a Custom Report Item Run-Time Component](creating-a-custom-report-item-run-time-component.md) </span></span>  
 [<span data-ttu-id="fc3d6-174">사용자 지정 보고서 항목 디자인 타임 구성 요소 만들기</span><span class="sxs-lookup"><span data-stu-id="fc3d6-174">Creating a Custom Report Item Design-Time Component</span></span>](creating-a-custom-report-item-design-time-component.md)  
  
  
