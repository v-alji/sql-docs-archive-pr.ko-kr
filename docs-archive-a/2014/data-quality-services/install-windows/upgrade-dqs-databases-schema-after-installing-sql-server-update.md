---
title: SQL Server 업데이트 설치 후 DQS 데이터베이스 스키마 업그레이드 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: c8f3fbae-02c4-464d-a35c-7108f48c58cb
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 80a1714ea250cf7cf5d34bc9d208a42a64284308
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651915"
---
# <a name="upgrade-dqs-databases-schema-after-installing-sql-server-update"></a><span data-ttu-id="ecd9e-102">SQL Server 업데이트 설치 후 DQS 데이터베이스 스키마 업그레이드</span><span class="sxs-lookup"><span data-stu-id="ecd9e-102">Upgrade DQS Databases Schema After Installing SQL Server Update</span></span>
  <span data-ttu-id="ecd9e-103">이전에 구성한 DQS 인스턴스에 SQL Server 업데이트(패치, 핫픽스 또는 누적 업데이트)를 설치한 후에 **upgrade** 명령줄 매개 변수로 DQSInstaller.exe 파일을 실행하여 DQS 데이터베이스를 업그레이드해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd9e-103">After you have installed a SQL Server update (patch, hotfix, or cumulative update) on a previously configured DQS instance, you might have to upgrade the DQS databases schema by running the DQSInstaller.exe file with the **upgrade** command line parameter.</span></span> <span data-ttu-id="ecd9e-104">그렇지 않으면 Data Quality 클라이언트를 사용하여 Data Quality Server에 연결하려고 할 때 다음과 같은 오류 메시지가 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd9e-104">Otherwise, you might receive the following error while trying to connect to Data Quality Server using your Data Quality Client:</span></span>  
  
```  
An error occurred in the Microsoft .NET Framework while trying to load assembly id 65581.  
```  
  
 <span data-ttu-id="ecd9e-105">DQS 데이터베이스 스키마를 업그레이드해도 DQS 데이터베이스의 기존 데이터(기술 자료, 데이터 품질 프로젝트, DQS_STAGING_DATA 데이터베이스의 내보낸 결과)에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd9e-105">Upgrading DQS databases schema does not impact your existing data in the DQS databases (knowledge bases, data quality projects, and exported results in the DQS_STAGING_DATA database).</span></span> <span data-ttu-id="ecd9e-106">그러나 스키마 업그레이드 중에 데이터 손실을 방지하기 위해 DQS 데이터베이스 스키마를 업그레이드하기 전에 DQS 데이터베이스를 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd9e-106">However, you must back up your DQS databases before upgrading DQS databases schema to prevent any accidental data loss during the schema upgrade.</span></span> <span data-ttu-id="ecd9e-107">DQS 데이터베이스 백업에 대한 자세한 내용은 [Backing Up and Restoring DQS Databases](../backing-up-and-restoring-dqs-databases.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ecd9e-107">For information about backing up DQS databases, see [Backing Up and Restoring DQS Databases](../backing-up-and-restoring-dqs-databases.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ecd9e-108">대부분의 경우 SQL Server를 업데이트하려면 DQS 데이터베이스 스키마로 업그레이드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd9e-108">Most of the SQL Server updates will require an upgrade to the DQS databases schema.</span></span> <span data-ttu-id="ecd9e-109">DQS 데이터베이스 스키마로 업그레이드해야 하는 SQL Server 업데이트에 대한 자세한 내용은 [DQS 업그레이드: Data Quality Services에서 누적 업데이트 또는 핫픽스 패치 설치](https://go.microsoft.com/fwlink/?LinkID=251565)의 1.A 단계를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ecd9e-109">For information about the SQL Server updates that will require an upgrade to the DQS databases schema, see the chart in step 1.A in [Upgrade DQS: Installing Cumulative Updates or Hotfix Patches on Data Quality Services](https://go.microsoft.com/fwlink/?LinkID=251565).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ecd9e-110">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="ecd9e-110">Prerequisites</span></span>  
  
-   <span data-ttu-id="ecd9e-111">[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 컴퓨터에서 Administrators 그룹의 멤버로 로그온해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd9e-111">You must be logged on as a member of the Administrators group on the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] computer.</span></span>  
  
-   <span data-ttu-id="ecd9e-112">Windows 사용자 계정은 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 가 설치된 SQL Server 인스턴스에서 sysadmin 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd9e-112">Your Windows user account must be a member of the sysadmin fixed server role in the SQL Server instance where [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] is installed.</span></span>  
  
### <a name="to-upgrade-dqs-databases-schema"></a><span data-ttu-id="ecd9e-113">DQS 데이터베이스 스키마를 업그레이드하려면</span><span class="sxs-lookup"><span data-stu-id="ecd9e-113">To upgrade DQS databases schema</span></span>  
  
1.  <span data-ttu-id="ecd9e-114">스키마 업그레이드를 계속하기 전에 DQS 데이터베이스를 백업하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd9e-114">(Recommended) Back up your DQS databases before you proceed with the schema upgrade.</span></span> <span data-ttu-id="ecd9e-115">DQS 데이터베이스 백업에 대한 자세한 내용은 [Backing Up and Restoring DQS Databases](../backing-up-and-restoring-dqs-databases.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ecd9e-115">For information about backing up DQS databases, see [Backing Up and Restoring DQS Databases](../backing-up-and-restoring-dqs-databases.md).</span></span>  
  
2.  <span data-ttu-id="ecd9e-116">명령 프롬프트를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd9e-116">Start Command Prompt.</span></span>  
  
3.  <span data-ttu-id="ecd9e-117">명령 프롬프트에서 디렉터리를 DQSInstaller.exe가 있는 위치로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd9e-117">At the command prompt, change your directory to the location where DQSInstaller.exe is available.</span></span> <span data-ttu-id="ecd9e-118">SQL Server의 기본 인스턴스를 설치한 경우 DQSInstaller.exe 파일은 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd9e-118">If you installed the default instance of SQL Server, the DQSInstaller.exe file will be available at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn:</span></span>  
  
    ```  
    cd C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn  
    ```  
  
4.  <span data-ttu-id="ecd9e-119">명령 프롬프트에 다음 명령을 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="ecd9e-119">At the command prompt, type the following command, and press ENTER:</span></span>  
  
    ```  
    dqsinstaller.exe -upgrade  
    ```  
  
5.  <span data-ttu-id="ecd9e-120">설치 관리자에서 계속하기 전에 DQS 데이터베이스를 백업하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd9e-120">The installer prompts you for backing up the DQS databases before proceeding.</span></span> <span data-ttu-id="ecd9e-121">DQS 데이터베이스를 이미 백업했으면 `Y` 또는 `Yes`를 입력하고 ENTER 키를 눌러 업그레이드를 계속하십시오.</span><span class="sxs-lookup"><span data-stu-id="ecd9e-121">If you have already backed up your DQS databases, type `Y` or `Yes` and press ENTER to continue with the upgrade.</span></span>  
  
6.  <span data-ttu-id="ecd9e-122">DQS 데이터베이스 스키마 업그레이드에 성공하면 완료 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecd9e-122">A completion message is displayed after successful upgrade of the DQS databases schema.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ecd9e-123">다음 단계</span><span class="sxs-lookup"><span data-stu-id="ecd9e-123">Next Steps</span></span>  
 <span data-ttu-id="ecd9e-124">Data Quality 클라이언트 애플리케이션에서 업그레이드된 Data Quality Server에 로그온합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd9e-124">Log on to the upgraded Data Quality Server from a Data Quality Client application.</span></span>  
  
 <span data-ttu-id="ecd9e-125">SQL Server 업데이트 설치 후 DQS 데이터베이스 스키마 업그레이드 및 관련 문제 해결 단계에 대한 자세한 내용은 [DQS 업그레이드: Data Quality Services에서 누적 업데이트 또는 핫픽스 패치 설치](https://go.microsoft.com/fwlink/?LinkID=251565)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ecd9e-125">For more information about upgrading DQS databases schema after installing SQL Server updates and associated troubleshooting steps, see [Upgrade DQS: Installing Cumulative Updates or Hotfix Patches on Data Quality Services](https://go.microsoft.com/fwlink/?LinkID=251565).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecd9e-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ecd9e-126">See Also</span></span>  
 <span data-ttu-id="ecd9e-127">[Data Quality Services 설치](install-data-quality-services.md) </span><span class="sxs-lookup"><span data-stu-id="ecd9e-127">[Install Data Quality Services](install-data-quality-services.md) </span></span>  
 [<span data-ttu-id="ecd9e-128">.NET Framework 업데이트 후 SQLCLR 어셈블리 업그레이드</span><span class="sxs-lookup"><span data-stu-id="ecd9e-128">Upgrade SQLCLR Assemblies After .NET Framework Update</span></span>](upgrade-sqlclr-assemblies-after-net-framework-update.md)  
  
  
