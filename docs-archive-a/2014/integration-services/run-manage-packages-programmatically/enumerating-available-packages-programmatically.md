---
title: 프로그래밍 방식으로 사용 가능 패키지 열거 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- programmatically enumerate packages [SSIS]
- existence testing [Integration Services]
- enumerating packages [Integration Services]
ms.assetid: 254ec7ee-d3ff-4361-8995-46e9b9c4dc95
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 053f2e598b1cc18e68ee2182092188367ee7f10c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729556"
---
# <a name="enumerating-available-packages-programmatically"></a><span data-ttu-id="a2e4a-102">프로그래밍 방식으로 사용 가능 패키지 열거</span><span class="sxs-lookup"><span data-stu-id="a2e4a-102">Enumerating Available Packages Programmatically</span></span>
  <span data-ttu-id="a2e4a-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 프로그래밍 방식으로 사용할 때 개별 패키지 또는 폴더가 있는 여부를 확인하거나 로드 및 실행할 수 있는 저장된 패키지를 열거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2e4a-103">As you work programmatically with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, you may want to determine whether an individual package or folder exists, or to enumerate the saved packages that are available to load and execute.</span></span> <span data-ttu-id="a2e4a-104"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 네임스페이스의 <xref:Microsoft.SqlServer.Dts.Runtime> 클래스는 이 요구 사항을 충족하기 위한 다양한 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a2e4a-104">The <xref:Microsoft.SqlServer.Dts.Runtime.Application> class of the <xref:Microsoft.SqlServer.Dts.Runtime> namespace provides a variety of methods to satisfy these requirements.</span></span>  
  
##  <a name="determining-whether-a-package-or-folder-exists"></a><a name="exists"></a> <span data-ttu-id="a2e4a-105">패키지 또는 폴더가 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="a2e4a-105">Determining Whether a Package or Folder Exists</span></span>  
 <span data-ttu-id="a2e4a-106">저장된 패키지가 있는지 여부를 프로그래밍 방식으로 확인하려면 해당 패키지를 로드 및 실행하기 전에 다음 메서드 중 하나를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="a2e4a-106">To determine programmatically whether a saved package exists, call one of the following methods before attempting to load and run it:</span></span>  
  
|<span data-ttu-id="a2e4a-107">스토리지 위치</span><span class="sxs-lookup"><span data-stu-id="a2e4a-107">Storage Location</span></span>|<span data-ttu-id="a2e4a-108">호출할 메서드</span><span class="sxs-lookup"><span data-stu-id="a2e4a-108">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="a2e4a-109">SSIS 패키지 저장소</span><span class="sxs-lookup"><span data-stu-id="a2e4a-109">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnSqlServer%2A>|  
  
 <span data-ttu-id="a2e4a-110">폴더가 있는지 여부를 프로그래밍 방식으로 확인하려면 해당 폴더에 저장된 패키지를 나열하기 전에 다음 메서드 중 하나를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="a2e4a-110">To determine programmatically whether a folder exists before attempting to list the packages stored in it, call one of the following methods:</span></span>  
  
|<span data-ttu-id="a2e4a-111">스토리지 위치</span><span class="sxs-lookup"><span data-stu-id="a2e4a-111">Storage Location</span></span>|<span data-ttu-id="a2e4a-112">호출할 메서드</span><span class="sxs-lookup"><span data-stu-id="a2e4a-112">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="a2e4a-113">SSIS 패키지 저장소</span><span class="sxs-lookup"><span data-stu-id="a2e4a-113">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnSqlServer%2A>|  
  
 [<span data-ttu-id="a2e4a-114">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="a2e4a-114">Back to top</span></span>](#top)  
  
##  <a name="enumerating-available-packages"></a><a name="listing"></a> <span data-ttu-id="a2e4a-115">사용 가능한 패키지 열거</span><span class="sxs-lookup"><span data-stu-id="a2e4a-115">Enumerating Available Packages</span></span>  
 <span data-ttu-id="a2e4a-116">저장된 패키지 목록을 프로그래밍 방식으로 가져오려면 다음 메서드 중 하나를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="a2e4a-116">To obtain a list of saved packages programmatically, call one of the following methods:</span></span>  
  
|<span data-ttu-id="a2e4a-117">스토리지 위치</span><span class="sxs-lookup"><span data-stu-id="a2e4a-117">Storage Location</span></span>|<span data-ttu-id="a2e4a-118">호출할 메서드</span><span class="sxs-lookup"><span data-stu-id="a2e4a-118">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="a2e4a-119">SSIS 패키지 저장소</span><span class="sxs-lookup"><span data-stu-id="a2e4a-119">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerPackageInfos%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageInfos%2A>|  
  
 <span data-ttu-id="a2e4a-120">다음 예제는 이러한 메서드의 사용 방법을 보여 주는 콘솔 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="a2e4a-120">The following samples are console applications that demonstrate the use of these methods.</span></span>  
  
###  <a name="example-ssis-package-store"></a><a name="listing_store"></a> <span data-ttu-id="a2e4a-121">예(SSIS 패키지 저장소)</span><span class="sxs-lookup"><span data-stu-id="a2e4a-121">Example (SSIS Package Store)</span></span>  
 <span data-ttu-id="a2e4a-122"><xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerPackageInfos%2A> 메서드를 사용하면 SSIS 패키지 저장소에 저장된 패키지를 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2e4a-122">Use the <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerPackageInfos%2A> method to list packages stored in the SSIS Package Store.</span></span> <span data-ttu-id="a2e4a-123">SSIS 패키지 저장소에서 관리하는 기본 스토리지 위치는 파일 시스템과 MSDB입니다.</span><span class="sxs-lookup"><span data-stu-id="a2e4a-123">The default storage locations that are managed by the SSIS Package store are File System and MSDB.</span></span> <span data-ttu-id="a2e4a-124">이러한 위치에 논리적 폴더를 추가로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2e4a-124">You can create additional logical folders within these locations.</span></span>  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim sqlFolder As String  
    Dim sqlServer As String  
  
    Dim ssisApplication As Application  
    Dim sqlPackages As PackageInfos  
    Dim sqlPackage As PackageInfo  
  
    sqlServer = "."  
  
    ssisApplication = New Application()  
  
    ' Get packages stored in MSDB.  
    sqlFolder = "MSDB"  
    sqlPackages = ssisApplication.GetDtsServerPackageInfos(sqlFolder, sqlServer)  
    If sqlPackages.Count > 0 Then  
      Console.WriteLine("Packages stored in MSDB:")  
      For Each sqlPackage In sqlPackages  
        Console.WriteLine(sqlPackage.Name)  
      Next  
      Console.WriteLine()  
    End If  
  
    ' Get packages stored in the File System.  
    sqlFolder = "File System"  
    sqlPackages = ssisApplication.GetDtsServerPackageInfos(sqlFolder, sqlServer)  
    If sqlPackages.Count > 0 Then  
      Console.WriteLine("Packages stored in the File System:")  
      For Each sqlPackage In sqlPackages  
        Console.WriteLine(sqlPackage.Name)  
      Next  
    End If  
  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace EnumeratePackagesSSIS_CS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
  
      string sqlFolder;  
      string sqlServer;  
  
      Application ssisApplication;  
      PackageInfos sqlPackages;  
  
      sqlServer = ".";  
  
      ssisApplication = new Application();  
  
      // Get packages stored in MSDB.  
      sqlFolder = "MSDB";  
      sqlPackages = ssisApplication.GetDtsServerPackageInfos(sqlFolder, sqlServer);  
      if (sqlPackages.Count > 0)  
      {  
        Console.WriteLine("Packages stored in MSDB:");  
        foreach (PackageInfo sqlPackage in sqlPackages)  
        {  
          Console.WriteLine(sqlPackage.Name);  
        }  
        Console.WriteLine();  
      }  
  
      // Get packages stored in the File System.  
      sqlFolder = "File System";  
      sqlPackages = ssisApplication.GetDtsServerPackageInfos(sqlFolder, sqlServer);  
      if (sqlPackages.Count > 0)  
      {  
        Console.WriteLine("Packages stored in the File System:");  
        foreach (PackageInfo sqlPackage in sqlPackages)  
        {  
          Console.WriteLine(sqlPackage.Name);  
        }  
      }  
  
      Console.Read();  
  
    }  
  
  }  
  
}  
```  
  
 [<span data-ttu-id="a2e4a-125">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="a2e4a-125">Back to top</span></span>](#top)  
  
###  <a name="example-sql-server"></a><a name="listing_sql"></a> <span data-ttu-id="a2e4a-126">예(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a2e4a-126">Example (SQL Server)</span></span>  
 <span data-ttu-id="a2e4a-127"><xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageInfos%2A> 메서드를 사용하면 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]의 인스턴스에 저장된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 패키지를 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2e4a-127">Use the <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageInfos%2A> method to list [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages that are stored in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim sqlFolder As String  
    Dim sqlServer As String  
    Dim sqlUser As String  
    Dim sqlPassword As String  
  
    Dim ssisApplication As Application  
    Dim sqlPackages As PackageInfos  
    Dim sqlPackage As PackageInfo  
  
    sqlFolder = String.Empty  
    sqlServer = "(local)"  
    sqlUser = String.Empty  
    sqlPassword = String.Empty  
  
    ssisApplication = New Application()  
  
    sqlPackages = ssisApplication.GetPackageInfos(sqlFolder, sqlServer, sqlUser, sqlPassword)  
  
    For Each sqlPackage In sqlPackages  
      Console.WriteLine(sqlPackage.Name)  
    Next  
  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace EnumeratePackagesSql_CS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
  
      string sqlFolder;  
      string sqlServer;  
      string sqlUser;  
      string sqlPassword;  
  
      Application ssisApplication;  
      PackageInfos sqlPackages;  
  
      sqlFolder = String.Empty;  
      sqlServer = "(local)";  
      sqlUser = String.Empty;  
      sqlPassword = String.Empty;  
  
      ssisApplication = new Application();  
  
      sqlPackages = ssisApplication.GetPackageInfos(sqlFolder, sqlServer, sqlUser, sqlPassword);  
  
      foreach (PackageInfo sqlPackage in sqlPackages)  
      {  
        Console.WriteLine(sqlPackage.Name);  
      }  
  
      Console.Read();  
  
    }  
  }  
}  
```  
  
 [<span data-ttu-id="a2e4a-128">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="a2e4a-128">Back to top</span></span>](#top)  
  
<span data-ttu-id="a2e4a-129">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="a2e4a-129">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="a2e4a-130">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="a2e4a-130">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="a2e4a-131">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="a2e4a-131">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="a2e4a-132">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="a2e4a-132">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2e4a-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a2e4a-133">See Also</span></span>  
 [<span data-ttu-id="a2e4a-134">패키지 관리&#40;SSIS 서비스&#41;</span><span class="sxs-lookup"><span data-stu-id="a2e4a-134">Package Management &#40;SSIS Service&#41;</span></span>](../service/package-management-ssis-service.md)  
  
  
