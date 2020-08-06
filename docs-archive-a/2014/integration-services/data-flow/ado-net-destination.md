---
title: ADO NET 대상 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetdest.f1
helpviewer_keywords:
- destinations [Integration Services], ADO.NET
- ADO.NET destination
ms.assetid: cb883990-d875-4d8b-b868-45f9f15ebeae
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8289a8c91c7b78749a341cc95055562d01164866
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732875"
---
# <a name="ado-net-destination"></a><span data-ttu-id="92d8e-102">ADO.NET 대상</span><span class="sxs-lookup"><span data-stu-id="92d8e-102">ADO NET Destination</span></span>
  <span data-ttu-id="92d8e-103">ADO.NET 대상은 데이터베이스 테이블이나 뷰를 사용하는 다양한 [!INCLUDE[vstecado](../../includes/vstecado-md.md)]호환 데이터베이스로 데이터를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="92d8e-103">The ADO NET destination loads data into a variety of [!INCLUDE[vstecado](../../includes/vstecado-md.md)]-compliant databases that use a database table or view.</span></span> <span data-ttu-id="92d8e-104">이 데이터를 기존 테이블이나 뷰에 로드하는 옵션이 제공되거나 새 테이블을 만들고 데이터를 새 테이블에 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92d8e-104">You have the option of loading this data into an existing table or view, or you can create a new table and load the data into the new table.</span></span>  
  
 <span data-ttu-id="92d8e-105">ADO NET 대상을 사용하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92d8e-105">You can use the ADO NET destination to connect to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span> <span data-ttu-id="92d8e-106">OLE DB를 사용하여 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 에 연결할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="92d8e-106">Connecting to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] by using OLE DB is not supported.</span></span> <span data-ttu-id="92d8e-107">[!INCLUDE[ssSDS](../../includes/sssds-md.md)]에 대한 자세한 내용은 [일반 지침 및 제한 사항(Azure SQL Database)](https://go.microsoft.com/fwlink/?LinkId=248228)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92d8e-107">For more information about [!INCLUDE[ssSDS](../../includes/sssds-md.md)], see [General Guidelines and Limitations (Azure SQL Database)](https://go.microsoft.com/fwlink/?LinkId=248228).</span></span>  
  
## <a name="troubleshooting-the-ado-net-destination"></a><span data-ttu-id="92d8e-108">ADO.NET 대상 문제 해결</span><span class="sxs-lookup"><span data-stu-id="92d8e-108">Troubleshooting the ADO NET Destination</span></span>  
 <span data-ttu-id="92d8e-109">ADO.NET 대상이 외부 데이터 공급자에 대해 수행하는 호출을 로깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92d8e-109">You can log the calls that the ADO NET destination makes to external data providers.</span></span> <span data-ttu-id="92d8e-110">이 로깅 기능을 사용하여 ADO.NET 대상이 수행하는 외부 데이터 원본에 대한 데이터 저장 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92d8e-110">You can use this logging capability to troubleshoot the saving of data to external data sources that the ADO NET destination performs.</span></span> <span data-ttu-id="92d8e-111">ADO.NET 대상이 외부 데이터 공급자에 대해 수행하는 호출을 로깅하려면 패키지 로깅을 설정하고 패키지 수준에서 **Diagnostic** 이벤트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92d8e-111">To log the calls that the ADO NET destination makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="92d8e-112">자세한 내용은 [패키지 실행 문제 해결 도구](../troubleshooting/troubleshooting-tools-for-package-execution.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92d8e-112">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="configuring-the-ado-net-destination"></a><span data-ttu-id="92d8e-113">ADO.NET 대상 구성</span><span class="sxs-lookup"><span data-stu-id="92d8e-113">Configuring the ADO NET Destination</span></span>  
 <span data-ttu-id="92d8e-114">이 대상은 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 연결 관리자를 사용하여 데이터 원본에 연결하며 연결 관리자에서는 사용할 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 공급자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="92d8e-114">This destination uses an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to connect to a data source and the connection manager specifies the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] provider to use.</span></span> <span data-ttu-id="92d8e-115">자세한 내용은 [ADO.NET Connection Manager](../connection-manager/ado-net-connection-manager.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92d8e-115">For more information, see [ADO.NET Connection Manager](../connection-manager/ado-net-connection-manager.md).</span></span>  
  
 <span data-ttu-id="92d8e-116">ADO.NET 대상에는 입력 열과 대상 데이터 원본 열 사이의 매핑이 포함되므로</span><span class="sxs-lookup"><span data-stu-id="92d8e-116">An ADO NET destination includes mappings between input columns and columns in the destination data source.</span></span> <span data-ttu-id="92d8e-117">입력 열을 모든 대상 열에 매핑하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92d8e-117">You do not have to map input columns to all destination columns.</span></span> <span data-ttu-id="92d8e-118">그러나 일부 대상 열의 속성에서 입력 열을 매핑해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92d8e-118">However, the properties of some destination columns can require the mapping of input columns.</span></span> <span data-ttu-id="92d8e-119">그렇지 않으면 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92d8e-119">Otherwise, errors might occur.</span></span> <span data-ttu-id="92d8e-120">예를 들어 대상 열에 Null 값이 허용되지 않는 경우에는 입력 열을 해당 대상 열로 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="92d8e-120">For example, if a destination column does not allow for null values, you must map an input column to that destination column.</span></span> <span data-ttu-id="92d8e-121">또한 매핑된 열의 데이터 형식이 호환되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="92d8e-121">In addition, the data types of mapped columns must be compatible.</span></span> <span data-ttu-id="92d8e-122">예를 들어 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 공급자에서 지원하지 않을 경우 문자열 데이터 형식의 입력 열을 숫자 데이터 형식의 대상 열에 매핑할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="92d8e-122">For example, you cannot map an input column with a string data type to a destination column with a numeric data type if the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] provider does not support this mapping.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="92d8e-123">는 데이터 형식이 이미지로 설정된 열에 텍스트 삽입을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="92d8e-123">does not support inserting text into columns whose data type is set to image.</span></span> <span data-ttu-id="92d8e-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식에 대한 자세한 내용은 [데이터 형식&#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92d8e-124">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="92d8e-125">ADO.NET 대상은 DT_DBTIME 유형으로 설정된 입력 열을 datetime 유형으로 설정된 데이터베이스 열에 매핑하는 작업을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="92d8e-125">The ADO NET destination does not support mapping an input column whose type is set to DT_DBTIME to a database column whose type is set to datetime.</span></span> <span data-ttu-id="92d8e-126">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 데이터 형식에 대한 자세한 내용은 [Integration Services 데이터 형식](integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92d8e-126">For more information about [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types, see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="92d8e-127">ADO.NET 대상에는 하나의 일반 입력과 하나의 오류 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92d8e-127">The ADO NET destination has one regular input and one error output.</span></span>  
  
 <span data-ttu-id="92d8e-128">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92d8e-128">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="92d8e-129">**ADO.NET 대상 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="92d8e-129">For more information about the properties that you can set in the **ADO NET Destination Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="92d8e-130">ADO NET 대상 편집기&#40;연결 관리자 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="92d8e-130">ADO NET Destination Editor &#40;Connection Manager Page&#41;</span></span>](../ado-net-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="92d8e-131">ADO NET 대상 편집기&#40;매핑 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="92d8e-131">ADO NET Destination Editor &#40;Mappings Page&#41;</span></span>](../ado-net-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="92d8e-132">ADO NET 대상 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="92d8e-132">ADO NET Destination Editor &#40;Error Output Page&#41;</span></span>](../ado-net-destination-editor-error-output-page.md)  
  
 <span data-ttu-id="92d8e-133">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="92d8e-133">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="92d8e-134">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="92d8e-134">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="92d8e-135">Common Properties</span><span class="sxs-lookup"><span data-stu-id="92d8e-135">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="92d8e-136">ADO.NET 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="92d8e-136">ADO NET Custom Properties</span></span>](ado-net-custom-properties.md)  
  
 <span data-ttu-id="92d8e-137">속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92d8e-137">For more information about how to set properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
