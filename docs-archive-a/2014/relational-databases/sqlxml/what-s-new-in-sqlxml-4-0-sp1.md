---
title: SQLXML 4.0 s p 1의 새로운 기능&#39;| Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- SQLNCLI, SQLXML
- what's new [SQLXML]
- SQLXML, what's new
- migrating SQLXML applications
- redistributing SQLXML
- SQL Server Native Client, SQLXML
- side-by-side installations [SQLXML]
ms.assetid: 48f7720b-1705-402d-93ce-097ff1737877
author: rothja
ms.author: jroth
ms.openlocfilehash: 880937520385fbe6ce64be3fdfcbbf7d11c73741
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729348"
---
# <a name="what39s-new-in-sqlxml-40-sp1"></a><span data-ttu-id="2c660-102">SQLXML 4.0 s p 1의 새로운&#39;기능</span><span class="sxs-lookup"><span data-stu-id="2c660-102">What&#39;s New in SQLXML 4.0 SP1</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="2c660-103">SQLXML 4.0 SP1에는 다양한 업데이트와 향상된 기능이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-103">SQLXML 4.0 SP1 includes various updates and enhancements.</span></span> <span data-ttu-id="2c660-104">이 항목에서는 업데이트를 요약하고 사용 가능한 경우 자세한 정보 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-104">This topic summarizes the updates and provides links to more detailed information, where available.</span></span> <span data-ttu-id="2c660-105">SQLXML 4.0 SP1에서는 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]에서 도입된 새로운 데이터 형식을 지원하기 위한 향상된 기능을 추가로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-105">SQLXML 4.0 SP1 provides additional enhancements to support the new data types introduced in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span> <span data-ttu-id="2c660-106">이 항목은 다음과 같은 주제로 이루어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-106">This topic includes the following subjects:</span></span>  
  
-   <span data-ttu-id="2c660-107">SQLXML 4.0 SP1 설치</span><span class="sxs-lookup"><span data-stu-id="2c660-107">Installing SQLXML 4.0 SP1</span></span>  
  
-   <span data-ttu-id="2c660-108">병렬 설치 문제</span><span class="sxs-lookup"><span data-stu-id="2c660-108">Side-by-Side Installation Issues</span></span>  
  
-   <span data-ttu-id="2c660-109">SQLXML 4.0 및 MSXML</span><span class="sxs-lookup"><span data-stu-id="2c660-109">SQLXML 4.0 and MSXML</span></span>  
  
-   <span data-ttu-id="2c660-110">SQLXML 4.0 재배포</span><span class="sxs-lookup"><span data-stu-id="2c660-110">Redistributing SQLXML 4.0</span></span>  
  
-   <span data-ttu-id="2c660-111">Native Client에 대 한 지원 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c660-111">Support for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client</span></span>  
  
-   <span data-ttu-id="2c660-112">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서 도입된 데이터 형식 지원</span><span class="sxs-lookup"><span data-stu-id="2c660-112">Support for Data Types Introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]</span></span>  
  
-   <span data-ttu-id="2c660-113">SQLXML 4.0에 대한 XML 대량 로드 변경 내용</span><span class="sxs-lookup"><span data-stu-id="2c660-113">XML Bulk Load Changes for SQLXML 4.0</span></span>  
  
-   <span data-ttu-id="2c660-114">SQLXML 4.0에 대한 레지스트리 키 변경 내용</span><span class="sxs-lookup"><span data-stu-id="2c660-114">Registry Key Changes for SQLXML 4.0</span></span>  
  
-   <span data-ttu-id="2c660-115">마이그레이션 문제</span><span class="sxs-lookup"><span data-stu-id="2c660-115">Migration Issues</span></span>  
  
## <a name="installing-sqlxml-40-sp1"></a><span data-ttu-id="2c660-116">SQLXML 4.0 SP1 설치</span><span class="sxs-lookup"><span data-stu-id="2c660-116">Installing SQLXML 4.0 SP1</span></span>  
 <span data-ttu-id="2c660-117">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이전에 SQLXML 4.0은 SQL Server와 함께 제공되었으며 SQL Server Express를 제외한 모든 버전의 SQL Server에 기본적으로 함께 설치되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-117">Before [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], SQLXML 4.0 was released with SQL Server and was part of the default installation of all SQL Server versions except for SQL Server Express.</span></span> <span data-ttu-id="2c660-118">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]부터는 최신 버전의 SQLXML(SQLXML 4.0 SP1)이 더 이상 SQL Server에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-118">Starting with [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the latest version of SQLXML (SQLXML 4.0 SP1) is no longer included in SQL Server.</span></span> <span data-ttu-id="2c660-119">SQLXML 4.0 s p 1을 설치 하려면 SQLXML 4.0 s p 1 [의 설치 위치](https://www.microsoft.com/download/details.aspx?id=30403)에서 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-119">To install SQLXML 4.0 SP1, download it from [Install Location for SQLXML 4.0 SP1](https://www.microsoft.com/download/details.aspx?id=30403).</span></span>  
  
 <span data-ttu-id="2c660-120">SQLXML 4.0 SP1 파일은 다음 위치에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-120">The SQLXML 4.0 SP1 files are installed in the following location:</span></span>  
  
 `%PROGRAMFILES%\SQLXML 4.0\`  
  
> [!NOTE]  
>  <span data-ttu-id="2c660-121">설치 프로세스의 일부로 SQLXML 4.0에 적합한 모든 레지스트리 설정이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-121">All appropriate registry settings for SQLXML 4.0 are made as part of the installation process.</span></span>  
  
 <span data-ttu-id="2c660-122">64비트 Windows 운영 체제의 Windows on Windows(WOW64)에서 32비트 SQLXML 애플리케이션을 실행하려면 sqlxml4.msi라는 64비트 SQLXML 4.0 SP1 패키지를 실행해야 합니다. 이 패키지는 다운로드 센터에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-122">To allow 32-bit SQLXML applications to run under Windows on Windows (WOW64) on 64-bit Windows operating systems, run the 64-bit SQLXML 4.0 SP1 package, named sqlxml4.msi, which can be found on the Download Center.</span></span>  
  
#### <a name="uninstalling-sqlxml-40-sp1"></a><span data-ttu-id="2c660-123">SQLXML 4.0 SP1 제거</span><span class="sxs-lookup"><span data-stu-id="2c660-123">Uninstalling SQLXML 4.0 SP1</span></span>  
 <span data-ttu-id="2c660-124">SQLXML 3.0 SP3, SQLXML 4.0 및 SQLXML 4.0 SP1 사이에는 공유되는 레지스트리 키가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-124">Shared registry keys exist between SQLXML 3.0 SP3, SQLXML 4.0 and SQLXML 4.0 SP1.</span></span> <span data-ttu-id="2c660-125">SQLXML 3.0 SP3이 설치되어 있는 컴퓨터에서 이후 버전의 SQLXML을 제거한 경우 SQLXML 3.0 SP3을 다시 설치해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-125">If the later versions of SQLXML are uninstalled on the same computer which contains SQLXML 3.0 SP3, you might need to reinstall SQLXML 3.0 SP3.</span></span>  
  
## <a name="side-by-side-installation-issues"></a><span data-ttu-id="2c660-126">병렬 설치 문제</span><span class="sxs-lookup"><span data-stu-id="2c660-126">Side-by-Side Installation Issues</span></span>  
 <span data-ttu-id="2c660-127">SQLXML 4.0 설치 프로세스에서는 이전 버전의 SQLXML에 의해 설치된 파일을 제거하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-127">The installation process for SQLXML 4.0 does not remove the files that were installed by earlier versions of SQLXML.</span></span> <span data-ttu-id="2c660-128">따라서 버전별 여러 SQLXML 설치에 대한 DLL이 컴퓨터에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-128">Therefore, you can have DLLs for several different version-distinctive installations of SQLXML on your computer.</span></span> <span data-ttu-id="2c660-129">이러한 함께 설치를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-129">You can run the installations side-by-side.</span></span> <span data-ttu-id="2c660-130">SQLXML 4.0에는 버전 독립 및 버전 종속 PROGID가 모두 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-130">SQLXML 4.0 includes both version-independent and version-dependent PROGIDs.</span></span> <span data-ttu-id="2c660-131">모든 프로덕션 애플리케이션은 버전 종속 PROGID를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-131">All production applications should use version-dependent PROGIDs.</span></span>  
  
## <a name="sqlxml-40-sp1-and-msxml"></a><span data-ttu-id="2c660-132">SQLXML 4.0 SP1 및 MSXML</span><span class="sxs-lookup"><span data-stu-id="2c660-132">SQLXML 4.0 SP1 and MSXML</span></span>  
 <span data-ttu-id="2c660-133">SQLXML 4.0은 MSXML을 설치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-133">SQLXML 4.0 does not install MSXML.</span></span> <span data-ttu-id="2c660-134">SQLXML 4.0은 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이후 설치의 일부로 설치되는 MSXML 6.0을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-134">SQLXML 4.0 uses MSXML 6.0, which is installed as part of the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later installation.</span></span>  
  
## <a name="redistributing-sqlxml-40-sp1"></a><span data-ttu-id="2c660-135">SQLXML 4.0 SP1 재배포</span><span class="sxs-lookup"><span data-stu-id="2c660-135">Redistributing SQLXML 4.0 SP1</span></span>  
 <span data-ttu-id="2c660-136">재배포 가능 설치 관리자 패키지를 사용하여 SQLXML 4.0 SP1을 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-136">You can distribute SQLXML 4.0 SP1 using the redistributable installer package.</span></span> <span data-ttu-id="2c660-137">여러 패키지를 단일 설치인 것처럼 보이게 설치하려는 경우 chainer와 부트스트래퍼 기술을 사용하는 것이 하나의 방법이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-137">One way to install multiple packages in what seems to the user to be a single installation is to use chainer and bootstrapper technology.</span></span> <span data-ttu-id="2c660-138">자세한 내용은 Visual Studio 2005용 사용자 지정 부트스트래퍼 패키지 작성 및 사용자 지정 필수 구성 요소 추가를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2c660-138">For more information, see Authoring a Custom Bootstrapper Package for Visual Studio 2005 and Adding Custom Prerequisites.</span></span>  
  
 <span data-ttu-id="2c660-139">애플리케이션을 처음에 개발된 플랫폼이 아니라 다른 플랫폼에서 사용하려는 경우에는 Microsoft 다운로드 센터에서 x64, Itanium 및 x86용 sqlncli.msi 버전을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-139">If your application targets a platform other than the one it was developed on, you can download versions of sqlncli.msi for x64, Itanium, and x86 from the Microsoft Download Center.</span></span>  
  
 <span data-ttu-id="2c660-140">MSXML 6.0용 개별 재배포 설치 프로그램(msxml6.msi)도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-140">There are also separate redistribution installation programs for MSXML 6.0 (msxml6.msi).</span></span> <span data-ttu-id="2c660-141">해당 프로그램은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 CD의 다음 위치에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-141">These can be found on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation CD in the following location:</span></span>  
  
 `%CD%\Setup\`  
  
 <span data-ttu-id="2c660-142">이러한 설치 파일을 사용하여 CD에서 직접 MSXML 6.0을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-142">These installation files can be used to install MSXML 6.0 directly from the CD.</span></span> <span data-ttu-id="2c660-143">사용자 지정 애플리케이션과 함께 MSXML 6.0 및 SQLXML 4.0 SP1을 자유롭게 재배포하는 데 설치 파일을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-143">They can also be used to freely redistribute MSXML 6.0 along with SQLXML 4.0 SP1 with your own custom applications.</span></span>  
  
 <span data-ttu-id="2c660-144">애플리케이션에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client를 데이터 공급자로 사용하는 경우 이 프로그램도 재배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-144">You will also need to redistribute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client if you are using it as the data provider with your application.</span></span> <span data-ttu-id="2c660-145">자세한 내용은 [Installing SQL Server Native Client](../native-client/applications/installing-sql-server-native-client.md)(SQL Server Native Client 설치)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2c660-145">For more information, see [Installing SQL Server Native Client](../native-client/applications/installing-sql-server-native-client.md).</span></span>  
  
## <a name="support-for-sql-server-native-client"></a><span data-ttu-id="2c660-146">SQL Server Native Client 지원</span><span class="sxs-lookup"><span data-stu-id="2c660-146">Support for SQL Server Native Client</span></span>  
 <span data-ttu-id="2c660-147">SQLXML 4.0은 SQLOLEDB 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 공급자를 모두 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-147">SQLXML 4.0 supports both the SQLOLEDB and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client providers.</span></span> <span data-ttu-id="2c660-148">Native client는 동일한 버전의 native Client 공급자를 사용 하는 것이 좋습니다. native client는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `Date, Time` `DateTime2` 및 `dateTimeOffset` 데이터 형식과 같이 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] native client에서 지 원하는의, 및 데이터 형식과 같이 서버에 제공 되는 새로운 데이터 형식을 지원 하도록 개발 되었습니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2c660-148">It is recommended that you use the same version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client provider and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is developed to support any new data types that ship in the server, such as the `Date, Time`, `DateTime2`, and `dateTimeOffset` data types in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and supported by [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2c660-149">Native Client는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에 처음 도입된 데이터 액세스 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-149">Native Client is a data access technology that was introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="2c660-150">이 기술은 SQLOLEDB 공급자와 SQLODBC 드라이버를 하나의 네이티브 DLL(동적 링크 라이브러리)로 조합한 것이며 MDAC(Microsoft Data Access Components)와는 분리된 고유한 새 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-150">It combines the SQLOLEDB Provider and the SQLODBC Driver into one native dynamic link library (DLL), while also providing new functionality that is separate and distinct from the Microsoft Data Access Components (MDAC).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2c660-151">Native Client를 사용하여 새 애플리케이션을 만들 수도 있고 MDAC 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows의 SQLOLEDB 및 SQLODBC에서 지원하지 않지만 [!INCLUDE[msCoName](../../includes/msconame-md.md)]에 도입된 기능을 활용해야 하는 기존 애플리케이션을 향상시킬 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-151">Native Client can be used to create new applications or enhance existing applications that need to take advantage of features introduced in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are not supported by SQLOLEDB and SQLODBC in MDAC and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.</span></span> <span data-ttu-id="2c660-152">예를 들어 FOR XML 같은 클라이언트 쪽 SQLXML 기능에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 사용하려면 `xml` Native Client가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-152">For example, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is required for client-side SQLXML features, such as FOR XML, to use the `xml` data type.</span></span> <span data-ttu-id="2c660-153">자세한 내용은 [클라이언트 쪽 XML 서식 &#40;sqlxml 4.0&#41;](formatting/client-side-xml-formatting-sqlxml-4-0.md), [ADO를 사용 하 여 Sqlxml 4.0 쿼리 실행](using-ado-to-execute-sqlxml-4-0-queries.md)및 [SQL Server Native Client 프로그래밍](../native-client/sql-server-native-client-programming.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2c660-153">For more information, see [Client-side XML Formatting &#40;SQLXML 4.0&#41;](formatting/client-side-xml-formatting-sqlxml-4-0.md), [Using ADO to Execute SQLXML 4.0 Queries](using-ado-to-execute-sqlxml-4-0-queries.md), and [SQL Server Native Client Programming](../native-client/sql-server-native-client-programming.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2c660-154">SQLXML 4.0은 SQLXML 3.0과 완전히 호환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-154">SQLXML 4.0 is not completely backward compatible with SQLXML 3.0.</span></span> <span data-ttu-id="2c660-155">일부 버그 수정 및 기타 기능 변경, 특히 SQLXML ISAPI 지원 제거로 인해 SQLXML 4.0에서는 IIS 가상 디렉터리를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-155">Because of some bug fixes and other functional changes, particularly the removal of SQLXML ISAPI support, you cannot use IIS virtual directories with SQLXML 4.0.</span></span> <span data-ttu-id="2c660-156">대부분의 애플리케이션은 약간만 수정해도 실행되지만 SQLXML 4.0과 함께 프로덕션에 배치하기 전에 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-156">Although most applications will run with minor modifications, you must test them before putting them into production with SQLXML 4.0.</span></span>  
  
## <a name="support-for-data-types-introduced-in-sql-server-2005-and-sql-server-2008"></a><span data-ttu-id="2c660-157">SQL Server 2005 및 SQL Server 2008에 도입된 데이터 형식 지원</span><span class="sxs-lookup"><span data-stu-id="2c660-157">Support for Data Types Introduced in SQL Server 2005 and SQL Server 2008</span></span>  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<span data-ttu-id="2c660-158">는 `xml` 데이터 형식을 도입 했으며 SQLXML 4.0는 `xml` 데이터 형식을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-158">introduced the `xml` data type, and SQLXML 4.0 supports the `xml` data type.</span></span> <span data-ttu-id="2c660-159">자세한 내용은 [SQLXML 4.0의 Xml 데이터 형식 지원](xml-data-type-support-in-sqlxml-4-0.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2c660-159">For more information, see [xml Data Type Support in SQLXML 4.0](xml-data-type-support-in-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="2c660-160">XML 뷰를 매핑하거나, XML을 대량 로드하거나, XML Updategram을 실행할 때 SQLXML에서 `xml` 데이터 형식을 사용하는 방법의 예는 다음 항목에 제공된 예를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2c660-160">For examples of how to use the `xml` data type in SQLXML when mapping XML views, bulk loading XML or executing XML updategrams, refer to examples provided in the following topics.</span></span>  
  
-   [<span data-ttu-id="2c660-161">테이블 및 열에 대한 XSD 요소 및 특성의 기본 매핑</span><span class="sxs-lookup"><span data-stu-id="2c660-161">Default Mapping of XSD Elements and Attributes to Tables and Columns</span></span>](../sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
  
-   [<span data-ttu-id="2c660-162">XML Updategram을 사용하여 데이터 삽입</span><span class="sxs-lookup"><span data-stu-id="2c660-162">Inserting Data by Using XML Updategrams</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)  
  
-   [<span data-ttu-id="2c660-163">XML 문서 대량 로드 예</span><span class="sxs-lookup"><span data-stu-id="2c660-163">Examples of Bulk Loading XML Documents</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)  
  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]<span data-ttu-id="2c660-164">에는 `Date, Time` , `DateTime2` 및 **DateTimeOffset** 데이터 형식이 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-164">introduced the `Date, Time`, `DateTime2`, and **DateTimeOffset** data types.</span></span> <span data-ttu-id="2c660-165">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에 기본 제공되는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client OLE DB Provider(SQLNCLI11)와 함께 SQLXML 4.0 SP1을 사용하는 경우 이러한 네 가지 새로운 데이터 형식이 기본 제공 스칼라 형식으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-165">SQLXML 4.0 SP1 will enable these four new data types as built-in scalar types when used with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client OLE DB Provider (SQLNCLI11), which ships in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="xml-bulk-load-changes-for-sqlxml-40-sp1"></a><span data-ttu-id="2c660-166">SQLXML 4.0 SP1에 대한 XML 대량 로드 변경 내용</span><span class="sxs-lookup"><span data-stu-id="2c660-166">XML Bulk Load Changes for SQLXML 4.0 SP1</span></span>  
  
-   <span data-ttu-id="2c660-167">SQLXML 4.0의 경우 데이터 형식을 사용 하 여 SchemaGen 오버플로 필드가 생성 됩니다 `xml` .</span><span class="sxs-lookup"><span data-stu-id="2c660-167">For SQLXML 4.0, the SchemaGen overflow field is created using the `xml` data type.</span></span> <span data-ttu-id="2c660-168">자세한 내용은 [SQL SERVER XML 대량 로드 개체 모델](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/sql-server-xml-bulk-load-object-model-sqlxml-4-0.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2c660-168">For more information, see [SQL Server XML Bulk Load Object Model](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/sql-server-xml-bulk-load-object-model-sqlxml-4-0.md).</span></span>  
  
-   <span data-ttu-id="2c660-169">이전에 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic 애플리케이션을 만들었으며 SQLXML 4.0을 사용하려는 경우 Xblkld4.dll을 참조하여 애플리케이션을 다시 컴파일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-169">If you have previously created [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic applications and you want to use SQLXML 4.0, you must recompile the application with reference to Xblkld4.dll.</span></span>  
  
-   <span data-ttu-id="2c660-170">Visual Basic Scripting Edition 애플리케이션의 경우 사용할 DLL을 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-170">For Visual Basic Scripting Edition applications, you must register the DLL you want to use.</span></span> <span data-ttu-id="2c660-171">다음 예에서 버전 독립 PROGID를 지정하면 애플리케이션은 마지막으로 등록된 DLL을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-171">In the following example, if you specify version-independent PROGIDs, the application depends on the last registered DLL:</span></span>  
  
    ```  
    set objBulkLoad = CreateObject("SQLXMLBulkLoad.SQLXMLBulkLoad")   
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="2c660-172">버전 종속 PROGID는 SQLXMLBulkLoad.SQLXMLBulkLoad.4.0입니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-172">The version-dependent PROGID is SQLXMLBulkLoad.SQLXMLBulkLoad.4.0.</span></span>  
  
## <a name="registry-key-changes-for-sqlxml-40"></a><span data-ttu-id="2c660-173">SQLXML 4.0에 대한 레지스트리 키 변경 내용</span><span class="sxs-lookup"><span data-stu-id="2c660-173">Registry Key Changes for SQLXML 4.0</span></span>  
 <span data-ttu-id="2c660-174">SQLXML 4.0에서는 이전 버전의 레지스트리 키가 다음으로 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-174">In SQLXML 4.0, the registry keys have changed from the earlier releases to the following:</span></span>  
  
 <span data-ttu-id="2c660-175">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\TemplateCacheSize</span><span class="sxs-lookup"><span data-stu-id="2c660-175">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\TemplateCacheSize</span></span>  
  
 <span data-ttu-id="2c660-176">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\SchemaCacheSize</span><span class="sxs-lookup"><span data-stu-id="2c660-176">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\SchemaCacheSize</span></span>  
  
 <span data-ttu-id="2c660-177">SQLXML 4.0에 대해 이러한 키를 적용하려는 경우 설정을 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-177">You must change the settings if you want these keys to be in effect for SQLXML 4.0.</span></span>  
  
 <span data-ttu-id="2c660-178">또한 SQLXML 4.0에서는 다음 레지스트리 키가 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-178">In addition, SQLXML 4.0 introduces the following registry keys:</span></span>  
  
-   `HKEY_LOCAL_MACHINE\Software\Microsoft\MSSQLServer\Client\SQLXML4\ReportErrorsWithSQLInfo`  
  
     <span data-ttu-id="2c660-179">기본적으로 SQLXML 4.0은 이전 버전의 SQLXML과 같이 고급 SQLXML 오류를 반환하는 대신 OLE DB 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 제공하는 원시 오류 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-179">By default, SQLXML 4.0 returns native error information provided by OLE DB and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instead of a high-level SQLXML error (as was the case in earlier versions of SQLXML).</span></span> <span data-ttu-id="2c660-180">이 동작을 사용하지 않으려면 DWORD 유형의 이 레지스트리 키 값을 0으로 설정해야 합니다(기본값은 1임).</span><span class="sxs-lookup"><span data-stu-id="2c660-180">If you do not want this behavior, the value of this registry key of type DWORD must be set to 0 (default is 1).</span></span>  
  
-   <span data-ttu-id="2c660-181">HKEY_LOCAL_MACHINE\Software\Microsoft\MSSQLServer\Client\SQLXML4\FORXML_GenerateGUIDBraces</span><span class="sxs-lookup"><span data-stu-id="2c660-181">HKEY_LOCAL_MACHINE\Software\Microsoft\MSSQLServer\Client\SQLXML4\FORXML_GenerateGUIDBraces</span></span>  
  
     <span data-ttu-id="2c660-182">기본적으로 SQLXML은 묶는 괄호 없이 SQL Server GUID 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-182">By default, SQLXML return SQL Server GUID values without the enclosing braces.</span></span> <span data-ttu-id="2c660-183">GUID 값을 중괄호와 함께 반환 하려면 (예: {*SOME GUID*})이 레지스트리 키의 값을 1로 설정 해야 합니다 (기본값은 0).</span><span class="sxs-lookup"><span data-stu-id="2c660-183">If you want the GUID value returned with the braces (for example, {*some GUID*}), value of this registry key must be set to 1 (default is 0).</span></span>  
  
-   <span data-ttu-id="2c660-184">HKEY_LOCAL_MACHINE\Software\Microsoft\MSSQLServer\Client\SQLXML4\SQL2000CompatMode</span><span class="sxs-lookup"><span data-stu-id="2c660-184">HKEY_LOCAL_MACHINE\Software\Microsoft\MSSQLServer\Client\SQLXML4\SQL2000CompatMode</span></span>  
  
     <span data-ttu-id="2c660-185">기본적으로 XML 파서가 데이터를 로드할 때 XML 1.0 규칙에 따라 공백이 정규화됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-185">By default, when the XML parser loads the data, white spaces are normalized according to the XML 1.0 rules.</span></span> <span data-ttu-id="2c660-186">이로 인해 데이터의 일부 공백 문자가 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-186">This results in loss of some of the white space characters in your data.</span></span> <span data-ttu-id="2c660-187">따라서 의미상으로는 데이터가 같지만 구문 분석 후에 데이터의 텍스트 표현이 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-187">Thus, the textual representation of your data may not be the same after parsing, although semantically the data is the same.</span></span>  
  
     <span data-ttu-id="2c660-188">이 키는 데이터의 공백 문자를 유지할 수 있도록 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-188">This key is introduced so that you can choose to keep the white space characters in the data.</span></span> <span data-ttu-id="2c660-189">이 레지스트리 키를 추가하고 해당 값을 0으로 설정하면 특성 값의 경우 XML의 공백 문자(LF, CR 및 탭)가 인코딩되어 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-189">If you add this registry key and set its value to 0, white space characters (LF, CR, and tab) in the XML are returned encoded in case of attribute values.</span></span> <span data-ttu-id="2c660-190">요소 값의 경우 CR만 인코딩되어 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-190">In case of element values, only CR is returned encoded.</span></span>  
  
     <span data-ttu-id="2c660-191">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-191">For example:</span></span>  
  
    ```  
    CREATE TABLE T( Col1 int, Col2 nvarchar(100));  
    GO  
    -- Insert data with tab, line feed and carriage return).  
    INSERT INTO T VALUES (1, 'This is a tab    . This is a line feed and CR   
     more text');  
    GO  
    -- Test this query (without the registry key).  
    SELECT * FROM T   
    FOR XML AUTO;  
    -- This is the result (no encoding of special characters).  
    <?xml version="1.0" encoding="utf-8" ?>  
    <r>  
      <T Col1="1"   
         Col2="This is a tab    . This is a line feed and CR   
     more text"/>  
    </r>  
    -- Now add registry key with value 0 and execute the query again.  
    -- Note the encoding for carriage return, line-feed and tab in the attribute value.  
    <?xml version="1.0" encoding="utf-8" ?>  
    <r>  
      <T Col1="1"   
         Col2="This is a tab    . This is a line feed and CR   
     more text"/>  
    </r>  
  
    -- Update the query and specify ELEMENTS directive  
    SELECT * FROM T  
    FOR XML AUTO, ELEMENTS  
    -- Only the carriage return is returned encoded.  
    <?xml version="1.0" encoding="utf-8" ?>  
    <r>  
       <T>  
          <Col1>1</Col1>  
          <Col2>This is a tab    . This is a line feed and CR   
     more text</Col2>  
       </T>  
    </r>  
    ```  
  
## <a name="migration-issues"></a><span data-ttu-id="2c660-192">마이그레이션 문제</span><span class="sxs-lookup"><span data-stu-id="2c660-192">Migration Issues</span></span>  
 <span data-ttu-id="2c660-193">다음은 SQLXML 4.0로의 레거시 SQLXML 애플리케이션 마이그레이션에 영향을 줄 수 있는 문제입니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-193">The following are issues that could impact migration of your legacy SQLXML applications to SQLXML 4.0.</span></span>  
  
### <a name="ado-and-sqlxml-40-queries"></a><span data-ttu-id="2c660-194">ADO 및 SQLXML 4.0 쿼리</span><span class="sxs-lookup"><span data-stu-id="2c660-194">ADO and SQLXML 4.0 Queries</span></span>  
 <span data-ttu-id="2c660-195">SQLXML의 이전 버전에서는 IIS 가상 디렉터리와 SQLXML ISAPI 필터를 사용한 URL 기반 쿼리 실행에 대한 지원이 제공되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-195">In earlier versions of SQLXML, support for URL-based query execution using IIS virtual directories and the SQLXML ISAPI filter was provided.</span></span> <span data-ttu-id="2c660-196">SQLXML 4.0을 사용하는 애플리케이션에서는 더 이상 이 지원을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-196">For applications that use SQLXML 4.0, this support is no longer available.</span></span>  
  
 <span data-ttu-id="2c660-197">대신 MDAC(Microsoft Data Access Components) 2.6 이상 버전에서 처음 도입된 ADO(ActiveX Data Objects)에 대한 SQLXML 확장을 사용하여 SQLXML 쿼리, 템플릿 및 Updategram을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-197">Instead, SQLXML queries, templates, and updategrams can be executed by using the SQLXML extensions to ActiveX Data Objects (ADO) first introduced in Microsoft Data Access Components (MDAC) 2.6 and later.</span></span>  
  
 <span data-ttu-id="2c660-198">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2c660-198">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="supportability-for-sqlxml-30-isapi-and-data-types-introduced-in-sql-server-2005"></a><span data-ttu-id="2c660-199">SQL Server 2005에서 도입된 데이터 형식 및 SQLXML 3.0 ISAPI 지원 가능성</span><span class="sxs-lookup"><span data-stu-id="2c660-199">Supportability for SQLXML 3.0 ISAPI and Data Types Introduced in SQL Server 2005</span></span>  
 <span data-ttu-id="2c660-200">SQLXML 4.0에서 ISAPI 지원이 제거 되었으므로 솔루션에 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [xml 데이터 형식](/sql/t-sql/xml/xml-transact-sql) 또는 [udt (사용자 정의 데이터 형식)](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) , 웹 기반 액세스 등의 향상 된 데이터 형식 지정 기능이 필요한 경우 [sqlxml 관리 되는 클래스](../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md) 와 같은 다른 솔루션이 나 SQL Server 2005 용 네이티브 XML 웹 서비스와 같은 다른 유형의 HTTP 처리기를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-200">Because ISAPI support has been removed from SQLXML 4.0, if your solution requires the enhanced data typing features introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] such as the [xml data type](/sql/t-sql/xml/xml-transact-sql) or [user-defined data types (UDTs)](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) and Web-based access, you will need to use another solution such as [SQLXML managed classes](../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md) or another type of HTTP handler, such as Native XML Web Services for SQL Server 2005.</span></span>  
  
 <span data-ttu-id="2c660-201">또는 이러한 형식 확장이 필요 하지 않은 경우 SQLXML 3.0을 계속 사용 하 여 및 설치에 연결할 수 있습니다 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2c660-201">Alternately, if you do not require these type extensions, you can continue to use SQLXML 3.0 to connect to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] installations.</span></span> <span data-ttu-id="2c660-202">SQLXML 3.0 ISAPI 지원은 이러한 이후 버전에서 작동하지만 `xml`에서 도입된 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 데이터 형식 또는 UDT 유형 지원을 지원하거나 인식하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-202">The SQLXML 3.0 ISAPI support will work against these later versions but does not support or recognize the `xml` data type or UDT type support introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
### <a name="xml-bulk-load-security-changes-for-temporary-files"></a><span data-ttu-id="2c660-203">임시 파일에 대한 XML 대량 로드 보안 변경</span><span class="sxs-lookup"><span data-stu-id="2c660-203">XML Bulk Load Security Changes for Temporary Files</span></span>  
 <span data-ttu-id="2c660-204">SQLXML 4.0 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 경우 XML 대량 로드 파일 권한이 대량 로드 작업을 실행하는 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-204">For SQLXML 4.0 and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], XML Bulk Load file permissions are granted to the user executing the bulk load operation.</span></span> <span data-ttu-id="2c660-205">읽기 및 쓰기 권한은 파일 시스템에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-205">Read and Write permissions are inherited from the file system.</span></span> <span data-ttu-id="2c660-206">SQLXML 및 SQL Server의 이전 버전에서는 SQLXML 하의 XML 대량 로드 시 보안이 유지되지 않고 모든 사용자가 읽을 수 있는 임시 파일이 만들어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-206">In previous releases of SQLXML and SQL Server, XML Bulk Load under SQLXML would create temporary files that were not secured and could be readable by anyone.</span></span>  
  
### <a name="migration-issues-for-client-side-for-xml"></a><span data-ttu-id="2c660-207">클라이언트 쪽 FOR XML에 대한 마이그레이션 문제</span><span class="sxs-lookup"><span data-stu-id="2c660-207">Migration Issues for Client-Side FOR XML</span></span>  
 <span data-ttu-id="2c660-208">실행 엔진의 변경으로 인해에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기본 테이블에 대 한 메타 데이터의 다른 값을 반환 하는 경우에는 FOR XML 쿼리가 실행 될 때 반환 됩니다 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2c660-208">Due to changes in the execution engine, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might return different values in the metadata for a base table than would be returned if the FOR XML query was executed under [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="2c660-209">이 경우 FOR XML 쿼리 결과에 대한 클라이언트 쪽 형식 지정으로 인해 쿼리가 실행되는 버전에 따라 다른 출력이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-209">In cases where this occurs, client-side formatting of the FOR XML query results will have differing output depending on which version the query is run against.</span></span>  
  
 <span data-ttu-id="2c660-210">`xml` 데이터 형식 열에 대해 SQLXML 3.0을 사용하여 클라이언트 쪽에서 FOR XML 쿼리를 실행하는 경우 결과 데이터가 완전히 엔터티화된 문자열로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-210">If a FOR XML query is executed client-side using SQLXML 3.0 over an `xml` data type column, the data in the results will come back as a fully entitized string.</span></span> <span data-ttu-id="2c660-211">SQLXML 4.0에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client(SQLNCLI11)를 공급자로 지정하면 데이터가 XML로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c660-211">In SQLXML 4.0, if the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) is specified as the provider, the data will be returned as XML.</span></span>  
  
  
