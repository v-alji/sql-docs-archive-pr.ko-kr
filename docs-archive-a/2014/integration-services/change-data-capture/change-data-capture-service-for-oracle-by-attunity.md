---
title: Attunity Oracle CDC Service | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 22ec8a5c-9550-4d38-8a4a-485ec3e53ea8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 68e68e9edd91bd1d0c718b32e29c3b29f74778c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651858"
---
# <a name="change-data-capture-service-for-oracle-by-attunity"></a><span data-ttu-id="c7e20-102">Attunity Oracle CDC Service</span><span class="sxs-lookup"><span data-stu-id="c7e20-102">Change Data Capture Service for Oracle by Attunity</span></span>
  <span data-ttu-id="c7e20-103">Oracle CDC Service는 Oracle 트랜잭션 로그를 검색하고 관련 Oracle 테이블의 변경 내용을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 변경 테이블에 캡처하는 Windows 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="c7e20-103">The CDC Service for Oracle is a Windows service that scans Oracle transaction logs and captures changes to Oracle tables of interest into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] change tables.</span></span> <span data-ttu-id="c7e20-104">Oracle에서 캡처한 변경 내용이 저장되는 SQL 변경 테이블은 네이티브 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 변경 데이터 캡처 기능에서 사용하는 변경 테이블과 같은 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="c7e20-104">The SQL change tables where the changes captured from Oracle are stored are the same type of change tables used in the native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Change Data Capture feature.</span></span> <span data-ttu-id="c7e20-105">따라서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 대한 변경 내용을 사용하는 것만큼 쉽게 이 변경 내용을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7e20-105">This makes consuming these changes as easy as consuming changes made to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
## <a name="installation"></a><span data-ttu-id="c7e20-106">설치</span><span class="sxs-lookup"><span data-stu-id="c7e20-106">Installation</span></span>  
 <span data-ttu-id="c7e20-107">캡처되는 원본 Oracle 데이터베이스와 대상 CDC 데이터베이스가 위치하는 대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 액세스할 수 있는 지원되는 Windows 컴퓨터에 Oracle CDC Service를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7e20-107">The CDC Service for Oracle can be installed on any supported Windows computer with access to the source Oracle database(s) being captured and the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance where the target CDC database resides.</span></span> <span data-ttu-id="c7e20-108">CDC Service는 Oracle 데이터베이스와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스의 로컬 설치가 필요 없으며 지원되는 클라이언트만 있으면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7e20-108">The CDC Service does not need a local installation of the Oracle database or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, only their supported clients.</span></span> <span data-ttu-id="c7e20-109">필요한 데이터베이스 구성 요소를 설치하는 위치에 대한 자세한 내용은 이 항목의 **데이터베이스 필수 구성 요소** 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c7e20-109">For information about where to install the required database components, see **Database Prerequisites** in this topic.</span></span>  
  
 <span data-ttu-id="c7e20-110">Oracle용 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC Service를 설치하면 서비스 구성 UI와 서비스 프로그램이 선택한 위치에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7e20-110">The installation of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC Service for Oracle places the service configuration UI and the service program in the selected location.</span></span> <span data-ttu-id="c7e20-111">Oracle CDC Service는 Oracle CDC Service 구성 콘솔을 사용하여 별도로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7e20-111">The CDC Service for Oracle is configured separately using the Oracle CDC Service Configuration Console.</span></span> <span data-ttu-id="c7e20-112">Oracle CDC Service 구성에 대한 자세한 내용은 [Change Data Capture Service for Oracle by Attunity F1 도움말](change-data-capture-service-for-oracle-by-attunity-f1-help.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c7e20-112">For more information on configuring the Oracle CDC Service, see [Change Data Capture Service for Oracle by Attunity F1 Help](change-data-capture-service-for-oracle-by-attunity-f1-help.md).</span></span>  
  
 <span data-ttu-id="c7e20-113">Oracle CDC Service를 설치 하려면 SQL Server 설치 미디어에서 **AttunityOracleCdcService.msi** 를 수동으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7e20-113">To install the CDC Service for Oracle, manually run **AttunityOracleCdcService.msi** from the SQL Server installation media.</span></span> <span data-ttu-id="c7e20-114">X86 및 x 64 용 설치 패키지는 SQL Server 설치 미디어의 \*\*.\Tools\AttunityCDCOracle \\ \*\* 에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7e20-114">Installation packages for x86 and x64 are located in **.\Tools\AttunityCDCOracle\\** on the SQL Server installation media.</span></span>  
  
 <span data-ttu-id="c7e20-115">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client가 설치되는 지원되는 Windows 컴퓨터에 Oracle CDC Service를 설치할 수 있으며 대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 설치되는 동일한 컴퓨터에 설치할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7e20-115">The CDC Service for Oracle can be installed on any supported Windows computer where the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client is installed; it does not need to be installed on the same computer where the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span>  
  
## <a name="supported-windows-environments"></a><span data-ttu-id="c7e20-116">지원되는 Windows 환경</span><span class="sxs-lookup"><span data-stu-id="c7e20-116">Supported Windows Environments</span></span>  
 <span data-ttu-id="c7e20-117">Attunity Oracle CDC Service는 다음 Windows 환경에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7e20-117">The Change Data Capture Service for Oracle by Attunity can run in the following Windows environments:</span></span>  
  
-   <span data-ttu-id="c7e20-118">Windows 8</span><span class="sxs-lookup"><span data-stu-id="c7e20-118">Windows 8</span></span>  
  
-   <span data-ttu-id="c7e20-119">Windows 7 32비트(x86) 및 64비트(x64)</span><span class="sxs-lookup"><span data-stu-id="c7e20-119">Windows 7 32-bit (x86) and 64-bit (x64)</span></span>  
  
-   <span data-ttu-id="c7e20-120">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="c7e20-120">Windows Server 2012</span></span>  
  
-   <span data-ttu-id="c7e20-121">Windows Server 2008 R2(서비스 팩 1)</span><span class="sxs-lookup"><span data-stu-id="c7e20-121">Windows Server 2008 R2 with Service Pack 1</span></span>  
  
-   <span data-ttu-id="c7e20-122">Windows Server 2008 32비트(x86) 및 64비트(x64) 서비스 팩 2</span><span class="sxs-lookup"><span data-stu-id="c7e20-122">Windows Server 2008 32-bit (x86) and 64-bit (x64) with Service Pack 2</span></span>  
  
## <a name="database-prerequisites"></a><span data-ttu-id="c7e20-123">데이터베이스 필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="c7e20-123">Database Prerequisites</span></span>  
 <span data-ttu-id="c7e20-124">Oracle CDC Service를 사용하려면 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client Oracle 소프트웨어를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7e20-124">To work with the CDC Service for Oracle you must install the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client Oracle software.</span></span> <span data-ttu-id="c7e20-125">이 항목은 Oracle CDC Service를 설치하기 전에 Oracle에서 구하여 설치해야 하는 필수 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c7e20-125">This is a prerequisite that should be obtained from Oracle and installed before installing the Oracle CDC Service.</span></span> <span data-ttu-id="c7e20-126">또한 SQL Server 설치 프로그램을 사용하여 SQL Server ODBC 클라이언트를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7e20-126">Additionally, you need to install the SQL Server ODBC Client using SQL Server Setup.</span></span>  
  
 <span data-ttu-id="c7e20-127">Oracle CDC Service는 다음 버전을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c7e20-127">The CDC Service for Oracle supports the following versions:</span></span>  
  
### <a name="source-oracle-database"></a><span data-ttu-id="c7e20-128">원본 Oracle 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="c7e20-128">Source Oracle Database</span></span>  
  
-   <span data-ttu-id="c7e20-129">Oracle 데이터베이스 11x, 모든 버전</span><span class="sxs-lookup"><span data-stu-id="c7e20-129">Oracle Database 11x, any version</span></span>  
  
-   <span data-ttu-id="c7e20-130">Oracle 데이터베이스 10x, 모든 버전</span><span class="sxs-lookup"><span data-stu-id="c7e20-130">Oracle Database 10x, any version</span></span>  
  
### <a name="target-sql-server-database"></a><span data-ttu-id="c7e20-131">대상 SQL Server 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="c7e20-131">Target SQL Server Database</span></span>  
 <span data-ttu-id="c7e20-132">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c7e20-132">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="running-the-installation-program"></a><span data-ttu-id="c7e20-133">설치 프로그램 실행</span><span class="sxs-lookup"><span data-stu-id="c7e20-133">Running the Installation Program</span></span>  
 <span data-ttu-id="c7e20-134">Oracle CDC Service를 설치하려면 사용 중인 Windows 플랫폼(32/64비트)에 맞는 설치 마법사를 열고 화면에 나타나는 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="c7e20-134">To install the CDC Service for Oracle, open the installation wizard for the Windows platform you are using (32/64-bit) and follow the directions on the screen.</span></span>  
  
## <a name="uninstalling-change-data-capture-service-for-oracle-by-attunity"></a><span data-ttu-id="c7e20-135">Attunity Oracle CDC Service 제거</span><span class="sxs-lookup"><span data-stu-id="c7e20-135">Uninstalling Change Data Capture Service for Oracle by Attunity</span></span>  
 <span data-ttu-id="c7e20-136">제어판, 프로그램 및 기능을 사용하여 Oracle CDC Service를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="c7e20-136">You uninstall the CDC Service for Oracle using Control Panel, Programs and Features.</span></span>  
  
 <span data-ttu-id="c7e20-137">CDC Service를 제거해도 만들어진 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스는 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7e20-137">Uninstalling the CDC Service does not delete the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases created.</span></span> <span data-ttu-id="c7e20-138">도구를 완전히 제거하려면 작업한 대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 만들어진 MSXDBCDC 데이터베이스와 특정 CDC 데이터베이스를 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7e20-138">For complete removal of the tool, you must remove the MSXDBCDC database and the specific CDC databases that were created in the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you worked with.</span></span>  
  
 <span data-ttu-id="c7e20-139">CDC Service 소프트웨어를 한 컴퓨터에서 제거하고 다른 컴퓨터에 설치하려면 다음 정의를 제공하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7e20-139">If you uninstall the CDC Service software from one machine and install it on another computer, you only need to provide the following definitions:</span></span>  
  
-   <span data-ttu-id="c7e20-140">서비스 계정</span><span class="sxs-lookup"><span data-stu-id="c7e20-140">Service account</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c7e20-141">연결 문자열 및 자격 증명</span><span class="sxs-lookup"><span data-stu-id="c7e20-141">connect string and credentials</span></span>  
  
-   <span data-ttu-id="c7e20-142">마스터 암호</span><span class="sxs-lookup"><span data-stu-id="c7e20-142">The master password</span></span>  
  
 <span data-ttu-id="c7e20-143">다른 모든 정의는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 저장되며 다른 컴퓨터의 이전 설치에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7e20-143">All the other definitions are stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and are available from the previous installation on another computer.</span></span>  
  
## <a name="in-this-documentation"></a><span data-ttu-id="c7e20-144">이 설명서의 내용</span><span class="sxs-lookup"><span data-stu-id="c7e20-144">In This Documentation</span></span>  
  
-   [<span data-ttu-id="c7e20-145">Attunity Oracle CDC Service 시스템 아키텍처</span><span class="sxs-lookup"><span data-stu-id="c7e20-145">Change Data Capture Service for Oracle by Attunity System Architecture</span></span>](change-data-capture-service-for-oracle-by-attunity-system-architecture.md)  
  
-   [<span data-ttu-id="c7e20-146">Oracle CDC Service</span><span class="sxs-lookup"><span data-stu-id="c7e20-146">The Oracle CDC Service</span></span>](the-oracle-cdc-service.md)  
  
-   [<span data-ttu-id="c7e20-147">Attunity Oracle CDC Service F1 도움말</span><span class="sxs-lookup"><span data-stu-id="c7e20-147">Change Data Capture Service for Oracle by Attunity F1 Help</span></span>](change-data-capture-service-for-oracle-by-attunity-f1-help.md)  
  
-   [<span data-ttu-id="c7e20-148">Attunity Oracle CDC Service 방법 가이드</span><span class="sxs-lookup"><span data-stu-id="c7e20-148">Change Data Capture Service for Oracle by Attunity How to Guide</span></span>](change-data-capture-service-for-oracle-by-attunity-how-to-guide.md)  
  
## <a name="see-also"></a><span data-ttu-id="c7e20-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c7e20-149">See Also</span></span>  
 [<span data-ttu-id="c7e20-150">Oracle CDC Service 작업</span><span class="sxs-lookup"><span data-stu-id="c7e20-150">Working with the Oracle CDC Service</span></span>](working-with-the-oracle-cdc-service.md)  
  
  
