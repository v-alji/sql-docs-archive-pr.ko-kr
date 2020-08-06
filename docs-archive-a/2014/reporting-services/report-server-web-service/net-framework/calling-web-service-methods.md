---
title: 웹 서비스 메서드 호출 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- Web service [Reporting Services], calls
- calling Web service
- Report Server Web service, SOAP
- XML Web service [Reporting Services], calls
- Report Server Web service, calls
- XML Web service [Reporting Services], SOAP
- SOAP [Reporting Services], calls
ms.assetid: f6f0c6e3-8bb5-4c44-9d19-1872edc72746
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 87f1485b4e3c0ed064e42bb3b411fece96eba8d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730143"
---
# <a name="calling-web-service-methods"></a><span data-ttu-id="daeb6-102">웹 서비스 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="daeb6-102">Calling Web Service Methods</span></span>
  <span data-ttu-id="daeb6-103">프록시 클래스를 사용 하 여 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 웹 서비스 작업을 호출 하는 경우 해당 클래스의 메서드를 사용 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="daeb6-103">When you use a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] proxy class to call Web service operations, you do so by using the methods of that class.</span></span> <span data-ttu-id="daeb6-104">이러한 메서드는 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 클래스 라이브러리의 다른 클래스 메서드와 같이 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="daeb6-104">These methods respond like any other method of a class in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] class library.</span></span> <span data-ttu-id="daeb6-105">모든 웹 서비스 메서드는 공용 액세스 권한을 가지며 알맞은 수의 인수와 인수 유형을 제공하도록 요구합니다.</span><span class="sxs-lookup"><span data-stu-id="daeb6-105">All Web service methods have public access and require you to supply the appropriate number of arguments and argument types.</span></span> <span data-ttu-id="daeb6-106">프로젝트에서 프록시 클래스의 인스턴스를 만들었으면 메서드를 호출하여 보고서 서버를 통해 보고 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daeb6-106">After you have created an instance of the proxy class in your project, you can call the methods to perform reporting operations via the report server.</span></span> <span data-ttu-id="daeb6-107">다음 C# 코드는 <xref:ReportService2010.ReportingService2010> 프록시 클래스의 <xref:ReportService2010.ReportingService2010.ListChildren%2A> 메서드 사용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="daeb6-107">The following C# code illustrates the use of the <xref:ReportService2010.ReportingService2010.ListChildren%2A> method of the <xref:ReportService2010.ReportingService2010> proxy class.</span></span> <span data-ttu-id="daeb6-108">이 코드는 보고서 서버 데이터베이스의 모든 항목 목록이 포함된 <xref:ReportService2010.CatalogItem> 개체 배열을 반환하는 웹 서비스 재귀 호출을 수행하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="daeb6-108">The code is used to make a recursive call to the Web service that returns an array of <xref:ReportService2010.CatalogItem> objects that contains a list of all items in the report server database:</span></span>  
  
```vb  
Dim rs As New ReportingService2010()  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
Dim items As CatalogItem() = rs.ListChildren("/", True)  
```  
  
```csharp  
ReportingService2010 rs = new ReportingService2010();  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
CatalogItem[] items = rs.ListChildren("/", true);  
```  
  
## <a name="see-also"></a><span data-ttu-id="daeb6-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="daeb6-109">See Also</span></span>  
 <span data-ttu-id="daeb6-110">[웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="daeb6-110">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="daeb6-111">[보고서 서버 웹 서비스](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="daeb6-111">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 [<span data-ttu-id="daeb6-112">기술 참조&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="daeb6-112">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
