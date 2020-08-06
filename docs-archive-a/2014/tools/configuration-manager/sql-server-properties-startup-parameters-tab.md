---
title: SQL Server 속성 (시작 매개 변수 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 16942624-5374-446c-8de4-ee6ed34d6e94
author: stevestein
ms.author: sstein
ms.openlocfilehash: 66c4b71433face008ba78af93579cf175fb4bed4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650330"
---
# <a name="sql-server-properties-startup-parameters-tab"></a><span data-ttu-id="8b80d-102">SQL Server 속성(시작 매개 변수 탭)</span><span class="sxs-lookup"><span data-stu-id="8b80d-102">SQL Server Properties (Startup Parameters Tab)</span></span>
  <span data-ttu-id="8b80d-103">이 대화 상자를 사용하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)]에 대한 시작 매개 변수를 추가하거나 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-103">Use this dialog box to add or remove startup parameters for the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="8b80d-104">시작 매개 변수는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 성능에 많은 영향을 미칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-104">Startup parameters can have a large effect on the [!INCLUDE[ssDE](../../includes/ssde-md.md)] performance.</span></span> <span data-ttu-id="8b80d-105">시작 매개 변수를 추가하거나 변경하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 " [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 시작 옵션 사용" 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8b80d-105">Before adding or changing startup parameters, see the topic "Using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Startup Options" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8b80d-106">옵션</span><span class="sxs-lookup"><span data-stu-id="8b80d-106">Options</span></span>  
 <span data-ttu-id="8b80d-107">**시작 매개 변수 지정**</span><span class="sxs-lookup"><span data-stu-id="8b80d-107">**Specify a startup parameter**</span></span>  
 <span data-ttu-id="8b80d-108">매개 변수를 추가하려면 매개 변수를 입력한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-108">To add a parameter, type the parameter, and then click **Add**.</span></span>  
  
 <span data-ttu-id="8b80d-109">필수 매개 변수 중 하나를 수정하려면 **기존 매개 변수** 상자에서 매개 변수를 선택하고 **시작 매개 변수 지정** 상자에서 값을 변경한 다음 **업데이트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-109">To modify one of the required parameters, select the parameter in the **Existing parameters** box, change the values in the **Specify a startup parameter** box, and then click **Update**.</span></span>  
  
 <span data-ttu-id="8b80d-110">**기존 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="8b80d-110">**Existing parameters**</span></span>  
 <span data-ttu-id="8b80d-111">매개 변수를 제거하려면 매개변수를 선택한 다음 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-111">To remove a parameter, select a parameter, and then click **Remove**.</span></span>  
  
## <a name="parameter-format"></a><span data-ttu-id="8b80d-112">매개 변수 형식</span><span class="sxs-lookup"><span data-stu-id="8b80d-112">Parameter Format</span></span>  
 <span data-ttu-id="8b80d-113">매개 변수 사이에 구분 기호를 입력하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-113">Do not enter a separator between parameters.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8b80d-114">구성 관리자에서 구분 기호를 자동으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-114">Configuration Manager automatically adds the separator.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8b80d-115">구성 관리자에서 다음 매개 변수 요구 사항을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-115">Configuration Manager enforces the following parameter requirements.</span></span>  
  
-   <span data-ttu-id="8b80d-116">선행 공백과 후행 공백은 시작 매개 변수에서 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-116">Leading and trailing spaces are trimmed from any startup parameter.</span></span>  
  
-   <span data-ttu-id="8b80d-117">모든 시작 매개 변수는 –(대시)로 시작하고 두 번째 값은 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-117">All startup parameters start with a - (dash) and the second value is a letter.</span></span>  
  
## <a name="required-parameters"></a><span data-ttu-id="8b80d-118">필수 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8b80d-118">Required Parameters</span></span>  
 <span data-ttu-id="8b80d-119">필수 매개 변수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-119">The following parameters are required.</span></span> <span data-ttu-id="8b80d-120">필수 매개 변수는 변경할 수 있지만 제거할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-120">They can be changed but not removed.</span></span>  
  
-   <span data-ttu-id="8b80d-121">-d는 **master.mdf** 파일(master 데이터베이스 데이터 파일)의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-121">-d is the path of the **master.mdf** file (the master database data file).</span></span>  
  
-   <span data-ttu-id="8b80d-122">-l는 **master.ldf** 파일(master 데이터베이스 로그 파일)의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-122">-l is the path of the **master.ldf** file (the master database log file).</span></span>  
  
-   <span data-ttu-id="8b80d-123">-e는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-123">-e is the path of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log files.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="8b80d-124">파일 경로 매개 변수가 잘못된 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-124">If the file path parameters are incorrect [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might not start.</span></span>  
  
 <span data-ttu-id="8b80d-125">master 데이터베이스를 이동하는 방법은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 "시스템 데이터베이스 이동" 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8b80d-125">For more information about how to move the master database, see the topic "Moving System Databases" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="optional-parameters"></a><span data-ttu-id="8b80d-126">선택적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8b80d-126">Optional Parameters</span></span>  
 <span data-ttu-id="8b80d-127">모든 지원되는 시작 매개 변수는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 " [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 시작 옵션 사용" 항목에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-127">All of the supported startup parameters are described in the topic "Using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Startup Options," in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="8b80d-128">시작 매개 변수 -T*trace#* 은 지정된 추적 플래그( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trace# *) 적용 시*인스턴스를 시작해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-128">A startup parameter of -T*trace#* indicates that an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should be started with a specified trace flag (*trace#*) in effect.</span></span> <span data-ttu-id="8b80d-129">추적 플래그는 비표준 동작으로 서버를 시작하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-129">Trace flags are used to start the server with nonstandard behavior.</span></span> <span data-ttu-id="8b80d-130">추적 플래그에 대한 자세한 내용은[!INCLUDE[tsql](../../includes/tsql-md.md)]온라인 설명서에서 "추적 플래그( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] )" 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8b80d-130">For more information about trace flags, see the topic "Trace Flags ([!INCLUDE[tsql](../../includes/tsql-md.md)])" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="8b80d-131">인터넷에서 문서화되지 않은 추가 시작 매개 변수 및 추적 플래그를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-131">You might see additional undocumented startup parameters and trace flags described on the Internet.</span></span> <span data-ttu-id="8b80d-132">문서화되지 않은 시작 매개 변수 및 추적 플래그를 만들어 특수한 문제를 해결하거나 테스트하는 데 필요한 특정 조건을 강제 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-132">Undocumented startup parameters and trace flags are created to address uncommon problems or to force certain conditions required for testing.</span></span> <span data-ttu-id="8b80d-133">문서화되지 않은 시작 매개 변수를 사용하면 예기치 못한 결과가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-133">Using undocumented startup parameters can have unexpected results.</span></span> <span data-ttu-id="8b80d-134">문서화되지 않은 매개 변수는 Microsoft 고객 지원 서비스에서 안내하는 경우에만 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="8b80d-134">Do not use undocumented parameters unless directed by Microsoft Customer Support Services.</span></span>  
  
 <span data-ttu-id="8b80d-135">다음 목록에서는 일부 일반적인 선택 매개 변수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-135">The following list describes some common optional parameters.</span></span>  
  
|<span data-ttu-id="8b80d-136">매개 변수</span><span class="sxs-lookup"><span data-stu-id="8b80d-136">Parameter</span></span>|<span data-ttu-id="8b80d-137">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="8b80d-137">Short description</span></span>|  
|---------------|-----------------------|  
|<span data-ttu-id="8b80d-138">-M</span><span class="sxs-lookup"><span data-stu-id="8b80d-138">-m</span></span>|<span data-ttu-id="8b80d-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 단일 사용자 모드로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-139">Starts an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode.</span></span>|  
|<span data-ttu-id="8b80d-140">-T1204</span><span class="sxs-lookup"><span data-stu-id="8b80d-140">-T1204</span></span>|<span data-ttu-id="8b80d-141">교착 상태에 있는 잠금의 유형과 리소스 및 현재 영향을 받은 명령을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-141">Returns the resources and types of locks participating in a deadlock and also the current command affected.</span></span>|  
|<span data-ttu-id="8b80d-142">-T1224</span><span class="sxs-lookup"><span data-stu-id="8b80d-142">-T1224</span></span>|<span data-ttu-id="8b80d-143">잠금 수를 기반으로 잠금 에스컬레이션을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-143">Disables lock escalation based on the number of locks.</span></span>|  
|<span data-ttu-id="8b80d-144">-T3608</span><span class="sxs-lookup"><span data-stu-id="8b80d-144">-T3608</span></span>|<span data-ttu-id="8b80d-145">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 master 데이터베이스를 제외한 모든 데이터베이스를 자동으로 시작 및 복구하지 못하도록 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-145">Prevents [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from automatically starting and recovering any database except the master database.</span></span>|  
|<span data-ttu-id="8b80d-146">-T7806</span><span class="sxs-lookup"><span data-stu-id="8b80d-146">-T7806</span></span>|<span data-ttu-id="8b80d-147">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]에 DAC(관리자 전용 연결)를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-147">Enables a dedicated administrator connection (DAC) on [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span>|  
  
> [!CAUTION]  
>  <span data-ttu-id="8b80d-148">일부 선택 매개 변수는 서버 동작을 변경하고 성능에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-148">Some optional parameters can change server behavior and may affect performance.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="8b80d-149">사용 권한</span><span class="sxs-lookup"><span data-stu-id="8b80d-149">Permissions</span></span>  
 <span data-ttu-id="8b80d-150">이 페이지는 레지스트리에서 관련 항목을 변경할 수 있는 사용자만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-150">Use of this page is restricted to users who can change the related entries in the registry.</span></span> <span data-ttu-id="8b80d-151">해당되는 사용자는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8b80d-151">This includes the following users.</span></span>  
  
-   <span data-ttu-id="8b80d-152">로컬 Administrators 그룹의 멤버</span><span class="sxs-lookup"><span data-stu-id="8b80d-152">Members of the local administrators group.</span></span>  
  
-   <span data-ttu-id="8b80d-153">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 사용되는 도메인 계정( [!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 도메인 계정에서 실행하도록 구성된 경우)</span><span class="sxs-lookup"><span data-stu-id="8b80d-153">The domain account that is used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], if the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is configured to run under a domain account.</span></span>  
  
## <a name="books-online-references"></a><span data-ttu-id="8b80d-154">온라인 설명서 참조</span><span class="sxs-lookup"><span data-stu-id="8b80d-154">Books Online References</span></span>  
 <span data-ttu-id="8b80d-155">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시작 매개 변수에 대한 자세한 내용은[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 "방법: 서버 시작 옵션 구성( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자)"을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8b80d-155">For additional information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startup parameters, see "How to: Configure Server Startup Options ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
  
