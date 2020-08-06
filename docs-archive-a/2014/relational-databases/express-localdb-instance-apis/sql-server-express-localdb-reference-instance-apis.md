---
title: SQL Server Express LocalDB 인스턴스 API 참조 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: faec46da-0536-4de3-96f3-83e607c8a8b6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5934bc5159998db22d7c560b31457524773e74eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728251"
---
# <a name="sql-server-express-localdb-instance-api-reference"></a><span data-ttu-id="f9086-102">SQL Server Express LocalDB 인스턴스 API 참조</span><span class="sxs-lookup"><span data-stu-id="f9086-102">SQL Server Express LocalDB Instance API Reference</span></span>
  <span data-ttu-id="f9086-103">기존 서비스 기반 SQL Server 환경에서는 단일 컴퓨터에 설치되는 개별 SQL Server 인스턴스가 실제로 분리됩니다. 즉, 각 인스턴스가 개별적으로 설치 및 제거되고, 별도의 이진 파일 집합을 사용하며, 별도의 서비스 프로세스에 따라 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-103">In the traditional, service-based SQL Server world, individual SQL Server instances installed on a single computer are physically separated; that is, each instance must be installed and removed separately, has a separate set of binaries, and runs under a separate service process.</span></span> <span data-ttu-id="f9086-104">SQL Server 인스턴스 이름을 사용하여 연결할 SQL Server 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-104">The SQL Server instance name is used to specify which SQL Server instance the user wants to connect to.</span></span>  
  
 <span data-ttu-id="f9086-105">SQL Server Express LocalDB 인스턴스 API는 단순화 된 "light" 인스턴스 모델을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-105">The SQL Server Express LocalDB instance API uses a simplified, "light" instance model.</span></span> <span data-ttu-id="f9086-106">개별 LocalDB 인스턴스가 디스크와 레지스트리에서 분리되지만, 동일한 공유 LocalDB 이진 파일 집합을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-106">Although individual LocalDB instances are separated on the disk and in the registry, they use the same set of shared LocalDB binaries.</span></span> <span data-ttu-id="f9086-107">또한 LocalDB는 서비스를 사용하지 않으며, LocalDB 인스턴스는 LocalDB 인스턴스 API 호출을 통해 요청될 때 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-107">Moreover, LocalDB does not use services; LocalDB instances are launched on demand through LocalDB instance API calls.</span></span> <span data-ttu-id="f9086-108">LocalDB에서는 인스턴스 이름을 사용하여 작업할 LocalDB 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-108">In LocalDB, the instance name is used to specify which of the LocalDB instances the user wants to work with.</span></span>  
  
 <span data-ttu-id="f9086-109">LocalDB 인스턴스는 항상 단일 사용자가 소유 하며 인스턴스 공유를 사용 하도록 설정 하지 않으면이 사용자의 컨텍스트에서만 표시 되 고 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-109">A LocalDB instance is always owned by a single user and is visible and accessible only from this user's context, unless instance sharing is enabled.</span></span>  
  
 <span data-ttu-id="f9086-110">기술적으로 LocalDB 인스턴스는 기존 SQL Server 인스턴스와 다르지만 용도는 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-110">Although technically LocalDB instances are not the same as traditional SQL Server instances, their intended use is similar.</span></span> <span data-ttu-id="f9086-111">이러한 유사성을 강조 하 고 사용자를 SQL Server 하는 것을 보다 직관적으로 만드는 *인스턴스* 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-111">They are called *instances* to emphasize this similarity and to make them more intuitive to SQL Server users.</span></span>  
  
 <span data-ttu-id="f9086-112">LocalDB에서는 AI(Automatic Instance) 및 NI(Named Instance)의 두 가지 인스턴스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-112">LocalDB supports two kinds of instances: automatic instances (AI) and named instances (NI).</span></span> <span data-ttu-id="f9086-113">LocalDB 인스턴스에 대한 식별자는 인스턴스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-113">The identifier for a LocalDB instance is the instance name.</span></span>  
  
## <a name="automatic-localdb-instances"></a><span data-ttu-id="f9086-114">자동 LocalDB 인스턴스</span><span class="sxs-lookup"><span data-stu-id="f9086-114">Automatic LocalDB Instances</span></span>  
 <span data-ttu-id="f9086-115">자동 LocalDB 인스턴스는 "공용"입니다. 사용자를 위해 자동으로 만들어지고 관리 되며 모든 응용 프로그램에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-115">Automatic LocalDB instances are "public"; they are created and managed automatically for the user and can be used by any application.</span></span> <span data-ttu-id="f9086-116">사용자의 컴퓨터에 설치 된 모든 버전의 LocalDB에 대해 하나의 자동 LocalDB 인스턴스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-116">One automatic LocalDB instance exists for every version of LocalDB that is installed on the user's computer.</span></span>  
  
 <span data-ttu-id="f9086-117">자동 LocalDB 인스턴스는 효율적으로 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-117">Automatic LocalDB instances provide seamless instance management.</span></span> <span data-ttu-id="f9086-118">사용자는 인스턴스를 만들 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-118">The user does not need to create the instance.</span></span> <span data-ttu-id="f9086-119">자동 LocalDB를 사용하면 애플리케이션을 쉽게 설치하고 다른 컴퓨터로 쉽게 마이그레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-119">This enables users to easily install applications and to migrate to different computers.</span></span> <span data-ttu-id="f9086-120">대상 컴퓨터에 지정된 버전의 LocalDB가 설치되어 있을 경우 해당 버전에 대한 자동 LocalDB 인스턴스를 대상 컴퓨터에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-120">If the target computer has the specified version of LocalDB installed, the automatic LocalDB instance for that version is also available on that computer.</span></span>  
  
### <a name="automatic-instance-management"></a><span data-ttu-id="f9086-121">자동 인스턴스 관리</span><span class="sxs-lookup"><span data-stu-id="f9086-121">Automatic Instance Management</span></span>  
 <span data-ttu-id="f9086-122">사용자는 자동 LocalDB 인스턴스를 만들 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-122">A user does not need to create an automatic LocalDB instance.</span></span> <span data-ttu-id="f9086-123">지정 된 버전의 LocalDB를 사용자의 컴퓨터에서 사용할 수 있는 경우 인스턴스가 처음 사용 될 때 인스턴스가 지연 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-123">The instance is lazily created the first time the instance is used, provided that the specified version of LocalDB is available on the user's computer.</span></span> <span data-ttu-id="f9086-124">사용자의 관점에서 자동 인스턴스는 LocalDB 이진 파일이 있는 경우 항상 존재 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-124">From the user's point of view, the automatic instance is always present if the LocalDB binaries are present.</span></span>  
  
 <span data-ttu-id="f9086-125">삭제, 공유, 공유 해제 등과 같은 다른 인스턴스 관리 작업도 자동 인스턴스에 대해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-125">Other instance management operations, such as Delete, Share, and Unshare, also work for automatic instances.</span></span> <span data-ttu-id="f9086-126">특히 자동 인스턴스를 삭제하면 인스턴스가 효율적으로 다시 설정되어 다음에 시작할 때 다시 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-126">In particular, deleting an automatic instance effectively resets the instance, which will be re-created on the next Start operation.</span></span> <span data-ttu-id="f9086-127">시스템 데이터베이스가 손상된 경우 자동 인스턴스를 삭제해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-127">Deleting an automatic instance may be required if the system databases become corrupted.</span></span>  
  
### <a name="automatic-instance-naming-rules"></a><span data-ttu-id="f9086-128">자동 인스턴스 명명 규칙</span><span class="sxs-lookup"><span data-stu-id="f9086-128">Automatic Instance Naming Rules</span></span>  
 <span data-ttu-id="f9086-129">자동 LocalDB 인스턴스는 예약된 네임스페이스에 속하는 특수한 인스턴스 이름 패턴을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-129">Automatic LocalDB instances have a special pattern for the instance name that belongs to a reserved namespace.</span></span> <span data-ttu-id="f9086-130">이는 명명된 LocalDB 인스턴스와 이름이 충돌하는 것을 방지하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-130">This is necessary to prevent name conflicts with named LocalDB instances.</span></span>  
  
 <span data-ttu-id="f9086-131">자동 인스턴스 이름은 단일 "v" 문자가 앞에 오는 LocalDB 기준 릴리스 버전 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-131">The automatic instance name is the LocalDB baseline release version number preceded by a single "v" character.</span></span> <span data-ttu-id="f9086-132">이는 "v"와 두 개의 숫자 사이에 마침표를 두는 것과 같습니다. 예: v 11.0 또는 V 12.00.</span><span class="sxs-lookup"><span data-stu-id="f9086-132">This looks like "v" plus two numbers with a period between them; for example, v11.0 or V12.00.</span></span>  
  
 <span data-ttu-id="f9086-133">잘못된 자동 인스턴스 이름의 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-133">Examples of illegal automatic instance names are:</span></span>  
  
-   <span data-ttu-id="f9086-134">11.0 (시작 부분에 "v" 문자가 없음)</span><span class="sxs-lookup"><span data-stu-id="f9086-134">11.0 (missing the "v" character at the beginning)</span></span>  
  
-   <span data-ttu-id="f9086-135">v11(점과 버전의 두 번째 숫자가 없음)</span><span class="sxs-lookup"><span data-stu-id="f9086-135">v11 (missing a period and the second number of the version)</span></span>  
  
-   <span data-ttu-id="f9086-136">v11.</span><span class="sxs-lookup"><span data-stu-id="f9086-136">v11.</span></span> <span data-ttu-id="f9086-137">(버전의 두 번째 숫자가 없음)</span><span class="sxs-lookup"><span data-stu-id="f9086-137">(missing the second number of the version)</span></span>  
  
-   <span data-ttu-id="f9086-138">v11.0.1.2(버전 번호가 세 개 이상의 부분으로 구성됨)</span><span class="sxs-lookup"><span data-stu-id="f9086-138">v11.0.1.2 (version number has more than two parts)</span></span>  
  
## <a name="named-localdb-instances"></a><span data-ttu-id="f9086-139">명명된 LocalDB 인스턴스</span><span class="sxs-lookup"><span data-stu-id="f9086-139">Named LocalDB Instances</span></span>  
 <span data-ttu-id="f9086-140">명명 된 LocalDB 인스턴스는 "private"입니다. 인스턴스는 인스턴스를 만들고 관리 하는 단일 응용 프로그램에 의해 소유 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-140">Named LocalDB instances are "private"; an instance is owned by a single application that is responsible for creating and managing the instance.</span></span> <span data-ttu-id="f9086-141">명명된 LocalDB 인스턴스는 격리되며 향상된 성능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-141">Named LocalDB instances provide isolation and improve performance.</span></span>  
  
### <a name="named-instance-creation"></a><span data-ttu-id="f9086-142">명명된 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="f9086-142">Named Instance Creation</span></span>  
 <span data-ttu-id="f9086-143">사용자는 LocalDB 관리 API를 통해 명시적으로 명명된 인스턴스를 만들거나, 관리 애플리케이션에 대한 app.config 파일을 통해 암시적으로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-143">The user must create named instances explicitly through the LocalDB management API, or implicitly through the app.config file for a managed application.</span></span> <span data-ttu-id="f9086-144">관리 애플리케이션은 API를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-144">A managed application may also use the API.</span></span>  
  
 <span data-ttu-id="f9086-145">명명된 각각의 인스턴스에는 연결된 LocalDB 버전이 있습니다. 즉, 지정된 LocalDB 이진 파일 집합을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-145">Each named instance has an associated LocalDB version; that is, it points to a specified set of LocalDB binaries.</span></span> <span data-ttu-id="f9086-146">명명된 인스턴스의 버전은 인스턴스를 만드는 과정에서 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-146">The version for the named instance is set during the instance creation process.</span></span>  
  
### <a name="named-instance-naming-rules"></a><span data-ttu-id="f9086-147">명명된 인스턴스 명명 규칙</span><span class="sxs-lookup"><span data-stu-id="f9086-147">Named Instance Naming Rules</span></span>  
 <span data-ttu-id="f9086-148">LocalDB 인스턴스 이름은 최대 128자까지 지정할 수 있으며, `sysname` 데이터 형식에 따라 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-148">A LocalDB instance name can have up to a total of 128 characters (the limit is imposed by the `sysname` data type).</span></span> <span data-ttu-id="f9086-149">이는 NetBIOS 이름이 16자의 ASCII 문자로 제한되는 기존 SQL Server 인스턴스 이름과 비교할 때 중요한 차이점입니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-149">This is a significant difference compared to traditional SQL Server instance names, which are limited to NetBIOS names of 16 ASCII characters.</span></span> <span data-ttu-id="f9086-150">이러한 차이가 있는 이유는 LocalDB는 데이터베이스를 파일로 처리 하므로 파일 기반 의미 체계를 의미 하기 때문에 사용자가 인스턴스 이름을 자유롭게 선택할 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-150">The reason for this difference is that LocalDB treats databases as files, and therefore implies file-based semantics, so it's intuitive for users to have more freedom in choosing instance names.</span></span>  
  
 <span data-ttu-id="f9086-151">LocalDB 인스턴스 이름은 파일 이름 구성 요소에 적합한 모든 유니코드 문자를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-151">A LocalDB instance name can contain any Unicode characters that are legal within the filename component.</span></span> <span data-ttu-id="f9086-152">파일 이름 구성 요소에 잘못 된 문자가 포함 되는 경우 일반적으로 ASCII/유니코드 문자 1 ~ 31, 따옴표 ("), 보다 작음 ( \<), greater than (> ), 파이프 (|), 백스페이스 (\b), 탭 (\t), 콜론 (:), 별표 (\*), 물음표 (?), 백슬래시 ( \\ ) 및 슬래시 (/) 문자가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-152">Illegal characters in a filename component generally include the following characters: ASCII/Unicode characters 1 through 31, as well as quote ("), less than (\<), greater than (>), pipe (|), backspace (\b), tab (\t), colon (:), asterisk (\*), question mark (?), backslash (\\), and forward slash (/).</span></span> <span data-ttu-id="f9086-153">null 문자(\0)는 문자열 종료를 나타내는 데 사용되므로 허용됩니다. 첫 번째 null 문자 뒤의 모든 문자가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-153">Note that the null character (\0) is allowed because it is used for string termination; everything after the first null character will be ignored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f9086-154">부적합한 문자 목록은 운영 체제에 따라 다르며 이후 릴리스에서 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-154">The list of illegal characters may depend on the operating system and may change in future releases.</span></span>  
  
 <span data-ttu-id="f9086-155">인스턴스 이름의 선행 공백과 후행 공백은 무시되므로 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-155">Leading and trailing white spaces in instance names are ignored and will be trimmed.</span></span>  
  
 <span data-ttu-id="f9086-156">이름 충돌을 방지 하기 위해 앞의 "자동 인스턴스 명명 규칙"에서 설명한 것 처럼 명명 된 LocalDB 인스턴스는 자동 인스턴스의 명명 패턴을 따르는 이름을 가질 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-156">To avoid naming conflicts, named LocalDB instances cannot have a name that follows the naming pattern for automatic instances, as described earlier in "Automatic Instance Naming Rules."</span></span> <span data-ttu-id="f9086-157">자동 인스턴스 명명 패턴을 따르는 이름을 사용 하 여 명명 된 인스턴스를 만들려고 하면 기본 인스턴스가 효과적으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-157">An attempt to create a named instance with a name that follows the automatic instance naming pattern effectively creates a default instance.</span></span>  
  
## <a name="sql-server-express-localdb-reference-topics"></a><span data-ttu-id="f9086-158">SQL Server Express LocalDB 참조 항목</span><span class="sxs-lookup"><span data-stu-id="f9086-158">SQL Server Express LocalDB Reference Topics</span></span>  
 [<span data-ttu-id="f9086-159">SQL Server Express LocalDB 헤더 및 버전 정보</span><span class="sxs-lookup"><span data-stu-id="f9086-159">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
 <span data-ttu-id="f9086-160">LocalDB 인스턴스 API를 찾을 수 있도록 헤더 파일 정보와 레지스트리 키를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-160">Provides header file information and registry keys for finding the LocalDB instance API.</span></span>  
  
 [<span data-ttu-id="f9086-161">명령줄 관리 도구: SqlLocalDB.exe</span><span class="sxs-lookup"><span data-stu-id="f9086-161">Command-Line Management Tool: SqlLocalDB.exe</span></span>](command-line-management-tool-sqllocaldb-exe.md)  
 <span data-ttu-id="f9086-162">명령줄에서 LocalDB 인스턴스를 관리하는 도구인 SqlLocalDB.exe에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-162">Describes SqlLocalDB.exe, a tool for managing LocalDB instances from the command line.</span></span>  
  
 [<span data-ttu-id="f9086-163">LocalDBCreateInstance 함수</span><span class="sxs-lookup"><span data-stu-id="f9086-163">LocalDBCreateInstance Function</span></span>](localdbcreateinstance-function.md)  
 <span data-ttu-id="f9086-164">새 LocalDB 인스턴스를 만드는 함수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-164">Describes the function to create a new LocalDB instance.</span></span>  
  
 [<span data-ttu-id="f9086-165">LocalDBDeleteInstance 함수</span><span class="sxs-lookup"><span data-stu-id="f9086-165">LocalDBDeleteInstance Function</span></span>](localdbdeleteinstance-function.md)  
 <span data-ttu-id="f9086-166">LocalDB 인스턴스를 제거하는 함수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-166">Describes the function to remove a LocalDB instance.</span></span>  
  
 [<span data-ttu-id="f9086-167">LocalDBFormatMessage 함수</span><span class="sxs-lookup"><span data-stu-id="f9086-167">LocalDBFormatMessage Function</span></span>](localdbformatmessage-function.md)  
 <span data-ttu-id="f9086-168">LocalDB 오류에 대한 지역화된 설명을 반환하는 함수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-168">Describes the function to return the localized description for a LocalDB error.</span></span>  
  
 [<span data-ttu-id="f9086-169">LocalDBGetInstanceInfo 함수</span><span class="sxs-lookup"><span data-stu-id="f9086-169">LocalDBGetInstanceInfo Function</span></span>](localdbgetinstanceinfo-function.md)  
 <span data-ttu-id="f9086-170">LocalDB 인스턴스의 존재 여부, 버전 정보, 실행 여부 등과 같은 LocalDB 관련 정보를 가져오는 함수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-170">Describes the function to get information for a LocalDB instance, such as whether it exists, version information, whether it is running, and so on.</span></span>  
  
 [<span data-ttu-id="f9086-171">LocalDBGetInstances 함수</span><span class="sxs-lookup"><span data-stu-id="f9086-171">LocalDBGetInstances Function</span></span>](localdbgetinstances-function.md)  
 <span data-ttu-id="f9086-172">지정된 버전의 모든 LocalDB 인스턴스를 반환하는 함수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-172">Describes the function to return all the LocalDB instances with a specified version.</span></span>  
  
 [<span data-ttu-id="f9086-173">LocalDBGetVersionInfo 함수</span><span class="sxs-lookup"><span data-stu-id="f9086-173">LocalDBGetVersionInfo Function</span></span>](localdbgetversioninfo-function.md)  
 <span data-ttu-id="f9086-174">지정된 LocalDB 버전에 대한 정보를 반환하는 함수를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-174">Describes the function to return information for a specified LocalDB version.</span></span>  
  
 [<span data-ttu-id="f9086-175">LocalDBGetVersions 함수</span><span class="sxs-lookup"><span data-stu-id="f9086-175">LocalDBGetVersions Function</span></span>](localdbgetversions-function.md)  
 <span data-ttu-id="f9086-176">컴퓨터에서 사용할 수 있는 모든 LocalDB 버전을 반환하는 함수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-176">Describes the function to return all LocalDB versions available on a computer.</span></span>  
  
 [<span data-ttu-id="f9086-177">LocalDBShareInstance 함수</span><span class="sxs-lookup"><span data-stu-id="f9086-177">LocalDBShareInstance Function</span></span>](localdbshareinstance-function.md)  
 <span data-ttu-id="f9086-178">지정된 LocalDB 인스턴스를 공유하는 함수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-178">Describes the function to share a specified LocalDB instance.</span></span>  
  
 [<span data-ttu-id="f9086-179">LocalDBStartInstance 함수</span><span class="sxs-lookup"><span data-stu-id="f9086-179">LocalDBStartInstance Function</span></span>](localdbstartinstance-function.md)  
 <span data-ttu-id="f9086-180">지정된 LocalDB 인스턴스를 시작하는 함수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-180">Describes the function to start a specified LocalDB instance.</span></span>  
  
 [<span data-ttu-id="f9086-181">LocalDBStartTracing 함수</span><span class="sxs-lookup"><span data-stu-id="f9086-181">LocalDBStartTracing Function</span></span>](localdbstarttracing-function.md)  
 <span data-ttu-id="f9086-182">사용자에 대한 API 추적을 사용하도록 설정하는 함수를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-182">Describes the function to enable API tracing for a user.</span></span>  
  
 [<span data-ttu-id="f9086-183">LocalDBStopInstance 함수</span><span class="sxs-lookup"><span data-stu-id="f9086-183">LocalDBStopInstance Function</span></span>](localdbstopinstance-function.md)  
 <span data-ttu-id="f9086-184">지정된 LocalDB 인스턴스를 중지하는 함수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-184">Describes the function to stop a specified LocalDB instance from running.</span></span>  
  
 [<span data-ttu-id="f9086-185">LocalDBStopTracing 함수</span><span class="sxs-lookup"><span data-stu-id="f9086-185">LocalDBStopTracing Function</span></span>](localdbstoptracing-function.md)  
 <span data-ttu-id="f9086-186">사용자에 대한 API 추적을 사용하지 않도록 설정하는 함수를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-186">Describes the function to disable API tracing for a user.</span></span>  
  
 [<span data-ttu-id="f9086-187">LocalDBUnshareInstance 함수</span><span class="sxs-lookup"><span data-stu-id="f9086-187">LocalDBUnshareInstance Function</span></span>](localdbunshareinstance-function.md)  
 <span data-ttu-id="f9086-188">지정된 LocalDB 인스턴스 공유를 중지하는 함수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f9086-188">Describes the function to stop sharing a specified LocalDB instance.</span></span>  
  
  
