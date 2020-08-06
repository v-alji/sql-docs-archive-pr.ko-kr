---
title: SQL Server PowerShell 공급자에 인스턴스 지정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 9373de68-fd43-45f2-b9a6-149c96610aeb
author: stevestein
ms.author: sstein
ms.openlocfilehash: cc04bacc1ff36b0b5ce526a377fcdb750ad134a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650139"
---
# <a name="specify-instances-in-the-sql-server-powershell-provider"></a><span data-ttu-id="db91b-102">SQL Server PowerShell 공급자에 인스턴스 지정</span><span class="sxs-lookup"><span data-stu-id="db91b-102">Specify Instances in the SQL Server PowerShell Provider</span></span>
  <span data-ttu-id="db91b-103">SQL Server PowerShell 공급자에 대해 지정되는 경로는 [!INCLUDE[ssDE](../includes/ssde-md.md)] 의 인스턴스와 해당 인스턴스가 실행 중인 컴퓨터를 식별해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db91b-103">The paths specified for the SQL Server PowerShell provider must identify the instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)] and the computer it is running on.</span></span> <span data-ttu-id="db91b-104">컴퓨터와 인스턴스를 지정하는 구문은 SQL Server 식별자 규칙과 Windows PowerShell 경로 규칙을 모두 준수해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db91b-104">The syntax for specifying the computer and the instance must comply with both the rules for SQL Server identifiers and Windows PowerShell paths.</span></span>  
  
1.  <span data-ttu-id="db91b-105">**시작하기 전에:**  [제한 사항](#LimitationsRestrictions)</span><span class="sxs-lookup"><span data-stu-id="db91b-105">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions)</span></span>  
  
2.  <span data-ttu-id="db91b-106">**인스턴스를 지정하려면**  [예](#Examples)</span><span class="sxs-lookup"><span data-stu-id="db91b-106">**To specify an instance:**  [Examples](#Examples)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="db91b-107">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="db91b-107">Before You Begin</span></span>  
 <span data-ttu-id="db91b-108">SQL Server 공급자 경로에서 SQLSERVER:\SQL 다음에 오는 첫 번째 노드는 [!INCLUDE[ssDE](../includes/ssde-md.md)]인스턴스를 실행하는 컴퓨터 이름입니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="db91b-108">The first node following the SQLSERVER:\SQL in a SQL Server provider path is the name of the computer that is running the instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)]; for example:</span></span>  
  
```  
SQLSERVER:\SQL\MyComputer  
```  
  
 <span data-ttu-id="db91b-109">[!INCLUDE[ssDE](../includes/ssde-md.md)]인스턴스와 동일한 컴퓨터에 Windows PowerShell을 실행하는 경우 컴퓨터 이름 대신 localhost 또는 (local)을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db91b-109">If you are running Windows PowerShell on the same computer as the instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)], you can use either localhost or (local) instead of the name of the computer.</span></span> <span data-ttu-id="db91b-110">localhost 또는 (로컬)을 사용하는 스크립트는 다른 컴퓨터 이름을 반영하도록 변경하지 않고도 모든 컴퓨터에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db91b-110">Scripts that use localhost or (local) can be run on any computer without having to be changed to reflect the different computer names.</span></span>  
  
 <span data-ttu-id="db91b-111">[!INCLUDE[ssDE](../includes/ssde-md.md)] 실행 프로그램의 여러 인스턴스를 동일한 컴퓨터에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db91b-111">You can run multiple instances of the [!INCLUDE[ssDE](../includes/ssde-md.md)] executable program on the same computer.</span></span> <span data-ttu-id="db91b-112">SQL Server 공급자 경로에서 컴퓨터 이름 다음에 오는 노드는 인스턴스를 식별합니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="db91b-112">The node following the computer name in a SQL Server provider path identifies the instance; for example:</span></span>  
  
```  
SQLSERVER:\SQL\MyComputer\MyInstance  
```  
  
 <span data-ttu-id="db91b-113">각 컴퓨터는 기본 [!INCLUDE[ssDE](../includes/ssde-md.md)]인스턴스를 한 개 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db91b-113">Each computer can have one default instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="db91b-114">기본 인스턴스는 설치할 때 이름을 지정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="db91b-114">You do not specify a name for the default instance when you install it.</span></span> <span data-ttu-id="db91b-115">연결 문자열에 컴퓨터 이름만 지정하면 해당 컴퓨터의 기본 인스턴스로 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="db91b-115">If you specify only a computer name in a connection string, you are connected to the default instance on that computer.</span></span> <span data-ttu-id="db91b-116">컴퓨터의 다른 모든 인스턴스는 명명된 인스턴스여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db91b-116">All other instances on the computer must be named instances.</span></span> <span data-ttu-id="db91b-117">인스턴스 이름은 설치 시 지정하고, 연결 문자열에는 컴퓨터 이름과 인스턴스 이름을 모두 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db91b-117">You specify the instance name during setup, and connection strings must specify both the computer name and the instance name.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="db91b-118">제한 사항</span><span class="sxs-lookup"><span data-stu-id="db91b-118">Limitations and Restrictions</span></span>  
 <span data-ttu-id="db91b-119">PowerShell 스크립트에서 마침표(.)를 사용하여 로컬 컴퓨터를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db91b-119">You cannot use a period (.) to specify the local computer in PowerShell scripts.</span></span> <span data-ttu-id="db91b-120">마침표는 PowerShell에서 명령으로 해석되기 때문에 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db91b-120">The period is not supported because the period is interpreted as a command by PowerShell.</span></span>  
  
 <span data-ttu-id="db91b-121">(local)의 괄호 문자는 일반적으로 Windows PowerShell에서 명령으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="db91b-121">The parenthesis characters in (local) are normally treated as commands by Windows PowerShell.</span></span> <span data-ttu-id="db91b-122">따라서 경로에 사용할 수 있도록 괄호 문자를 인코딩 또는 이스케이프하거나, 경로를 큰따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db91b-122">You must either encode them or escape them for use in a path, or enclose the path in double-quotation marks.</span></span> <span data-ttu-id="db91b-123">자세한 내용은 SQL Server 식별자 인코딩 및 디코딩을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="db91b-123">For more information, see Encode and Decode SQL Server Identifiers.</span></span>  
  
 <span data-ttu-id="db91b-124">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 공급자는 항상 인스턴스 이름을 지정하도록 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="db91b-124">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider requires that you always specify an instance name.</span></span> <span data-ttu-id="db91b-125">기본 인스턴스의 인스턴스 이름은 DEFAULT로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db91b-125">For default instances, you must specify an instance name of DEFAULT.</span></span>  
  
##  <a name="examples-computer-and-instance-names"></a><a name="Examples"></a><span data-ttu-id="db91b-126">예와 컴퓨터 및 인스턴스 이름</span><span class="sxs-lookup"><span data-stu-id="db91b-126">Examples; Computer and Instance Names</span></span>  
 <span data-ttu-id="db91b-127">이 예에서는 localhost 및 DEFAULT를 사용하여 로컬 컴퓨터의 기본 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db91b-127">This example uses localhost and DEFAULT to specify the default instance on the local computer:</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT
```  
  
 <span data-ttu-id="db91b-128">(local)의 괄호 문자는 일반적으로 Windows PowerShell에서 명령으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="db91b-128">The parenthesis characters in (local) are normally treated as commands by Windows PowerShell.</span></span> <span data-ttu-id="db91b-129">다음 중 하나를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db91b-129">You must either:</span></span>  
  
-   <span data-ttu-id="db91b-130">경로 문자열을 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="db91b-130">Enclose the path string in quotes:</span></span>  
  
    ```powershell
    Set-Location "SQLSERVER:\SQL\(local)\DEFAULT"  
    ```  
  
-   <span data-ttu-id="db91b-131">역따옴표 문자(\`)를 사용하여 괄호를 이스케이프 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="db91b-131">Escape the parenthesis using the back tick character (\`):</span></span>  
  
    ```powershell
    Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
    ```  
  
-   <span data-ttu-id="db91b-132">16진수 표현을 사용하여 괄호를 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="db91b-132">Encode the parenthesis using their hexadecimal representation:</span></span>  
  
    ```powershell
    Set-Location SQLSERVER:\SQL\%28local%29\DEFAULT  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="db91b-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="db91b-133">See Also</span></span>  
 <span data-ttu-id="db91b-134">[PowerShell에서 SQL Server 식별자](sql-server-identifiers-in-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="db91b-134">[SQL Server Identifiers in PowerShell](sql-server-identifiers-in-powershell.md) </span></span>  
 <span data-ttu-id="db91b-135">[SQL Server PowerShell 공급자](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="db91b-135">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="db91b-136">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="db91b-136">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
