---
title: 인스턴스 구성 | Microsoft Docs
ms.custom: ''
ms.date: 05/04/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
f1_keywords:
- instance configuration, Setup
helpviewer_keywords:
- Instance Name page [SQL Server Installation Wizard]
- SQL Server Installation Wizard, Instance Name page
ms.assetid: 5bf822fc-6dec-4806-a153-e200af28e9a5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 86a9538e81881a3b42b95447f4264200e2fe9d4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653149"
---
# <a name="instance-configuration"></a><span data-ttu-id="5c632-102">인스턴스 구성</span><span class="sxs-lookup"><span data-stu-id="5c632-102">Instance Configuration</span></span>
  <span data-ttu-id="5c632-103">**설치 마법사의** 인스턴스 구성 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 페이지를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 기본 인스턴스를 만들지 또는 명명된 인스턴스를 만들지 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-103">Use the **Instance Configuration** page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard to specify whether to create a default instance or a named instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5c632-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 아직 설치되지 않은 경우 명명된 인스턴스를 지정하지 않으면 기본 인스턴스가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-104">If an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not already installed, a default instance will be created unless you specify a named instance.</span></span>  
  
 <span data-ttu-id="5c632-105">각 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스는 특정 데이터 정렬과 기타 옵션이 지정된 고유의 서비스 집합으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-105">Each instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consists of a distinct set of services that have specific settings for collations and other options.</span></span> <span data-ttu-id="5c632-106">디렉터리 구조, 레지스트리 구조 및 서비스 이름은 모두 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 중 작성한 인스턴스 이름과 특정 인스턴스 ID를 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-106">The directory structure, registry structure, and service names all reflect the instance name and a specific instance ID created during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span>  
  
 <span data-ttu-id="5c632-107">인스턴스는 기본 인스턴스이거나 명명된 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-107">An instance is either the default instance or a named instance.</span></span> <span data-ttu-id="5c632-108">기본 인스턴스 이름은 MSSQLSERVER입니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-108">The default instance name is MSSQLSERVER.</span></span> <span data-ttu-id="5c632-109">연결을 위해 클라이언트에서 인스턴스 이름을 지정할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-109">It does not require a client to specify the name of the instance to make a connection.</span></span> <span data-ttu-id="5c632-110">명명된 인스턴스는 설치 중 사용자가 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-110">A named instance is determined by the user during Setup.</span></span> <span data-ttu-id="5c632-111">기본 인스턴스를 먼저 설치하지 않고도 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 명명된 인스턴스로 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-111">You can install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a named instance without installing the default instance first.</span></span> <span data-ttu-id="5c632-112">버전과 관계없이 한 번에 하나의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]설치만 기본 인스턴스가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-112">Only one installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], regardless of version, can be the default instance at one time.</span></span>  
  
 <span data-ttu-id="5c632-113">**오류!**</span><span class="sxs-lookup"><span data-stu-id="5c632-113">**Alert!**</span></span> <span data-ttu-id="5c632-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep을 사용할 경우 **인스턴스 구성** 페이지에서 준비 인스턴스를 완료할 때 인스턴스 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-114">With [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep, you can specify the instance name when you complete a prepared instance on the **Instance Configuration** page.</span></span> <span data-ttu-id="5c632-115">시스템에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 기존 기본 인스턴스가 없는 경우 완료하려는 준비 인스턴스를 기본 인스턴스로 구성하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-115">You can choose to configure the prepared instance you are completing as a default instance if there is no existing default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the machine.</span></span>  
  
## <a name="multiple-instances"></a><span data-ttu-id="5c632-116">여러 인스턴스</span><span class="sxs-lookup"><span data-stu-id="5c632-116">Multiple Instances</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="5c632-117">는 단일 서버 또는 프로세서에서 여러 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 지원하지만 하나의 인스턴스만 기본 인스턴스가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-117">supports multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a single server or processor, but only one instance can be the default instance.</span></span> <span data-ttu-id="5c632-118">다른 모든 인스턴스는 명명된 인스턴스여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-118">All others must be named instances.</span></span> <span data-ttu-id="5c632-119">한 컴퓨터에서 여러 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 동시에 실행할 수 있으며 각 인스턴스는 다른 인스턴스와 독립적으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-119">A computer can run multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] concurrently, and each instance runs independently of other instances.</span></span>  
  
 <span data-ttu-id="5c632-120">자세한 내용은 [Maximum Capacity Specifications for SQL Server](../maximum-capacity-specifications-for-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5c632-120">For more information, see [Maximum Capacity Specifications for SQL Server](../maximum-capacity-specifications-for-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5c632-121">옵션</span><span class="sxs-lookup"><span data-stu-id="5c632-121">Options</span></span>  
 <span data-ttu-id="5c632-122">장애 조치(Failover) 클러스터 인스턴스만 - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치 클러스터 네트워크 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-122">Failover cluster instances only - Specify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster network name.</span></span> <span data-ttu-id="5c632-123">이 이름은 네트워크에서 장애 조치(Failover) 클러스터 인스턴스를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-123">This name identifies the failover cluster instance on the network.</span></span>  
  
 <span data-ttu-id="5c632-124">기본 또는 명명된 인스턴스 - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 기본 인스턴스 또는 명명된 인스턴스를 설치할지 결정할 때 다음 정보를 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="5c632-124">Default or Named instance - Consider the following information when you decide whether to install a default or named instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="5c632-125">데이터베이스 서버에 단일 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 설치할 경우 이 인스턴스는 기본 인스턴스여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-125">If you plan to install a single instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a database server, it should be a default instance.</span></span>  
  
-   <span data-ttu-id="5c632-126">동일한 컴퓨터에 여러 인스턴스를 설치할 경우에는 명명된 인스턴스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-126">Use a named instance for situations where you plan to have multiple instances on the same computer.</span></span> <span data-ttu-id="5c632-127">한 서버에서 기본 인스턴스 한 개만 호스팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-127">A server can host only one default instance.</span></span>  
  
-   <span data-ttu-id="5c632-128">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 를 설치하는 애플리케이션은 이를 명명된 인스턴스로 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-128">Any application that installs [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] should install it as a named instance.</span></span> <span data-ttu-id="5c632-129">이렇게 하면 여러 애플리케이션을 동일한 컴퓨터에 설치한 경우 충돌을 최소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-129">This will minimizes conflict when multiple applications are installed on the same computer.</span></span>  
  
 <span data-ttu-id="5c632-130">**기본 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="5c632-130">**Default instance**</span></span>  
 <span data-ttu-id="5c632-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 기본 인스턴스를 설치하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-131">Select this option to install a default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5c632-132">한 컴퓨터에서는 기본 인스턴스를 하나만 호스팅할 수 있으며 나머지 인스턴스는 모두 명명된 인스턴스여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-132">A computer can host only one default instance; all other instances must be named.</span></span> <span data-ttu-id="5c632-133">그러나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기본 인스턴스가 설치되어 있으면 동일한 컴퓨터에 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 기본 인스턴스를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-133">However, if you have a default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installed, you can add a default instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to the same computer.</span></span>  
  
 <span data-ttu-id="5c632-134">**명명된 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="5c632-134">**Named instance**</span></span>  
 <span data-ttu-id="5c632-135">새 명명된 인스턴스를 만들려는 경우 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-135">Select this option to create a new named instance.</span></span> <span data-ttu-id="5c632-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 이름을 지정할 때 다음에 주의합니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-136">Be aware of the following when you name an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="5c632-137">인스턴스 이름은 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-137">Instance names are not case sensitive.</span></span>  
  
-   <span data-ttu-id="5c632-138">인스턴스 이름은 밑줄(_)로 시작하거나 끝낼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-138">Instance names cannot start or end with an underscore (_).</span></span>  
  
-   <span data-ttu-id="5c632-139">인스턴스 이름에는 용어 "Default" 또는 다른 예약 키워드를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-139">Instance names cannot contain the term "Default" or other reserved keywords.</span></span> <span data-ttu-id="5c632-140">인스턴스 이름에 예약 키워드를 사용한 경우 설치 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-140">If a reserved keyword is used in an instance name, a Setup error will occur.</span></span> <span data-ttu-id="5c632-141">자세한 내용은 [예약 된 키워드 &#40;transact-sql&#41;](/sql/t-sql/language-elements/reserved-keywords-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5c632-141">For more information, see [Reserved Keywords &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reserved-keywords-transact-sql).</span></span>  
  
-   <span data-ttu-id="5c632-142">인스턴스 이름으로 MSSQLServer를 지정하면 기본 인스턴스가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-142">If you specify MSSQLServer for the instance name, a default instance will be created.</span></span>  
  
-   <span data-ttu-id="5c632-143">[!INCLUDE[ssGeminiLong](../../includes/ssgeminilong-md.md)] 는 항상 'PowerPivot'이라고 명명된 인스턴스로 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-143">An installation of [!INCLUDE[ssGeminiLong](../../includes/ssgeminilong-md.md)] is always installed as a named instance of 'PowerPivot'.</span></span> <span data-ttu-id="5c632-144">이 기능 역할에는 다른 인스턴스 이름을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-144">You cannot specify a different instance name for this feature role.</span></span>  
  
-   <span data-ttu-id="5c632-145">인스턴스 이름은 16자로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-145">Instance names are limited to 16 characters.</span></span>  
  
-   <span data-ttu-id="5c632-146">인스턴스 이름의 첫 글자는 문자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-146">The first character in the instance name must be a letter.</span></span> <span data-ttu-id="5c632-147">허용되는 문자는 유니코드 표준 2.0에서 정의된 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-147">Acceptable letters are those defined by the Unicode Standard 2.0.</span></span> <span data-ttu-id="5c632-148">여기에는 a - z, A - Z의 라틴어 문자와 기타 언어의 문자가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-148">These include Latin characters a-z, A-Z, and letter characters from other languages.</span></span>  
  
-   <span data-ttu-id="5c632-149">이어지는 글자는 유니코드 표준 2.0에 정의된 문자, 기본 라틴어 또는 기타 국가별 스크립트에 정의된 숫자, 달러 기호($) 또는 밑줄(_)이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-149">Subsequent characters can be letters defined by the Unicode Standard 2.0, decimal numbers from Basic Latin or other national scripts, the dollar sign ($), or an underscore (_).</span></span>  
  
-   <span data-ttu-id="5c632-150">공백이나 다른 특수 문자는 인스턴스 이름에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-150">Embedded spaces or other special characters are not allowed in instance names.</span></span> <span data-ttu-id="5c632-151">백슬래시(\\), 쉼표(,), 콜론(:), 세미콜론(;), 작은따옴표('), 앰퍼샌드(&), 하이픈(-) 및 @ 기호도 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-151">The backslash (\\), comma (,), colon (:), semi-colon (;), single quote ('), ampersand (&), hyphen (-), and at sign (@) are also not allowed.</span></span>  
  
-   <span data-ttu-id="5c632-152">**현재 Windows 코드 페이지에서 유효한 문자만 인스턴스 이름에 사용할 수 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . 지원 되지 않는 유니코드 문자를 사용 하는 경우 설치 오류가 발생 합니다.**</span><span class="sxs-lookup"><span data-stu-id="5c632-152">**Only characters that are valid in the current Windows code page can be used in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance names. If an unsupported Unicode character is used, a Setup error will occur.**</span></span>  
  
 <span data-ttu-id="5c632-153">**감지된 인스턴스 및 기능**</span><span class="sxs-lookup"><span data-stu-id="5c632-153">**Detected instances and features**</span></span>  
 <span data-ttu-id="5c632-154">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 프로그램이 실행 중인 컴퓨터에 설치된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 및 구성 요소 목록을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-154">View a list of installed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances and components on the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup is running.</span></span>  
  
 <span data-ttu-id="5c632-155">**인스턴스 ID** - 기본적으로 인스턴스 이름이 인스턴스 ID로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-155">**Instance ID** - By default, the instance name is used as the Instance ID.</span></span> <span data-ttu-id="5c632-156">인스턴스 ID는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스의 설치 디렉터리 및 레지스트리 키를 식별하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-156">This is used to identify installation directories and registry keys for your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5c632-157">이는 기본 인스턴스와 명명된 인스턴스에 모두 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-157">This is the case for default instances and named instances.</span></span> <span data-ttu-id="5c632-158">기본 인스턴스의 경우 인스턴스 이름 및 인스턴스 ID는 MSSQLSERVER입니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-158">For a default instance, the instance name and instance ID would be MSSQLSERVER.</span></span> <span data-ttu-id="5c632-159">기본 인스턴스 ID가 아닌 ID를 사용하려면 **인스턴스 ID** 필드에 해당 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-159">To use a non-default instance ID, specify it in the **Instance ID** field.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5c632-160">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep을 사용할 경우 이 페이지에 표시되는 인스턴스 ID는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep 프로세스의 이미지 준비 단계 중에 지정한 인스턴스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-160">With [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep, the Instance ID displayed on this page is the Instance ID specified during the prepare image step of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep process.</span></span> <span data-ttu-id="5c632-161">이미지 완료 단계에서는 다른 인스턴스 ID를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-161">You will not be able to specify a different Instance ID during the complete image step.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5c632-162">밑줄(_)로 시작되거나 숫자 기호(#) 또는 달러 기호($)가 들어 있는 인스턴스 ID는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-162">Instance IDs that begin with an underscore (_) or that contain the number sign (#) or the dollar sign ($) are not supported.</span></span>  
  
 <span data-ttu-id="5c632-163">디렉터리, 파일 위치 및 인스턴스 ID 명명에 대한 자세한 내용은 [SQL Server 기본 인스턴스 및 명명된 인스턴스의 파일 위치](../../../2014/sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5c632-163">For more information about directories, file locations, and instance ID naming, see [File Locations for Default and Named Instances of SQL Server](../../../2014/sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md).</span></span>  
  
 <span data-ttu-id="5c632-164">지정된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 모든 구성 요소는 하나의 단위로 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-164">All components of a given instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are managed as a unit.</span></span> <span data-ttu-id="5c632-165">모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 팩 및 업그레이드는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스의 모든 구성 요소에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-165">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service packs and upgrades will apply to every component of an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="5c632-166">같은 인스턴스 이름을 공유하는 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소는 다음 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-166">All components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that share the same instance name must meet the following criteria:</span></span>  
  
-   <span data-ttu-id="5c632-167">**같은 버전**</span><span class="sxs-lookup"><span data-stu-id="5c632-167">**Same version**</span></span>  
  
-   <span data-ttu-id="5c632-168">**같은 에디션**</span><span class="sxs-lookup"><span data-stu-id="5c632-168">**Same edition**</span></span>  
  
-   <span data-ttu-id="5c632-169">**같은 언어 설정**</span><span class="sxs-lookup"><span data-stu-id="5c632-169">**Same language settings**</span></span>  
  
-   <span data-ttu-id="5c632-170">**같은 클러스터형 상태**</span><span class="sxs-lookup"><span data-stu-id="5c632-170">**Same clustered state**</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="5c632-171">는 클러스터 인식형이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="5c632-171">is not cluster-aware.</span></span>  
  
-   <span data-ttu-id="5c632-172">**같은 운영 체제**</span><span class="sxs-lookup"><span data-stu-id="5c632-172">**Same operating system**</span></span>  
  
  
