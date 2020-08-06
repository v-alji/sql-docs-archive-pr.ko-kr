---
title: 데이터베이스 엔진 PowerShell에서 인증 관리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: ab9212a6-6628-4f08-a38c-d3156e05ddea
author: stevestein
ms.author: sstein
ms.openlocfilehash: 018a2698a43148af971622f54c8418bf23c2c781
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729547"
---
# <a name="manage-authentication-in-database-engine-powershell"></a><span data-ttu-id="9408d-102">데이터베이스 엔진 PowerShell에서 인증 관리</span><span class="sxs-lookup"><span data-stu-id="9408d-102">Manage Authentication in Database Engine PowerShell</span></span>
  <span data-ttu-id="9408d-103">기본적으로 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 구성 요소는 Windows 인증을 사용하여 [!INCLUDE[ssDE](../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9408d-103">By default, the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell components use Windows Authentication when connecting to an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="9408d-104">PowerShell 가상 드라이브를 정의하거나 `-Username`에 대한 `-Password` 및 `Invoke-Sqlcmd` 매개 변수를 지정하여 SQL Server 인증을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9408d-104">You can use SQL Server Authentication by either defining a PowerShell virtual drive, or by specifying the `-Username` and `-Password` parameters for `Invoke-Sqlcmd`.</span></span>  
  
1.  <span data-ttu-id="9408d-105">**시작하기 전 주의 사항:**  [사용 권한](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="9408d-105">**Before you begin:**  [Permissions](#Permissions)</span></span>  
  
2.  <span data-ttu-id="9408d-106">**To set authentication, using:**  [A Virtual Drive](#SQLAuthVirtDrv), [Invoke-Sqlcmd](#SQLAuthInvSqlCmd)</span><span class="sxs-lookup"><span data-stu-id="9408d-106">**To set authentication, using:**  [A Virtual Drive](#SQLAuthVirtDrv), [Invoke-Sqlcmd](#SQLAuthInvSqlCmd)</span></span>  
  
##  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9408d-107">권한</span><span class="sxs-lookup"><span data-stu-id="9408d-107">Permissions</span></span>  
 <span data-ttu-id="9408d-108">[!INCLUDE[ssDE](../includes/ssde-md.md)] 의 인스턴스에서 수행할 수 있는 모든 동작은 인스턴스에 연결하는 데 사용되는 인증 자격 증명에 부여된 사용 권한에 의해 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="9408d-108">All actions you can perform in an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)] are controlled by the permissions granted to the authentication credentials used to connect to the instance.</span></span> <span data-ttu-id="9408d-109">기본적으로 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 공급자 및 cmdlet은 [!INCLUDE[ssDE](../includes/ssde-md.md)]에 대한 Windows 인증 연결을 만들기 위해 실행하는 Windows 계정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9408d-109">By default, the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider and cmdlets use the Windows account under which it is running to make a Windows Authentication connection to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="9408d-110">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증 연결을 만들려면 SQL Server 인증 로그인 ID 및 암호를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9408d-110">To make a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication connection you must supply a SQL Server Authentication login ID and password.</span></span> <span data-ttu-id="9408d-111">공급자를 사용 하는 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 로그인 자격 증명을 가상 드라이브에 연결한 다음 디렉터리 변경 명령 ()을 사용 하 여 `cd` 해당 드라이브에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9408d-111">When using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider, you must associate the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login credentials with a virtual drive, and then use the change directory command (`cd`) to connect to that drive.</span></span> <span data-ttu-id="9408d-112">Windows PowerShell에서는 보안 자격 증명만 가상 드라이브에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9408d-112">In Windows PowerShell, security credentials can only be associated with virtual drives.</span></span>  
  
##  <a name="sql-server-authentication-using-a-virtual-drive"></a><a name="SQLAuthVirtDrv"></a> <span data-ttu-id="9408d-113">가상 드라이브를 통한 SQL Server 인증</span><span class="sxs-lookup"><span data-stu-id="9408d-113">SQL Server Authentication Using a Virtual Drive</span></span>  
 <span data-ttu-id="9408d-114">**SQL Server 인증 로그인과 연관된 가상 드라이브를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="9408d-114">**To create a virtual drive associated with a SQL Server Authentication login**</span></span>  
  
1.  <span data-ttu-id="9408d-115">다음 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9408d-115">Create a function that:</span></span>  
  
    1.  <span data-ttu-id="9408d-116">가상 드라이브에 제공할 이름, 로그인 ID 및 가상 드라이브에 연결할 공급자 경로에 대한 매개 변수를 포함하는 함수</span><span class="sxs-lookup"><span data-stu-id="9408d-116">Has parameters for the name to give the virtual drive, the login ID, and the provider path to associate with the virtual drive.</span></span>  
  
    2.  <span data-ttu-id="9408d-117">`read-host`를 사용하여 사용자에게 암호를 묻는 함수</span><span class="sxs-lookup"><span data-stu-id="9408d-117">Uses `read-host` to prompt the user for the password.</span></span>  
  
    3.  <span data-ttu-id="9408d-118">`new-object`를 사용하여 자격 증명 개체를 만드는 함수</span><span class="sxs-lookup"><span data-stu-id="9408d-118">Uses `new-object` to create a credentials object.</span></span>  
  
    4.  <span data-ttu-id="9408d-119">`new-psdrive`를 사용하여 제공된 자격 증명으로 가상 드라이브를 만드는 함수</span><span class="sxs-lookup"><span data-stu-id="9408d-119">Uses `new-psdrive` to create a virtual drive with the supplied credentials.</span></span>  
  
2.  <span data-ttu-id="9408d-120">함수를 호출하여 제공된 자격 증명으로 가상 드라이브를 만드는 함수</span><span class="sxs-lookup"><span data-stu-id="9408d-120">Invoke the function to create a virtual drive with the supplied credentials.</span></span>  
  
### <a name="example-virtual-drive"></a><span data-ttu-id="9408d-121">예제(가상 드라이브)</span><span class="sxs-lookup"><span data-stu-id="9408d-121">Example (Virtual Drive)</span></span>  
 <span data-ttu-id="9408d-122">이 예에서는 지정된 **인증 로그인 및 인스턴스에 연결된 가상 드라이브를 만드는 데 사용할 수 있는** sqldrive [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 라는 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9408d-122">This example creates a function named **sqldrive** that you can use to create a virtual drive that is associated with the specified [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication login and instance.</span></span>  
  
 <span data-ttu-id="9408d-123">**sqldrive** 함수는 로그인에 대한 암호를 입력하라는 메시지를 표시하고 사용자가 입력하는 암호를 마스킹합니다.</span><span class="sxs-lookup"><span data-stu-id="9408d-123">The **sqldrive** function prompts you to enter the password for your login, masking the password as you type it in.</span></span> <span data-ttu-id="9408d-124">그런 다음 디렉터리 변경 명령 ()을 사용 하 여 `cd` 가상 드라이브 이름을 사용 하 여 경로에 연결할 때마다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 드라이브를 만들 때 제공한 인증 로그인 자격 증명을 사용 하 여 모든 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9408d-124">Then, whenever you use the change directory command (`cd`) to connect to a path by using the virtual drive name, all operations are performed by using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication login credentials that you supplied when you created the drive.</span></span>  
  
```powershell
## Create a function that specifies the login and prompts for the password.  
  
function sqldrive  
{  
    param( [string]$name, [string]$login = "MyLogin", [string]$root = "SQLSERVER:\SQL\MyComputer\MyInstance" )  
    $pwd = Read-Host -AsSecureString -Prompt "Password"  
    $cred = New-Object System.Management.Automation.PSCredential -argumentlist $login, $pwd  
    New-PSDrive $name -PSProvider SqlServer -Root $root -Credential $cred -Scope 1  
}  
  
## Use the sqldrive function to create a SQLAuth virtual drive.  
sqldrive SQLAuth  
  
## CD to the virtual drive, which invokes the supplied authentication credentials.  
cd SQLAuth  
```  
  
##  <a name="sql-server-authentication-using-invoke-sqlcmd"></a><a name="SQLAuthInvSqlCmd"></a> <span data-ttu-id="9408d-125">Invoke-Sqlcmd를 통한 SQL Server 인증</span><span class="sxs-lookup"><span data-stu-id="9408d-125">SQL Server Authentication Using Invoke-Sqlcmd</span></span>  
 <span data-ttu-id="9408d-126">**Invoke-Sqlcmd를 사용하여 SQL Server를 인증하려면**</span><span class="sxs-lookup"><span data-stu-id="9408d-126">**To use Invoke-Sqlcmd with SQL Server Authentication**</span></span>  
  
1.  <span data-ttu-id="9408d-127">`-Username` 매개 변수를 사용하여 로그인 ID를 지정하고 `-Password` 매개 변수를 사용하여 연결된 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9408d-127">Use the `-Username` parameter to specify a login ID, and the `-Password` parameter to specify the associated password.</span></span>  
  
### <a name="example-invoke-sqlcmd"></a><span data-ttu-id="9408d-128">예제(Invoke-Sqlcmd)</span><span class="sxs-lookup"><span data-stu-id="9408d-128">Example (Invoke-Sqlcmd)</span></span>  
 <span data-ttu-id="9408d-129">이 예에서는 read-host cmdlet을 사용하여 사용자에게 암호를 물은 다음 SQL Server 인증을 사용하여 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9408d-129">This example uses the read-host cmdlet to prompt the user for a password, and then connects using SQL Server Authentication.</span></span>  
  
```powershell
## Prompt the user for their password.  
$pwd = Read-Host -AsSecureString -Prompt "Password"  
  
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance" -Username "MyLogin" -Password $pwd  
```  
  
## <a name="see-also"></a><span data-ttu-id="9408d-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9408d-130">See Also</span></span>  
 <span data-ttu-id="9408d-131">[SQL Server PowerShell](sql-server-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="9408d-131">[SQL Server PowerShell](sql-server-powershell.md) </span></span>  
 <span data-ttu-id="9408d-132">[SQL Server PowerShell 공급자](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="9408d-132">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="9408d-133">Invoke-Sqlcmd cmdlet</span><span class="sxs-lookup"><span data-stu-id="9408d-133">Invoke-Sqlcmd cmdlet</span></span>](../database-engine/invoke-sqlcmd-cmdlet.md)  
