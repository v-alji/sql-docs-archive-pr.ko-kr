---
title: .NET Framework 업데이트 후 SQLCLR 어셈블리 업그레이드 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b1a008cc-7e6b-4655-a869-bd429f986400
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 45d60db413e11828f26bd03e1c8f350645838d12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651913"
---
# <a name="upgrade-sqlclr-assemblies-after-net-framework-update"></a><span data-ttu-id="0fb45-102">.NET Framework 업데이트 후 SQLCLR 어셈블리 업그레이드</span><span class="sxs-lookup"><span data-stu-id="0fb45-102">Upgrade SQLCLR Assemblies After .NET Framework Update</span></span>
  [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] <span data-ttu-id="0fb45-103">(DQS)는 Microsoft .NET Framework 4 어셈블리를 참조하는 SQLCR(SQL 공용 언어 런타임)의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="0fb45-103">(DQS) is a collection of SQL Common Language Runtime (SQLCR) routines that reference Microsoft .NET Framework 4 assemblies.</span></span> <span data-ttu-id="0fb45-104">참조되는 이러한 .NET Framework 어셈블리에 영향을 주는 .NET Framework 업데이트를 컴퓨터에 설치하면 GAC(전역 어셈블리 캐시)의 어셈블리 MVID(모듈 버전 ID)가 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb45-104">When you install any .NET Framework updates on your computer that affect any such referenced .NET Framework assembly, it leads to a change in the Module Version ID (MVID) of the assembly in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="0fb45-105">이렇게 되면 GAC의 참조되는 어셈블리 MVID와 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]의 어셈블리 MVID 간에 불일치가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb45-105">This causes a mismatch between the MVIDs of the referenced assembly in GAC and the assembly in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="0fb45-106">.NET Framework 업데이트를 위해 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 컴퓨터를 다시 시작해야 하는 경우 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 컴퓨터를 다시 시작하면 영향을 받는 SQLCLR 어셈블리가 자동으로 업그레이드되어 MVID 불일치 문제가 해결됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fb45-106">If the .NET Framework update requires you to restart the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] computer, the affected SQLCLR assemblies are upgraded automatically to fix the MVID mismatch issue on restarting the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] computer.</span></span> <span data-ttu-id="0fb45-107">그러나 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 서버 컴퓨터를 다시 시작할 필요가 없는 .NET Framework 업데이트의 경우 어셈블리 MVID의 불일치로 인해 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 를 사용하여 [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]에 연결하려고 할 때 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb45-107">However, for .NET Framework updates that do not require you to restart your [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] computer, an error occurs due to the mismatch in the MVIDs of the assemblies when you try to connect to a [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] using a [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]:</span></span>  
  
```  
A new version of .NET was installed on this machine. In order to continue to work with DQS please run dqsinstaller.exe -upgradedlls.  
```  
  
 <span data-ttu-id="0fb45-108">이 문제를 해결하려면 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 영향을 받는 SQLCLR 어셈블리를 업그레이드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb45-108">To fix this issue, the affected SQLCLR assemblies in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] must be upgraded.</span></span> <span data-ttu-id="0fb45-109">DQS 데이터베이스를 다시 만드는 것을 건너뛰고 영향을 받는 어셈블리만 업그레이드하도록 **upgradedlls** 명령줄 매개 변수를 사용하여 DQSInstaller.exe를 실행하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fb45-109">You can do so by running the DQSInstaller.exe file with the **upgradedlls** command line parameter to skip recreating the DQS databases, and just upgrade the affected assemblies.</span></span> <span data-ttu-id="0fb45-110">이렇게 하면 기술 자료, 데이터 품질 프로젝트 및 DQS의 다른 데이터를 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb45-110">This ensures that your knowledge bases, data quality projects, and any other data in DQS are preserved.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0fb45-111">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="0fb45-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="0fb45-112">[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 컴퓨터에서 Administrators 그룹의 멤버로 로그온해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb45-112">You must be logged on as a member of the Administrators group on the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] computer.</span></span>  
  
-   <span data-ttu-id="0fb45-113">Windows 사용자 계정은 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 가 설치된 SQL Server 인스턴스에서 sysadmin 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb45-113">Your Windows user account must be a member of the sysadmin fixed server role in the SQL Server instance where [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] is installed.</span></span>  
  
### <a name="to-upgrade-sqlclr-assemblies"></a><span data-ttu-id="0fb45-114">SQLCLR 어셈블리를 업그레이드하려면</span><span class="sxs-lookup"><span data-stu-id="0fb45-114">To upgrade SQLCLR Assemblies</span></span>  
  
1.  <span data-ttu-id="0fb45-115">명령 프롬프트를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb45-115">Start Command Prompt.</span></span>  
  
2.  <span data-ttu-id="0fb45-116">명령 프롬프트에서 디렉터리를 DQSInstaller.exe가 있는 위치로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb45-116">At the command prompt, change your directory to the location where DQSInstaller.exe is available.</span></span> <span data-ttu-id="0fb45-117">SQL Server의 기본 인스턴스를 설치한 경우 DQSInstaller.exe 파일은 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb45-117">If you installed the default instance of SQL Server, the DQSInstaller.exe file will be available at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn:</span></span>  
  
    ```  
    cd C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn  
    ```  
  
3.  <span data-ttu-id="0fb45-118">명령 프롬프트에 다음 명령을 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="0fb45-118">At the command prompt, type the following command, and press ENTER:</span></span>  
  
    ```  
    dqsinstaller.exe -upgradedlls  
    ```  
  
4.  <span data-ttu-id="0fb45-119">나머지 단계는 [DQSInstaller.exe를 실행하여 Data Quality 서버 설치 완료](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#WindowsExplorer) 의 [시작 화면, 시작 메뉴 또는 Windows 탐색기에서 DQSInstaller.exe 실행](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)섹션에 설명된 2~6단계와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb45-119">Rest of the steps are same as steps 2-6 in the [Run DQSInstaller.exe from Start Screen, Start Menu or Windows Explorer](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#WindowsExplorer) section in [Run DQSInstaller.exe to Complete Data Quality Server Installation](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fb45-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0fb45-120">See Also</span></span>  
 <span data-ttu-id="0fb45-121">[Data Quality Services 설치](install-data-quality-services.md) </span><span class="sxs-lookup"><span data-stu-id="0fb45-121">[Install Data Quality Services](install-data-quality-services.md) </span></span>  
 [<span data-ttu-id="0fb45-122">SQL Server 업데이트 설치 후 DQS 데이터베이스 스키마 업그레이드</span><span class="sxs-lookup"><span data-stu-id="0fb45-122">Upgrade DQS Databases Schema After Installing SQL Server Update</span></span>](upgrade-dqs-databases-schema-after-installing-sql-server-update.md)  
  
  
