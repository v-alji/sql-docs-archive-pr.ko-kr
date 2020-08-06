---
title: SQL Server Compact Edition 대상 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlservercompactdest.f1
helpviewer_keywords:
- destinations [Integration Services], SQL Server Compact
- SQL Server Compact, destination
- inserting data
ms.assetid: 697742ba-cc14-414d-8187-1845ad0dd99b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bfeb0bfce54c9ebefb5c526656be6b736dc0d82b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659578"
---
# <a name="sql-server-compact-edition-destination"></a><span data-ttu-id="e9f43-102">SQL Server Compact Edition 대상</span><span class="sxs-lookup"><span data-stu-id="e9f43-102">SQL Server Compact Edition Destination</span></span>
  <span data-ttu-id="e9f43-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 대상은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 데이터베이스에 데이터를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="e9f43-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination writes data to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact databases.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e9f43-104">64비트 컴퓨터에서는 32비트 모드로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 데이터 원본에 연결하는 패키지를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9f43-104">On a 64-bit computer, you must run packages that connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact data sources in 32-bit mode.</span></span> <span data-ttu-id="e9f43-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Compact 데이터 원본에 연결할 때 사용하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 공급자는 32비트 버전에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9f43-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact provider that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] uses to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact data sources is available only in a 32-bit version.</span></span>  
  
 <span data-ttu-id="e9f43-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 대상을 구성할 때는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 대상에서 데이터를 삽입하는 테이블의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e9f43-106">You configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination by specifying the name of the table into which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination inserts the data.</span></span> <span data-ttu-id="e9f43-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 대상의 사용자 지정 속성인 TableName에는 테이블 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9f43-107">The custom property TableName of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination contains the table name.</span></span>  
  
 <span data-ttu-id="e9f43-108">이 대상은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 연결 관리자를 사용하여 데이터 원본에 연결하며 연결 관리자에서는 사용할 OLE DB 공급자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e9f43-108">This destination uses an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connection manager to connect to a data source, and the connection manager specifies the OLE DB provider to use.</span></span> <span data-ttu-id="e9f43-109">자세한 내용은 [SQL Server Compact Edition 연결 관리자](../connection-manager/sql-server-compact-edition-connection-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e9f43-109">For more information, see [SQL Server Compact Edition Connection Manager](../connection-manager/sql-server-compact-edition-connection-manager.md).</span></span>  
  
 <span data-ttu-id="e9f43-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 대상은 패키지 로드 시 속성 식을 사용하여 업데이트할 수 있는 TableName 사용자 지정 속성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e9f43-110">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination includes the TableName custom property, which can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="e9f43-111">자세한 내용은 [Integration Services&#40;SSIS&#41; 식](../expressions/integration-services-ssis-expressions.md), [패키지에서 속성 식 사용](../expressions/use-property-expressions-in-packages.md) 및 [SQL Server Compact Edition 대상 사용자 지정 속성](sql-server-compact-edition-destination-custom-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e9f43-111">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../expressions/use-property-expressions-in-packages.md), and [SQL Server Compact Edition Destination Custom Properties](sql-server-compact-edition-destination-custom-properties.md).</span></span>  
  
 <span data-ttu-id="e9f43-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 대상에는 하나의 입력이 있으며 오류 출력은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e9f43-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination has one input and does not support an error output.</span></span>  
  
## <a name="configuration-of-the-sql-server-compact-edition-destination"></a><span data-ttu-id="e9f43-113">SQL Server Compact Edition 대상 구성</span><span class="sxs-lookup"><span data-stu-id="e9f43-113">Configuration of the SQL Server Compact Edition Destination</span></span>  
 <span data-ttu-id="e9f43-114">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9f43-114">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="e9f43-115">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9f43-115">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="e9f43-116">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="e9f43-116">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="e9f43-117">Common Properties</span><span class="sxs-lookup"><span data-stu-id="e9f43-117">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="e9f43-118">SQL Server 대상 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="e9f43-118">SQL Server Destination Custom Properties</span></span>](sql-server-destination-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="e9f43-119">관련 작업</span><span class="sxs-lookup"><span data-stu-id="e9f43-119">Related Tasks</span></span>  
 <span data-ttu-id="e9f43-120">이 구성 요소의 속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e9f43-120">For more information about how to set properties of this component, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9f43-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e9f43-121">See Also</span></span>  
 [<span data-ttu-id="e9f43-122">데이터 흐름</span><span class="sxs-lookup"><span data-stu-id="e9f43-122">Data Flow</span></span>](data-flow.md)  
  
  
