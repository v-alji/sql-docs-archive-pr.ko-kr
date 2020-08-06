---
title: 유틸리티 관리 (SQL Server 유틸리티) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 3e5a00c3-8905-40f0-9ddc-d924df9c2f0d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fca4ea655ffdcf8471d1340016d16f2c5b9c352a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731991"
---
# <a name="utility-administration-sql-server-utility"></a><span data-ttu-id="66823-102">유틸리티 관리(SQL Server 유틸리티)</span><span class="sxs-lookup"><span data-stu-id="66823-102">Utility Administration (SQL Server Utility)</span></span>
  <span data-ttu-id="66823-103">유틸리티 관리 탭을 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 유틸리티의 정책, 보안 및 데이터 웨어하우스 설정을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66823-103">Use the Utility Administration tabs to manage policy, security, and data warehouse settings for a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="66823-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 유틸리티 개념에 대한 자세한 내용은 [SQL Server 유틸리티 기능 및 태스크](../relational-databases/manage/sql-server-utility-features-and-tasks.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="66823-104">For more information about [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility concepts, see [SQL Server Utility Features and Tasks](../relational-databases/manage/sql-server-utility-features-and-tasks.md).</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="66823-105">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="66823-105">UI element list</span></span>  
 <span data-ttu-id="66823-106">정책 탭 - 정책 탭을 사용하여 전역 모니터링 정책을 보거나 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66823-106">Policy tab - Use the policy tab to view or specify global monitoring policies.</span></span>  
  
 <span data-ttu-id="66823-107">전역 데이터 계층 애플리케이션의 모니터링 정책을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="66823-107">Set global data-tier application monitoring policies.</span></span> <span data-ttu-id="66823-108">이 옵션의 값 목록을 확장하려면 정책 이름 옆에 있는 화살표를 클릭하거나 정책 제목을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66823-108">To expand the list of values for this option, click on the arrow next to the policy name, or click on the policy title.</span></span>  
 <span data-ttu-id="66823-109">언제 애플리케이션에서 프로세서 용량이 부족합니까?</span><span class="sxs-lookup"><span data-stu-id="66823-109">When is an application running out of processor capacity?</span></span> <span data-ttu-id="66823-110">이 정책을 변경하려면 정책 설명 오른쪽에 있는 컨트롤을 사용하고 **적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66823-110">To change this policy, use the control to the right of the policy description, then click **Apply**.</span></span> <span data-ttu-id="66823-111">아래쪽에 있는 단추를 사용하여 기본값으로 복원하거나 변경을 취소할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66823-111">You can also restore default values or discard changes using buttons at the bottom of the display.</span></span>  
  
-   <span data-ttu-id="66823-112">프로세서 사용률의 기본 최대값은 70%입니다.</span><span class="sxs-lookup"><span data-stu-id="66823-112">The default maximum value for processor utilization is 70%.</span></span>  
  
-   <span data-ttu-id="66823-113">프로세서 사용률의 기본 최소값은 0%입니다.</span><span class="sxs-lookup"><span data-stu-id="66823-113">The default minimum value for processor utilization is 0%.</span></span>  
  
 <span data-ttu-id="66823-114">언제 애플리케이션에서 파일 공간이 부족합니까?</span><span class="sxs-lookup"><span data-stu-id="66823-114">When is an application running out of file space?</span></span> <span data-ttu-id="66823-115">데이터 파일이나 로그 파일 공간 사용률에 대한 정책을 변경하려면 정책 설명 오른쪽에 있는 컨트롤을 사용하고 **적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66823-115">To change the policy for data file or log file space utilization, use the control to the right of the policy description, then click **Apply**.</span></span> <span data-ttu-id="66823-116">아래쪽에 있는 단추를 사용하여 기본값으로 복원하거나 변경을 취소할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66823-116">You can also restore default values or discard changes using buttons at the bottom of the display.</span></span>  
  
-   <span data-ttu-id="66823-117">파일 공간 사용률의 기본 최대값은 70%입니다.</span><span class="sxs-lookup"><span data-stu-id="66823-117">The default maximum value for file space utilization is 70%.</span></span>  
  
-   <span data-ttu-id="66823-118">파일 공간 사용률의 기본 최소값은 0%입니다.</span><span class="sxs-lookup"><span data-stu-id="66823-118">The default minimum value for file space utilization is 0%.</span></span>  
  
 <span data-ttu-id="66823-119">전역 SQL Server의 관리되는 인스턴스 애플리케이션 모니터링 정책을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="66823-119">Set global SQL Server managed instance application monitoring policies.</span></span> <span data-ttu-id="66823-120">이 옵션의 값 목록을 확장하려면 정책 이름 옆에 있는 화살표를 클릭하거나 정책 제목을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66823-120">To expand the list of values for this option, click on the arrow next to the policy name, or click on the policy title.</span></span>  
 <span data-ttu-id="66823-121">언제 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 관리되는 인스턴스에서 프로세서 용량이 부족합니까?</span><span class="sxs-lookup"><span data-stu-id="66823-121">When is a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] running out of processor capacity?</span></span> <span data-ttu-id="66823-122">이 정책을 변경하려면 정책 설명 오른쪽에 있는 컨트롤을 사용하고 **적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66823-122">To change this policy, use the control to the right of the policy description, then click **Apply**.</span></span> <span data-ttu-id="66823-123">아래쪽에 있는 단추를 사용하여 기본값으로 복원하거나 변경을 취소할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66823-123">You can also restore default values or discard changes using buttons at the bottom of the display.</span></span>  
  
-   <span data-ttu-id="66823-124">인스턴스 프로세서 사용률의 기본 최대값은 70%입니다.</span><span class="sxs-lookup"><span data-stu-id="66823-124">The default maximum value for instance processor utilization is 70%.</span></span>  
  
-   <span data-ttu-id="66823-125">인스턴스 프로세서 사용률의 기본 최소값은 0%입니다.</span><span class="sxs-lookup"><span data-stu-id="66823-125">The default minimum value for instance processor utilization is 0%.</span></span>  
  
 <span data-ttu-id="66823-126">언제 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 관리되는 인스턴스 컴퓨터에서 프로세서 용량이 부족합니까?</span><span class="sxs-lookup"><span data-stu-id="66823-126">When is a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] computer running out of processor capacity?</span></span> <span data-ttu-id="66823-127">이 정책을 변경하려면 정책 설명 오른쪽에 있는 컨트롤을 사용하고 **적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66823-127">To change this policy, use the control to the right of the policy description, then click **Apply**.</span></span> <span data-ttu-id="66823-128">아래쪽에 있는 단추를 사용하여 기본값으로 복원하거나 변경을 취소할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66823-128">You can also restore default values or discard changes using buttons at the bottom of the display.</span></span>  
  
-   <span data-ttu-id="66823-129">컴퓨터 프로세서 사용률의 기본 최대값은 70%입니다.</span><span class="sxs-lookup"><span data-stu-id="66823-129">The default maximum value for computer processor utilization is 70%.</span></span>  
  
-   <span data-ttu-id="66823-130">컴퓨터 프로세서 사용률의 기본 최소값은 0%입니다.</span><span class="sxs-lookup"><span data-stu-id="66823-130">The default minimum value for computer processor utilization is 0%.</span></span>  
  
 <span data-ttu-id="66823-131">언제 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 관리되는 인스턴스에서 파일 공간이 부족합니까?</span><span class="sxs-lookup"><span data-stu-id="66823-131">When is a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] running out of file space?</span></span> <span data-ttu-id="66823-132">데이터 파일이나 로그 파일 공간 사용률에 대한 정책을 변경하려면 정책 설명 오른쪽에 있는 컨트롤을 사용하고 **적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66823-132">To change the policy for data file or log file space utilization , use the control to the right of the policy description, then click **Apply**.</span></span> <span data-ttu-id="66823-133">아래쪽에 있는 단추를 사용하여 기본값으로 복원하거나 변경을 취소할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66823-133">You can also restore default values or discard changes using buttons at the bottom of the display.</span></span>  
  
-   <span data-ttu-id="66823-134">파일 공간 사용률의 기본 최대값은 70%입니다.</span><span class="sxs-lookup"><span data-stu-id="66823-134">The default maximum value for file space utilization is 70%.</span></span>  
  
-   <span data-ttu-id="66823-135">파일 공간 사용률의 기본 최소값은 0%입니다.</span><span class="sxs-lookup"><span data-stu-id="66823-135">The default minimum value for file space utilization is 0%.</span></span>  
  
 <span data-ttu-id="66823-136">언제 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 관리되는 인스턴스 컴퓨터에서 스토리지 볼륨 공간이 부족합니까?</span><span class="sxs-lookup"><span data-stu-id="66823-136">When is a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] computer running out of storage volume space?</span></span> <span data-ttu-id="66823-137">이 정책을 변경하려면 정책 설명 오른쪽에 있는 컨트롤을 사용하고 **적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66823-137">To change this policy, use the control to the right of the policy description, then click **Apply**.</span></span> <span data-ttu-id="66823-138">아래쪽에 있는 단추를 사용하여 기본값으로 복원하거나 변경을 취소할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66823-138">You can also restore default values or discard changes using buttons at the bottom of the display.</span></span>  
  
-   <span data-ttu-id="66823-139">컴퓨터 볼륨 공간 사용률의 기본 최대값은 70%입니다.</span><span class="sxs-lookup"><span data-stu-id="66823-139">The default maximum value for computer volume space utilization is 70%.</span></span>  
  
-   <span data-ttu-id="66823-140">컴퓨터 볼륨 공간 사용률의 기본 최소값은 0%입니다.</span><span class="sxs-lookup"><span data-stu-id="66823-140">The default minimum value for computer volume space utilization is 0%.</span></span>  
  
 <span data-ttu-id="66823-141">매우 불안정한 리소스에 의해 발생하는 정책 위반 노이즈를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="66823-141">Reducing policy violation noise from highly volatile resources.</span></span> <span data-ttu-id="66823-142">이 기능의 컨트롤을 확장하려면 오른쪽에 표시되는 아래쪽 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66823-142">To expand the controls for this feature, click on the down-arrow on the right side of the display.</span></span>  
 <span data-ttu-id="66823-143">자세한 내용은 [CPU 사용 정책에서 노이즈 줄이기&#40;SQL Server 유틸리티&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="66823-143">For more information, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="66823-144">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="66823-144">UI element list</span></span>  
 <span data-ttu-id="66823-145">보안 탭 - UCP를 관리하거나 읽을 수 있는 권한이 있는 로그인 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="66823-145">Security tab - Displays login names with permissions to administer or read from the UCP.</span></span>  
  
 <span data-ttu-id="66823-146">Utility 읽기 역할에 추가될 UCP에서 로그인을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="66823-146">Select the logins from the UCP that will be added to the Utility Reader role.</span></span>  
 <span data-ttu-id="66823-147">Utility 읽기 권한이 있는 사용자 계정으로 다음과 같은 작업을 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66823-147">The Utility Reader privilege allows the user account to:</span></span>  
  
-   <span data-ttu-id="66823-148">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 유틸리티에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="66823-148">Connect to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility.</span></span>  
  
-   <span data-ttu-id="66823-149">SSMS의 유틸리티 탐색기에서 모든 뷰포인트를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="66823-149">See all viewpoints in the Utility Explorer in SSMS.</span></span>  
  
-   <span data-ttu-id="66823-150">SSMS의 유틸리티 탐색기의 유틸리티 관리 노드에 있는 설정을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="66823-150">See settings on the Utility Administration node in Utility Explorer in SSMS.</span></span>  
  
 <span data-ttu-id="66823-151">유틸리티 관리자는 SQL Server Utility에 SQL Server 인스턴스를 등록하거나 제거할 수 있으며 관리되는 인스턴스의 정책을 수정하고 UCP의 관리 설정을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66823-151">Utility administrators can enroll instances of SQL Server into and remove instances of SQL Server from a SQL Server Utility, as well as modify policies on managed instances and modify administration settings on the UCP.</span></span>  
  
 <span data-ttu-id="66823-152">유틸리티 관리자가 되려면 SQL Server 인스턴스에 대한 sysadmin 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66823-152">To be a Utility administrator, you must have sysadmin privileges on the instance of SQL Server.</span></span> <span data-ttu-id="66823-153">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] UCP에 대한 사용자 계정을 추가하거나 변경하려면 SSMS의 개체 탐색기를 사용하여 SQL Server UCP 인스턴스의 서버 로그인에 사용자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="66823-153">To add or change user accounts for the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] UCP, use Object Explorer in SSMS to add the user to the server logins of the UCP instance of SQL Server.</span></span> <span data-ttu-id="66823-154">자세한 내용은 [sp_addlogin&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="66823-154">For more information, see [sp_addlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql).</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="66823-155">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="66823-155">UI element list</span></span>  
 <span data-ttu-id="66823-156">데이터 웨어하우스 탭 - 유틸리티 관리 데이터 웨어하우스에 대한 구성 세부 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="66823-156">Data Warehouse tab - Displays configuration details for the utility management data warehouse.</span></span>  
  
 <span data-ttu-id="66823-157">데이터 보존</span><span class="sxs-lookup"><span data-stu-id="66823-157">Data Retention</span></span>  
 <span data-ttu-id="66823-158">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 관리되는 인스턴스에 대해 수집된 사용률 정보의 데이터 보존 기간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="66823-158">Specify the data retention period for utilization information collected for managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="66823-159">기본 기간은 1년입니다.</span><span class="sxs-lookup"><span data-stu-id="66823-159">The default time period is 1 year.</span></span> <span data-ttu-id="66823-160">최소값은 1개월입니다.</span><span class="sxs-lookup"><span data-stu-id="66823-160">The minimum value is 1 month.</span></span> <span data-ttu-id="66823-161">지원되는 가장 긴 기간은 2년입니다.</span><span class="sxs-lookup"><span data-stu-id="66823-161">The longest supported value is 2 years.</span></span>  
  
 <span data-ttu-id="66823-162">유틸리티 데이터 웨어하우스 구성 정보</span><span class="sxs-lookup"><span data-stu-id="66823-162">Utility Data Warehouse Configuration Information</span></span>  
 <span data-ttu-id="66823-163">다음 구성 설정은 이 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]릴리스에서 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="66823-163">The following configuration settings are not configurable in this release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="66823-164">UMDW 이름: Sysutility_mdw_\<GUID>_DATA.</span><span class="sxs-lookup"><span data-stu-id="66823-164">UMDW name: Sysutility_mdw_\<GUID>_DATA.</span></span>  
  
-   <span data-ttu-id="66823-165">컬렉션 집합 업로드 빈도: 15분마다</span><span class="sxs-lookup"><span data-stu-id="66823-165">Collection set upload frequency: Every 15 minutes.</span></span>  
  
 <span data-ttu-id="66823-166">UMDW 디렉터리는 구성할 수 있으며 \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\입니다. 여기서 \<System drive>는 일반적으로 C:\ 드라이브입니다.</span><span class="sxs-lookup"><span data-stu-id="66823-166">The UMDW directory is configurable: \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\, where \<System drive> is normally the C:\ drive.</span></span> <span data-ttu-id="66823-167">로그 파일 UMDW_\<GUID>_LOG는 같은 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66823-167">The log file, UMDW_\<GUID>_LOG, is located in the same directory.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="66823-168">UMDW(sysutility_mdw) 파일 위치는 detach/attach 또는 ALTER DATABASE를 사용하여 변경할 수 있으며</span><span class="sxs-lookup"><span data-stu-id="66823-168">The UMDW (sysutility_mdw) file location can be changed using detach/attach or ALTER DATABASE.</span></span> <span data-ttu-id="66823-169">ALTER DATABASE를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="66823-169">We recommend the use of ALTER DATABASE.</span></span> <span data-ttu-id="66823-170">자세한 내용은 [ALTER DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="66823-170">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
 <span data-ttu-id="66823-171">제품 기본값으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="66823-171">Go back to out-of-the-box defaults</span></span>  
 <span data-ttu-id="66823-172">이 탭의 설정을 기본값으로 다시 설정하려면 **기본값 복원** 단추를 클릭하고 **적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66823-172">To reset settings on this tab to default values, click the **Restore Defaults** button, then click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66823-173">참고 항목</span><span class="sxs-lookup"><span data-stu-id="66823-173">See Also</span></span>  
 <span data-ttu-id="66823-174">[유틸리티 대시보드 &#40;SQL Server 유틸리티&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="66823-174">[Utility Dashboard &#40;SQL Server Utility&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md) </span></span>  
 <span data-ttu-id="66823-175">[배포된 데이터 계층 애플리케이션 세부 정보&#40;SQL Server 유틸리티&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="66823-175">[Deployed Data-tier Application Details &#40;SQL Server Utility&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md) </span></span>  
 <span data-ttu-id="66823-176">[관리되는 인스턴스 세부 정보&#40;SQL Server 유틸리티&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="66823-176">[Managed Instance Details &#40;SQL Server Utility&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md) </span></span>  
 [<span data-ttu-id="66823-177">SQL Server 유틸리티에서 SQL Server 인스턴스 모니터링</span><span class="sxs-lookup"><span data-stu-id="66823-177">Monitor Instances of SQL Server in the SQL Server Utility</span></span>](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md)  
  
  
