---
title: 큐브 뷰 표현 (테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 6d2636c4-dae4-448f-a1d4-dbee739e177c
author: minewiskan
ms.author: owend
ms.openlocfilehash: ca8a66d3134748fd524dc0c6b524d944213533e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649223"
---
# <a name="perspective-representation-tabular"></a><span data-ttu-id="9e8fe-102">큐브 뷰 표현(테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="9e8fe-102">Perspective Representation (Tabular)</span></span>
  <span data-ttu-id="9e8fe-103">큐브 뷰는 클라이언트 애플리케이션을 위해 모델을 더 작은 부분으로 간소화하거나 집중시키는 메커니즘입니다.</span><span class="sxs-lookup"><span data-stu-id="9e8fe-103">A perspective is a mechanism to simplify or focus the model into a smaller portion of it for the client application.</span></span>  
  
 <span data-ttu-id="9e8fe-104">큐브 뷰 표현을 만들고 조작 하는 방법에 대 한 자세한 설명은 [큐브 뷰 표현 (테이블 형식)](perspective-representation-tabular.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e8fe-104">See [Perspective Representation (Tabular)](perspective-representation-tabular.md) for a detailed explanation on how to create and manipulate the perspective representation.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="9e8fe-105">큐브 뷰는 보안 메커니즘이 아니므로 다른 인터페이스를 통해 큐브 뷰 밖에 있는 개체에 계속 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8fe-105">Perspectives are not a security mechanism; objects outside the perspective can still be accessed by the user through other interfaces.</span></span>  
  
## <a name="perspective-representation"></a><span data-ttu-id="9e8fe-106">큐브 뷰 표현</span><span class="sxs-lookup"><span data-stu-id="9e8fe-106">Perspective Representation</span></span>  
 <span data-ttu-id="9e8fe-107">AMO 개체를 기준으로 큐브 뷰 표현은 <xref:Microsoft.AnalysisServices.Perspective>와 일 대 일 매핑 관계를 가지며 그 밖의 주요 AMO 개체는 필수 항목이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="9e8fe-107">In terms of AMO objects a perspective representation has a one to one mapping relationship with <xref:Microsoft.AnalysisServices.Perspective> and no other main AMO objects are required.</span></span>  
  
### <a name="perspective-in-amo"></a><span data-ttu-id="9e8fe-108">AMO의 큐브 뷰</span><span class="sxs-lookup"><span data-stu-id="9e8fe-108">Perspective in AMO</span></span>  
 <span data-ttu-id="9e8fe-109">다음 코드 조각에서는 테이블 형식 모델에서 큐브 뷰를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9e8fe-109">The following code snippet shows how to create a perspective in a Tabular model.</span></span> <span data-ttu-id="9e8fe-110">이 코드 조각의 키 요소는 perspectiveElements입니다. 이 개체는 사용자에게 노출되는 테이블 형식 모델의 모든 개체에 대한 그래픽 표현입니다.</span><span class="sxs-lookup"><span data-stu-id="9e8fe-110">The key element in this piece of code is the perspectiveElements; this object is a graphical representation of all the objects in the tabular model that are exposed to the user.</span></span> <span data-ttu-id="9e8fe-111">*perspectiveElements* 에는 4 개의 열이 포함 되어 있습니다 .이 시나리오에서는 열 1, 2 및 3만 관련 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8fe-111">*perspectiveElements* contains 4 columns and for this scenario only columns 1, 2 and 3 are relevant.</span></span> <span data-ttu-id="9e8fe-112">열 1은 표시되는 요소 형식인 -elementTypeValue-를 포함합니다. 열 2는 요소의 전체 이름인 --를 포함하며 큐브 뷰에 요소를 입력하려면 이 이름을 구문 분석해야 합니다. 열 3은 확인란 항목인 -checkedElement-를 포함하며 이 항목은 요소가 큐브 뷰의 일부인지 여부를 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="9e8fe-112">Column 1 contains the type of element displayed -elementTypeValue-; column 2 contains the complete name of the element --, that probably will need to parsed to enter the element in the perspective; column 3 contains a checkbox item -checkedElement- that tells if the element is part of the perspective or not.</span></span>  
  
```  
  
private void updatePerspective_Click(  
                     AMO.Cube modelCube  
                  ,  DataGridView perspectiveElements  
                  ,  string updatedPerspectiveID  
             )  
{  
    //Update is done by delete first, create new and insert after  
    //if perspective doesn't exist then create first and insert after  
    updatedPerspectiveID = updatedPerspectiveID.Trim();  
    if (modelCube.Perspectives.Contains(updatedPerspectiveID))  
    {  
        modelCube.Perspectives.Remove(updatedPerspectiveID, true);  
        newDatabase.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.UpdateOrCreate);  
    }  
    AMO.Perspective currentPerspective = modelCube.Perspectives.Add(updatedPerspectiveID, updatedPerspectiveID);  
  
    foreach (DataGridViewRow currentDGVRow in perspectiveElements.Rows)  
    {  
        bool checkedElement = (bool)currentDGVRow.Cells[3].Value;  
        if (checkedElement)  
        {  
            string elementTypeValue = currentDGVRow.Cells[1].Value.ToString();  
            string elementNameValue = currentDGVRow.Cells[2].Value.ToString();  
            switch (elementTypeValue)  
            {  
                case "Column: Attribute":  
                case "Column: Calculated Column":  
                    {  
                        string perspectiveDimensionName = Regex.Match(elementNameValue, @"(?<=')(.*?)(?=')").ToString();  
                        string perspectiveDimensionAttributeName = Regex.Match(elementNameValue, @"(?<=\[)(.*?)(?=\])").ToString();  
                        AMO.PerspectiveDimension currentPerspectiveDimension;  
                        if (!currentPerspective.Dimensions.Contains(perspectiveDimensionName))  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions.Add(perspectiveDimensionName);  
                        }  
                        else  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions[perspectiveDimensionName];  
                        }  
                        if (!currentPerspectiveDimension.Attributes.Contains(perspectiveDimensionAttributeName))  
                        {  
                            currentPerspectiveDimension.Attributes.Add(perspectiveDimensionAttributeName);  
                        }  
                    }  
                    break;  
                case "Hierarchy":  
                    {  
                        string perspectiveDimensionName = Regex.Match(elementNameValue, @"(?<=')(.*?)(?=')").ToString();  
                        string perspectiveDimensionHierarchyName = Regex.Match(elementNameValue, @"(?<=\[)(.*?)(?=\])").ToString();  
                        AMO.PerspectiveDimension currentPerspectiveDimension;  
                        if (!currentPerspective.Dimensions.Contains(perspectiveDimensionName))  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions.Add(perspectiveDimensionName);  
                        }  
                        else  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions[perspectiveDimensionName];  
                        }  
                        if (!currentPerspectiveDimension.Hierarchies.Contains(perspectiveDimensionHierarchyName))  
                        {  
                            currentPerspectiveDimension.Hierarchies.Add(perspectiveDimensionHierarchyName);  
                        }  
                    }  
                    break;  
                case "Measure":  
                    {  
                        string perspectiveMeasureGroupName = Regex.Match(elementNameValue, @"(?<=')(.*?)(?=')").ToString();  
                        string measureName = Regex.Match(elementNameValue, @"(?<=\[)(.*?)(?=\])").ToString();  
                        string perspectiveMeasureName = string.Format("[Measures].[{0}]", measureName);  
                        AMO.PerspectiveCalculation currentPerspectiveCalculation = new AMO.PerspectiveCalculation(perspectiveMeasureName, AMO.PerspectiveCalculationType.Member);  
                        if (!currentPerspective.Calculations.Contains(perspectiveMeasureName))  
                        {  
                            currentPerspective.Calculations.Add(currentPerspectiveCalculation);  
                        }  
                        if (modelCube.MdxScripts["MdxScript"].CalculationProperties.Contains(string.Format("KPIs.[{0}]", measureName)))  
                        {//Current Measure is also a KPI ==> will be added to the KPIs collection of the perspective  
                            AMO.PerspectiveKpi currentPerspectiveKpi = new AMO.PerspectiveKpi(perspectiveMeasureName);  
                            if (!currentPerspective.Kpis.Contains(perspectiveMeasureName))  
                            {  
                                currentPerspective.Kpis.Add(currentPerspectiveKpi);  
                            }  
                        }  
                    }  
                    break;  
                default:  
                    break;  
            }  
        }  
    }  
  
    newDatabase.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.CreateOrReplace);  
    MessageBox.Show(String.Format("Perpective successfully updated."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Information);  
}  
  
```  
  
## <a name="amo2tabular-sample"></a><span data-ttu-id="9e8fe-113">AMO2Tabular 예제</span><span class="sxs-lookup"><span data-stu-id="9e8fe-113">AMO2Tabular sample</span></span>  
 <span data-ttu-id="9e8fe-114">그러나 AMO를 사용하여 큐브 뷰 표현을 만들고 조작하는 방법을 알아보려면 AMO to Tabular 예제의 원본 코드를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9e8fe-114">However, to have an understanding on how to use AMO to create and manipulate perspective representations see the source code of the AMO to Tabular sample.</span></span> <span data-ttu-id="9e8fe-115">예제는 Codeplex에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8fe-115">The sample is available at Codeplex.</span></span> <span data-ttu-id="9e8fe-116">코드에 대한 중요 정보: 코드는 여기에서 설명한 논리적 개념에 대한 지원으로만 제공되며 프로덕션 환경에서 사용해서는 안 됩니다. 그리고 교육 목적 이외의 목적으로는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8fe-116">An important note about the code: the code is provided only as a support to the logical concepts explained here and should not be used in a production environment; nor should it be used for other purpose other than the pedagogical one.</span></span>  
  
  
