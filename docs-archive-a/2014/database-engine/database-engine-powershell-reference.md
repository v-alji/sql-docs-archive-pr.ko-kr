---
title: 데이터베이스 엔진 PowerShell 참조 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3c379a43-c497-47dd-8e7d-2b015c068bb7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2d72f9fcedee02e475369c32a7c263578c9ff156
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651880"
---
# <a name="database-engine-powershell-reference"></a><span data-ttu-id="af008-102">데이터베이스 엔진 PowerShell 참조</span><span class="sxs-lookup"><span data-stu-id="af008-102">Database Engine PowerShell Reference</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]<span data-ttu-id="af008-103">에는 [!INCLUDE[ssDE](../includes/ssde-md.md)]에서 일반적인 작업을 수행하는 데 사용할 수 있는 여러 가지 Windows PowerShell 2.0 cmdlet이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af008-103">includes a set of Windows PowerShell 2.0 cmdlets for performing common actions in the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="af008-104">또한 쿼리 식과 URN(Uniform Resource Name)을 SQL Server PowerShell 경로로 변경하거나 [!INCLUDE[ssDE](../includes/ssde-md.md)]에서 하나 이상의 개체를 지정하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af008-104">In addition, Query Expressions and Uniform Resource Names (URN) can be converted to SQL Server PowerShell paths, or used to specify one or more objects in the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
## <a name="database-engine-cmdlets"></a><span data-ttu-id="af008-105">데이터베이스 엔진 cmdlet</span><span class="sxs-lookup"><span data-stu-id="af008-105">Database Engine Cmdlets</span></span>  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] <span data-ttu-id="af008-106">에 있는 [!INCLUDE[ssDE](../includes/ssde-md.md)]용 cmdlet은 상대적으로 적습니다.</span><span class="sxs-lookup"><span data-stu-id="af008-106">includes relatively few cmdlets for the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="af008-107">[!INCLUDE[ssDE](../includes/ssde-md.md)] 에서 사용할 수 있는 대부분의 PowerShell 스크립트는 SQL Server PowerShell 공급자 및 관리 효율성 개체 모델을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="af008-107">Most PowerShell scripts working with the [!INCLUDE[ssDE](../includes/ssde-md.md)] use the SQL Server PowerShell provider and the manageability object models.</span></span> <span data-ttu-id="af008-108">자세한 내용은 [SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="af008-108">For more information, see [SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md).</span></span>  
  
 <span data-ttu-id="af008-109">Windows PowerShell 환경의 SQL Server cmdlet에 대한 도움말을 보는 방법은 [Get Help SQL Server PowerShell](../powershell/sql-server-powershell.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="af008-109">To learn how to get help about the SQL Server cmdlets in a Windows PowerShell environment, see [Get Help SQL Server PowerShell](../powershell/sql-server-powershell.md).</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="af008-110">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="af008-110">In This Section</span></span>  
 <span data-ttu-id="af008-111">이 섹션에는 이러한 cmdlet에 대한 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af008-111">This section contains information about these cmdlets.</span></span>  
  
|<span data-ttu-id="af008-112">Description</span><span class="sxs-lookup"><span data-stu-id="af008-112">Description</span></span>|<span data-ttu-id="af008-113">cmdlet</span><span class="sxs-lookup"><span data-stu-id="af008-113">Cmdlet</span></span>|  
|-----------------|------------|  
|<span data-ttu-id="af008-114">`sqlcmd` 유틸리티를 사용하여 실행할 수 있는 Transact-SQL 스크립트 및 XQuery 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="af008-114">Runs Transact-SQL and XQuery scripts, such as scripts that can be run using the `sqlcmd` utility.</span></span>|[<span data-ttu-id="af008-115">Invoke-Sqlcmd cmdlet</span><span class="sxs-lookup"><span data-stu-id="af008-115">Invoke-Sqlcmd cmdlet</span></span>](../../2014/database-engine/invoke-sqlcmd-cmdlet.md)|  
|<span data-ttu-id="af008-116">데이터베이스 엔진 개체가 정책 기반 관리 정책을 준수하는지 여부를 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="af008-116">Evaluates whether a Database Engine object complies with a Policy-based Management policy.</span></span>|[<span data-ttu-id="af008-117">Invoke-PolicyEvaluation cmdlet</span><span class="sxs-lookup"><span data-stu-id="af008-117">Invoke-PolicyEvaluation cmdlet</span></span>](../../2014/database-engine/invoke-policyevaluation-cmdlet.md)|  
  
### <a name="information-about-other-cmdlets"></a><span data-ttu-id="af008-118">다른 cmdlet에 대한 정보</span><span class="sxs-lookup"><span data-stu-id="af008-118">Information About Other Cmdlets</span></span>  
 <span data-ttu-id="af008-119">`Encode-Sqlname` 및 `Decode-Sqlname` cmdlet을 사용하면 PowerShell 경로에서 지원되지 않는 문자가 포함된 SQL Server 식별자를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af008-119">The `Encode-Sqlname` and `Decode-Sqlname` cmdlets help you specify SQL Server identifiers that contain characters not supported in PowerShell paths.</span></span> <span data-ttu-id="af008-120">자세한 내용은 [SQL Server Identifiers in PowerShell](../powershell/sql-server-identifiers-in-powershell.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="af008-120">For more information, see [SQL Server Identifiers in PowerShell](../powershell/sql-server-identifiers-in-powershell.md).</span></span>  
  
 <span data-ttu-id="af008-121">`Convert-UrnToPath` cmdlet을 사용하면 [!INCLUDE[ssDE](../includes/ssde-md.md)] 개체의 URN을 SQL Server PowerShell 공급자의 경로로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af008-121">Use the `Convert-UrnToPath` cmdlet to convert a Unique Resource Name for a [!INCLUDE[ssDE](../includes/ssde-md.md)] object to a path for the SQL Server PowerShell provider.</span></span> <span data-ttu-id="af008-122">자세한 내용은 [Convert URNs to SQL Server Provider Paths](../../2014/database-engine/convert-urns-to-sql-server-provider-paths.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="af008-122">For more information, see [Convert URNs to SQL Server Provider Paths](../../2014/database-engine/convert-urns-to-sql-server-provider-paths.md).</span></span>  
  
## <a name="query-expressions-and-unique-resource-names"></a><span data-ttu-id="af008-123">쿼리 식 및 Unique Resource Names</span><span class="sxs-lookup"><span data-stu-id="af008-123">Query Expressions and Unique Resource Names</span></span>  
 <span data-ttu-id="af008-124">쿼리 식은 개체 모델 계층 구조에 있는 하나 이상의 개체를 열거하는 조건 집합을 지정하기 위해 XPath와 유사한 구문을 사용하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="af008-124">Query expressions are strings that use syntax similar to XPath to specify a set of criteria that enumerate one or more objects in an object model hierarchy.</span></span> <span data-ttu-id="af008-125">URN(Unique Resource Name)은 단일 개체를 고유하게 식별하는 특정 유형의 쿼리 식 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="af008-125">A Unique Resource Name (URN) is a specific type of query expression string that uniquely identifies a single object.</span></span> <span data-ttu-id="af008-126">자세한 내용은 [Query Expressions and Uniform Resource Names](../powershell/query-expressions-and-uniform-resource-names.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="af008-126">For more information, see [Query Expressions and Uniform Resource Names](../powershell/query-expressions-and-uniform-resource-names.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af008-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="af008-127">See Also</span></span>  
 [<span data-ttu-id="af008-128">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="af008-128">SQL Server PowerShell</span></span>](../powershell/sql-server-powershell.md)  
  
  
