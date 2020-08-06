---
title: ADO.NET 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connection managers [Integration Services], ADO.NET
- ADO.NET connection manager [Integration Services]
- connections [Integration Services], ADO.NET
ms.assetid: fc5daa2f-0159-4bda-9402-c87f1035a96f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9bdc25eeeae93fe0bd85deb55bfc86c55ab91ee5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651227"
---
# <a name="adonet-connection-manager"></a><span data-ttu-id="fd3c2-102">ADO.NET 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="fd3c2-102">ADO.NET Connection Manager</span></span>
  <span data-ttu-id="fd3c2-103">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 연결 관리자를 사용하면 패키지에서 .NET 공급자를 사용하여 데이터 원본에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd3c2-103">An [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager enables a package to access data sources by using a .NET provider.</span></span> <span data-ttu-id="fd3c2-104">이 연결 관리자는 일반적으로와 같은 데이터 원본에 액세스 하는 데 사용 되며 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , c #과 같은 언어를 사용 하 여 관리 코드로 작성 된 사용자 지정 작업에서 OLE DB 및 XML을 통해 노출 되는 데이터 원본에도 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd3c2-104">This connection manager is typically used to access data sources such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and also data sources exposed through OLE DB and XML in custom tasks that are written in managed code by using a language such C#.</span></span>  
  
 <span data-ttu-id="fd3c2-105">[!INCLUDE[vstecado](../../includes/vstecado-md.md)]패키지에 연결 관리자를 추가 하면에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 런타임에 연결로 확인 되는 연결 관리자를 만들고, [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 연결 관리자 속성을 설정 하 고, 연결 관리자를 `Connections` 패키지의 컬렉션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd3c2-105">When you add an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to a package, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that is resolved as an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span>  
  
 <span data-ttu-id="fd3c2-106">연결 관리자의 `ConnectionManagerType` 속성이 `ADO.NET`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd3c2-106">The `ConnectionManagerType` property of the connection manager is set to `ADO.NET`.</span></span> <span data-ttu-id="fd3c2-107">`ConnectionManagerType`의 값은 연결 관리자에서 사용되는 .NET 공급자 이름이 포함되도록 한정됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd3c2-107">The value of `ConnectionManagerType` is qualified to include the name of the .NET provider that the connection manager uses.</span></span>  
  
## <a name="adonet-connection-manager-troubleshooting"></a><span data-ttu-id="fd3c2-108">ADO.NET 연결 관리자 문제 해결</span><span class="sxs-lookup"><span data-stu-id="fd3c2-108">ADO.NET Connection Manager Troubleshooting</span></span>  
 <span data-ttu-id="fd3c2-109">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 연결 관리자가 외부 데이터 공급자에 대해 수행하는 호출을 로깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd3c2-109">You can log the calls that the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager makes to external data providers.</span></span> <span data-ttu-id="fd3c2-110">이 로깅 기능을 사용하여 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 연결 관리자가 수행하는 외부 데이터 원본에 대한 연결 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd3c2-110">You can use this logging capability to troubleshoot the connections that the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager makes to external data sources.</span></span> <span data-ttu-id="fd3c2-111">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 연결 관리자가 외부 데이터 공급자에 대해 수행하는 호출을 로깅하려면 패키지 로깅을 설정하고 패키지 수준에서 **Diagnostic** 이벤트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fd3c2-111">To log the calls that the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="fd3c2-112">자세한 내용은 [패키지 실행 문제 해결 도구](../troubleshooting/troubleshooting-tools-for-package-execution.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fd3c2-112">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
 <span data-ttu-id="fd3c2-113">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 연결 관리자에서 특정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 날짜 데이터 형식의 데이터를 읽으면 다음 표에 표시된 결과가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd3c2-113">When being read by an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager, data of certain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date data types will generate the results shown in the following table.</span></span>  
  
|<span data-ttu-id="fd3c2-114">SQL Server 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="fd3c2-114">SQL Server data type</span></span>|<span data-ttu-id="fd3c2-115">결과</span><span class="sxs-lookup"><span data-stu-id="fd3c2-115">Result</span></span>|  
|--------------------------|------------|  
|<span data-ttu-id="fd3c2-116">`time`, `datetimeoffset`</span><span class="sxs-lookup"><span data-stu-id="fd3c2-116">`time`, `datetimeoffset`</span></span>|<span data-ttu-id="fd3c2-117">매개 변수가 있는 SQL 명령이 패키지에 사용되지 않을 경우 패키지가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="fd3c2-117">The package fails unless the package uses parameterized SQL commands.</span></span> <span data-ttu-id="fd3c2-118">매개 변수가 있는 SQL 명령을 사용하려면 패키지에서 SQL 실행 태스크를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="fd3c2-118">To use parameterized SQL commands, use the Execute SQL Task in your package.</span></span> <span data-ttu-id="fd3c2-119">자세한 내용은 [SQL 실행 태스크](../control-flow/execute-sql-task.md) 및 [SQL 실행 태스크의 매개 변수 및 반환 코드](../parameters-and-return-codes-in-the-execute-sql-task.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fd3c2-119">For more information, see [Execute SQL Task](../control-flow/execute-sql-task.md) and [Parameters and Return Codes in the Execute SQL Task](../parameters-and-return-codes-in-the-execute-sql-task.md).</span></span>|  
|`datetime2`|<span data-ttu-id="fd3c2-120">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 연결 관리자가 밀리초 값을 자릅니다.</span><span class="sxs-lookup"><span data-stu-id="fd3c2-120">The [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager truncates the millisecond value.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="fd3c2-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식 및 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 데이터 형식에 매핑하는 방법에 대한 자세한 내용은 [데이터 형식&#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) 및 [Integration Services 데이터 형식](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fd3c2-121">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types and how they map to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) and [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="adonet-connection-manager-configuration"></a><span data-ttu-id="fd3c2-122">ADO.NET 연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="fd3c2-122">ADO.NET Connection Manager Configuration</span></span>  
 <span data-ttu-id="fd3c2-123">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 연결 관리자는 다음과 같은 방법으로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd3c2-123">You can configure an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager in the following ways:</span></span>  
  
 <span data-ttu-id="fd3c2-124">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd3c2-124">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
-   <span data-ttu-id="fd3c2-125">선택된 .NET 공급자에 대한 요구 사항을 만족하도록 구성된 특정 연결 문자열을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fd3c2-125">Provide a specific connection string configured to meet the requirements of the selected .NET provider.</span></span>  
  
-   <span data-ttu-id="fd3c2-126">공급자에 따라 연결할 데이터 원본의 이름을 포함시킵니다.</span><span class="sxs-lookup"><span data-stu-id="fd3c2-126">Depending on the provider, include the name of the data source to connect to.</span></span>  
  
-   <span data-ttu-id="fd3c2-127">선택된 공급자에 적합한 보안 자격 증명을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fd3c2-127">Provide security credentials as appropriate for the selected provider.</span></span>  
  
-   <span data-ttu-id="fd3c2-128">연결 관리자에서 만든 연결이 런타임에 유지될지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fd3c2-128">Indicate whether the connection that is created from the connection manager is retained at run time.</span></span>  
  
 <span data-ttu-id="fd3c2-129">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 연결 관리자의 여러 구성 옵션은 연결 관리자에서 사용되는 .NET 공급자에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="fd3c2-129">Many of configuration options of the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager depend on the .NET provider that the connection manager uses.</span></span>  
  
 <span data-ttu-id="fd3c2-130">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="fd3c2-130">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click one of the following topic:</span></span>  
  
-   [<span data-ttu-id="fd3c2-131">ADO.NET 연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="fd3c2-131">Configure ADO.NET Connection Manager</span></span>](../configure-ado-net-connection-manager.md)  
  
 <span data-ttu-id="fd3c2-132">연결 관리자를 프로그래밍 방식으로 구성하는 방법에 대한 자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 및 [프로그래밍 방식으로 연결 추가](../building-packages-programmatically/adding-connections-programmatically.md)로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd3c2-132">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd3c2-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fd3c2-133">See Also</span></span>  
 [<span data-ttu-id="fd3c2-134">Integration Services&#40;SSIS&#41; 연결</span><span class="sxs-lookup"><span data-stu-id="fd3c2-134">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
