---
title: Try 및 Catch 블록 사용 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], try/catch blocks
- try/catch blocks [Reporting Services]
ms.assetid: a7a9ef53-e3b6-4bf7-81f3-d85615954e6f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a6aadb392fa4117484f3373ae232c3ed9c4b1d63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739214"
---
# <a name="using-try-and-catch-blocks"></a><span data-ttu-id="fd7aa-102">Try 및 Catch 블록 사용</span><span class="sxs-lookup"><span data-stu-id="fd7aa-102">Using Try and Catch Blocks</span></span>
  <span data-ttu-id="fd7aa-103">조건문을 코드에 추가하여 보고서 서버에 대한 잘못된 요청을 제한한 후에는 try/catch 블록을 사용하여 적절한 예외 처리를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd7aa-103">After you limit invalid requests to the report server by adding conditional statements to your code, you should supply adequate exception handling through the use of try/catch blocks.</span></span> <span data-ttu-id="fd7aa-104">이를 통해 유효하지 않은 요청에 대한 또 하나의 보호막을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd7aa-104">This technique provides another layer of protection against requests that are not valid.</span></span> <span data-ttu-id="fd7aa-105">보고서 서버에 대한 요청이 try 블록 안에 포함되어 있으며 이 요청으로 인해 보고서 서버에서 예외가 throw되는 경우 이 예외는 catch 블록에서 catch되므로 애플리케이션이 갑자기 종료되는 것을 막을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd7aa-105">If a request to the report server is encased in a try block and that request causes the report server to throw an exception, the exception is caught in the catch block, thus preventing your application from ending unexpectedly.</span></span> <span data-ttu-id="fd7aa-106">예외가 catch되면 예외를 사용하여 사용자에게 다른 작업을 수행하도록 지시하거나 오류가 발생했음을 친숙한 방법으로 알려줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd7aa-106">Once the exception is caught, you can use the exception to either instruct the user to do something differently, or just let the user know, in a friendly way, that an error has occurred.</span></span> <span data-ttu-id="fd7aa-107">그런 다음 finally 블록을 사용하여 리소스를 정리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd7aa-107">You can then use a finally block to clean up any resources.</span></span> <span data-ttu-id="fd7aa-108">일반적인 예외 처리 계획을 생성하여 불필요한 try/catch 블록 중복을 피하는 것이 가장 이상적입니다.</span><span class="sxs-lookup"><span data-stu-id="fd7aa-108">Ideally, you should generate a general exception-handling plan to avoid unnecessary duplication of try/catch blocks.</span></span>  
  
 <span data-ttu-id="fd7aa-109">다음 예에서는 try/catch 블록을 사용하여 예외 처리 코드의 안정성을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="fd7aa-109">The following example uses try/catch blocks to enhance the reliability of the exception handling code.</span></span>  
  
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
         "consult the online documentation";  
  
      MessageBox.Show(message, "Invalid Input Error");  
   }  
   else // Publish the report  
   {  
      Byte[] definition = null;  
      Warning[] warnings = {};  
      string name = nameTextBox.Text;  
  
      try  
      {  
         FileStream stream = File.OpenRead("MyReport.rdl");  
         definition = new Byte[stream.Length];  
         stream.Read(definition, 0, (int) stream.Length);  
         stream.Close();  
         // Create report with user-defined name  
         rs.CreateCatalogItem("Report", name, "/Samples", false, definition, null, out warnings);  
         MessageBox.Show("Report: {0} created successfully", name);  
      }  
  
      // Catch expected exceptions beginning with the most specific,  
      // moving to the least specific  
      catch(IOException ex)  
      {  
         MessageBox.Show(ex.Message, "File IO Exception");  
      }  
  
      catch (SoapException ex)  
      {  
         // The exception is a SOAP exception, so use  
         // the Detail property's Message element.  
         MessageBox.Show(ex.Detail["Message"].InnerXml, "SOAP Exception");   
      }  
  
      catch (Exception ex)  
      {  
         MessageBox.Show(ex.Message, "General Exception");  
      }  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd7aa-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fd7aa-110">See Also</span></span>  
 <span data-ttu-id="fd7aa-111">[Reporting Services에서 예외 처리 소개](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="fd7aa-111">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="fd7aa-112">Reporting Services SoapException 클래스</span><span class="sxs-lookup"><span data-stu-id="fd7aa-112">Reporting Services SoapException Class</span></span>](../soapexception-class/reporting-services-soapexception-class.md)  
  
  
