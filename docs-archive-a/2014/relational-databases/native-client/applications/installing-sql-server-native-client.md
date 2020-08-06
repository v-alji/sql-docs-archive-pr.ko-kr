---
title: SQL Server Native Client 설치 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, uninstalling
- SQLNCLI, installing
- SQLNCLI, uninstalling
- Setup [SQL Server Native Client]
- uninstalling SQL Server Native Client
- data access [SQL Server Native Client], uninstalling SQL Server Native Client
- installing SQL Server Native Client
- SQL Server Native Client, installing
- data access [SQL Server Native Client], installing SQL Server Native Client
- removing SQL Server Native Client
ms.assetid: c6abeab2-0052-49c9-be79-cfbc50bff5c1
author: rothja
ms.author: jroth
ms.openlocfilehash: 86a30924dc6dfc0b5b4f4dc176f0186d8f35b2f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652073"
---
# <a name="installing-sql-server-native-client"></a><span data-ttu-id="0b903-102">SQL Server Native Client 설치</span><span class="sxs-lookup"><span data-stu-id="0b903-102">Installing SQL Server Native Client</span></span>
  <span data-ttu-id="0b903-103">Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0은 [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]을(를) 설치할 때 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b903-103">Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 is installed when you install [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)].</span></span> <span data-ttu-id="0b903-104">[!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Native Client는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0b903-104">There is no [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Native Client.</span></span> <span data-ttu-id="0b903-105">자세한 내용은 [SQL Server Native Client의 새로운 기능](../sql-server-native-client.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0b903-105">For more information, see [What's New in SQL Server Native Client](../sql-server-native-client.md).</span></span> <span data-ttu-id="0b903-106">sqlncli.msi는 SQL Server 2012 기능 팩 웹 페이지에서도 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b903-106">You can also get sqlncli.msi from the SQL Server 2012 Feature Pack web page.</span></span> <span data-ttu-id="0b903-107">최신 버전의 SQL Server Native Client을 다운로드 하려면 [Microsoft?? SQL Server?? 2012 SP2 기능 팩](https://www.microsoft.com/download/details.aspx?id=43339)</span><span class="sxs-lookup"><span data-stu-id="0b903-107">To download the most recent version of the SQL Server Native Client, go to [Microsoft?? SQL Server?? 2012 SP2 Feature Pack](https://www.microsoft.com/download/details.aspx?id=43339).</span></span> <span data-ttu-id="0b903-108">SQL Server 2012 이전 버전의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client도 컴퓨터에 설치되어 있으면 이전 버전과 함께 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0이 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b903-108">If a previous version of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client earlier than SQL Server 2012 is also installed on the computer, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 will be installed side-by-side with the earlier version.</span></span>  
  
 <span data-ttu-id="0b903-109">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 파일(sqlncli11.dll, sqlnclir11.rll 및 s11ch_sqlncli.chm)은 다음 위치에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b903-109">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client files (sqlncli11.dll, sqlnclir11.rll, and s11ch_sqlncli.chm) are installed to the following location:</span></span>  
  
 `%SYSTEMROOT%\system32\`  
  
> [!NOTE]  
>  <span data-ttu-id="0b903-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자 및 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버에 대한 모든 적절한 레지스트리 설정은 설치 프로세스의 일부로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b903-110">All appropriate registry settings for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver are made as part of the installation process.</span></span>  
  
 <span data-ttu-id="0b903-111">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 헤더 및 라이브러리 파일(sqlncli.h 및 sqlncli11.lib)은 다음 위치에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b903-111">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client header and library files (sqlncli.h and sqlncli11.lib) are installed in the following location:</span></span>  
  
 `%PROGRAMFILES%\Microsoft SQL Server\110\SDK`  
  
 <span data-ttu-id="0b903-112">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 설치의 일부로 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client를 설치하는 방법 이외에 sqlncli.msi라는 재배포 가능 설치 프로그램을 사용할 수도 있습니다. sqlncli.msi는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 설치 디스크의 다음 위치에 있습니다. `%CD%\Setup\`</span><span class="sxs-lookup"><span data-stu-id="0b903-112">In addition to installing [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client as part of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation, there is also a redistributable installation program named sqlncli.msi, which can be found on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation disk in the following location: `%CD%\Setup\`.</span></span>  
  
 <span data-ttu-id="0b903-113">sqlncli.msi를 통해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b903-113">You can distribute [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client through sqlncli.msi.</span></span> <span data-ttu-id="0b903-114">애플리케이션을 배포할 때 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client를 설치해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b903-114">You might have to install [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client when you deploy an application.</span></span> <span data-ttu-id="0b903-115">여러 패키지를 단일 설치인 것처럼 보이게 설치하려는 경우 chainer와 부트스트래퍼 기술을 사용하는 것이 하나의 방법이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b903-115">One way to install multiple packages in what seems to the user to be a single installation is to use chainer and bootstrapper technology.</span></span> <span data-ttu-id="0b903-116">자세한 내용은 [Visual Studio 2005용 사용자 지정 부트스트래퍼 패키지 제작](https://go.microsoft.com/fwlink/?LinkId=115667) 및 [사용자 지정 필수 구성 요소 추가](https://go.microsoft.com/fwlink/?LinkId=115668)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0b903-116">For more information, see [Authoring a Custom Bootstrapper Package for Visual Studio 2005](https://go.microsoft.com/fwlink/?LinkId=115667) and [Adding Custom Prerequisites](https://go.microsoft.com/fwlink/?LinkId=115668).</span></span>  
  
 <span data-ttu-id="0b903-117">x64 및 Itanium 버전의 sqlncli.msi가 32비트 버전의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client도 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="0b903-117">The x64 and Itanium versions of sqlncli.msi also install the 32-bit version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="0b903-118">애플리케이션을 처음에 개발된 플랫폼이 아니라 다른 플랫폼에서 사용하려는 경우에는 Microsoft 다운로드 센터에서 x64, Itanium 및 x86용 sqlncli.msi 버전을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b903-118">If your application targets a platform other than the one it was developed on, you can download versions of sqlncli.msi for x64, Itanium, and x86 from the Microsoft Download Center.</span></span>  
  
 <span data-ttu-id="0b903-119">sqlncli.msi를 호출하면 클라이언트 구성 요소만 기본적으로 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b903-119">When you invoke sqlncli.msi, only the client components are installed by default.</span></span> <span data-ttu-id="0b903-120">클라이언트 구성 요소는 Native Client를 사용 하 여 개발 된 응용 프로그램을 실행할 수 있도록 지 원하는 파일입니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0b903-120">The client components are files that support running an application that was developed using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="0b903-121">SDK 구성 요소도 함께 설치하려면 명령줄에 `ADDLOCAL=All`을 지정하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b903-121">To also install the SDK components, specify `ADDLOCAL=All` on the command line.</span></span> <span data-ttu-id="0b903-122">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="0b903-122">For example:</span></span>  
  
 `msiexec /i sqlncli.msi ADDLOCAL=ALL APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
## <a name="silent-install"></a><span data-ttu-id="0b903-123">자동 설치</span><span class="sxs-lookup"><span data-stu-id="0b903-123">Silent Install</span></span>  
 <span data-ttu-id="0b903-124">msiexec 명령에 /passive, /qn, /qb, or /qr 옵션을 사용할 경우 IACCEPTSQLNCLILICENSETERMS=YES를 지정하여 최종 사용자 사용권 약관에 동의함을 명시적으로 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b903-124">If you use the /passive, /qn, /qb, or /qr option with msiexec, you must also specify IACCEPTSQLNCLILICENSETERMS=YES, to explicitly indicate that you accept the terms of the end user license.</span></span> <span data-ttu-id="0b903-125">이 옵션은 모두 대문자로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b903-125">This option must be specified in all capital letters.</span></span>  
  
## <a name="uninstalling-sql-server-native-client"></a><span data-ttu-id="0b903-126">SQL Server Native Client 제거</span><span class="sxs-lookup"><span data-stu-id="0b903-126">Uninstalling SQL Server Native Client</span></span>  
 <span data-ttu-id="0b903-127">서버 및 도구와 같은 응용 프로그램은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] native client에 종속 되므로 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 모든 종속 응용 프로그램이 제거 될 때까지 native client를 제거 하지 않는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b903-127">Because applications such as [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] server and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tools depend on [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, it is important not to uninstall [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client until all dependent applications are uninstalled.</span></span> <span data-ttu-id="0b903-128">응용 프로그램이 Native Client에 종속 된다는 경고를 공급자에 게 제공 하려면 다음과 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 같이 MSI에서 APPGUID 설치 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b903-128">To provider users with a warning that your application depends on [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, use the APPGUID install option in your MSI, as follows:</span></span>  
  
 `msiexec /i sqlncli.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
 <span data-ttu-id="0b903-129">APPGUID에는 제품 코드를 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b903-129">The value passed to APPGUID is your specific product code.</span></span> <span data-ttu-id="0b903-130">제품 코드는 Microsoft 설치 관리자를 사용하여 애플리케이션 설치 프로그램 번들을 작성할 때 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b903-130">A product code must be created when using Microsoft Installer to bundle your application setup program.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b903-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0b903-131">See Also</span></span>  
 <span data-ttu-id="0b903-132">[SQL Server Native Client를 사용 하 여 응용 프로그램 빌드](installing-sql-server-native-client.md) </span><span class="sxs-lookup"><span data-stu-id="0b903-132">[Building Applications with SQL Server Native Client](installing-sql-server-native-client.md) </span></span>  
 [<span data-ttu-id="0b903-133">설치 방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="0b903-133">Installation How-to Topics</span></span>](../../../sql-server/install/installation-how-to-topics.md)  
  
  
