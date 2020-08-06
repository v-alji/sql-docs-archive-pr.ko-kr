---
title: 사용자 지정 보고서 항목 디자인 타임 구성 요소 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, creating
ms.assetid: 323fd58a-a462-4c48-b188-77ebc0b4212e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b663dc3b0a9c54d1674bf153ee09dd36e0de7a00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639416"
---
# <a name="creating-a-custom-report-item-design-time-component"></a><span data-ttu-id="42f6e-102">사용자 지정 보고서 항목 디자인 타임 구성 요소 만들기</span><span class="sxs-lookup"><span data-stu-id="42f6e-102">Creating a Custom Report Item Design-Time Component</span></span>
  <span data-ttu-id="42f6e-103">사용자 지정 보고서 항목 디자인 타임 구성 요소는 Visual Studio 보고서 디자이너 환경에서 사용할 수 있는 컨트롤입니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-103">A custom report item design-time component is a control that can be used in the Visual Studio Report Designer environment.</span></span> <span data-ttu-id="42f6e-104">사용자 지정 보고서 항목 디자인 타임 구성 요소는 끌어서 놓기 작업이 가능하고 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 속성 브라우저와 통합되고 사용자 지정 속성 편집기를 제공하는 활성화된 디자인 화면을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-104">The custom report item design-time component provides an activated design surface that can accept drag-and-drop operations, integration with the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] property browser, and the ability to provide custom property editors.</span></span>  
  
 <span data-ttu-id="42f6e-105">사용자 지정 보고서 항목 디자인 타임 구성 요소를 사용하여 사용자는 디자인 환경에서 보고서에 사용자 지정 보고서 항목을 배치하고, 사용자 지정 보고서 항목에 사용자 지정 데이터 속성을 설정한 다음, 사용자 지정 보고서 항목을 보고서 프로젝트의 일부로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-105">With a custom report item design-time component, the user can position a custom report item on a report in the design environment, set custom data properties on the custom report item, and then save the custom report item as part of the report project.</span></span>  
  
 <span data-ttu-id="42f6e-106">개발 환경에서 디자인 타임 구성 요소를 사용하여 설정된 속성은 호스트 디자인 환경에 의해 직렬화 및 역직렬화된 다음 RDL(Report Definition Language) 파일에 요소로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-106">The properties that are set using the design-time component in the development environment are serialized and deserialized by the host design environment and then stored as elements in the Report Definition Language (RDL) file.</span></span> <span data-ttu-id="42f6e-107">보고서 처리기에 의해 보고서가 실행되면, 디자인 타임 구성 요소를 사용하여 설정된 속성을 보고서 처리기가 사용자 지정 보고서 항목 런타임 구성 요소로 전달하고, 이 런타임 구성 요소는 사용자 지정 보고서 항목을 렌더링한 뒤 다시 보고서 처리기로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-107">When the report is executed by the report processor, the properties that are set using the design-time component are passed by the report processor to a custom report item run-time component, which renders the custom report item and passes it back to the report processor.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="42f6e-108">사용자 지정 보고서 항목 디자인 타임 구성 요소는 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 구성 요소로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-108">The custom report item design-time component is implemented as a [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] component.</span></span> <span data-ttu-id="42f6e-109">이 문서에서는 사용자 지정 보고서 항목 디자인 타임 구성 요소와 관련된 구현 세부 사항을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-109">This document will describe implementation details specific to the custom report item design-time component.</span></span> <span data-ttu-id="42f6e-110">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]를 사용하여 구성 요소를 개발하는 방법은 MSDN 라이브러리에서 [Visual Studio의 구성 요소](https://go.microsoft.com/fwlink/?LinkId=116576)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="42f6e-110">For more information about developing components using the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], see [Components in Visual Studio](https://go.microsoft.com/fwlink/?LinkId=116576) in the MSDN library.</span></span>  
  
 <span data-ttu-id="42f6e-111">완전히 구현된 사용자 지정 보고서 항목 예는 [SQL Server Reporting Services 제품 예제](https://go.microsoft.com/fwlink/?LinkId=177889)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42f6e-111">For a sample of a fully implemented custom report item, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="implementing-a-design-time-component"></a><span data-ttu-id="42f6e-112">디자인 타임 구성 요소 구현</span><span class="sxs-lookup"><span data-stu-id="42f6e-112">Implementing a Design-Time Component</span></span>  
 <span data-ttu-id="42f6e-113">사용자 지정 보고서 항목 디자인 타임 구성 요소의 주 클래스는 `Microsoft.ReportDesigner.CustomReportItemDesigner` 클래스에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-113">The main class of a custom report item design-time component is inherited from the `Microsoft.ReportDesigner.CustomReportItemDesigner` class.</span></span> <span data-ttu-id="42f6e-114">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 컨트롤에 사용된 표준 특성 외에, 구성 요소 클래스에서 `CustomReportItem` 특성을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-114">In addition to the standard attributes used for a [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] control, your component class should define a `CustomReportItem` attribute.</span></span> <span data-ttu-id="42f6e-115">이 특성은 reportserver.config 파일에 정의된 사용자 지정 보고서 항목의 이름과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-115">This attribute must correspond to the name of the custom report item as it is defined in the reportserver.config file.</span></span> <span data-ttu-id="42f6e-116">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 특성 목록은 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 설명서에서 "특성(Attributes)"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="42f6e-116">For a list of [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] attributes, see Attributes in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
 <span data-ttu-id="42f6e-117">다음 코드 예제는 사용자 지정 보고서 항목 디자인 타임 컨트롤에 적용되는 특성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-117">The following code example shows attributes being applied to a custom report item design-time control:</span></span>  
  
```csharp  
namespace PolygonsCRI  
{  
    [LocalizedName("Polygons")]  
    [Editor(typeof(CustomEditor), typeof(ComponentEditor))]  
        [ToolboxBitmap(typeof(PolygonsDesigner),"Polygons.ico")]  
        [CustomReportItem("Polygons")]  
  
    public class PolygonsDesigner : CustomReportItemDesigner  
    {  
...  
```  
  
### <a name="initializing-the-component"></a><span data-ttu-id="42f6e-118">구성 요소 초기화</span><span class="sxs-lookup"><span data-stu-id="42f6e-118">Initializing the Component</span></span>  
 <span data-ttu-id="42f6e-119"><xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> 클래스를 사용하여 사용자 지정 보고서 항목에 대해 사용자가 지정한 속성을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-119">You pass user-specified properties for a custom report item using a <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> class.</span></span> <span data-ttu-id="42f6e-120">`CustomReportItemDesigner` 클래스 구현에서 `InitializeNewComponent` 메서드를 무시하고 구성 요소 <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> 클래스의 새 인스턴스를 만들어 이를 기본값으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-120">Your implementation of the `CustomReportItemDesigner` class should override the `InitializeNewComponent` method to create a new instance of your component's <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> class and set it to default values.</span></span>  
  
 <span data-ttu-id="42f6e-121">다음 코드 예제는 `CustomReportItemDesigner.InitializeNewComponent` 메서드를 무시하고 구성 요소의 <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> 클래스를 초기화하는 사용자 지정 보고서 항목 디자인 타임 구성 요소 클래스의 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-121">The following code example shows an example of a custom report item design-time component class overriding the `CustomReportItemDesigner.InitializeNewComponent` method to initialize the component's <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> class:</span></span>  
  
```csharp  
public override void InitializeNewComponent()  
        {  
            CustomData = new CustomData();  
            CustomData.DataRowHierarchy = new DataHierarchy();  
  
            // Shape grouping  
            CustomData.DataRowHierarchy.DataMembers.Add(new DataMember());  
            CustomData.DataRowHierarchy.DataMembers[0].Group = new Group();  
            CustomData.DataRowHierarchy.DataMembers[0].Group.Name = Name + "_Shape";  
            CustomData.DataRowHierarchy.DataMembers[0].Group.GroupExpressions.Add(new ReportExpression());  
  
            // Point grouping  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers.Add(new DataMember());  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers[0].Group = new Group();  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers[0].Group.Name = Name + "_Point";  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers[0].Group.GroupExpressions.Add(new ReportExpression());  
  
            // Static column  
            CustomData.DataColumnHierarchy = new DataHierarchy();  
            CustomData.DataColumnHierarchy.DataMembers.Add(new DataMember());  
  
            // Points  
            IList<IList<DataValue>> dataValues = new List<IList<DataValue>>();  
            CustomData.DataRows.Add(dataValues);  
            CustomData.DataRows[0].Add(new List<DataValue>());  
            CustomData.DataRows[0][0].Add(NewDataValue("X", ""));  
            CustomData.DataRows[0][0].Add(NewDataValue("Y", ""));  
        }  
```  
  
### <a name="modifying-component-properties"></a><span data-ttu-id="42f6e-122">구성 요소 속성 수정</span><span class="sxs-lookup"><span data-stu-id="42f6e-122">Modifying Component Properties</span></span>  
 <span data-ttu-id="42f6e-123">디자인 환경에서 여러 가지 방법으로 `CustomData` 속성을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-123">You can modify `CustomData` properties in the design environment in several ways.</span></span> <span data-ttu-id="42f6e-124">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 속성 브라우저를 사용하여 <xref:System.ComponentModel.BrowsableAttribute> 특성으로 표시된, 디자인 타임 구성 요소에서 노출한 속성을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-124">You can modify any properties that are exposed by the design-time component that are marked with the <xref:System.ComponentModel.BrowsableAttribute> attribute by using the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] property browser.</span></span> <span data-ttu-id="42f6e-125">또한 사용자 지정 보고서 항목의 디자인 화면으로 항목을 끌어 오거나, 디자인 환경에서 컨트롤을 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **속성**을 선택하여 사용자 지정 속성 창을 표시하는 방법으로 속성을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-125">In addition, you can modify properties by dragging items onto the custom report item's design surface, or by right-clicking the control in the design environment and selecting **Properties** on the shortcut menu to display a custom properties window.</span></span>  
  
 <span data-ttu-id="42f6e-126">다음 코드 예제는 <xref:System.ComponentModel.BrowsableAttribute> 특성이 적용된 `Microsoft.ReportDesigner.CustomReportItemDesigner.CustomData` 속성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-126">The following code example shows a `Microsoft.ReportDesigner.CustomReportItemDesigner.CustomData` property that has the <xref:System.ComponentModel.BrowsableAttribute> attribute applied:</span></span>  
  
```csharp  
[Browsable(true), Category("Data")]  
public string DataSetName  
{  
      get  
      {  
         return CustomData.DataSetName;  
      }  
      set  
      {  
         CustomData.DataSetName = value;  
      }  
   }  
  
```  
  
 <span data-ttu-id="42f6e-127">디자인 타임 구성 요소를 사용자 지정 속성 편집기 대화 상자로 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-127">You can provide your design-time component with a custom properties editor dialog box.</span></span> <span data-ttu-id="42f6e-128">사용자 지정 속성 편집기 구현은 <xref:System.ComponentModel.ComponentEditor> 클래스에서 상속해야 하며, 속성 편집에 사용할 수 있는 대화 상자 인스턴스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-128">The custom property editor implementation should inherit from the <xref:System.ComponentModel.ComponentEditor> class, and it should create an instance of a dialog box that can be used for property editing.</span></span>  
  
 <span data-ttu-id="42f6e-129">다음 예제는 <xref:System.ComponentModel.ComponentEditor>에서 상속되어 사용자 지정 속성 편집기 대화 상자를 표시하는 클래스의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-129">The following example shows an implementation of a class that inherits from <xref:System.ComponentModel.ComponentEditor> and displays a custom property editor dialog box:</span></span>  
  
```csharp  
internal sealed class CustomEditor : ComponentEditor  
{  
   public override bool EditComponent(  
      ITypeDescriptorContext context, object component)  
    {  
     PolygonsDesigner designer = (PolygonsDesigner)component;  
     PolygonProperties dialog = new PolygonProperties();  
     dialog.m_designerComponent = designer;  
     DialogResult result = dialog.ShowDialog();  
     if (result == DialogResult.OK)  
     {  
        designer.Invalidate();  
        designer.ChangeService().OnComponentChanged(designer, null, null, null);  
        return true;  
     }  
     else  
        return false;  
    }  
}  
```  
  
 <span data-ttu-id="42f6e-130">사용자 지정 속성 편집기 대화 상자에서 보고서 디자이너 식 편집기를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-130">Your custom property editor dialog box can invoke the Report Designer Expression Editor.</span></span> <span data-ttu-id="42f6e-131">다음 예제에서는 사용자가 콤보 상자에서 첫 번째 요소를 선택하면 식 편집기가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-131">In the following example, the Expression Editor is invoked when the user selects the first element in the combo box:</span></span>  
  
```csharp  
private void EditableCombo_SelectedIndexChanged(object sender,   
    EventArgs e)  
{  
   ComboBox combo = (ComboBox)sender;  
   if (combo.SelectedIndex == 0 && m_launchEditor)  
   {  
      m_launchEditor = false;  
      ExpressionEditor editor = new ExpressionEditor();  
      string newValue;  
      newValue = (string)editor.EditValue(null, m_designerComponent.Site, m_oldComboValue);  
      combo.Items[0] = newValue;  
   }  
}  
  
```  
  
### <a name="using-designer-verbs"></a><span data-ttu-id="42f6e-132">디자이너 동사 사용</span><span class="sxs-lookup"><span data-stu-id="42f6e-132">Using Designer Verbs</span></span>  
 <span data-ttu-id="42f6e-133">디자이너 동사는 이벤트 처리기에 연결된 메뉴 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-133">A designer verb is a menu command linked to an event handler.</span></span> <span data-ttu-id="42f6e-134">사용자 지정 보고서 항목 런타임 컨트롤이 디자인 환경에서 사용될 때 구성 요소의 바로 가기 메뉴에 표시할 디자이너 동사를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-134">You can add designer verbs that will appear in a component's shortcut menu when your custom report item run-time control is being used in the design environment.</span></span> <span data-ttu-id="42f6e-135">`Verbs` 속성을 사용하여 런타임 구성 요소에서 사용 가능한 디자이너 동사 목록을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-135">You can return the list of available designer verbs from your run-time component by using the `Verbs` property.</span></span>  
  
 <span data-ttu-id="42f6e-136">다음 코드 예제는 <xref:System.ComponentModel.Design.DesignerVerbCollection>에 추가할 디자이너 동사 및 이벤트 처리기와 이벤트 처리기 코드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-136">The following code example shows a designer verb and an event handler being added to the <xref:System.ComponentModel.Design.DesignerVerbCollection>, as well as the event handler code:</span></span>  
  
```csharp  
public override DesignerVerbCollection Verbs  
{  
    get  
    {  
        if (m_verbs == null)  
        {  
            m_verbs = new DesignerVerbCollection();  
            m_verbs.Add(new DesignerVerb("Proportional Scaling", new EventHandler(OnProportionalScaling)));  
         m_verbs[0].Checked = (GetCustomProperty("poly:Proportional") == bool.TrueString);  
        }  
  
        return m_verbs;  
    }  
}  
  
private void OnProportionalScaling(object sender, EventArgs e)  
{  
   bool proportional = !  
        (GetCustomProperty("poly:Proportional") == bool.TrueString);  
   m_verbs[0].Checked = proportional;  
   SetCustomProperty("poly:Proportional", proportional.ToString());  
   ChangeService().OnComponentChanged(this, null, null, null);  
   Invalidate();  
}  
```  
  
### <a name="using-adornments"></a><span data-ttu-id="42f6e-137">도구 영역(adornment) 사용</span><span class="sxs-lookup"><span data-stu-id="42f6e-137">Using Adornments</span></span>  
 <span data-ttu-id="42f6e-138">사용자 지정 보고서 항목 클래스는 `Microsoft.ReportDesigner.Design.Adornment` 클래스도 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-138">Custom report item classes can also implement a `Microsoft.ReportDesigner.Design.Adornment` class.</span></span> <span data-ttu-id="42f6e-139">도구 영역(adornment)을 사용하면 사용자 지정 보고서 항목 컨트롤의 주 사각형 디자인 화면 바깥에 일정 영역이 생깁니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-139">An adornment allows the custom report item control to provide areas outside the main rectangle of the design surface.</span></span> <span data-ttu-id="42f6e-140">이 영역은 마우스 클릭 및 끌어서 놓기 작업과 같은 사용자 인터페이스 이벤트를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f6e-140">These areas can handle user interface events, such as mouse clicks and drag-and-drop operations.</span></span> <span data-ttu-id="42f6e-141">`Adornment`네임 스페이스에 정의 된 클래스는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] `Microsoft.ReportDesigner` Windows Forms에 있는 클래스의 통과 구현입니다 <xref:System.Windows.Forms.Design.Behavior.Adorner> .</span><span class="sxs-lookup"><span data-stu-id="42f6e-141">The `Adornment` class that is defined in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] `Microsoft.ReportDesigner` namespace is a pass-through implementation of the <xref:System.Windows.Forms.Design.Behavior.Adorner> class found in Windows Forms.</span></span> <span data-ttu-id="42f6e-142">클래스에 대 한 전체 설명서는 `Adorner` MSDN library의 [동작 서비스 개요](https://go.microsoft.com/fwlink/?LinkId=116673) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="42f6e-142">For complete documentation on the `Adorner` class, see [Behavior Service Overview](https://go.microsoft.com/fwlink/?LinkId=116673) in the MSDN library.</span></span> <span data-ttu-id="42f6e-143">클래스를 구현 하는 샘플 코드는 `Microsoft.ReportDesigner.Design.Adornment` [SQL Server Reporting Services 제품 샘플](https://go.microsoft.com/fwlink/?LinkId=177889)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="42f6e-143">For sample code that implements a `Microsoft.ReportDesigner.Design.Adornment` class, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
 <span data-ttu-id="42f6e-144">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]에서 Windows Forms를 프로그래밍하고 사용하는 방법은 MSDN Library에서 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="42f6e-144">For more information about programming and using Windows Forms in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], see these topics in the MSDN Library:</span></span>  
  
-   <span data-ttu-id="42f6e-145">구성 요소의 디자인 타임 특성</span><span class="sxs-lookup"><span data-stu-id="42f6e-145">Design-Time Attributes for Components</span></span>  
  
-   <span data-ttu-id="42f6e-146">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]의 구성 요소</span><span class="sxs-lookup"><span data-stu-id="42f6e-146">Components in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]</span></span>  
  
-   <span data-ttu-id="42f6e-147">연습: Visual Studio의 디자인 타임 기능을 사용하는 Windows Forms 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="42f6e-147">Walkthrough: Creating a Windows Forms Control that Takes Advantage of Visual Studio Design-Time Features</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42f6e-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="42f6e-148">See Also</span></span>  
 <span data-ttu-id="42f6e-149">[사용자 지정 보고서 항목 아키텍처](custom-report-item-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="42f6e-149">[Custom Report Item Architecture](custom-report-item-architecture.md) </span></span>  
 <span data-ttu-id="42f6e-150">[사용자 지정 보고서 항목 런타임 구성 요소 만들기](creating-a-custom-report-item-run-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="42f6e-150">[Creating a Custom Report Item Run-Time Component](creating-a-custom-report-item-run-time-component.md) </span></span>  
 <span data-ttu-id="42f6e-151">[사용자 지정 보고서 항목 클래스 라이브러리](custom-report-item-class-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="42f6e-151">[Custom Report Item Class Libraries](custom-report-item-class-libraries.md) </span></span>  
 [<span data-ttu-id="42f6e-152">방법: 사용자 지정 보고서 항목 배포</span><span class="sxs-lookup"><span data-stu-id="42f6e-152">How to: Deploy a Custom Report Item</span></span>](how-to-deploy-a-custom-report-item.md)  
  
  
