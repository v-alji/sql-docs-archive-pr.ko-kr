---
title: Reporting Services 예외 처리에 관한 모범 사례 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], best practices
ms.assetid: 72fecf28-f02e-4338-b50f-0b21f520302d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2e0561c19fbd3e709a0440a55f023f938eabf692
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649932"
---
# <a name="best-practices-for-reporting-services-exception-handling"></a><span data-ttu-id="f9125-102">Reporting Services 예외 처리를 위한 최상의 방법</span><span class="sxs-lookup"><span data-stu-id="f9125-102">Best Practices for Reporting Services Exception Handling</span></span>
  <span data-ttu-id="f9125-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 애플리케이션을 개발할 때 예외 발생을 없애거나 줄이기 위해 사용할 수 있는 방법이 다수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9125-103">When developing [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] applications, there are several methodologies you can use to eliminate or reduce the occurrence of exceptions.</span></span> <span data-ttu-id="f9125-104">예외가 발생하면 사용자에게 간단 명료한 오류 메시지를 제공하고 적절한 예외 처리를 추가하여 애플리케이션이 갑자기 종료되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9125-104">When exceptions do occur, provide clear and concise error messages to the user, and add adequate exception handling to prevent your applications from ending unexpectedly.</span></span>  
  
 <span data-ttu-id="f9125-105">보고서 서버 웹 서비스에 요청을 보내는 애플리케이션은 다음 기능을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9125-105">An application that sends requests to the Report Server Web service should do the following:</span></span>  
  
-   <span data-ttu-id="f9125-106">잘못된 요청을 최대한 방지하여 예외 발생을 막습니다.</span><span class="sxs-lookup"><span data-stu-id="f9125-106">Avoid causing exceptions by preventing as many invalid requests as possible.</span></span>  
  
-   <span data-ttu-id="f9125-107">예외를 catch하고 가능한 경우 항상 특정 오류 처리 코드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f9125-107">Catch exceptions and provide specific error-handling code whenever possible.</span></span>  
  
-   <span data-ttu-id="f9125-108">예외를 throw하지 않는 오류 사례를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="f9125-108">Deal with error cases that do not throw exceptions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f9125-109">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="f9125-109">In This Section</span></span>  
  
|<span data-ttu-id="f9125-110">항목</span><span class="sxs-lookup"><span data-stu-id="f9125-110">Topic</span></span>|<span data-ttu-id="f9125-111">Description</span><span class="sxs-lookup"><span data-stu-id="f9125-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f9125-112">잘못된 요청 방지</span><span class="sxs-lookup"><span data-stu-id="f9125-112">Preventing Invalid Requests</span></span>](preventing-invalid-requests.md)|<span data-ttu-id="f9125-113">잘못된 요청이 보고서 서버에 전송되지 않도록 하기 위한 기술에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f9125-113">Describes techniques for preventing requests that are not valid from being sent to the report server.</span></span>|  
|[<span data-ttu-id="f9125-114">Try 및 Catch 블록 사용</span><span class="sxs-lookup"><span data-stu-id="f9125-114">Using Try and Catch Blocks</span></span>](using-try-and-catch-blocks.md)|<span data-ttu-id="f9125-115">try/catch 블록으로 애플리케이션의 안정성을 향상시킬 수 있는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f9125-115">Describes how to further enhance the reliability of your application with try/catch blocks.</span></span>|  
|[<span data-ttu-id="f9125-116">예외를 발생하지 않는 경고 및 사례 처리</span><span class="sxs-lookup"><span data-stu-id="f9125-116">Handling Warnings and Cases That Do Not Cause Exceptions</span></span>](handling-warnings-and-cases-that-do-not-cause-exceptions.md)|<span data-ttu-id="f9125-117">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에서 예외가 throw되지 않는 오류를 처리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f9125-117">Explains how to handle errors that do not result in an exception being thrown by [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="f9125-118">Detail 속성을 사용하여 특정 오류 처리</span><span class="sxs-lookup"><span data-stu-id="f9125-118">Using the Detail Property to Handle Specific Errors</span></span>](using-the-detail-property-to-handle-specific-errors.md)|<span data-ttu-id="f9125-119">**SoapException** 개체의 **Detail** 속성을 사용하여 특정 오류를 프로그래밍 방식으로 처리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f9125-119">Explains how to programmatically handle specific errors by using the **Detail** property of the **SoapException** object.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f9125-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f9125-120">See Also</span></span>  
 <span data-ttu-id="f9125-121">[Detail 속성](../soapexception-class/detail-property.md) </span><span class="sxs-lookup"><span data-stu-id="f9125-121">[Detail Property](../soapexception-class/detail-property.md) </span></span>  
 <span data-ttu-id="f9125-122">[Reporting Services에서 예외 처리 소개](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="f9125-122">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="f9125-123">Reporting Services SoapException 클래스</span><span class="sxs-lookup"><span data-stu-id="f9125-123">Reporting Services SoapException Class</span></span>](../soapexception-class/reporting-services-soapexception-class.md)  
  
  
