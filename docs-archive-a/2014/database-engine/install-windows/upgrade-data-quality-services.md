---
title: Data Quality Services 업그레이드 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: f396666b-7754-4efc-9507-0fd114cc32d5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9d2544df341a831f2f676ec58150ed64a800fb96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649159"
---
# <a name="upgrade-data-quality-services"></a><span data-ttu-id="0b2c4-102">Data Quality Services 업그레이드</span><span class="sxs-lookup"><span data-stu-id="0b2c4-102">Upgrade Data Quality Services</span></span>
  <span data-ttu-id="0b2c4-103">이 항목에서는 기존 DQS(Data Quality Services) 설치를 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2로 업그레이드하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-103">This topic provides information on how to upgrade your existing installation of Data Quality Services (DQS) to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2.</span></span> <span data-ttu-id="0b2c4-104">DQS의 Data Quality 서버를 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드할 때 DQS 데이터베이스 스키마도 업그레이드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-104">As part of upgrading your Data Quality Server in DQS to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you must also upgrade the DQS databases schema.</span></span>  
  
> [!IMPORTANT]
>  -   <span data-ttu-id="0b2c4-105">스키마 업그레이드 중에 데이터 손실을 방지하기 위해 DQS를 업그레이드하기 전에 DQS 데이터베이스를 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-105">You must back up your DQS databases before upgrading DQS to prevent any accidental data loss during the schema upgrade.</span></span> <span data-ttu-id="0b2c4-106">DQS 데이터베이스 백업에 대한 자세한 내용은 [Backing Up and Restoring DQS Databases](../../data-quality-services/backing-up-and-restoring-dqs-databases.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-106">For information about backing up DQS databases, see [Backing Up and Restoring DQS Databases](../../data-quality-services/backing-up-and-restoring-dqs-databases.md).</span></span>  
> -   <span data-ttu-id="0b2c4-107">데이터 품질 태스크를 수행하기 위해 Integration Services의 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] DQS 정리 변환 편집기 [나 최신 또는 이전 버전의 Data Quality 클라이언트를 사용하여](../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md) 버전의 Data Quality 서버에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-107">You can connect to the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of Data Quality Server by using the current or an earlier version of Data Quality Client or the [DQS Cleansing Transformation](../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md) in Integration Services to perform your data quality tasks.</span></span>  
> -   <span data-ttu-id="0b2c4-108">Data Quality Services 및 MDS(Master Data Services)를 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] CTP2로 업그레이드한 후 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SP1 버전의 Excel용 MDS(Master Data Services) 추가 기능을 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-108">You can continue using the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 version of Master Data Services Add-In for Excel after upgrading Data Quality Services and Master Data Services to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2.</span></span> <span data-ttu-id="0b2c4-109">하지만 SQL Server 2014 CTP2로 업그레이드한 후에는 이전 버전의 Excel용 MDS(Master Data Services) 추가 기능이 모두 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-109">However, any earlier version of the Master Data Services Add-In for Excel will not work after upgrading to SQL Server 2014 CTP2.</span></span> <span data-ttu-id="0b2c4-110">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 버전의 Excel용 MDS(Master Data Services) 추가 기능은 [여기](https://go.microsoft.com/fwlink/?LinkId=328664)서 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-110">You can download the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 version of Master Data Services Add-In for Excel from [here](https://go.microsoft.com/fwlink/?LinkId=328664).</span></span>  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="0b2c4-111">필수 조건</span><span class="sxs-lookup"><span data-stu-id="0b2c4-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="0b2c4-112">[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 컴퓨터에서 Administrators 그룹의 멤버로 로그온해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-112">You must be logged on as a member of the Administrators group on the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] computer.</span></span>  
  
-   <span data-ttu-id="0b2c4-113">Windows 사용자 계정은 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 가 설치된 SQL Server 인스턴스에서 sysadmin 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-113">Your Windows user account must be a member of the sysadmin fixed server role in the SQL Server instance where [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] is installed.</span></span>  
  
##  <a name="upgrading-dqs"></a><a name="Upgrade"></a> <span data-ttu-id="0b2c4-114">DQS 업그레이드</span><span class="sxs-lookup"><span data-stu-id="0b2c4-114">Upgrading DQS</span></span>  
 <span data-ttu-id="0b2c4-115">DQS를 업그레이드하려면:</span><span class="sxs-lookup"><span data-stu-id="0b2c4-115">To upgrade DQS:</span></span>  
  
1.  <span data-ttu-id="0b2c4-116">업그레이드 프로세스를 시작하기 전에 DQS 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-116">Back up your DQS databases before you start the upgrade process.</span></span> <span data-ttu-id="0b2c4-117">DQS 데이터베이스 백업에 대한 자세한 내용은 [Backing Up and Restoring DQS Databases](../../data-quality-services/backing-up-and-restoring-dqs-databases.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-117">For information about backing up DQS databases, see [Backing Up and Restoring DQS Databases](../../data-quality-services/backing-up-and-restoring-dqs-databases.md).</span></span>  
  
2.  <span data-ttu-id="0b2c4-118">DQS가 설치된 SQL Server 인스턴스를 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-118">Upgrade the SQL Server instance where DQS is installed to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
    1.  <span data-ttu-id="0b2c4-119">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 설치 마법사를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-119">Run the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup wizard.</span></span>  
  
    2.  <span data-ttu-id="0b2c4-120">왼쪽 창에서 **설치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-120">In the left pane, click **Installation**.</span></span>  
  
    3.  <span data-ttu-id="0b2c4-121">오른쪽 창에서 **SQL Server 2005, SQL Server 2008, SQL Server 2008 R2 또는 SQL Server 2012에서 업그레이드**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-121">In the right pane, click **Upgrade from SQL Server 2005, SQL Server 2008, SQL Server 2008 R2 or SQL Server 2012**.</span></span>  
  
    4.  <span data-ttu-id="0b2c4-122">설치 마법사를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-122">Complete the Setup wizard.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="0b2c4-123">SQL Server 인스턴스가 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 로 업그레이드되고 Data Quality 클라이언트가 이 컴퓨터에 설치되어 있지 않은 경우 최신 Data Quality 클라이언트도 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-123">This will upgrade your SQL Server instance to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] and also install the latest Data Quality Client, if Data Quality Client was previously installed on this computer.</span></span> <span data-ttu-id="0b2c4-124">Data Quality 클라이언트가 다른 컴퓨터에 설치되어 있으면 해당 컴퓨터에서 2단계의 하위 단계를 실행하여 최신 버전의 Data Quality 클라이언트를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-124">If you have Data Quality Client installed on other computers, you must run the sub steps in Step 2 on those computers to install the current version of Data Quality Client.</span></span> <span data-ttu-id="0b2c4-125">설치 마법사는 기존 버전의 Data Quality 클라이언트와 함께 최신 버전의 Data Quality 클라이언트를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-125">The Setup wizard installs the current version of Data Quality Client alongside the existing version of Data Quality Client.</span></span> <span data-ttu-id="0b2c4-126">DQS 데이터베이스 스키마를 업그레이드한 후 최신 또는 이전 버전의 Data Quality 클라이언트를 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 버전의 Data Quality 서버에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-126">After you upgrade the DQS databases schema, you can connect to the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of Data Quality Server by using the current or an earlier version of Data Quality Client.</span></span>  
  
3.  <span data-ttu-id="0b2c4-127">DQS 데이터베이스 스키마를 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-127">Upgrade the DQS databases schema.</span></span>  
  
    1.  <span data-ttu-id="0b2c4-128">관리자로 명령 프롬프트를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-128">Start Command Prompt as an administrator.</span></span>  
  
    2.  <span data-ttu-id="0b2c4-129">명령 프롬프트에서 디렉터리를 DQSInstaller.exe가 있는 위치로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-129">At the command prompt, change your directory to the location where DQSInstaller.exe is available.</span></span> <span data-ttu-id="0b2c4-130">기본 SQL Server 인스턴스의 경우 DQSInstaller.exe 파일은 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-130">For the default instance of SQL Server, the DQSInstaller.exe file is available at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn:</span></span>  
  
        ```  
        cd C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn  
        ```  
  
    3.  <span data-ttu-id="0b2c4-131">명령 프롬프트에 다음 명령을 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-131">At the command prompt, type the following command, and press ENTER:</span></span>  
  
        ```  
        dqsinstaller.exe -upgrade  
        ```  
  
    4.  <span data-ttu-id="0b2c4-132">설치 관리자에서 계속하기 전에 DQS 데이터베이스를 백업하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-132">The installer prompts you for backing up the DQS databases before proceeding.</span></span> <span data-ttu-id="0b2c4-133">DQS 데이터베이스를 이미 백업했으면 `Y` 또는 `Yes`를 입력한 후 ENTER 키를 눌러 업그레이드를 계속하십시오.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-133">If you have already backed up your DQS databases, type `Y` or `Yes`, and then press ENTER to continue with the upgrade.</span></span>  
  
    5.  <span data-ttu-id="0b2c4-134">DQS 데이터베이스 스키마 업그레이드에 성공하면 완료 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-134">A completion message is displayed after successful upgrade of the DQS databases schema.</span></span>  
  
##  <a name="verifying-the-dqs-databases-schema-upgrade"></a><a name="Verify"></a> <span data-ttu-id="0b2c4-135">DQS 데이터베이스 스키마 업그레이드 확인</span><span class="sxs-lookup"><span data-stu-id="0b2c4-135">Verifying the DQS Databases Schema Upgrade</span></span>  
 <span data-ttu-id="0b2c4-136">DQS 데이터베이스 스키마가 성공적으로 업그레이드되었는지 확인하려면 DQS_MAIN 및 DQS_PROJECTS 데이터베이스에서 A_DB_VERSION 테이블을 쿼리하여 각 데이터베이스의 현재 버전을 확인하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-136">To verify that DQS databases schema have successfully upgraded, you can check the current version in the DQS_MAIN and DQS_PROJECTS databases by querying the A_DB_VERSION table in each database.</span></span> <span data-ttu-id="0b2c4-137">이렇게 하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-137">To do so:</span></span>  
  
1.  <span data-ttu-id="0b2c4-138">SQL Server Management Studio를 시작하고 업그레이드된 DQS 데이터베이스 스키마가 포함된 SQL Server 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-138">Start SQL Server Management Studio, and connect to the SQL Server instance that contains the upgraded DQS databases schema.</span></span>  
  
2.  <span data-ttu-id="0b2c4-139">다음 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-139">Run the following query:</span></span>  
  
    ```  
    SELECT * FROM DQS_MAIN.dbo.A_DB_VERSION WHERE STATUS=2;  
    SELECT * FROM DQS_PROJECTS.dbo.A_DB_VERSION WHERE STATUS=2;  
    ```  
  
3.  <span data-ttu-id="0b2c4-140">출력에는 업그레이드 날짜와 함께 각 업그레이드에 대한 항목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-140">The output will display an entry for each upgrade along with the date of the upgrade.</span></span> <span data-ttu-id="0b2c4-141">최신 날짜의 최대 VERSION_ID 및 ASSEMBLY_VERSION이 현재 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-141">The maximum VERSION_ID and ASSEMBLY_VERSION on the latest date is the current version.</span></span> <span data-ttu-id="0b2c4-142">STATUS 열의 값이 2이면 성공을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-142">A value of 2 in the STATUS column indicates success.</span></span> <span data-ttu-id="0b2c4-143">오류가 발생한 경우 ERROR 열에 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-143">If an error has occurred, the error will be listed in the ERROR column.</span></span> <span data-ttu-id="0b2c4-144">예제 출력:</span><span class="sxs-lookup"><span data-stu-id="0b2c4-144">A sample output:</span></span>  
  
    |<span data-ttu-id="0b2c4-145">ID</span><span class="sxs-lookup"><span data-stu-id="0b2c4-145">ID</span></span>|<span data-ttu-id="0b2c4-146">UPGRADE_DATE</span><span class="sxs-lookup"><span data-stu-id="0b2c4-146">UPGRADE_DATE</span></span>|<span data-ttu-id="0b2c4-147">VERSION_ID</span><span class="sxs-lookup"><span data-stu-id="0b2c4-147">VERSION_ID</span></span>|<span data-ttu-id="0b2c4-148">ASSEMBLY_VERSION</span><span class="sxs-lookup"><span data-stu-id="0b2c4-148">ASSEMBLY_VERSION</span></span>|<span data-ttu-id="0b2c4-149">USER_NAME</span><span class="sxs-lookup"><span data-stu-id="0b2c4-149">USER_NAME</span></span>|<span data-ttu-id="0b2c4-150">상태</span><span class="sxs-lookup"><span data-stu-id="0b2c4-150">STATUS</span></span>|<span data-ttu-id="0b2c4-151">오류</span><span class="sxs-lookup"><span data-stu-id="0b2c4-151">ERROR</span></span>|  
    |--------|-------------------|-----------------|-----------------------|----------------|------------|-----------|  
    |<span data-ttu-id="0b2c4-152">1000</span><span class="sxs-lookup"><span data-stu-id="0b2c4-152">1000</span></span>|<span data-ttu-id="0b2c4-153">2013-08-11 05:26:39.567</span><span class="sxs-lookup"><span data-stu-id="0b2c4-153">2013-08-11 05:26:39.567</span></span>|<span data-ttu-id="0b2c4-154">1200</span><span class="sxs-lookup"><span data-stu-id="0b2c4-154">1200</span></span>|<span data-ttu-id="0b2c4-155">11.0.3000.0</span><span class="sxs-lookup"><span data-stu-id="0b2c4-155">11.0.3000.0</span></span>|\<DOMAIN\UserName>|<span data-ttu-id="0b2c4-156">2</span><span class="sxs-lookup"><span data-stu-id="0b2c4-156">2</span></span>||  
    |<span data-ttu-id="0b2c4-157">1001</span><span class="sxs-lookup"><span data-stu-id="0b2c4-157">1001</span></span>|<span data-ttu-id="0b2c4-158">2013-09-19 15:09:37.750</span><span class="sxs-lookup"><span data-stu-id="0b2c4-158">2013-09-19 15:09:37.750</span></span>|<span data-ttu-id="0b2c4-159">1600</span><span class="sxs-lookup"><span data-stu-id="0b2c4-159">1600</span></span>|<span data-ttu-id="0b2c4-160">12.0.xxxx.0</span><span class="sxs-lookup"><span data-stu-id="0b2c4-160">12.0.xxxx.0</span></span>|\<DOMAIN\UserName>|<span data-ttu-id="0b2c4-161">2</span><span class="sxs-lookup"><span data-stu-id="0b2c4-161">2</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="0b2c4-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0b2c4-162">See Also</span></span>  
 <span data-ttu-id="0b2c4-163">[Data Quality Services 설치](../../data-quality-services/install-windows/install-data-quality-services.md) </span><span class="sxs-lookup"><span data-stu-id="0b2c4-163">[Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md) </span></span>  
 <span data-ttu-id="0b2c4-164">[Data Quality 서버 개체 제거](../../sql-server/install/remove-data-quality-server-objects.md) </span><span class="sxs-lookup"><span data-stu-id="0b2c4-164">[Remove Data Quality Server Objects](../../sql-server/install/remove-data-quality-server-objects.md) </span></span>  
 [<span data-ttu-id="0b2c4-165">SQL Server 2014로 업그레이드</span><span class="sxs-lookup"><span data-stu-id="0b2c4-165">Upgrade to SQL Server 2014</span></span>](upgrade-sql-server.md)  
  
  
