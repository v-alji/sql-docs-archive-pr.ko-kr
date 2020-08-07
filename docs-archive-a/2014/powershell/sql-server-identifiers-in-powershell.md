---
title: PowerShell의 SQL Server 식별자 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
helpviewer_keywords:
- Cmdlets [SQL Server], Encode-Sqlname
- PowerShell [SQL Server], identifiers
- Encode-Sqlname cmdlet
- PowerShell [SQL Server], Encode-Sqlname
- Decode-Sqlname cmdlet
- PowerShell [SQL Server], Decode-Sqlname
- identifiers [SQL Server], PowerShell
- Cmdlets [SQL Server], Decode-Sqlname
ms.assetid: 651099b0-33b4-453a-a864-b067f21eb8b9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5c54fb352fb17c099bda78c80f00f91dbba428f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730767"
---
# <a name="sql-server-identifiers-in-powershell"></a><span data-ttu-id="83b72-102">PowerShell의 SQL Server 식별자</span><span class="sxs-lookup"><span data-stu-id="83b72-102">SQL Server Identifiers in PowerShell</span></span>
  <span data-ttu-id="83b72-103">Windows PowerShell의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 공급자는 Windows PowerShell 경로에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 식별자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="83b72-103">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider for Windows PowerShell uses [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifiers in Windows PowerShell paths.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="83b72-104">식별자는 Windows PowerShell이 경로에서 지원하지 않는 문자를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83b72-104">identifiers can contain characters that Windows PowerShell does not support in paths.</span></span> <span data-ttu-id="83b72-105">Windows PowerShell 경로에서 식별자를 사용할 때는 이러한 문자를 이스케이프 처리하거나 특수 인코딩을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83b72-105">You must escape these characters or use special encoding for them when using the identifiers in Windows PowerShell paths.</span></span>  
  
## <a name="sql-server-identifiers-in-windows-powershell-paths"></a><span data-ttu-id="83b72-106">Windows PowerShell 경로의 SQL Server 식별자</span><span class="sxs-lookup"><span data-stu-id="83b72-106">SQL Server Identifiers in Windows PowerShell Paths</span></span>  
 <span data-ttu-id="83b72-107">Windows PowerShell 공급자는 Windows 파일 시스템에 사용되는 것과 유사한 경로 구조를 사용하여 데이터 계층 구조를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="83b72-107">Windows PowerShell providers expose data hierarchies using a path structure similar to that used for the Windows file system.</span></span> <span data-ttu-id="83b72-108">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 공급자는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 개체에 대한 경로를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="83b72-108">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider implements paths to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects.</span></span> <span data-ttu-id="83b72-109">[!INCLUDE[ssDE](../includes/ssde-md.md)]의 경우 드라이브는 SQLSERVER:로 설정되고 첫 번째 폴더는 \SQL로 설정되며 데이터베이스 개체는 컨테이너 및 항목으로 참조됩니다.</span><span class="sxs-lookup"><span data-stu-id="83b72-109">For the [!INCLUDE[ssDE](../includes/ssde-md.md)], the drive is set to SQLSERVER:, the first folder is set to \SQL, and the database objects are referenced as containers and items.</span></span> <span data-ttu-id="83b72-110">다음은 기본 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 인스턴스에서 [!INCLUDE[ssDE](../includes/ssde-md.md)]데이터베이스의 Purchasing 스키마에 있는 Vendor 테이블에 대한 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="83b72-110">This is the path to the Vendor table in the Purchasing schema of the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database in a default instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)]:</span></span>  
  
```  
SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Purchasing.Vendor  
```  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="83b72-111">식별자는 테이블 또는 열 이름과 같은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 개체의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="83b72-111">identifiers are the names of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects, such as table or column names.</span></span> <span data-ttu-id="83b72-112">다음과 같이 두 가지 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 식별자 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83b72-112">There are two types of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifiers:</span></span>  
  
-   <span data-ttu-id="83b72-113">일반 식별자는 Windows PowerShell 경로에서도 지원되는 문자 집합으로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="83b72-113">Regular identifiers are limited to a set of characters that are also supported in Windows PowerShell paths.</span></span> <span data-ttu-id="83b72-114">이러한 이름은 변경하지 않고 Windows PowerShell 경로에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83b72-114">These names can be used in Windows PowerShell paths without being changed.</span></span>  
  
-   <span data-ttu-id="83b72-115">구분 식별자에는 Windows PowerShell 경로 이름에서 지원되지 않는 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83b72-115">Delimited identifiers can use characters not supported in Windows PowerShell path names.</span></span> <span data-ttu-id="83b72-116">구분 식별자가 대괄호로 묶이면(예: [IdentifierName]) 대괄호로 묶은 식별자라고 하고 큰따옴표로 묶이면(예: "IdentifierName") 따옴표 붙은 식별자라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="83b72-116">Delimited identifiers are called bracketed identifiers if they are enclosed in brackets ([IdentifierName]) and quoted identifiers if they are enclosed in double quotes ("IdentifierName").</span></span> <span data-ttu-id="83b72-117">구분 식별자가 Windows PowerShell 경로에 지원되지 않는 문자를 사용하는 경우 해당 식별자를 컨테이너 또는 항목 이름으로 사용하기 전에 문자를 인코딩하거나 이스케이프 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83b72-117">If a delimited identifier uses characters not supported in Windows PowerShell paths, the characters must either be encoded or escaped before using the identifier as a container or item name.</span></span> <span data-ttu-id="83b72-118">인코딩은 모든 문자에 대해 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="83b72-118">Encoding works for all characters.</span></span> <span data-ttu-id="83b72-119">콜론 문자(:)와 같은 일부 문자는 이스케이프 처리되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83b72-119">Some characters, such as the colon character (:), cannot be escaped.</span></span>  
  
## <a name="sql-server-identifiers-in-cmdlets"></a><span data-ttu-id="83b72-120">cmdlet의 SQL Server 식별자</span><span class="sxs-lookup"><span data-stu-id="83b72-120">SQL Server Identifiers in cmdlets</span></span>  
 <span data-ttu-id="83b72-121">일부 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlet에는 식별자를 입력으로 사용하는 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83b72-121">Some [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlets have a parameter that takes an identifier as input.</span></span> <span data-ttu-id="83b72-122">매개 변수 값은 일반적으로 따옴표가 붙은 문자열 상수나 문자열 변수로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="83b72-122">The parameter values are typically supplied as quoted string constants or in string variables.</span></span> <span data-ttu-id="83b72-123">식별자가 문자열 상수나 변수로 제공되면 Windows PowerShell에서 지원하는 문자 집합과 충돌하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83b72-123">When identifiers are supplied as string constants or in variables, there is no conflict with the set of characters that are supported by Windows PowerShell.</span></span>  
  
## <a name="sql-server-identifier-tasks"></a><span data-ttu-id="83b72-124">SQL Server 식별자 태스크</span><span class="sxs-lookup"><span data-stu-id="83b72-124">SQL Server Identifier Tasks</span></span>  
  
|<span data-ttu-id="83b72-125">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="83b72-125">Task Description</span></span>|<span data-ttu-id="83b72-126">항목</span><span class="sxs-lookup"><span data-stu-id="83b72-126">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="83b72-127">인스턴스가 실행 중인 컴퓨터 이름을 포함하여 인스턴스 이름을 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83b72-127">Describes how to specify an instance name, including the name of the computer the instance is running on.</span></span>|[<span data-ttu-id="83b72-128">SQL Server PowerShell 공급자에 인스턴스 지정</span><span class="sxs-lookup"><span data-stu-id="83b72-128">Specify Instances in the SQL Server PowerShell Provider</span></span>](sql-server-powershell-provider.md)|  
|<span data-ttu-id="83b72-129">Windows PowerShell 경로에서 지원되지 않는 구분 식별자의 문자에 대한 16진수 인코딩을 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83b72-129">Describes how to specify the hexadecimal encoding for characters in delimited identifiers that are not supported in Windows PowerShell paths.</span></span> <span data-ttu-id="83b72-130">또한 16진수 문자를 해독하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83b72-130">Also describes how to decode the hexadecimal characters.</span></span>|[<span data-ttu-id="83b72-131">SQL Server 식별자 인코딩 및 디코딩</span><span class="sxs-lookup"><span data-stu-id="83b72-131">Encode and Decode SQL Server Identifiers</span></span>](encode-and-decode-sql-server-identifiers.md)|  
|<span data-ttu-id="83b72-132">PowerShell 경로에서 지원되지 않는 문자에 대해 Windows PowerShell 이스케이프 문자를 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83b72-132">Describes how to use the Windows PowerShell escape character for characters not supported in PowerShell paths.</span></span>|[<span data-ttu-id="83b72-133">SQL Server 식별자 이스케이프</span><span class="sxs-lookup"><span data-stu-id="83b72-133">Escape SQL Server Identifiers</span></span>](escape-sql-server-identifiers.md)|  
  
## <a name="see-also"></a><span data-ttu-id="83b72-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="83b72-134">See Also</span></span>  
 <span data-ttu-id="83b72-135">[SQL Server PowerShell 공급자](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="83b72-135">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 <span data-ttu-id="83b72-136">[SQL Server PowerShell](sql-server-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="83b72-136">[SQL Server PowerShell](sql-server-powershell.md) </span></span>  
 [<span data-ttu-id="83b72-137">데이터베이스 식별자</span><span class="sxs-lookup"><span data-stu-id="83b72-137">Database Identifiers</span></span>](../relational-databases/databases/database-identifiers.md)  
  
  
