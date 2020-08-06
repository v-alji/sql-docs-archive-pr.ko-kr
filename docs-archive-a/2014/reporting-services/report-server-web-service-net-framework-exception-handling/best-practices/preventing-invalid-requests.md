---
title: 잘못된 요청 방지 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- invalid requests [Reporting Services]
- exceptions [Reporting Services], invalid requests
- valid requests [Reporting Services]
ms.assetid: 4a4a2d97-4c10-43a9-8298-ef5a820ea549
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 12343955c46fb98fea75048a38749b1db993fa11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659809"
---
# <a name="preventing-invalid-requests"></a><span data-ttu-id="f25bc-102">잘못된 요청 방지</span><span class="sxs-lookup"><span data-stu-id="f25bc-102">Preventing Invalid Requests</span></span>
  <span data-ttu-id="f25bc-103">애플리케이션 흐름을 분석하고 보고서 서버로 전송되는 요청이 유효한지 확인하여 일부 유형의 예외가 throw되지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f25bc-103">You can prevent some types of exceptions from being thrown by analyzing your application flow and ensuring that the requests being sent to the report server are valid.</span></span> <span data-ttu-id="f25bc-104">예를 들어 사용자가 보고서의 이름, 데이터 원본 또는 기타 보고서 서버 항목을 추가하거나 갱신할 수 있는 애플리케이션의 경우 사용자가 입력하는 텍스트의 유효성을 검사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f25bc-104">For example, in applications that enable users to add or update the name of a report, data source, or other report server item, you should validate the text that a user might enter.</span></span> <span data-ttu-id="f25bc-105">또한 요청을 보고서 서버로 보내기 전에 항상 예약 문자를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f25bc-105">You should always check for reserved characters before sending the request to a report server.</span></span> <span data-ttu-id="f25bc-106">코드에서 **if**문 또는 기타 논리 구문을 사용하여 보고서 서버에 요청을 보내는 데 필요한 조건이 충족되지 않았음을 사용자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="f25bc-106">Use conditional **if** statements or other logical constructs in your code to alert the user that they have not met the conditions necessary to send requests to the report server.</span></span>  
  
 <span data-ttu-id="f25bc-107">다음의 간단한 C# 예에서는 사용자가 이름에 슬래시(/) 문자가 포함된 보고서를 만들려고 시도할 때 오류 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f25bc-107">In the following, simplified C# example, users are presented with a friendly error message when they attempt to create a report with a name that contains a forward slash (/) character.</span></span>  
  
```  
// C#  
private void PublishReport()  
{  
   int index;  
   string reservedChar;  
   string message;  
  
   // Check the text value of the name text box for "/",  
   // a reserved character  
   index = nameTextBox.Text.IndexOf(@"/");  
  
   if ( index != -1) // The text contains the character  
   {  
      reservedChar = nameTextBox.Text.Substring(index, 1);  
      // Build a user-friendly error message  
      message = "The name of the report cannot contain the reserved character " +  
         "\"" + reservedChar + "\". " +  
         "Please enter a valid name for the report. " +  
         "For more information about reserved characters, " +  
         "see the help documentation";  
  
      MessageBox.Show(message, "Invalid Input Error");  
   }  
   else // Publish the report  
   {  
      Byte[] definition = null;  
      Warning[] warnings = {};  
      string name = nameTextBox.Text;  
  
      FileStream stream = File.OpenRead("MyReport.rdl");  
      definition = new Byte[stream.Length];  
      stream.Read(definition, 0, (int) stream.Length);  
      stream.Close();  
      // Create report with user-defined name  
      rs.CreateCatalogItem("Report", name, "/Samples", false, definition, null, out warnings);  
      MessageBox.Show("Report: {0} created successfully", name);  
   }  
}  
```  
  
 <span data-ttu-id="f25bc-108">요청이 보고서 서버로 전송되기 전에 방지할 수 있는 오류 유형에 대한 자세한 내용은 [SoapException 오류 테이블](../soapexception-class/soapexception-errors-table.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f25bc-108">For more information about the types of errors that can be prevented before requests are sent to the report server, see [SoapException Errors Table](../soapexception-class/soapexception-errors-table.md).</span></span> <span data-ttu-id="f25bc-109">try/catch 블록을 사용하여 위의 예를 개선하는 방법은 [Try 및 Catch 블록 사용](using-try-and-catch-blocks.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f25bc-109">For more information about further enhancing the previous example using try/catch blocks, see [Using Try and Catch Blocks](using-try-and-catch-blocks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f25bc-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f25bc-110">See Also</span></span>  
 <span data-ttu-id="f25bc-111">[Reporting Services에서 예외 처리 소개](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="f25bc-111">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="f25bc-112">Reporting Services SoapException 클래스</span><span class="sxs-lookup"><span data-stu-id="f25bc-112">Reporting Services SoapException Class</span></span>](../soapexception-class/reporting-services-soapexception-class.md)  
  
  
