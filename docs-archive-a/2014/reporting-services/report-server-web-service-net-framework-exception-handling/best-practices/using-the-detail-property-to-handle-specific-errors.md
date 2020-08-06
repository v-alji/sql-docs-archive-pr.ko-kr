---
title: Detail 속성을 사용하여 특정 오류 처리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], Detail property
- Detail property
- InnerText property
ms.assetid: 4392633d-b46b-41e6-bc12-efb64e166704
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4f8ac62dc381d8f665a44fc0897ba1f4215aa8e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735000"
---
# <a name="using-the-detail-property-to-handle-specific-errors"></a><span data-ttu-id="c1ef0-102">Detail 속성을 사용하여 특정 오류 처리</span><span class="sxs-lookup"><span data-stu-id="c1ef0-102">Using the Detail Property to Handle Specific Errors</span></span>
  <span data-ttu-id="c1ef0-103">예외를 상세하게 분류하기 위해 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]는 SOAP 예외의 **Detail** 속성에서 자식 요소의 **InnerText** 속성으로 추가 오류 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef0-103">To further classify exceptions, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] returns additional error information in the **InnerText** property of the child elements in the SOAP exception's **Detail** property.</span></span> <span data-ttu-id="c1ef0-104">**Detail** 속성은 **XmlNode** 개체이므로 다음 코드를 사용하여 **Message** 자식 요소의 내부 텍스트에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef0-104">Because the **Detail** property is an **XmlNode** object, you can access the inner text of the **Message** child element using the following code.</span></span>  
  
 <span data-ttu-id="c1ef0-105">**Detail** 속성에 포함된 사용 가능한 모든 자식 요소 목록은 [Detail 속성](../soapexception-class/detail-property.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1ef0-105">For a list of all of the available child elements contained in the **Detail** property, see [Detail Property](../soapexception-class/detail-property.md).</span></span> <span data-ttu-id="c1ef0-106">자세한 내용은 SDK 설명서의 "Detail 속성"을 참조 하십시오 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c1ef0-106">For more information, see "Detail Property" in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
```vb  
Try  
' Code for accessing the report server  
Catch ex As SoapException  
   ' The exception is a SOAP exception, so use  
   ' the Detail property's Message element.  
   Console.WriteLine(ex.Detail("Message").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   // Code for accessing the report server  
}  
catch (SoapException ex)  
{  
   // The exception is a SOAP exception, so use  
   // the Detail property's Message element.  
   Console.WriteLine(ex.Detail["Message"].InnerXml);  
}  
```  
  
```vb  
Try  
' Code for accessing the report server  
Catch ex As SoapException  
   If ex.Detail("ErrorCode").InnerXml = "rsInvalidItemName" Then  
   End If ' Perform an action based on the specific error code  
End Try  
```  
  
```csharp  
try  
{  
   // Code for accessing the report server  
}  
catch (SoapException ex)  
{  
   if (ex.Detail["ErrorCode"].InnerXml == "rsInvalidItemName")  
   {  
      // Perform an action based on the specific error code  
   }  
}  
```  
  
 <span data-ttu-id="c1ef0-107">다음 코드 줄은 SOAP 예외로 콘솔에 반환되는 특정 오류 코드를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef0-107">The following line of code writes the specific error code being returned in the SOAP Exception to the console.</span></span> <span data-ttu-id="c1ef0-108">오류 코드를 평가하고 특정 동작을 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef0-108">You could also evaluate the error code and perform specific actions.</span></span>  
  
```vb  
Console.WriteLine(ex.Detail("ErrorCode").InnerXml)  
```  
  
```csharp  
Console.WriteLine(ex.Detail["ErrorCode"].InnerXml);  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1ef0-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c1ef0-109">See Also</span></span>  
 <span data-ttu-id="c1ef0-110">[Reporting Services에서 예외 처리 소개](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="c1ef0-110">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 <span data-ttu-id="c1ef0-111">[Reporting Services SoapException 클래스](../soapexception-class/reporting-services-soapexception-class.md) </span><span class="sxs-lookup"><span data-stu-id="c1ef0-111">[Reporting Services SoapException Class](../soapexception-class/reporting-services-soapexception-class.md) </span></span>  
 [<span data-ttu-id="c1ef0-112">SoapException 오류 테이블</span><span class="sxs-lookup"><span data-stu-id="c1ef0-112">SoapException Errors Table</span></span>](../soapexception-class/soapexception-errors-table.md)  
  
  
