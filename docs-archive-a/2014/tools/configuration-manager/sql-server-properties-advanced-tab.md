---
title: SQL Server 속성(고급 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 2ffd10fd-bac1-478f-9cff-96ed6c8b787f
author: stevestein
ms.author: sstein
ms.openlocfilehash: a9a77fd0a43627b49bb8719f6fa943408f64fcca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639193"
---
# <a name="sql-server-properties-advanced-tab"></a><span data-ttu-id="d0641-102">SQL Server 속성(고급 탭)</span><span class="sxs-lookup"><span data-stu-id="d0641-102">SQL Server Properties (Advanced Tab)</span></span>
  <span data-ttu-id="d0641-103">다음 속성은 기본적으로 **고급** 탭에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d0641-103">The following properties appear on the **Advanced** tab by default.</span></span> <span data-ttu-id="d0641-104">사용자 지정 속성을 정의한 경우 속성이 해당 값과 함께 이 탭에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d0641-104">If custom properties are defined, they also appear on this tab, with their values.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d0641-105">옵션</span><span class="sxs-lookup"><span data-stu-id="d0641-105">Options</span></span>  
 <span data-ttu-id="d0641-106">**클러스터형**</span><span class="sxs-lookup"><span data-stu-id="d0641-106">**Clustered**</span></span>  
 <span data-ttu-id="d0641-107">이 서비스가 클러스터형 서버의 리소스로 설치되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d0641-107">Indicates if this service is installed as a resource of a clustered server.</span></span>  
  
 <span data-ttu-id="d0641-108">**고객 의견 보내기**</span><span class="sxs-lookup"><span data-stu-id="d0641-108">**Customer Feedback Reporting**</span></span>  
 <span data-ttu-id="d0641-109">이 서비스에 대해 서비스 품질 모니터링이 활성화되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d0641-109">Indicates whether Service Quality Monitoring has been enabled on this service.</span></span> <span data-ttu-id="d0641-110">고객 의견 보고에 대한 자세한 내용은 온라인 설명서에서 "오류 및 사용 보고서 설정" 항목을 참고하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0641-110">For more information on Customer Feedback Reporting, search Books Online for the topic, "Error and Usage Report Settings."</span></span>  
  
 <span data-ttu-id="d0641-111">**데이터 경로**</span><span class="sxs-lookup"><span data-stu-id="d0641-111">**Data Path**</span></span>  
 <span data-ttu-id="d0641-112">이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치에 대한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]이진 파일 경로를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d0641-112">Displays the path to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] binaries for this installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d0641-113">**덤프 디렉터리**</span><span class="sxs-lookup"><span data-stu-id="d0641-113">**Dump Directory**</span></span>  
 <span data-ttu-id="d0641-114">오류 발생 시 메모리 덤프가 추가될 위치를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d0641-114">Displays the location where memory dumps are placed in case of an error.</span></span>  
  
 <span data-ttu-id="d0641-115">**오류 보고**</span><span class="sxs-lookup"><span data-stu-id="d0641-115">**Error Reporting**</span></span>  
 <span data-ttu-id="d0641-116">이 속성을 **예**로 설정하면 오류 발생 시 Dr. Watson 프로그램에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 또는 사용자의 오류 서버로 정보를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="d0641-116">When set to **Yes**, the Dr. Watson program forwards information to either [!INCLUDE[msCoName](../../includes/msconame-md.md)] or your error server if a serious failure occurs.</span></span> <span data-ttu-id="d0641-117">오류 보고에 대한 자세한 내용은 온라인 설명서에서 "오류 및 사용 보고서 설정" 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0641-117">For more information on Error Reporting, search Books Online for the topic, "Error and Usage Report Settings."</span></span> <span data-ttu-id="d0641-118">이 값을 변경하려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 개체 탐색기에서 사용자 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭한 다음 **기타 서버 설정** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d0641-118">To change this value, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer, right-click your server, click **Properties**, and then click the **Misc. Server Settings** page.</span></span> <span data-ttu-id="d0641-119">해당 옵션이 **오류 보고** 영역에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d0641-119">The options are presented in the **Information Reporting** area.</span></span>  
  
 <span data-ttu-id="d0641-120">**파일 버전**</span><span class="sxs-lookup"><span data-stu-id="d0641-120">**File Version**</span></span>  
 <span data-ttu-id="d0641-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 실행 파일의 버전을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d0641-121">Displays the version of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executable.</span></span>  
  
 <span data-ttu-id="d0641-122">**설치 경로**</span><span class="sxs-lookup"><span data-stu-id="d0641-122">**Install Path**</span></span>  
 <span data-ttu-id="d0641-123">이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치에 대한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]이진 파일 경로를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d0641-123">Displays the path to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] binaries for this installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d0641-124">**인스턴스 ID**</span><span class="sxs-lookup"><span data-stu-id="d0641-124">**Instance ID**</span></span>  
 <span data-ttu-id="d0641-125">이 서비스를 사용하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d0641-125">Indicates the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that used this service.</span></span>  
  
 <span data-ttu-id="d0641-126">**언어**</span><span class="sxs-lookup"><span data-stu-id="d0641-126">**Language**</span></span>  
 <span data-ttu-id="d0641-127">서버 메시지에 대한 기본 언어를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d0641-127">Displays the default language for server messages.</span></span>  
  
 <span data-ttu-id="d0641-128">**레지스트리 루트**</span><span class="sxs-lookup"><span data-stu-id="d0641-128">**Registry Root**</span></span>  
 <span data-ttu-id="d0641-129">이 애플리케이션에 사용되는 레지스트리 키의 위치를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d0641-129">Displays the location of the registry keys used by this application.</span></span>  
  
 <span data-ttu-id="d0641-130">**서비스 팩 수준**</span><span class="sxs-lookup"><span data-stu-id="d0641-130">**Service Pack Level**</span></span>  
 <span data-ttu-id="d0641-131">이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스의 서비스 팩 수준을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d0641-131">Displays the service pack level of this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d0641-132">**SKU 이름**</span><span class="sxs-lookup"><span data-stu-id="d0641-132">**SKU Name**</span></span>  
 <span data-ttu-id="d0641-133">제품 버전이라고도 하는 제품 SKU(Stock Keeping Unit)를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d0641-133">Displays the product stock keeping unit (SKU), sometimes called the product edition.</span></span>  
  
 <span data-ttu-id="d0641-134">**시작 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="d0641-134">**Startup Parameters**</span></span>  
 <span data-ttu-id="d0641-135">이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 사용되는 시작 매개 변수를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="d0641-135">Lists any startup parameters that are used by this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d0641-136">매개 변수는 세미콜론으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0641-136">Parameters are separated by semi-colons.</span></span> <span data-ttu-id="d0641-137">기본 매개 변수로는 master 데이터베이스의 데이터 파일(`master.mdf`), master 데이터베이스의 로그 파일(`mastlog.ldf`) 및 오류 로그 파일의 경로가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0641-137">The default parameters include the paths to the data file for the master database (`master.mdf`), the log file for the master database (`mastlog.ldf`), and the error log file.</span></span> <span data-ttu-id="d0641-138">시작 매개 변수 구문을 보려면 온라인 설명서에서 **SQL Server 서비스 시작 옵션 사용**항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0641-138">For the syntax of startup parameters, search Books Online for the topic **Using the SQL Server Service Startup Options.**</span></span>  
  
 <span data-ttu-id="d0641-139">**SKU(Stock Keeping Unit)**</span><span class="sxs-lookup"><span data-stu-id="d0641-139">**Stock Keeping Unit**</span></span>  
 <span data-ttu-id="d0641-140">제품 SKU(Stock Keeping Unit) 번호를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d0641-140">Displays the product stock keeping unit (SKU) number.</span></span>  
  
 <span data-ttu-id="d0641-141">**버전**</span><span class="sxs-lookup"><span data-stu-id="d0641-141">**Version**</span></span>  
 <span data-ttu-id="d0641-142">이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스의 버전 번호를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d0641-142">Displays the version number of this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d0641-143">**가상 서버 이름**</span><span class="sxs-lookup"><span data-stu-id="d0641-143">**Virtual Server Name**</span></span>  
 <span data-ttu-id="d0641-144">클러스터형 서버에**를 설치한 경우의** 가상 서버 이름 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 입니다.</span><span class="sxs-lookup"><span data-stu-id="d0641-144">**Virtual Server Name** when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed on a clustered server.</span></span>  
  
  
