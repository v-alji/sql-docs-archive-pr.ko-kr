---
title: 사용자 지정 보고서 항목 런타임 구성 요소 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, creating
ms.assetid: b3e15a4a-98f8-4dbb-b847-bbcb20327051
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 50c5c0211bc5cd1359af9d1493782bd9d96c2b3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639421"
---
# <a name="creating-a-custom-report-item-run-time-component"></a><span data-ttu-id="a34b7-102">사용자 지정 보고서 항목 런타임 구성 요소 만들기</span><span class="sxs-lookup"><span data-stu-id="a34b7-102">Creating a Custom Report Item Run-Time Component</span></span>
  <span data-ttu-id="a34b7-103">사용자 지정 보고서 항목 런타임 구성 요소는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLS 규격 언어를 사용 하 여 구성 요소로 구현 되며 런타임에 보고서 처리기에 의해 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a34b7-103">The custom report item run-time component is implemented as a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] component using any CLS-compliant language, and is called by the report processor at run time.</span></span> <span data-ttu-id="a34b7-104">사용자 지정 보고서 항목의 해당 디자인 타임 구성 요소를 수정하여 디자인 환경에서 런타임 구성 요소에 대한 속성을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a34b7-104">You define the properties for the run-time component in the design environment by modifying the custom report item's corresponding design-time component.</span></span>  

<!--
Replacing the following multiValue.....

ms.technology: 
  - "docset-sql-devref"
  - "reporting-services-native"

.....with the following single value.....

ms.technology: reporting-services
.

(GeneMi = MightyPen  ,  2019-04-20  ,  DevO= 1515083)
-->

 <span data-ttu-id="a34b7-105">완전히 구현된 사용자 지정 보고서 항목 예는 [SQL Server Reporting Services 제품 예제](https://go.microsoft.com/fwlink/?LinkId=177889)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a34b7-105">For a sample of a fully implemented custom report item, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="definition-and-instance-objects"></a><span data-ttu-id="a34b7-106">정의 및 인스턴스 개체</span><span class="sxs-lookup"><span data-stu-id="a34b7-106">Definition and Instance Objects</span></span>  
 <span data-ttu-id="a34b7-107">사용자 지정 보고서 항목을 구현하기 전에 *정의 개체*와 *인스턴스 개체*의 차이점을 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a34b7-107">Before implementing a custom report item it is important to understand the difference between *definition objects* and *instance objects*.</span></span> <span data-ttu-id="a34b7-108">정의 개체는 사용자 지정 보고서 항목의 RDL 표현을 제공하고, 인스턴스 개체는 정의 개체의 평가된 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="a34b7-108">Definition objects provide the RDL representation of the custom report item whereas instance objects are the evaluated versions of the definition objects.</span></span> <span data-ttu-id="a34b7-109">보고서의 각 항목에 정의 개체는 하나만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a34b7-109">There is only one definition object for each item on the report.</span></span> <span data-ttu-id="a34b7-110">식이 포함된 정의 개체의 속성에 액세스할 때 사용자는 평가되지 않은 식 문자열을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="a34b7-110">When accessing properties on a definition object that contain expressions, you will get the unevaluated expression string.</span></span> <span data-ttu-id="a34b7-111">인스턴스 개체는 정의 개체의 평가된 버전을 포함하고 항목의 정의 개체와 일 대 다 관계를 맺을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a34b7-111">Instance objects contain the evaluated versions of the definition objects and can have a one-to-many relationship with an item's definition object.</span></span> <span data-ttu-id="a34b7-112">예를 들어, 보고서의 정보 행에 <xref:Microsoft.ReportingServices.OnDemandReportRendering.Tablix>이 포함된 <xref:Microsoft.ReportingServices.OnDemandReportRendering.CustomReportItem> 데이터 영역이 있는 경우 정의 개체는 하나뿐이지만 인스턴스 개체는 데이터 영역의 각 행마다 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a34b7-112">For example, if a report has a <xref:Microsoft.ReportingServices.OnDemandReportRendering.Tablix> data region that contains a <xref:Microsoft.ReportingServices.OnDemandReportRendering.CustomReportItem> in a detail row, there will be only one definition object but there will be an instance object for each row in the data region.</span></span>  
  
## <a name="implementing-the-icustomreportitem-interface"></a><span data-ttu-id="a34b7-113">ICustomReportItem 인터페이스 구현</span><span class="sxs-lookup"><span data-stu-id="a34b7-113">Implementing the ICustomReportItem Interface</span></span>  
 <span data-ttu-id="a34b7-114">`CustomReportItem` 런타임 구성 요소를 만들려면 Microsoft.ReportingServices.ProcessingCore.dll에 정의된 <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem> 인터페이스를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a34b7-114">To create a `CustomReportItem` run-time component you will need to implement the <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem> interface that is defined in the Microsoft.ReportingServices.ProcessingCore.dll:</span></span>  
  
```csharp  
namespace Microsoft.ReportingServices.OnDemandReportRendering  
{  
    public interface ICustomReportItem  
    {  
        void GenerateReportItemDefinition(CustomReportItem customReportItem);  
void EvaluateReportItemInstance(CustomReportItem customReportItem);  
    }  
}  
```  
  
 <span data-ttu-id="a34b7-115"><xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem> 인터페이스를 구현한 후에는 <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.GenerateReportItemDefinition%2A> 및 <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.EvaluateReportItemInstance%2A> 메서드 스텁이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a34b7-115">After you have implemented the <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem> interface, two method stubs will be generated for you: <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.GenerateReportItemDefinition%2A> and <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.EvaluateReportItemInstance%2A>.</span></span> <span data-ttu-id="a34b7-116"><xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.GenerateReportItemDefinition%2A> 메서드가 먼저 호출되어, 정의 속성을 설정하고 이 정의 속성과 항목 렌더링에 사용되는 인스턴스 속성을 포함할 <xref:Microsoft.ReportingServices.OnDemandReportRendering.Image> 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a34b7-116">The <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.GenerateReportItemDefinition%2A> method is called first and is used for setting definition properties and creating the <xref:Microsoft.ReportingServices.OnDemandReportRendering.Image> object that will contain both the definition and instance properties that are used for rendering the item.</span></span> <span data-ttu-id="a34b7-117">정의 개체가 평가된 후 <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.EvaluateReportItemInstance%2A> 메서드가 호출되고, 항목 렌더링에 사용되는 인스턴스 개체를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a34b7-117">The <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.EvaluateReportItemInstance%2A> method is called after the definition objects have been evaluated, and it provides the instance objects that will be used for rendering the item.</span></span>  
  
 <span data-ttu-id="a34b7-118">다음은 컨트롤 이름을 이미지로 렌더링하는 사용자 지정 보고서 항목의 예제 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="a34b7-118">The following is an example implementation of a custom report item that renders the name of the control as an image.</span></span>  
  
```csharp  
namespace Microsoft.Samples.ReportingServices  
{  
    using System;  
    using System.Collections.Generic;  
    using System.Collections.Specialized;  
    using System.Drawing.Imaging;  
    using System.IO;  
    using System.Text;  
    using Microsoft.ReportingServices.OnDemandReportRendering;  
  
    public class PolygonsCustomReportItem : ICustomReportItem  
    {  
        #region ICustomReportItem Members  
  
        public void GenerateReportItemDefinition(CustomReportItem cri)  
        {  
            // Create the Image object that will be   
            // used to render the custom report item  
            cri.CreateCriImageDefinition();  
            Image polygonImage = (Image)cri.GeneratedReportItem;  
        }  
  
        public void EvaluateReportItemInstance(CustomReportItem cri)  
        {  
            // Get the Image definition  
            Image polygonImage = (Image)cri.GeneratedReportItem;  
  
            // Create the image for the custom report item  
            polygonImage.ImageInstance.ImageData = DrawImage(cri);  
        }  
  
        #endregion  
  
        /// <summary>  
        /// Creates an image of the CustomReportItem's name  
        /// </summary>  
        private byte[] DrawImage(CustomReportItem customReportItem)  
        {  
            int width = 1;          // pixels  
            int height = 1;         // pixels  
            int resolution = 75;    // dpi  
  
            System.Drawing.Bitmap bitmap = new System.Drawing.Bitmap(width, height);  
            bitmap.SetResolution(resolution, resolution);  
  
            System.Drawing.Graphics graphics = System.Drawing.Graphics.FromImage(bitmap);  
            graphics.PageUnit = System.Drawing.GraphicsUnit.Pixel;  
  
            // Get the Font for the Text  
            System.Drawing.Font font = new System.Drawing.Font(System.Drawing.FontFamily.GenericMonospace,  
                12, System.Drawing.FontStyle.Regular);  
  
            // Get the Brush for drawing the Text  
            System.Drawing.Brush brush = new System.Drawing.SolidBrush(System.Drawing.Color.LightGreen);  
  
            // Get the measurements for the image  
            System.Drawing.SizeF maxStringSize = graphics.MeasureString(customReportItem.Name, font);  
            width = (int)(maxStringSize.Width + 2 * font.GetHeight(resolution));  
            height = (int)(maxStringSize.Height + 2 * font.GetHeight(resolution));  
  
            bitmap.Dispose();  
            bitmap = new System.Drawing.Bitmap(width, height);  
            bitmap.SetResolution(resolution, resolution);  
  
            graphics.Dispose();  
            graphics = System.Drawing.Graphics.FromImage(bitmap);  
            graphics.PageUnit = System.Drawing.GraphicsUnit.Pixel;  
  
            // Draw the text  
            graphics.DrawString(customReportItem.Name, font, brush, font.GetHeight(resolution),   
                font.GetHeight(resolution));  
  
            // Create the byte array of the image data  
            MemoryStream memoryStream = new MemoryStream();  
            bitmap.Save(memoryStream, ImageFormat.Bmp);  
            memoryStream.Position = 0;  
            byte[] imageData = new byte[memoryStream.Length];  
            memoryStream.Read(imageData, 0, imageData.Length);  
  
            return imageData;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a34b7-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a34b7-119">See Also</span></span>  
 <span data-ttu-id="a34b7-120">[사용자 지정 보고서 항목 아키텍처](custom-report-item-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="a34b7-120">[Custom Report Item Architecture](custom-report-item-architecture.md) </span></span>  
 <span data-ttu-id="a34b7-121">[사용자 지정 보고서 항목 디자인 타임 구성 요소 만들기](creating-a-custom-report-item-design-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="a34b7-121">[Creating a Custom Report Item Design-Time Component](creating-a-custom-report-item-design-time-component.md) </span></span>  
 <span data-ttu-id="a34b7-122">[사용자 지정 보고서 항목 클래스 라이브러리](custom-report-item-class-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="a34b7-122">[Custom Report Item Class Libraries](custom-report-item-class-libraries.md) </span></span>  
 [<span data-ttu-id="a34b7-123">방법: 사용자 지정 보고서 항목 배포</span><span class="sxs-lookup"><span data-stu-id="a34b7-123">How to: Deploy a Custom Report Item</span></span>](how-to-deploy-a-custom-report-item.md)  
  
  
