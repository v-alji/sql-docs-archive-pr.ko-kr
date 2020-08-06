---
title: 네이티브 컴파일 관리자 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
f1_keywords:
- sql12.swb.nativecompilationwizard.f1
- swb.nativecompilationwizard.f1
ms.assetid: d3898a47-2985-4a08-bc70-fd8331a01b7b
author: rothja
ms.author: jroth
ms.openlocfilehash: b2182d89489af5da8bc3b85b89484fbbf72e4dfa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742064"
---
# <a name="native-compilation-advisor"></a><span data-ttu-id="deb5d-102">네이티브 컴파일 관리자</span><span class="sxs-lookup"><span data-stu-id="deb5d-102">Native Compilation Advisor</span></span>
  <span data-ttu-id="deb5d-103">트랜잭션 성능 보고서 도구( [Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)참조)는 네이티브 컴파일을 사용하도록 변환할 경우 효과적인 해석된 저장 프로시저에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="deb5d-103">Transaction performance reports tool (see [Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)) informs you about which interpreted stored procedures in your database will benefit if ported to use native compilation.</span></span> <span data-ttu-id="deb5d-104">네이티브 컴파일을 사용하도록 변환할 저장 프로시저를 식별한 후 네이티브 컴파일 관리자를 사용하여 해석된 저장 프로시저를 네이티브 컴파일로 마이그레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deb5d-104">After you identify a stored procedure that you would like to port to use native compilation, you can use the native compilation advisor to help you migrate the interpreted stored procedure to native compilation.</span></span> <span data-ttu-id="deb5d-105">고유하게 컴파일된 저장 프로시저에 대한 자세한 내용은 [Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="deb5d-105">For more information about natively compiled stored procedures, see [Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md).</span></span>  
  
 <span data-ttu-id="deb5d-106">먼저 해석된 저장 프로시저가 포함된 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="deb5d-106">To begin, connect to the instance that contains the interpreted stored procedure.</span></span> <span data-ttu-id="deb5d-107">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]또는 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 인스턴스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deb5d-107">You can connect to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], or [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] instance.</span></span> <span data-ttu-id="deb5d-108">하지만 메모리 최적화 관리자를 사용하여 마이그레이션 작업을 수행하려는 경우에는 메모리 내 OLTP 기능을 사용할 수 있는 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 인스턴스에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb5d-108">However, if you wish to perform a migration operation with the advisor, you must connect to a [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] instance on which In-Memory OLTP functionality is enabled.</span></span> <span data-ttu-id="deb5d-109">메모리 내 OLTP 요구 사항에 대한 자세한 내용은 [Requirements for Using Memory-Optimized Tables](memory-optimized-tables.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="deb5d-109">For more information about In-Memory OLTP requirements, see [Requirements for Using Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="deb5d-110">마이그레이션 방법에 대한 자세한 내용은 [메모리 내 OLTP – 일반적인 작업 패턴 및 마이그레이션 고려 사항](https://msdn.microsoft.com/library/dn673538.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="deb5d-110">For information about migration methodologies, see [In-Memory OLTP - Common Workload Patterns and Migration Considerations](https://msdn.microsoft.com/library/dn673538.aspx).</span></span>  
  
## <a name="walkthrough-using-the-native-compilation-advisor"></a><span data-ttu-id="deb5d-111">네이티브 컴파일 관리자 사용 연습</span><span class="sxs-lookup"><span data-stu-id="deb5d-111">Walkthrough Using the Native Compilation Advisor</span></span>  
 <span data-ttu-id="deb5d-112">**개체 탐색기**에서 변환할 저장 프로시저를 마우스 오른쪽 단추로 클릭하고 **네이티브 컴파일 관리자**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="deb5d-112">In **Object Explorer**, right click the stored procedure you want to convert, and select **Native Compilation Advisor**.</span></span> <span data-ttu-id="deb5d-113">**저장 프로시저 네이티브 컴파일 관리자**시작 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="deb5d-113">This will display the welcome page for the **Stored Procedure Native Compilation Advisor**.</span></span> <span data-ttu-id="deb5d-114">**다음**을 클릭하여 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="deb5d-114">Click **Next** to continue.</span></span>  
  
### <a name="stored-procedure-validation"></a><span data-ttu-id="deb5d-115">저장 프로시저 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="deb5d-115">Stored Procedure Validation</span></span>  
 <span data-ttu-id="deb5d-116">이 페이지에는 저장 프로시저에 네이티브 컴파일과 호환되지 않는 구문이 사용되었는지 여부가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="deb5d-116">This page will report if the stored procedure uses any constructs that are not compatible with native compilation.</span></span> <span data-ttu-id="deb5d-117">**다음** 을 클릭하여 세부 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deb5d-117">You can click **Next** to see details.</span></span> <span data-ttu-id="deb5d-118">네이티브 컴파일과 호환되지 않는 구문이 있는 경우 **다음** 을 클릭하여 세부 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deb5d-118">If there are constructs that are not compatible with native compilation, you can click **Next** to see details.</span></span>  
  
### <a name="stored-procedure-validation-result"></a><span data-ttu-id="deb5d-119">저장 프로시저 유효성 검사 결과</span><span class="sxs-lookup"><span data-stu-id="deb5d-119">Stored Procedure Validation Result</span></span>  
 <span data-ttu-id="deb5d-120">네이티브 컴파일과 호환되지 않는 구문이 있는 경우 **저장 프로시저 유효성 검사 결과** 페이지에 세부 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="deb5d-120">If there are constructs that are not compatible with native compilation, the **Stored Procedure Validation Result** page will display details.</span></span> <span data-ttu-id="deb5d-121">보고서를 생성하고( **보고서 생성**클릭), **네이티브 컴파일 관리자**를 종료하고, 코드가 네이티브 컴파일과 호환되도록 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deb5d-121">You can generate a report (click **Generate Report**), exit the **Native Compilation Advisor**, and update your code so that it is compatible with native compilation.</span></span>  
  
## <a name="code-sample"></a><span data-ttu-id="deb5d-122">코드 예제</span><span class="sxs-lookup"><span data-stu-id="deb5d-122">Code Sample</span></span>  
 <span data-ttu-id="deb5d-123">다음 예에서는 해석된 저장 프로시저와 네이티브 컴파일을 사용했을 때의 해당 저장 프로시저를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="deb5d-123">The following sample shows an interpreted stored procedure and the equivalent stored procedure for native compilation.</span></span> <span data-ttu-id="deb5d-124">이 예에서는 c:\data라는 디렉터리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="deb5d-124">The sample assumes a directory called c:\data.</span></span>  
  
```sql  
CREATE DATABASE Demo  
ON  
PRIMARY(NAME = [Demo_data],  
FILENAME = 'C:\DATA\Demo_data.mdf', size=500MB)  
, FILEGROUP [Demo_fg] CONTAINS MEMORY_OPTIMIZED_DATA(  
NAME = [Demo_dir],  
FILENAME = 'C:\DATA\Demo_dir')  
LOG ON (name = [Demo_log], Filename='C:\DATA\Demo_log.ldf', size=500MB)  
COLLATE Latin1_General_100_BIN2;  
GO  
USE Demo;  
GO  
  
CREATE TABLE [dbo].[SalesOrders]  
(  
     [order_id] [int] NOT NULL,  
     [order_date] [datetime] NOT NULL,  
     [order_status] [tinyint] NOT NULL  
  
CONSTRAINT [PK_SalesOrders] PRIMARY KEY NONCLUSTERED HASH   
(  
     [order_id]  
)WITH ( BUCKET_COUNT = 2097152)  
)WITH ( MEMORY_OPTIMIZED = ON )  
  
go  
  
CREATE PROCEDURE [dbo].[InsertOrder] @id INT, @date DATETIME2, @status TINYINT  
AS   
BEGIN   
  
  INSERT dbo.SalesOrders VALUES (@id, @date, @status)  
  
END  
  
go  
  
CREATE PROCEDURE [dbo].[InsertOrderXTP] @id INT, @date DATETIME2, @status TINYINT  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS   
BEGIN ATOMIC WITH   
(    TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
     LANGUAGE = N'us_english')  
  
  INSERT dbo.SalesOrders VALUES (@id, @date, @status)  
  
END  
go  
  
select * from SalesOrders  
go  
exec dbo.InsertOrder @id= 10, @date = '1956-01-01 12:00:00', @status = 1 ;  
exec dbo.InsertOrderXTP @id= 11, @date = '1956-01-01 12:01:00', @status = 2 ;  
select * from SalesOrders  
```  
  
## <a name="see-also"></a><span data-ttu-id="deb5d-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="deb5d-125">See Also</span></span>  
 [<span data-ttu-id="deb5d-126">메모리 내 OLTP로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="deb5d-126">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
