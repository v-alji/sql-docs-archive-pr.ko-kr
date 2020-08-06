---
title: URN을 SQL Server 공급자 경로로 변환 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c9b1b8f1-b117-4e87-9704-2170f62c5c8b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 56c2fdb5f84e57fe3f34348108f14418785659a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651263"
---
# <a name="convert-urns-to-sql-server-provider-paths"></a><span data-ttu-id="12755-102">URN을 SQL Server 공급자 경로로 변환</span><span class="sxs-lookup"><span data-stu-id="12755-102">Convert URNs to SQL Server Provider Paths</span></span>
  <span data-ttu-id="12755-103">SMO( [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Object) 모델은 개체의 URN(Uniform Resource Names)을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="12755-103">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Object model (SMO) builds Uniform Resource Names (URN) for its objects.</span></span> <span data-ttu-id="12755-104">각 URN은 SMO 개체를 고유하게 식별하며 `Convert-UrnToPath` cmdlet을 사용하여 SQL Server PowerShell 공급자 경로로 변환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12755-104">Each URN uniquely identifies a SMO object, and can be converted to a SQL Server PowerShell provider path by using the `Convert-UrnToPath` cmdlet.</span></span>  
  
## <a name="converting-urns-to-paths"></a><span data-ttu-id="12755-105">URN을 경로로 변환</span><span class="sxs-lookup"><span data-stu-id="12755-105">Converting URNs to Paths</span></span>  
 <span data-ttu-id="12755-106">각 URN에는 개체에 대한 경로와 동일한 정보가 다른 형식으로 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="12755-106">Each URN has the same information as a path to the object, but in a different form.</span></span> <span data-ttu-id="12755-107">예를 들어 테이블에 대한 경로는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="12755-107">For example, this is the path to a table:</span></span>  
  
 <span data-ttu-id="12755-108">SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Person.Address</span><span class="sxs-lookup"><span data-stu-id="12755-108">SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Person.Address</span></span>  
  
 <span data-ttu-id="12755-109">동일한 개체에 대한 URN은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="12755-109">And this is the URN to the same object:</span></span>  
  
 <span data-ttu-id="12755-110">Server[@Name='MyComputer']\Database[@Name='AdventureWorks2012']\Table[@Name='Address' and @Schema='Person']</span><span class="sxs-lookup"><span data-stu-id="12755-110">Server[@Name='MyComputer']\Database[@Name='AdventureWorks2012']\Table[@Name='Address' and @Schema='Person']</span></span>  
  
 <span data-ttu-id="12755-111">Windows PowerShell 스크립트로 SMO 개체를 만든 경우 `Urn` 속성을 참조하여 개체에 대한 URN을 가져온 다음 `Convert-UrnToPath` cmdlet을 사용하여 SMO URN 문자열을 Windows PowerShell 경로로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12755-111">If you have created a SMO object in a PowerShell script, you can reference the `Urn` property to get the URN for the object, and then use the `Convert-UrnToPath` cmdlet to convert the SMO URN string to a Windows PowerShell path.</span></span> <span data-ttu-id="12755-112">그런 다음 공급자를 사용하여 경로의 다른 위치를 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12755-112">You can then use the provider to navigate to different locations on the path.</span></span>  
  
 <span data-ttu-id="12755-113">노드 이름에 Windows PowerShell 경로 이름에서 지원되지 않는 확장 문자가 포함된 경우 `Convert-UrnToPath`는 이러한 문자를 해당 16진수 표현으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="12755-113">If node names contain extended characters that are not supported in Windows PowerShell path names, `Convert-UrnToPath` encodes them in their hexadecimal representation.</span></span> <span data-ttu-id="12755-114">예를 들어 "My:Table"은 "My%3ATable"로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="12755-114">For example "My:Table" is returned as "My%3ATable".</span></span>  
  
 <span data-ttu-id="12755-115">cmdlet 사용 예를 보려면 Windows PowerShell에서 다음을 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="12755-115">For examples of using the cmdlet, in Windows PowerShell, run:</span></span>  
  
```powershell
Get-Help Convert-UrnToPath -Examples  
```  
  
## <a name="see-also"></a><span data-ttu-id="12755-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="12755-116">See Also</span></span>  
 <span data-ttu-id="12755-117">[쿼리 식 및 Uniform Resource Name](../powershell/query-expressions-and-uniform-resource-names.md) </span><span class="sxs-lookup"><span data-stu-id="12755-117">[Query Expressions and Uniform Resource Names](../powershell/query-expressions-and-uniform-resource-names.md) </span></span>  
 <span data-ttu-id="12755-118">[SQL Server PowerShell 공급자](../powershell/sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="12755-118">[SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="12755-119">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="12755-119">SQL Server PowerShell</span></span>](../powershell/sql-server-powershell.md)  
