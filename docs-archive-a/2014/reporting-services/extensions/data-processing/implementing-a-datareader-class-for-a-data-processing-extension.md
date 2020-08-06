---
title: 데이터 처리 확장 프로그램에 대한 DataReader 클래스 구현 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], data readers
- data readers [Reporting Services]
- DataReader class
- read-only data
ms.assetid: 23e286e7-6074-4fbe-be29-203420d6c3d0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7c9e55741c72d624b7149435ced90550135d8b4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741592"
---
# <a name="implementing-a-datareader-class-for-a-data-processing-extension"></a><span data-ttu-id="3c4e8-102">데이터 처리 확장 프로그램에 대한 DataReader 클래스 구현</span><span class="sxs-lookup"><span data-stu-id="3c4e8-102">Implementing a DataReader Class for a Data Processing Extension</span></span>
  <span data-ttu-id="3c4e8-103">**DataReader** 개체가 있으면 클라이언트에서는 읽기 전용, 정방향 전용 데이터 스트림을 데이터 원본에서 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c4e8-103">The **DataReader** object enables a client to retrieve a read-only, forward-only stream of data from a data source.</span></span> <span data-ttu-id="3c4e8-104">결과는 쿼리 실행으로 반환되고 **DataReader** 클래스의 **Read** 메서드를 사용하여 요청할 때까지 클라이언트의 네트워크 버퍼에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c4e8-104">Results are returned as the query executes and are stored in the network buffer on the client until you request them using the **Read** method of the **DataReader** class.</span></span> <span data-ttu-id="3c4e8-105">**DataReader** 클래스를 만들려면 <xref:Microsoft.ReportingServices.DataProcessing.IDataReader>를 구현하고 선택적으로 <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension>을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="3c4e8-105">To create a **DataReader** class, implement <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> and optionally implement <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension>.</span></span> <span data-ttu-id="3c4e8-106">**DataReader** 개체를 사용하면 전체 쿼리 결과가 반환될 때까지 기다리지 않고 사용 가능할 때 즉시 데이터를 검색하고 (기본적으로) 한 번에 행 한 개씩만 메모리에 저장하여 시스템 오버헤드를 줄임으로써 애플리케이션 성능이 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="3c4e8-106">Using a **DataReader** object increases application performance both by retrieving data as soon as it is available, rather than waiting for the entire results of the query to be returned, and (by default) storing only one row at a time in memory, reducing system overhead.</span></span>  
  
 <span data-ttu-id="3c4e8-107">**Command** 클래스 인스턴스를 만든 후 **Command.ExecuteReader** 호출을 통해 데이터 원본에서 행을 검색하여 **DataReader** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3c4e8-107">After creating an instance of your **Command** class, you create a **DataReader** object by calling **Command.ExecuteReader** to retrieve rows from the data source.</span></span> <span data-ttu-id="3c4e8-108">**DataReader** 구현은 두 가지 기본적인 기능을 제공해야 하며, 이 두 가지 기능은 명령 실행에서 얻은 결과 집합에 대한 정방향 전용 액세스 기능과 각 행 내의 열 유형, 이름, 값에 대한 액세스 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="3c4e8-108">The **DataReader** implementation must provide two basic capabilities: forward-only access over the result sets obtained by executing a command and access to the column types, names, and values within each row.</span></span> <span data-ttu-id="3c4e8-109">클라이언트는 **DataReader** 개체의 **Read** 메서드를 사용하여 쿼리 결과에서 행을 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="3c4e8-109">Clients use the **Read** method of the **DataReader** object to obtain a row from the results of the query.</span></span>  
  
 <span data-ttu-id="3c4e8-110">보고서 디자이너에서 **DataReader** 개체는 결과 집합에 대한 스키마 정보 및 필드 목록을 검색하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c4e8-110">In Report Designer, your **DataReader** object is used to retrieve a list of fields as well as schema information about the result set.</span></span> <span data-ttu-id="3c4e8-111"><xref:Microsoft.ReportingServices.DataProcessing.IDataReader> 인터페이스의 **GetName**, **GetValue**, **GetFieldType,** 및 **GetOrdinal** 메서드를 구현하여 이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c4e8-111">This is accomplished by implementing the **GetName**, **GetValue**, **GetFieldType,** and **GetOrdinal** methods of the <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> interface.</span></span>  
  
 <span data-ttu-id="3c4e8-112"><xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension> 인터페이스를 통해 결과 집합에 대한 특정 집계 정보를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c4e8-112">The <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension> interface allows you to supply specific aggregation information about your result set.</span></span> <span data-ttu-id="3c4e8-113">예제 **DataReader** 클래스 구현은 [SQL Server Reporting Services 제품 예제](https://go.microsoft.com/fwlink/?LinkId=177889)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3c4e8-113">For a sample **DataReader** class implementation, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c4e8-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3c4e8-114">See Also</span></span>  
 <span data-ttu-id="3c4e8-115">[Reporting Services 확장 프로그램](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="3c4e8-115">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="3c4e8-116">[데이터 처리 확장 프로그램 구현](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="3c4e8-116">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="3c4e8-117">Reporting Services 확장 라이브러리</span><span class="sxs-lookup"><span data-stu-id="3c4e8-117">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
