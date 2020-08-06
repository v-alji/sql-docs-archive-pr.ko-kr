---
title: Integration Services 서비스 구성 (SSIS 서비스) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, configuring
- configuration files [Integration Services]
- service [Integration Services], configuring
- default configuration files
ms.assetid: 36d78393-a54c-44b0-8709-7f003f44c27f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c70c41377a2c302e1a021c6ade2a9d487579fa64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738631"
---
# <a name="configuring-the-integration-services-service-ssis-service"></a><span data-ttu-id="5db66-102">Integration Services 서비스 구성(SSIS 서비스)</span><span class="sxs-lookup"><span data-stu-id="5db66-102">Configuring the Integration Services Service (SSIS Service)</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="5db66-103">이 항목에서는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 관리하는 Windows 서비스인 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] <span data-ttu-id="5db66-104">는 이전 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]버전과의 호환성을 위한 서비스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="5db66-105">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]부터는 Integration Services 서버의 패키지와 같은 개체를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 <span data-ttu-id="5db66-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스는 구성 파일을 사용하여 해당 설정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-106">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service relies on a configuration file for its settings.</span></span> <span data-ttu-id="5db66-107">기본적으로이 구성 파일의 이름은 MsDtsSrvr.ini.xml이 고 파일 은%ProgramFiles%\Microsoft SQL Server\120\dts\binn입니다. 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-107">By default, the name for this configuration file is MsDtsSrvr.ini.xml, and the file is located in the folder, %ProgramFiles%\Microsoft SQL Server\120\DTS\Binn.</span></span>  
  
 <span data-ttu-id="5db66-108">일반적으로 이 구성 파일이나 이 구성 파일의 위치는 변경하지 않아도 되지만</span><span class="sxs-lookup"><span data-stu-id="5db66-108">Typically, you do not have to make any changes to this configuration file, nor do you have to change the file's default location.</span></span> <span data-ttu-id="5db66-109">패키지가 명명된 인스턴스, [!INCLUDE[ssDE](../includes/ssde-md.md)]의 원격 인스턴스 또는 여러 [!INCLUDE[ssDE](../includes/ssde-md.md)]인스턴스에 저장되는 경우에는 이 구성 파일을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-109">However, you will have to modify the configuration file if your packages are stored in a named instance or a remote instance of [!INCLUDE[ssDE](../includes/ssde-md.md)], or in multiple instances of the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="5db66-110">또한 이 구성 파일을 기본 위치 이외의 다른 위치로 이동할 경우 파일 위치를 지정하는 레지스트리 키도 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-110">Also, if you move the configuration file to a location other than the default location, you will have to modify the Registry key that specifies the file location.</span></span>  
  
## <a name="configuration-file-contents"></a><span data-ttu-id="5db66-111">파일 내용 구성</span><span class="sxs-lookup"><span data-stu-id="5db66-111">Configuration File Contents</span></span>  
 <span data-ttu-id="5db66-112">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]를 설치할 때 설치 프로세스는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스에 대한 구성 파일을 만들고 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-112">When you install [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], the setup process creates and installs the configuration file for the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="5db66-113">이 구성 파일에는 다음과 같은 설정이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-113">This configuration file contains the following settings:</span></span>  
  
-   <span data-ttu-id="5db66-114">서비스가 중지되면 패키지에 중지 명령이 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-114">Packages are sent a stop command when the service stops.</span></span>  
  
-   <span data-ttu-id="5db66-115">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 의 개체 탐색기에서 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 에 대해 표시할 루트 폴더는 MSDB와 파일 시스템 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-115">The root folders to display for [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] in Object Explorer of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] are the MSDB and File System folders.</span></span>  
  
-   <span data-ttu-id="5db66-116">서비스에서 관리 하는 파일 시스템의 패키지는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] %PROGRAMFILES%\MICROSOFT SQL Server\120\DTS\Packages.에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-116">The packages in the file system that the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service manages are located in %ProgramFiles%\Microsoft SQL Server\120\DTS\Packages.</span></span>  
  
 <span data-ttu-id="5db66-117">이 구성 파일은 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스에서 관리할 패키지가 들어 있는 msdb 데이터베이스도 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-117">This configuration file also specifies which msdb database contains the packages that the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service will manage.</span></span> <span data-ttu-id="5db66-118">기본적으로 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스는 [!INCLUDE[ssDE](../includes/ssde-md.md)] 와 동시에 설치되는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]인스턴스의 msdb 데이터베이스에 있는 패키지를 관리하도록 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-118">By default, the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is configured to manage packages in the msdb database of the instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)] that is installed at the same time as [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="5db66-119">[!INCLUDE[ssDE](../includes/ssde-md.md)] 인스턴스가 동시에 설치되지 않는 경우 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스는 [!INCLUDE[ssDE](../includes/ssde-md.md)]의 로컬 기본 인스턴스에 있는 msdb 데이터베이스에 저장된 패키지를 관리하도록 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-119">If an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)] is not installed at the same time, the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is configured to manage packages in the msdb database of the local, default instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
### <a name="default-configuration-file-example"></a><span data-ttu-id="5db66-120">기본 구성 파일 예</span><span class="sxs-lookup"><span data-stu-id="5db66-120">Default Configuration File Example</span></span>  
 <span data-ttu-id="5db66-121">다음 예에서는 아래의 설정을 지정하는 기본 구성 파일을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-121">The following example shows a default configuration file that specifies the following settings:</span></span>  
  
-   <span data-ttu-id="5db66-122">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스가 중지되면 패키지 실행도 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-122">Packages stop running when the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service stops.</span></span>  
  
-   <span data-ttu-id="5db66-123">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 의 패키지 스토리지에 대한 루트 폴더는 MSDB와 파일 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-123">The root folders for package storage in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] are MSDB and File System.</span></span>  
  
-   <span data-ttu-id="5db66-124">서비스에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 로컬 기본 인스턴스에 있는 msdb 데이터베이스에 저장된 패키지를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-124">The service manages packages that are stored in the msdb database of the local, default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="5db66-125">서비스에서 파일 시스템의 패키지 폴더에 저장된 패키지를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-125">The service manages packages that are stored in the file system in the Packages folder.</span></span>  
  
 <span data-ttu-id="5db66-126">**기본 구성 파일의 예**</span><span class="sxs-lookup"><span data-stu-id="5db66-126">**Example of a Default Configuration File**</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<DtsServiceConfiguration xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <StopExecutingPackagesOnShutdown>true</StopExecutingPackagesOnShutdown>  
  <TopLevelFolders>  
    <Folder xsi:type="SqlServerFolder">  
      <Name>MSDB</Name>  
      <ServerName>.</ServerName>  
    </Folder>  
    <Folder xsi:type="FileSystemFolder">  
      <Name>File System</Name>  
      <StorePath>..\Packages</StorePath>  
    </Folder>  
  </TopLevelFolders>    
</DtsServiceConfiguration>  
```  
  
## <a name="modification-of-the-configuration-file"></a><span data-ttu-id="5db66-127">구성 파일 수정</span><span class="sxs-lookup"><span data-stu-id="5db66-127">Modification of the Configuration File</span></span>  
 <span data-ttu-id="5db66-128">구성 파일을 수정하여 서비스가 중지되어도 패키지가 계속 실행되게 하거나 개체 탐색기에 추가 루트 폴더를 표시하거나 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스에서 관리할 파일 시스템의 다른 폴더 또는 추가 폴더를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-128">You can modify the configuration file to allow packages to continue running if the service stops, to display additional root folders in Object Explorer, or to specify a different folder or additional folders in the file system to be managed by [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="5db66-129">예를 들어 `SqlServerFolder` 유형의 추가 루트 폴더를 만들어 추가 [!INCLUDE[ssDE](../includes/ssde-md.md)] 인스턴스의 msdb 데이터베이스에 저장된 패키지를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-129">For example, you can create additional root folders of type, `SqlServerFolder`, to manage packages in the msdb databases of additional instances of [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5db66-130">일부 문자는 폴더 이름에 적합하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-130">Some characters are not valid in folder names.</span></span> <span data-ttu-id="5db66-131">폴더 이름에 적합한 문자는 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 클래스 **System.IO.Path** 와 **GetInvalidFilenameChars** 필드에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-131">Valid characters for folder names are determined by the [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] class **System.IO.Path** and the **GetInvalidFilenameChars** field.</span></span> <span data-ttu-id="5db66-132">**GetInvalidFilenameChars** 필드는 **Path** 클래스의 멤버에 전달된 경로 문자열 인수에 지정할 수 없는 플랫폼별 문자 배열을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-132">The **GetInvalidFilenameChars** field provides a platform-specific array of characters that cannot be specified in path string arguments passed to members of the **Path** class.</span></span> <span data-ttu-id="5db66-133">잘못된 문자 집합은 파일 시스템에 따라 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-133">The set of invalid characters can vary by file system.</span></span> <span data-ttu-id="5db66-134">일반적으로 따옴표("), 보다 작음(<) 문자 및 파이프(|) 문자가 잘못된 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-134">Typically, invalid characters are the quotation mark ("), less than (<) character, and pipe (|) character.</span></span>  
  
 <span data-ttu-id="5db66-135">그러나 [!INCLUDE[ssDE](../includes/ssde-md.md)]의 명명된 인스턴스나 원격 인스턴스에 저장된 패키지를 관리하려면 구성 파일을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-135">However, you will have to modify the configuration file to manage packages that are stored in a named instance or a remote instance of [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="5db66-136">구성 파일을 업데이트하지 않으면 **의** 개체 탐색기 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 를 사용하여 명명된 인스턴스나 원격 인스턴스의 msdb 데이터베이스에 저장된 패키지를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-136">If you do not update the configuration file, you cannot use **Object Explorer** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to view packages that are stored in the msdb database on the named instance or the remote instance.</span></span> <span data-ttu-id="5db66-137">**개체 탐색기** 를 사용하여 이러한 패키지를 보려고 하면 다음과 같은 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-137">If you try to use **Object Explorer** to view these packages, you receive the following error message:</span></span>  
  
 `Failed to retrieve data for this request. (Microsoft.SqlServer.SmoEnum)`  
  
 `The SQL Server specified in Integration Services service configuration is not present or is not available. This might occur when there is no default instance of SQL Server on the computer. For more information, see the topic "Configuring the Integration Services Service" in SQL Server 2008 Books Online.`  
  
 `Login Timeout Expired`  
  
 `An error has occurred while establishing a connection to the server. When connecting to SQL Server 2008, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.`  
  
 `Named Pipes Provider: Could not open a connection to SQL Server [2]. (MsDtsSvr).`  
  
 <span data-ttu-id="5db66-138">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스의 구성 파일을 수정하려면 텍스트 편집기를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-138">To modify the configuration file for the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, you use a text editor.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5db66-139">서비스 구성 파일을 수정한 후 업데이트된 서비스 구성을 사용하려면 서비스를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-139">After you modify the service configuration file, you must restart the service to use the updated service configuration.</span></span>  
  
### <a name="modified-configuration-file-example"></a><span data-ttu-id="5db66-140">수정된 구성 파일 예</span><span class="sxs-lookup"><span data-stu-id="5db66-140">Modified Configuration File Example</span></span>  
 <span data-ttu-id="5db66-141">다음 예에서는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]의 수정된 구성 파일을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-141">The following example shows a modified configuration file for [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="5db66-142">이 파일은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 서버의 `InstanceName` 이라는 `ServerName`의 명명된 인스턴스에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-142">This file is for a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] called `InstanceName` on a server named `ServerName`.</span></span>  
  
 <span data-ttu-id="5db66-143">**SQL Server의 명명된 인스턴스에 대한 수정된 구성 파일 예**</span><span class="sxs-lookup"><span data-stu-id="5db66-143">**Example of a Modified Configuration File for a Named Instance of SQL Server**</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<DtsServiceConfiguration xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <StopExecutingPackagesOnShutdown>true</StopExecutingPackagesOnShutdown>  
  <TopLevelFolders>  
    <Folder xsi:type="SqlServerFolder">  
      <Name>MSDB</Name>  
      <ServerName>ServerName\InstanceName</ServerName>  
    </Folder>  
    <Folder xsi:type="FileSystemFolder">  
      <Name>File System</Name>  
      <StorePath>..\Packages</StorePath>  
    </Folder>  
  </TopLevelFolders>    
</DtsServiceConfiguration>  
```  
  
## <a name="modification-of-the-configuration-file-location"></a><span data-ttu-id="5db66-144">구성 파일 위치 수정</span><span class="sxs-lookup"><span data-stu-id="5db66-144">Modification of the Configuration File Location</span></span>  
<span data-ttu-id="5db66-145">레지스트리 키 **HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT\MICROSOFT SQL Server\120\SSIS\ServiceConfigFile** 는 서비스에서 사용 하는 구성 파일의 위치와 이름을 지정 합니다 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5db66-145">The Registry key **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\SSIS\ServiceConfigFile** specifies the location and name for the configuration file that [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service uses.</span></span> <span data-ttu-id="5db66-146">레지스트리 키의 기본값은 **C:\Program FILES\MICROSOFT SQL Server\120\DTS\Binn\MsDtsSrvr.ini.xml**입니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-146">The default value of the Registry key is **C:\Program Files\Microsoft SQL Server\120\DTS\Binn\MsDtsSrvr.ini.xml**.</span></span> <span data-ttu-id="5db66-147">이 레지스트리의 값을 업데이트하여 구성 파일의 이름과 위치를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-147">You can update the value of the Registry key to use a different name and location for the configuration file.</span></span> <span data-ttu-id="5db66-148">경로의 버전 번호 (SQL Server의 경우 120 [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] )는 SQL Server 버전에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-148">Note that the version number in the path (120 for SQL Server  [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)]) will vary depending on the SQL Server version.</span></span> 
  
  
> [!CAUTION]  
>  <span data-ttu-id="5db66-149">레지스트리 키를 잘못 편집하면 운영 체제를 다시 설치해야 하는 심각한 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-149">Incorrectly editing the Registry can cause serious problems that may require you to reinstall your operating system.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="5db66-150">는 레지스트리를 잘못 편집하여 발생하는 문제에 대한 해결을 보증하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-150">cannot guarantee that problems resulting from editing the Registry incorrectly can be resolved.</span></span> <span data-ttu-id="5db66-151">레지스트리를 편집하기 전에 중요한 데이터를 백업하십시오.</span><span class="sxs-lookup"><span data-stu-id="5db66-151">Before editing the Registry, back up any valuable data.</span></span> <span data-ttu-id="5db66-152">레지스트리를 백업, 복원 및 편집하는 방법은 [!INCLUDE[msCoName](../includes/msconame-md.md)] 기술 자료 문서 [Microsoft Windows 레지스트리 설명](https://support.microsoft.com/kb/256986)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5db66-152">For information about how to back up, restore, and edit the Registry, see the [!INCLUDE[msCoName](../includes/msconame-md.md)] Knowledge Base article, [Description of the Microsoft Windows registry](https://support.microsoft.com/kb/256986).</span></span>  
  
 <span data-ttu-id="5db66-153">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스는 시작될 때 구성 파일을 로드하므로</span><span class="sxs-lookup"><span data-stu-id="5db66-153">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service loads the configuration file when the service is started.</span></span> <span data-ttu-id="5db66-154">레지스트리 항목의 변경 내용을 적용하려면 서비스를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5db66-154">Any changes to the Registry entry require that the service be restarted.</span></span>  
  
  
