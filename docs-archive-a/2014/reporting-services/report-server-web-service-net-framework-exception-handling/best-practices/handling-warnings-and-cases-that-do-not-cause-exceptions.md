---
title: 예외를 발생하지 않는 경고 및 사례 처리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], warnings that don't cause
- warnings [Reporting Services]
ms.assetid: 475c0713-6265-44e7-9ebc-ebdd1b89e0af
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 88d3daf63cf5f04975a2941d0634f357ce81456c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733563"
---
# <a name="handling-warnings-and-cases-that-do-not-cause-exceptions"></a><span data-ttu-id="7d482-102">예외를 발생하지 않는 경고 및 사례 처리</span><span class="sxs-lookup"><span data-stu-id="7d482-102">Handling Warnings and Cases That Do Not Cause Exceptions</span></span>
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]<span data-ttu-id="7d482-103">는 경고 및 특정 오류에 대해 예외를 throw하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7d482-103">does not throw exceptions for warnings and certain errors.</span></span> <span data-ttu-id="7d482-104">예를 들어 <xref:ReportService2010.ReportingService2010.CreateCatalogItem%2A> 메서드를 사용하여 새 보고서를 보고서 서버에 게시하는 경우 발생하는 경고는 <xref:ReportService2010.Warning> 개체의 배열의 형태로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d482-104">For example, when you use the <xref:ReportService2010.ReportingService2010.CreateCatalogItem%2A> method to publish a new report to a report server, any warnings that occur are returned as an array of <xref:ReportService2010.Warning> objects.</span></span> <span data-ttu-id="7d482-105">이러한 경고는 적절한 조치를 취할 수 있도록 처리되고 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d482-105">These warnings should be handled and displayed so that appropriate action can be taken.</span></span>  
  
```vb  
Try  
   rs.CreateCatalogItem(name, parentFolder, False, definition, Nothing, warnings)  
  
   If Not (warnings.Length = 0) Then  
      Dim warning As Warning  
      For Each warning In warnings  
         Console.WriteLine(warning.Message)  
      Next warning  
   Else  
      Console.WriteLine("Report {0} created successfully with no warnings", name)  
   End If  
  
Catch ex As SoapException  
   Console.WriteLine(ex.Detail("Message").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   rs.CreateCatalogItem("Report", name, parentFolder, false, definition, null, out warnings);  
  
   if (warnings.Length != 0)  
   {  
      foreach (Warning warning in warnings)  
      {  
         Console.WriteLine(warning.Message);  
      }  
   }  
   else  
      Console.WriteLine("Report {0} created successfully with no warnings", name);  
}  
  
catch (SoapException ex)  
{  
   Console.WriteLine(ex.Detail["Message"].InnerXml);  
}  
```  
  
 <span data-ttu-id="7d482-106">오류를 처리하는 또 하나의 방법은 특정 메서드의 반환 값을 평가하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7d482-106">Another way to handle errors is to evaluate the return values of certain methods.</span></span> <span data-ttu-id="7d482-107">예를 들어 <xref:ReportService2010.ReportingService2010.FindItems%2A> 메서드를 사용하여 보고서 서버 데이터베이스의 특정 항목을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d482-107">For example, the <xref:ReportService2010.ReportingService2010.FindItems%2A> method can be used to search for specific items in the report server database.</span></span> <span data-ttu-id="7d482-108">검색 조건과 일치하는 항목을 찾지 못할 경우 <xref:ReportService2010.CatalogItem> 개체의 null 배열이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d482-108">If no items are found that match the search criteria, a null array of <xref:ReportService2010.CatalogItem> objects is returned.</span></span> <span data-ttu-id="7d482-109">발견된 항목이 없는 경우 배열을 평가하고 `null`인지 확인한 후 사용자에게 알려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d482-109">You should evaluate the array, check for `null`, and let the user know if no items were found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d482-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7d482-110">See Also</span></span>  
 <xref:ReportService2010.CatalogItem>   
 <span data-ttu-id="7d482-111">[Reporting Services에서 예외 처리 소개](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="7d482-111">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="7d482-112">Reporting Services SoapException 클래스</span><span class="sxs-lookup"><span data-stu-id="7d482-112">Reporting Services SoapException Class</span></span>](../soapexception-class/reporting-services-soapexception-class.md)  
  
  
