---
title: ADO NET 원본 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetsource.f1
helpviewer_keywords:
- ADO.NET source
- sources [Integration Services], ADO.NET
- sources [Integration Services], DataReader
- .NET Framework [Integration Services]
- DataReader source
ms.assetid: 2a2f1750-2cda-4dda-9dca-623a96a6b3c0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eb50a6171ed29fc5328663d8ce9992e0462e02f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738565"
---
# <a name="ado-net-source"></a><span data-ttu-id="10455-102">ADO.NET 원본</span><span class="sxs-lookup"><span data-stu-id="10455-102">ADO NET Source</span></span>
  <span data-ttu-id="10455-103">ADO.NET 원본은 .NET 공급자의 데이터를 사용하며 데이터 흐름에서 해당 데이터를 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="10455-103">The ADO NET source consumes data from a .NET provider and makes the data available to the data flow.</span></span>  
  
 <span data-ttu-id="10455-104">ADO NET 원본을 사용하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10455-104">You can use the ADO NET source to connect to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span> <span data-ttu-id="10455-105">OLE DB를 사용하여 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 에 연결할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10455-105">Connecting to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] by using OLE DB is not supported.</span></span> <span data-ttu-id="10455-106">[!INCLUDE[ssSDS](../../includes/sssds-md.md)]에 대한 자세한 내용은 [일반 지침 및 제한 사항(Azure SQL Database)](https://go.microsoft.com/fwlink/?LinkId=248228)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10455-106">For more information about [!INCLUDE[ssSDS](../../includes/sssds-md.md)], see [General Guidelines and Limitations (Azure SQL Database)](https://go.microsoft.com/fwlink/?LinkId=248228).</span></span>  
  
## <a name="data-type-support"></a><span data-ttu-id="10455-107">데이터 형식 지원</span><span class="sxs-lookup"><span data-stu-id="10455-107">Data Type Support</span></span>  
 <span data-ttu-id="10455-108">원본은 특정 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 데이터 형식에 매핑되지 않는 모든 데이터 형식을 DT_NTEXT [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 데이터 형식으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="10455-108">The source converts any data type that does not map to a specific [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type to the DT_NTEXT [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type.</span></span> <span data-ttu-id="10455-109">데이터 형식이 `System.Object`인 경우에도 이러한 변환이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="10455-109">This conversion occurs even if the data type is `System.Object`.</span></span>  
  
 <span data-ttu-id="10455-110">DT_NTEXT 데이터 형식을 DT_WSTR 데이터 형식으로 변경하거나 DT_WSTR을 DT_NTEXT로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10455-110">You can change the DT_NTEXT data type to the DT_WSTR data type, or the change DT_WSTR to DT_NTEXT.</span></span> <span data-ttu-id="10455-111">데이터 형식을 변경하려면 ADO.NET 원본의 **고급 편집기** 대화 상자에서 **DataType** 속성을 설정하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10455-111">You change data types by setting the **DataType** property in the **Advanced Editor** dialog box of the ADO NET source.</span></span> <span data-ttu-id="10455-112">자세한 내용은 [Common Properties](../common-properties.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10455-112">For more information, see [Common Properties](../common-properties.md).</span></span>  
  
 <span data-ttu-id="10455-113">ADO.NET 원본 뒤에 데이터 변환을 사용하여 DT_NTEXT 데이터 형식을 DT_BYTES 또는 DT_STR 데이터 형식으로 변환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10455-113">The DT_NTEXT data type can also be converted to the DT_BYTES or DT_STR data type by using a Data Conversion transformation after the ADO NET source.</span></span> <span data-ttu-id="10455-114">자세한 내용은 [Data Conversion Transformation](transformations/data-conversion-transformation.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10455-114">For more information, see [Data Conversion Transformation](transformations/data-conversion-transformation.md).</span></span>  
  
 <span data-ttu-id="10455-115">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서 날짜 데이터 형식인 DT_DBDATE, DT_DBTIME2, DT_DBTIMESTAMP2 및 DT_DBTIMESTAMPOFFSET은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 특정 날짜 데이터 형식에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="10455-115">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], the date data types, DT_DBDATE, DT_DBTIME2, DT_DBTIMESTAMP2, and DT_DBTIMESTAMPOFFSET, map to certain date data types in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="10455-116">ADO.NET 원본을 구성하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 사용되는 날짜 데이터 형식을 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 에서 사용되는 날짜 데이터 형식으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10455-116">You can configure the ADO NET source to convert the date data types from those that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses to those that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] uses.</span></span> <span data-ttu-id="10455-117">ADO.NET 원본을 구성하여 이러한 날짜 데이터 형식을 변환하려면 **연결 관리자의** Type System Version [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 속성을 **Latest**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="10455-117">To configure the ADO NET source to convert these date data types, set the **Type System Version** property of the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to **Latest**.</span></span> <span data-ttu-id="10455-118">**Type System Version** 속성은 **연결 관리자** 대화 상자의 **모두** 페이지에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10455-118">(The **Type System Version** property is on the **All** page of the **Connection Manager** dialog box.</span></span> <span data-ttu-id="10455-119">**연결 관리자** 대화 상자를 열려면 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 연결 관리자를 마우스 오른쪽 단추로 클릭한 다음 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10455-119">To open the **Connection Manager** dialog box, right-click the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager, and then click **Edit**.)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="10455-120">**연결 관리자의** Type System Version [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 속성을 **SQL Server 2005**로 설정하면 시스템은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 날짜 데이터 형식을 DT_WSTR로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="10455-120">If the **Type System Version** property for the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager is set to **SQL Server 2005**, the system converts the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date data types to DT_WSTR.</span></span>  
  
 <span data-ttu-id="10455-121">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 연결 관리자가 공급자를 .NET Data Provider for [!INCLUDE[vstecado](../../includes/vstecado-md.md)] (SqlClient)로 지정하면 시스템은 UDT(사용자 정의 데이터 형식)를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] BLOB(Binary Large Object)으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="10455-121">The system converts user-defined data types (UDTs) to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] binary large objects (BLOB) when the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager specifies the provider as the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient).</span></span> <span data-ttu-id="10455-122">시스템은 UDT 데이터 형식을 변환할 때 다음 규칙을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="10455-122">The system applies the following rules when it converts the UDT data type:</span></span>  
  
-   <span data-ttu-id="10455-123">데이터가 큰 UDT가 아니면 시스템은 데이터를 DT_BYTES로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="10455-123">If the data is a non-large UDT, the system converts the data to DT_BYTES.</span></span>  
  
-   <span data-ttu-id="10455-124">데이터가 큰 UDT가 아니고 데이터베이스의 열에 대한 **Length** 속성이 -1 또는 8,000바이트보다 큰 값으로 설정되어 있으면 시스템은 데이터를 DT_IMAGE로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="10455-124">If the data is a non-large UDT, and the **Length** property of the column on the database is set to -1 or a value greater than 8,000 bytes, the system converts the data to DT_IMAGE.</span></span>  
  
-   <span data-ttu-id="10455-125">데이터가 큰 UDT이면 시스템은 데이터를 DT_ IMAGE로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="10455-125">If the data is a large UDT, the system converts the data to DT_IMAGE.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="10455-126">ADO.NET 원본이 오류 출력을 사용하도록 구성되지 않은 경우 시스템은 데이터를 8,000바이트 청크로 DT_IMAGE 열에 스트리밍합니다.</span><span class="sxs-lookup"><span data-stu-id="10455-126">If the ADO NET source is not configured to use error output, the system streams the data to the DT_IMAGE column in chunks of 8,000 bytes.</span></span> <span data-ttu-id="10455-127">ADO.NET 원본이 오류 출력을 사용하도록 구성된 경우에는 시스템이 전체 바이트 배열을 DT_IMAGE 열로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="10455-127">If the ADO NET source is configured to use error output, the system passes the whole array of bytes to the DT_IMAGE column.</span></span> <span data-ttu-id="10455-128">오류 출력을 사용할 구성 요소를 구성하는 방법에 대한 자세한 내용은 [데이터의 오류 처리](error-handling-in-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10455-128">For more information about how to configure components to use error output, see [Error Handling in Data](error-handling-in-data.md).</span></span>  
  
 <span data-ttu-id="10455-129">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 데이터 형식, 지원되는 데이터 형식 변환 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 비롯한 특정 데이터베이스에서의 데이터 형식 매핑에 대한 자세한 내용은 [Integration Services 데이터 형식](integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10455-129">For more information about the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types, supported data type conversions, and data type mapping across certain databases including [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="10455-130">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 데이터 형식을 관리 데이터 형식에 매핑하는 방법에 대한 자세한 내용은 [데이터 흐름의 데이터 형식 작업](../extending-packages-custom-objects/data-flow/working-with-data-types-in-the-data-flow.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10455-130">For information about mapping [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types to managed data types, see [Working with Data Types in the Data Flow](../extending-packages-custom-objects/data-flow/working-with-data-types-in-the-data-flow.md).</span></span>  
  
## <a name="ado-net-source-troubleshooting"></a><span data-ttu-id="10455-131">ADO.NET 원본 문제 해결</span><span class="sxs-lookup"><span data-stu-id="10455-131">ADO NET Source Troubleshooting</span></span>  
 <span data-ttu-id="10455-132">ADO.NET 원본이 외부 데이터 공급자에 대해 수행하는 호출을 로깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10455-132">You can log the calls that the ADO NET source makes to external data providers.</span></span> <span data-ttu-id="10455-133">이 로깅 기능을 사용하면 ADO.NET 원본이 외부 데이터 원본에서 데이터를 로드할 때 발생하는 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10455-133">You can use this logging capability to troubleshoot the loading of data from external data sources that the ADO NET source performs.</span></span> <span data-ttu-id="10455-134">ADO.NET 원본이 외부 데이터 공급자에 대해 수행하는 호출을 로깅하려면 패키지 로깅을 사용하고 패키지 수준에서 **Diagnostic** 이벤트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="10455-134">To log the calls that the ADO NET source makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="10455-135">자세한 내용은 [패키지 실행 문제 해결 도구](../troubleshooting/troubleshooting-tools-for-package-execution.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10455-135">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="ado-net-source-configuration"></a><span data-ttu-id="10455-136">ADO.NET 원본 구성</span><span class="sxs-lookup"><span data-stu-id="10455-136">ADO NET Source Configuration</span></span>  
 <span data-ttu-id="10455-137">결과 집합을 정의하는 SQL 문을 제공하여 ADO.NET 원본을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="10455-137">You configure the ADO NET source by providing the SQL statement that defines the result set.</span></span> <span data-ttu-id="10455-138">예를 들어 [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] 데이터베이스에 연결되고 SQL 문 `SELECT * FROM Production.Product`를 사용하는 ADO.NET 원본은 **Production.Product** 테이블에서 모든 행을 추출하고 다운스트림 구성 요소에 해당 데이터 세트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="10455-138">For example, an ADO NET source that connects to the [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] database and uses the SQL statement `SELECT * FROM Production.Product` extracts all the rows from the **Production.Product** table and provides the dataset to a downstream component.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="10455-139">SQL 문을 사용하여 임시 테이블의 결과를 반환하는 저장 프로시저를 호출하는 경우 WITH RESULT SETS 옵션을 사용하여 결과 집합의 메타데이터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="10455-139">When you use an SQL statement to invoke a stored procedure that returns results from a temporary table, use the WITH RESULT SETS option to define metadata for the result set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="10455-140">SQL 문을 사용하여 저장 프로시저를 실행했는데 다음 오류 메시지와 함께 작업이 실패할 경우 Exec 문 전에 `SET FMTONLY OFF` 문을 추가하여 오류를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10455-140">If you use an SQL statement to execute a stored procedure and the package fails with the following error, you may be able to resolve the error by adding the `SET FMTONLY OFF` statement before the exec statement.</span></span>  
>   
>  <span data-ttu-id="10455-141">**열 <열_이름>을(를) 데이터 원본에서 찾을 수 없습니다.**</span><span class="sxs-lookup"><span data-stu-id="10455-141">**Column <column_name> cannot be found at the datasource.**</span></span>  
  
 <span data-ttu-id="10455-142">ADO.NET 원본은 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 연결 관리자를 사용하여 데이터 원본에 연결하며 이 연결 관리자는 .NET 공급자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="10455-142">The ADO NET source uses an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to connect to a data source, and the connection manager specifies the .NET provider.</span></span> <span data-ttu-id="10455-143">자세한 내용은 [ADO.NET Connection Manager](../connection-manager/ado-net-connection-manager.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10455-143">For more information, see [ADO.NET Connection Manager](../connection-manager/ado-net-connection-manager.md).</span></span>  
  
 <span data-ttu-id="10455-144">ADO.NET 원본에는 하나의 일반 출력과 하나의 오류 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10455-144">The ADO NET source has one regular output and one error output.</span></span>  
  
 <span data-ttu-id="10455-145">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10455-145">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="10455-146">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="10455-146">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="10455-147">Common Properties</span><span class="sxs-lookup"><span data-stu-id="10455-147">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="10455-148">ADO.NET 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="10455-148">ADO NET Custom Properties</span></span>](ado-net-custom-properties.md)  
  
 <span data-ttu-id="10455-149">속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10455-149">For more information about how to set properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10455-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="10455-150">See Also</span></span>  
 <span data-ttu-id="10455-151">[DataReader 대상](datareader-destination.md) </span><span class="sxs-lookup"><span data-stu-id="10455-151">[DataReader Destination](datareader-destination.md) </span></span>  
 <span data-ttu-id="10455-152">[ADO.NET 대상](ado-net-destination.md) </span><span class="sxs-lookup"><span data-stu-id="10455-152">[ADO NET Destination](ado-net-destination.md) </span></span>  
 [<span data-ttu-id="10455-153">데이터 흐름</span><span class="sxs-lookup"><span data-stu-id="10455-153">Data Flow</span></span>](data-flow.md)  
  
  
