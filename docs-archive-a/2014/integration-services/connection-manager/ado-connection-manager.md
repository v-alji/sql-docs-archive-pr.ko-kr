---
title: ADO 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], ADO
- connection managers [Integration Services], ADO
- ADO connection manager [Integration Services]
ms.assetid: 490418bc-5ef1-41b8-a9c8-de38aa96e0f6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fb4b667733f81eebbaf2b6a2ab9b205c09fe2c66
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659613"
---
# <a name="ado-connection-manager"></a><span data-ttu-id="f4afb-102">ADO 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="f4afb-102">ADO Connection Manager</span></span>
  <span data-ttu-id="f4afb-103">ADO 연결 관리자를 사용하면 패키지에서 레코드 집합과 같은 ADO(ActiveX Data Objects) 개체에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4afb-103">An ADO connection manager enables a package to connect to ActiveX Data Objects (ADO) objects, such as a recordset.</span></span> <span data-ttu-id="f4afb-104">이 연결 관리자는 일반적으로 Microsoft Visual Basic 6.0과 같은 초기 버전의 언어로 작성된 사용자 지정 태스크나 데이터 원본에 연결하기 위해 ADO를 사용하는 기존 애플리케이션의 일부인 사용자 지정 태스크에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4afb-104">This connection manager is typically used in custom tasks written in an earlier version of a language, such as Microsoft Visual Basic 6.0, or in custom tasks that are part of an existing application that uses ADO to connect to a data source.</span></span>  
  
 <span data-ttu-id="f4afb-105">패키지에 ado 연결 관리자를 추가 하면에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 런타임에 ado 연결로 확인 되는 연결 관리자를 만들고, 연결 관리자 속성을 설정 하 고, 연결 관리자를 `Connections` 패키지의 컬렉션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4afb-105">When you add an ADO connection manager to a package, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to an ADO connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span> <span data-ttu-id="f4afb-106">연결 관리자의 `ConnectionManagerType` 속성이 `ADO`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4afb-106">The `ConnectionManagerType` property of the connection manager is set to `ADO`.</span></span>  
  
## <a name="troubleshooting-the-ado-connection-manager"></a><span data-ttu-id="f4afb-107">ADO 연결 관리자 문제 해결</span><span class="sxs-lookup"><span data-stu-id="f4afb-107">Troubleshooting the ADO Connection Manager</span></span>  
 <span data-ttu-id="f4afb-108">ADO 연결 관리자에서 특정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 날짜 데이터 형식을 읽으면 다음 표에 표시된 결과가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4afb-108">When being read by an ADO connection manager, certain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date data types will generate the results shown in the following table.</span></span>  
  
|<span data-ttu-id="f4afb-109">SQL Server 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="f4afb-109">SQL Server Data type</span></span>|<span data-ttu-id="f4afb-110">결과</span><span class="sxs-lookup"><span data-stu-id="f4afb-110">Result</span></span>|  
|--------------------------|------------|  
|<span data-ttu-id="f4afb-111">`time`, `datetimeoffset`</span><span class="sxs-lookup"><span data-stu-id="f4afb-111">`time`, `datetimeoffset`</span></span>|<span data-ttu-id="f4afb-112">매개 변수가 있는 SQL 명령이 패키지에 사용되지 않을 경우 패키지가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="f4afb-112">The package fails unless the package uses parameterized SQL commands.</span></span> <span data-ttu-id="f4afb-113">매개 변수가 있는 SQL 명령을 사용하려면 패키지에서 SQL 실행 태스크를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="f4afb-113">To use parameterized SQL commands, use the Execute SQL Task in your package.</span></span> <span data-ttu-id="f4afb-114">자세한 내용은 [SQL 실행 태스크](../control-flow/execute-sql-task.md) 및 [SQL 실행 태스크의 매개 변수 및 반환 코드](../parameters-and-return-codes-in-the-execute-sql-task.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4afb-114">For more information, see [Execute SQL Task](../control-flow/execute-sql-task.md) and [Parameters and Return Codes in the Execute SQL Task](../parameters-and-return-codes-in-the-execute-sql-task.md).</span></span>|  
|`datetime2`|<span data-ttu-id="f4afb-115">ADO 연결 관리자가 밀리초 값을 자릅니다.</span><span class="sxs-lookup"><span data-stu-id="f4afb-115">The ADO connection manager truncates the millisecond value.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="f4afb-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식 및 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 데이터 형식에 매핑하는 방법에 대한 자세한 내용은 [데이터 형식&#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) 및 [Integration Services 데이터 형식](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4afb-116">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types and how they map to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) and [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="configuring-the-ado-connection-manager"></a><span data-ttu-id="f4afb-117">ADO 연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="f4afb-117">Configuring the ADO Connection Manager</span></span>  
 <span data-ttu-id="f4afb-118">다음과 같은 방법으로 ADO 연결 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4afb-118">You can configure an ADO connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="f4afb-119">선택된 공급자에 대한 요구 사항을 만족하도록 구성된 특정 연결 문자열을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f4afb-119">Provide a specific connection string configured to meet the requirements of the selected provider.</span></span>  
  
-   <span data-ttu-id="f4afb-120">공급자에 따라 연결할 데이터 원본의 이름을 포함시킵니다.</span><span class="sxs-lookup"><span data-stu-id="f4afb-120">Depending on the provider, include the name of the data source to connect to.</span></span>  
  
-   <span data-ttu-id="f4afb-121">선택된 공급자에 적합한 보안 자격 증명을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f4afb-121">Provide security credentials as appropriate for the selected provider.</span></span>  
  
-   <span data-ttu-id="f4afb-122">연결 관리자에서 만든 연결이 런타임에 유지될지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f4afb-122">Indicate whether the connection that is created from the connection manager is retained at run time.</span></span>  
  
 <span data-ttu-id="f4afb-123">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4afb-123">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="f4afb-124">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="f4afb-124">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="f4afb-125">OLE DB 연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="f4afb-125">Configure OLE DB Connection Manager</span></span>](ole-db-connection-manager.md)  
  
 <span data-ttu-id="f4afb-126">연결 관리자를 프로그래밍 방식으로 구성하는 방법에 대한 자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 및 [프로그래밍 방식으로 연결 추가](../building-packages-programmatically/adding-connections-programmatically.md)로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4afb-126">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4afb-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f4afb-127">See Also</span></span>  
 [<span data-ttu-id="f4afb-128">Integration Services&#40;SSIS&#41; 연결</span><span class="sxs-lookup"><span data-stu-id="f4afb-128">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
