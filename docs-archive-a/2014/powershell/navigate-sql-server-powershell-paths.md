---
title: SQL Server PowerShell 경로 탐색 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: d68aca48-d161-45ed-9f4f-14122ed30218
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0a605479991c3e907cd9dcae254cc1bc04a49392
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741099"
---
# <a name="navigate-sql-server-powershell-paths"></a><span data-ttu-id="2bc35-102">SQL Server PowerShell 경로 탐색</span><span class="sxs-lookup"><span data-stu-id="2bc35-102">Navigate SQL Server PowerShell Paths</span></span>
  <span data-ttu-id="2bc35-103">[!INCLUDE[ssDE](../includes/ssde-md.md)] PowerShell 공급자는 SQL Server 인스턴스의 개체를 파일 경로와 비슷한 구조로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-103">The [!INCLUDE[ssDE](../includes/ssde-md.md)] PowerShell provider exposes the set of objects in an instance of SQL Server in a structure similar to a file path.</span></span> <span data-ttu-id="2bc35-104">Windows PowerShell cmdlet을 사용하여 공급자 경로를 탐색하고 사용자 지정 드라이브를 만들어 입력해야 하는 경로를 단축할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-104">You can use Windows PowerShell cmdlets to navigate the provider path, and create custom drives to shorten the path you have to type.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="2bc35-105">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="2bc35-105">Before You Begin</span></span>  
 <span data-ttu-id="2bc35-106">Windows PowerShell은 cmdlet을 구현하여 PowerShell 공급자가 지원하는 개체의 계층 구조를 보여주는 경로 구조를 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-106">Windows PowerShell implements cmdlets to navigate the path structure that represent the hierarchy of objects supported by a PowerShell provider.</span></span> <span data-ttu-id="2bc35-107">경로의 노드를 탐색한 후 다른 cmdlet을 사용하여 현재 개체에 대한 기본 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-107">When you have navigated to a node in the path, you can use other cmdlets to perform basic operations on the current object.</span></span> <span data-ttu-id="2bc35-108">cmdlet은 자주 사용되므로 간단한 정규 별칭을 가지고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-108">Because the cmdlets are used frequently, they have short, canonical aliases.</span></span> <span data-ttu-id="2bc35-109">또한 cmdlet을 유사한 명령 프롬프트 명령에 매핑하는 별칭 집합과 UNIX 셸 명령에 대한 별칭 집합도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-109">There is also one set of aliases that maps the cmdlets to similar command prompt commands, and another set for UNIX shell commands.</span></span>  
  
 <span data-ttu-id="2bc35-110">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 공급자는 다음 테이블과 같이 공급자 cmdlet의 하위 집합을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-110">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider implements a subset of the provider cmdlets, shown in the following table.</span></span>  
  
|<span data-ttu-id="2bc35-111">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2bc35-111">cmdlet</span></span>|<span data-ttu-id="2bc35-112">정규 별칭</span><span class="sxs-lookup"><span data-stu-id="2bc35-112">Canonical alias</span></span>|<span data-ttu-id="2bc35-113">cmd 별칭</span><span class="sxs-lookup"><span data-stu-id="2bc35-113">cmd alias</span></span>|<span data-ttu-id="2bc35-114">UNIX 셸 별칭</span><span class="sxs-lookup"><span data-stu-id="2bc35-114">UNIX shell alias</span></span>|<span data-ttu-id="2bc35-115">설명</span><span class="sxs-lookup"><span data-stu-id="2bc35-115">Description</span></span>|  
|------------|---------------------|---------------|----------------------|-----------------|  
|<span data-ttu-id="2bc35-116">**Get-Location**</span><span class="sxs-lookup"><span data-stu-id="2bc35-116">**Get-Location**</span></span>|<span data-ttu-id="2bc35-117">**gl**</span><span class="sxs-lookup"><span data-stu-id="2bc35-117">**gl**</span></span>|<span data-ttu-id="2bc35-118">**pwd**</span><span class="sxs-lookup"><span data-stu-id="2bc35-118">**pwd**</span></span>|<span data-ttu-id="2bc35-119">**pwd**</span><span class="sxs-lookup"><span data-stu-id="2bc35-119">**pwd**</span></span>|<span data-ttu-id="2bc35-120">현재 노드를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-120">Gets the current node.</span></span>|  
|`Set-Location`|<span data-ttu-id="2bc35-121">**sl**</span><span class="sxs-lookup"><span data-stu-id="2bc35-121">**sl**</span></span>|<span data-ttu-id="2bc35-122">**cd, chdir**</span><span class="sxs-lookup"><span data-stu-id="2bc35-122">**cd, chdir**</span></span>|<span data-ttu-id="2bc35-123">**cd, chdir**</span><span class="sxs-lookup"><span data-stu-id="2bc35-123">**cd, chdir**</span></span>|<span data-ttu-id="2bc35-124">현재 노드를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-124">Changes the current node.</span></span>|  
|<span data-ttu-id="2bc35-125">**Get-ChildItem**</span><span class="sxs-lookup"><span data-stu-id="2bc35-125">**Get-ChildItem**</span></span>|<span data-ttu-id="2bc35-126">**gci**</span><span class="sxs-lookup"><span data-stu-id="2bc35-126">**gci**</span></span>|<span data-ttu-id="2bc35-127">**dir**</span><span class="sxs-lookup"><span data-stu-id="2bc35-127">**dir**</span></span>|<span data-ttu-id="2bc35-128">**l**</span><span class="sxs-lookup"><span data-stu-id="2bc35-128">**ls**</span></span>|<span data-ttu-id="2bc35-129">현재 노드에 저장된 개체를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-129">Lists the objects stored at the current node.</span></span>|  
|<span data-ttu-id="2bc35-130">**Get-Item**</span><span class="sxs-lookup"><span data-stu-id="2bc35-130">**Get-Item**</span></span>|<span data-ttu-id="2bc35-131">**gi**</span><span class="sxs-lookup"><span data-stu-id="2bc35-131">**gi**</span></span>|||<span data-ttu-id="2bc35-132">현재 항목의 속성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-132">Returns the properties of the current item.</span></span>|  
|<span data-ttu-id="2bc35-133">**Rename-Item**</span><span class="sxs-lookup"><span data-stu-id="2bc35-133">**Rename-Item**</span></span>|<span data-ttu-id="2bc35-134">**rni**</span><span class="sxs-lookup"><span data-stu-id="2bc35-134">**rni**</span></span>|<span data-ttu-id="2bc35-135">**수락**</span><span class="sxs-lookup"><span data-stu-id="2bc35-135">**rn**</span></span>|<span data-ttu-id="2bc35-136">**ren**</span><span class="sxs-lookup"><span data-stu-id="2bc35-136">**ren**</span></span>|<span data-ttu-id="2bc35-137">개체 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-137">Renames an object.</span></span>|  
|<span data-ttu-id="2bc35-138">**Remove-Item**</span><span class="sxs-lookup"><span data-stu-id="2bc35-138">**Remove-Item**</span></span>|<span data-ttu-id="2bc35-139">**ri**</span><span class="sxs-lookup"><span data-stu-id="2bc35-139">**ri**</span></span>|<span data-ttu-id="2bc35-140">**del, rd**</span><span class="sxs-lookup"><span data-stu-id="2bc35-140">**del, rd**</span></span>|<span data-ttu-id="2bc35-141">**rm, rmdir**</span><span class="sxs-lookup"><span data-stu-id="2bc35-141">**rm, rmdir**</span></span>|<span data-ttu-id="2bc35-142">개체를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-142">Removes an object.</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2bc35-143">일부 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 식별자(개체 이름)의 경우 Windows PowerShell에서 지원하지 않는 문자가 경로 이름에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-143">Some [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifiers (object names) contain characters that Windows PowerShell does not support in path names.</span></span> <span data-ttu-id="2bc35-144">이러한 문자가 포함된 이름을 사용하는 방법은 [SQL Server Identifiers in PowerShell](sql-server-identifiers-in-powershell.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2bc35-144">For more information about how to use names that contain these characters, see [SQL Server Identifiers in PowerShell](sql-server-identifiers-in-powershell.md).</span></span>  
  
### <a name="sql-server-information-returned-by-get-childitem"></a><span data-ttu-id="2bc35-145">Get-ChildItem이 반환하는 SQL Server 정보</span><span class="sxs-lookup"><span data-stu-id="2bc35-145">SQL Server Information Returned by Get-ChildItem</span></span>  
 <span data-ttu-id="2bc35-146">**Get-ChildItem** 또는 **dir** 및 **ls** 별칭에서 반환하는 정보는 SQLSERVER: 경로에서의 현재 위치에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-146">The information returned by **Get-ChildItem** (or its **dir** and **ls** aliases) depends on your location in a SQLSERVER: path.</span></span>  
  
|<span data-ttu-id="2bc35-147">경로 위치</span><span class="sxs-lookup"><span data-stu-id="2bc35-147">Path location</span></span>|<span data-ttu-id="2bc35-148">Get-ChildItem 결과</span><span class="sxs-lookup"><span data-stu-id="2bc35-148">Get-ChildItem results</span></span>|  
|-------------------|----------------------------|  
|<span data-ttu-id="2bc35-149">SQLSERVER:\SQL</span><span class="sxs-lookup"><span data-stu-id="2bc35-149">SQLSERVER:\SQL</span></span>|<span data-ttu-id="2bc35-150">로컬 컴퓨터의 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-150">Returns the name of the local computer.</span></span> <span data-ttu-id="2bc35-151">SMO 또는 WMI를 사용하여 다른 컴퓨터에 있는 [!INCLUDE[ssDE](../includes/ssde-md.md)] 인스턴스에 연결한 경우에는 해당 컴퓨터도 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-151">If you have used the SMO or WMI to connect to instances of the [!INCLUDE[ssDE](../includes/ssde-md.md)] on other computers, those computers are also listed.</span></span>|  
|<span data-ttu-id="2bc35-152">SQLSERVER:\SQL\\*ComputerName*</span><span class="sxs-lookup"><span data-stu-id="2bc35-152">SQLSERVER:\SQL\\*ComputerName*</span></span>|<span data-ttu-id="2bc35-153">컴퓨터에 있는 [!INCLUDE[ssDE](../includes/ssde-md.md)] 인스턴스의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-153">The list of instances of the [!INCLUDE[ssDE](../includes/ssde-md.md)] on the computer.</span></span>|  
|<span data-ttu-id="2bc35-154">SQLSERVER: \ SQL \\ *ComputerName* \\ *InstanceName*</span><span class="sxs-lookup"><span data-stu-id="2bc35-154">SQLSERVER:\SQL\\*ComputerName*\\*InstanceName*</span></span>|<span data-ttu-id="2bc35-155">Endpoints, Certificates 및 Databases와 같은 인스턴스의 최상위 개체 유형 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-155">The list of top-level object types in the instance, such as Endpoints, Certificates, and Databases.</span></span>|  
|<span data-ttu-id="2bc35-156">Databases와 같은 개체 클래스 노드</span><span class="sxs-lookup"><span data-stu-id="2bc35-156">Object class node, such as Databases</span></span>|<span data-ttu-id="2bc35-157">데이터베이스(예: master, model, AdventureWorks20008R2) 목록과 같은 해당 유형의 개체 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-157">The list of objects of that type, such as the list of databases: master, model, AdventureWorks20008R2.</span></span>|  
|<span data-ttu-id="2bc35-158">AdventureWorks2012와 같은 개체 이름 노드</span><span class="sxs-lookup"><span data-stu-id="2bc35-158">Object name node, such as AdventureWorks2012</span></span>|<span data-ttu-id="2bc35-159">개체 내에 포함된 개체 유형 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-159">The list of object types contained within the object.</span></span> <span data-ttu-id="2bc35-160">예를 들어 데이터베이스는 테이블 및 뷰와 같은 개체 유형을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-160">For example, a database would list object types such as tables and views.</span></span>|  
  
 <span data-ttu-id="2bc35-161">기본적으로 **Get-ChildItem** 은 시스템 개체를 나열하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-161">By default, **Get-ChildItem** does not list any system objects.</span></span> <span data-ttu-id="2bc35-162">*Force* 매개 변수를 사용하여 **sys** 스키마의 개체와 같은 시스템 개체를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-162">Use the *Force* parameter to see system objects, such as the objects in the **sys** schema.</span></span>  
  
### <a name="custom-drives"></a><span data-ttu-id="2bc35-163">사용자 지정 드라이브</span><span class="sxs-lookup"><span data-stu-id="2bc35-163">Custom Drives</span></span>  
 <span data-ttu-id="2bc35-164">Windows PowerShell을 통해 사용자는 PowerShell 드라이브라고 하는 가상 드라이브를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-164">Windows PowerShell lets users define virtual drives, which are referred to as PowerShell drives.</span></span> <span data-ttu-id="2bc35-165">이러한 가상 드라이브는 경로 문의 시작 노드로 매핑되며</span><span class="sxs-lookup"><span data-stu-id="2bc35-165">These map over the starting nodes of a path statement.</span></span> <span data-ttu-id="2bc35-166">일반적으로 자주 형식화되는 경로를 줄이는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-166">They are typically used to shorten paths that are typed frequently.</span></span> <span data-ttu-id="2bc35-167">SQLSERVER: 경로가 길어지면 Windows PowerShell 창에서 공간을 차지하고 많은 텍스트를 입력해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-167">SQLSERVER: paths can get long, taking space in the Windows PowerShell window and requiring a lot of typing.</span></span> <span data-ttu-id="2bc35-168">특정 경로 노드에서 많은 작업을 수행하려는 경우 해당 노드에 매핑되는 사용자 지정 Windows PowerShell 드라이브를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-168">If you are going to do a lot of work at a particular path node, you can define a custom Windows PowerShell drive that maps to that node.</span></span>  
  
## <a name="use-powershell-cmdlet-aliases"></a><span data-ttu-id="2bc35-169">PowerShell cmdlet 별칭 사용</span><span class="sxs-lookup"><span data-stu-id="2bc35-169">Use PowerShell Cmdlet Aliases</span></span>  
 <span data-ttu-id="2bc35-170">**cmdlet 별칭 사용**</span><span class="sxs-lookup"><span data-stu-id="2bc35-170">**Use a cmdlet alias**</span></span>  
  
-   <span data-ttu-id="2bc35-171">전체 cmdlet 이름을 입력하는 대신 익숙한 명령 프롬프트 명령에 매핑되는 별칭이나 단축 별칭을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-171">Instead of typing a full cmdlet name, type a shorter alias, or one that maps to a familiar commend prompt command.</span></span>  
  
### <a name="alias-example-powershell"></a><span data-ttu-id="2bc35-172">별칭 예(PowerShell)</span><span class="sxs-lookup"><span data-stu-id="2bc35-172">Alias Example (PowerShell)</span></span>  
 <span data-ttu-id="2bc35-173">예를 들어 SQLSERVER:\SQL 폴더로 이동하고 해당 폴더의 자식 항목 목록을 요청하여 사용 가능한 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스 목록을 검색하려면 다음과 같은 cmdlet 또는 별칭의 집합 중 하나를 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-173">For example, you can use one of the following sets of cmdlets or aliases to retrieve a listing of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instances available to you by navigating to the SQLSERVER:\SQL folder and requesting the list of child items for the folder:</span></span>  
  
```powershell
## Shows using the full cmdet name.  
Set-Location SQLSERVER:\SQL  
Get-ChildItem  
  
## Shows using canonical aliases.  
sl SQLSERVER:\SQL  
gci  
  
## Shows using command prompt aliases.  
cd SQLSERVER:\SQL  
dir  
  
## Shows using Unix shell aliases.  
cd SQLSERVER:\SQL  
ls  
```  
  
## <a name="use-get-childitem"></a><span data-ttu-id="2bc35-174">Get-ChildItem 사용</span><span class="sxs-lookup"><span data-stu-id="2bc35-174">Use Get-ChildItem</span></span>  

### <a name="return-information-by-using-get-childitem"></a><span data-ttu-id="2bc35-175">Get-Childitem을 사용하여 정보 반환</span><span class="sxs-lookup"><span data-stu-id="2bc35-175">Return information by using Get-Childitem</span></span>
  
1.  <span data-ttu-id="2bc35-176">childrem의 목록을 원하는 노드로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-176">Navigate to the node for which you want a list of childrem</span></span>  
  
2.  <span data-ttu-id="2bc35-177">Get-childitem을 실행하여 목록 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-177">Run Get-Childitem to get the list.</span></span>  
  
### <a name="get-childitem-example-powershell"></a><span data-ttu-id="2bc35-178">Get-childitem 예(PowerShell)</span><span class="sxs-lookup"><span data-stu-id="2bc35-178">Get-ChildItem Example (PowerShell)</span></span>  
 <span data-ttu-id="2bc35-179">다음 예에서는 SQL Server 공급자 경로의 각 노드에 대해 Get-ChildItem이 반환하는 정보에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-179">These examples illustrate the information returned by Get-Childitem for different nodes in a SQL Server provider path.</span></span>  
  
```powershell
## Return the current computer and any computer  
## to which you have made a SQL or WMI connection.  
Set-Location SQLSERVER:\SQL  
Get-ChildItem  
  
## List the instances of the Database Engine on the local computer.  
Set-Location SQLSERVER:\SQL\localhost  
Get-ChildItem  
  
## Lists the categories of objects available in the  
## default instance on the local computer.  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT  
Get-ChildItem  
  
## Lists the databases from the local default instance.  
## The force parameter is used to include the system databases.  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases  
Get-ChildItem -force  
```  
  
## <a name="create-a-custom-drive"></a><span data-ttu-id="2bc35-180">사용자 지정 드라이브 만들기</span><span class="sxs-lookup"><span data-stu-id="2bc35-180">Create a Custom Drive</span></span>  

### <a name="create-and-use-a-custom-drive"></a><span data-ttu-id="2bc35-181">사용자 지정 드라이브 만들기 및 사용</span><span class="sxs-lookup"><span data-stu-id="2bc35-181">Create and use a custom drive</span></span>
  
1.  <span data-ttu-id="2bc35-182">`New-PSDrive`를 사용하여 사용자 지정 드라이브를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-182">Use `New-PSDrive` to define a custom drive.</span></span> <span data-ttu-id="2bc35-183">`Root` 매개 변수를 사용하여 사용자 지정 드라이브 이름에 표시되는 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-183">Use the `Root` parameter to specify the path that is represented by the custom drive name.</span></span>  
  
2.  <span data-ttu-id="2bc35-184">경로 탐색 cmdlet(예: `Set-Location`)에서 사용자 지정 드라이브 이름을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-184">Reference the custom drive name in path navigation cmdlets such as `Set-Location`.</span></span>  
  
### <a name="custom-drive-example-powershell"></a><span data-ttu-id="2bc35-185">사용자 지정 드라이브 예(PowerShell)</span><span class="sxs-lookup"><span data-stu-id="2bc35-185">Custom Drive Example (PowerShell)</span></span>  
 <span data-ttu-id="2bc35-186">이 예에서는 AdventureWorks2012 예제 데이터베이스의 배포된 복사본에 대해 노드에 매핑되는 AWDB라는 가상 드라이브를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-186">This example creates a virtual drive named AWDB that maps to the node for a deployed copy of the AdventureWorks2012 sample database.</span></span> <span data-ttu-id="2bc35-187">그런 다음 가상 드라이브를 사용하여 데이터베이스에서 테이블을 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="2bc35-187">The virtual drive is then used to navigate to a table in the database.</span></span>  
  
```powershell
## Create a new virtual drive.  
New-PSDrive -Name AWDB -Root SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012  
  
## Use AWDB: to navigate to a specific table.  
Set-Location AWDB:\Tables\Purchasing.Vendor  
```  
  
## <a name="see-also"></a><span data-ttu-id="2bc35-188">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2bc35-188">See Also</span></span>  
 <span data-ttu-id="2bc35-189">[SQL Server PowerShell 공급자](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="2bc35-189">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 <span data-ttu-id="2bc35-190">[SQL Server PowerShell 경로 작업](work-with-sql-server-powershell-paths.md) </span><span class="sxs-lookup"><span data-stu-id="2bc35-190">[Work With SQL Server PowerShell Paths](work-with-sql-server-powershell-paths.md) </span></span>  
 <span data-ttu-id="2bc35-191">[Urn를 SQL Server 공급자 경로로 변환](../database-engine/convert-urns-to-sql-server-provider-paths.md) </span><span class="sxs-lookup"><span data-stu-id="2bc35-191">[Convert URNs to SQL Server Provider Paths](../database-engine/convert-urns-to-sql-server-provider-paths.md) </span></span>  
 [<span data-ttu-id="2bc35-192">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="2bc35-192">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
