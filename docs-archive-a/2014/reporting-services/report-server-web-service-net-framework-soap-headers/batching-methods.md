---
title: 일괄 처리 메서드 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- methods [Reporting Services], batches
- BatchHeader SOAP header
- Web service [Reporting Services], methods
- Report Server Web service, batching
- batches [Reporting Services]
- XML Web service [Reporting Services], methods
- locking [Reporting Services]
- multiple Web service methods
ms.assetid: 86435534-c9fe-4b49-b88c-7fb6d21976b0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c778da186fdbbfaed17b9635d9ca7309a369552b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659804"
---
# <a name="batching-methods"></a><span data-ttu-id="c6115-102">일괄 처리 메서드</span><span class="sxs-lookup"><span data-stu-id="c6115-102">Batching Methods</span></span>
  <span data-ttu-id="c6115-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 SOAP 헤더를 사용하면 단일 작업에 여러 웹 서비스 메서드를 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6115-103">The use of SOAP headers in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enables you to include multiple Web service methods in a single operation.</span></span> <span data-ttu-id="c6115-104">메서드는 호출된 순서대로 단일 데이터베이스 트랜잭션의 범위 내에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6115-104">Methods run within the scope of a single database transaction, in the order in which they are called.</span></span>  
  
 <span data-ttu-id="c6115-105">다중 메서드 일괄 처리 작업을 사용할 때 얻을 수 있는 이점으로 롤백이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6115-105">Rollback is one advantage of using multiple-method batch operations.</span></span> <span data-ttu-id="c6115-106">일괄 처리 실행 도중 메서드 호출에서 오류가 발생하면 보고서 서버에서 일괄 처리 실행을 중지하고 모든 이전 작업을 롤백할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6115-106">If an error occurs on any of the method calls while a batch is running, the report server stops running the batch and rolls back any previous operations.</span></span> <span data-ttu-id="c6115-107">이 기능은 메서드 호출이 일괄 처리 내 다른 메서드 호출이 성공적으로 완료되는지 여부에 따라 달라지는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="c6115-107">This is useful when a method call depends on the successful completion of other method calls in that batch.</span></span>  
  
 <span data-ttu-id="c6115-108">웹 서비스에서는 다중 메서드 일괄 처리 작업에 대한 잠금 기능을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6115-108">The Web service does not provide locking semantics for multiple-method batch operations.</span></span> <span data-ttu-id="c6115-109">메시지가 서버에 전송되고 Execute 명령이 호출되기 전까지는 보고서 서버 데이터베이스의 행이 업데이트를 위해 잠기지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6115-109">Rows in the report server database are not locked for updating until the message is sent to the server and the Execute command is called.</span></span>  
  
 <span data-ttu-id="c6115-110">또한 데이터를 마지막으로 읽은 이후 데이터베이스가 변경되지 않았음을 보장하는 동시성 제어도 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c6115-110">There are also no concurrency controls to guarantee that the database has not changed since the data was last read.</span></span> <span data-ttu-id="c6115-111">두 클라이언트가 동일한 항목을 수정할 경우 매개 변수가 유효하면(예: 항목 이름이 바뀌지 않음) 마지막 업데이트가 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="c6115-111">If two clients modify the same item, the last update succeeds if the parameters are still valid (for example, the item has not been renamed).</span></span>  
  
 <span data-ttu-id="c6115-112">다음 예에서는 <xref:ReportService2005.ReportingService2005.CreateFolder%2A> 메서드를 세 번 호출하고 이러한 호출을 단일 일괄 처리로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c6115-112">The following example calls the <xref:ReportService2005.ReportingService2005.CreateFolder%2A> method three times and runs these calls as a single batch.</span></span> <span data-ttu-id="c6115-113"><xref:ReportService2005.ReportingService2005.CreateFolder%2A>에 대한 호출 중 하나라도 실패할 경우 전체 일괄 처리가 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6115-113">If any of the calls to <xref:ReportService2005.ReportingService2005.CreateFolder%2A> fail, the entire batch is canceled.</span></span>  
  
```vb  
Imports System  
Imports System.Web.Services.Protocols  
Imports myNamespace.MyReferenceName  
  
Class Sample  
    Sub Main(args() As String)  
        Dim rs As New ReportingService2005()  
        rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
      ' Set the base Web service URL of the source server  
      rs.Url = "http://<Server Name>/reportserver/ReportService2005.asmx"  
  
        Dim bh As New BatchHeader()  
  
        bh.BatchId = service.CreateBatch()  
        rs.BatchHeaderValue = bh  
        rs.CreateFolder("New Folder1", "/", Nothing)  
        rs.CreateFolder("New Folder2", "/", Nothing)  
        rs.CreateFolder("New Folder3", "/", Nothing)  
  
        Console.WriteLine("Creating folders...")  
        rs.BatchHeaderValue = bh  
        rs.ExecuteBatch()  
        Console.WriteLine("Folders created successfully.")  
  
        rs.BatchHeaderValue = Nothing  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Web.Services.Protocols;   
using myNamespace.MyReferenceName;  
  
class Sample  
{  
    static void Main(string[] args)  
    {  
        ReportingService2005 rs = new ReportingService2005();  
        rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
      // Set the base Web service URL of the source server  
      rs.Url = "http://<Server Name>/reportserver/ReportService2005.asmx"  
  
        BatchHeader bh = new BatchHeader();  
  
        bh1.BatchID = service.CreateBatch();  
        rs.BatchHeaderValue = bh;  
        rs.CreateFolder("New Folder1", "/", null);  
        rs.CreateFolder("New Folder2", "/", null);  
        rs.CreateFolder("New Folder3", "/", null);  
  
        Console.WriteLine("Creating folders...");  
        rs.BatchHeaderValue = bh1;  
        rs.ExecuteBatch();  
        Console.WriteLine("Folders created successfully.");  
  
        rs.BatchHeaderValue = null;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6115-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6115-114">See Also</span></span>  
 <xref:ReportService2005.ReportingService2005.CancelBatch%2A>   
 <xref:ReportService2005.ReportingService2005.CreateBatch%2A>   
 <span data-ttu-id="c6115-115">[SSRS&#41;&#40;기술 참조](../technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c6115-115">[Technical Reference &#40;SSRS&#41;](../technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="c6115-116">Reporting Services SOAP 헤더 사용</span><span class="sxs-lookup"><span data-stu-id="c6115-116">Using Reporting Services SOAP Headers</span></span>](using-reporting-services-soap-headers.md)  
  
  
