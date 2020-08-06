---
title: GenerateDatabaseRightsScript 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- GenerateDatabaseRightsScript (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- GenerateDatabaseRightsScript method
ms.assetid: f2e6dcc9-978f-4c2c-bafe-36c330247fd0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 768e73d13d3b06f7913c3c816fded1b28c56199f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737767"
---
# <a name="generatedatabaserightsscript-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="bbf0f-102">GenerateDatabaseRightsScript 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="bbf0f-102">GenerateDatabaseRightsScript Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="bbf0f-103">보고서 서버 데이터베이스와 보고서 서버 실행에 필요한 기타 데이터베이스에 사용자 권한을 부여하는 데 사용할 수 있는 SQL 스크립트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-103">Generates a SQL Script that can be used to grant a user rights to the report server database and other databases required for a report server to run.</span></span> <span data-ttu-id="bbf0f-104">호출자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 서버에 연결하여 해당 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-104">The caller is expected to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database server and execute the script.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbf0f-105">구문</span><span class="sxs-lookup"><span data-stu-id="bbf0f-105">Syntax</span></span>  
  
```vb  
Public Sub GenerateDatabaseRightsScript(ByVal UserName As String, _  
    ByVal DatabaseName As String, ByVal IsRemote As Boolean, _  
    ByVal IsWindowsUser As Boolean, ByRef Script As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GenerateDatabaseRightsScript(string UserName, string DatabaseName, bool IsRemote, bool IsWindowsUser, out string Script,   
out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbf0f-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="bbf0f-106">Parameters</span></span>  
 <span data-ttu-id="bbf0f-107">*UserName*</span><span class="sxs-lookup"><span data-stu-id="bbf0f-107">*UserName*</span></span>  
 <span data-ttu-id="bbf0f-108">스크립트에서 권한을 부여할 사용자의 이름 또는 Windows SID(보안 식별자)입니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-108">The user name or Windows security identifier (SID) of the user to which the script will grant rights.</span></span>  
  
 <span data-ttu-id="bbf0f-109">*DatabaseName*</span><span class="sxs-lookup"><span data-stu-id="bbf0f-109">*DatabaseName*</span></span>  
 <span data-ttu-id="bbf0f-110">스크립트에서 사용자에게 액세스가 허용되는 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-110">The database name to which the script will grant access to the user.</span></span>  
  
 <span data-ttu-id="bbf0f-111">*IsRemote*</span><span class="sxs-lookup"><span data-stu-id="bbf0f-111">*IsRemote*</span></span>  
 <span data-ttu-id="bbf0f-112">데이터베이스가 보고서 서버에 대해 원격인지 여부를 나타내는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-112">A Boolean value to indicating whether the database is remote from the report server.</span></span>  
  
 <span data-ttu-id="bbf0f-113">*IsWindowsUser*</span><span class="sxs-lookup"><span data-stu-id="bbf0f-113">*IsWindowsUser*</span></span>  
 <span data-ttu-id="bbf0f-114">지정된 사용자 이름이 Windows 사용자인지 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자인지를 나타내는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-114">A Boolean value indicating whether the specified user name is a Windows user or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user.</span></span>  
  
 <span data-ttu-id="bbf0f-115">*스크립트*</span><span class="sxs-lookup"><span data-stu-id="bbf0f-115">*Script*</span></span>  
 <span data-ttu-id="bbf0f-116">[out] 생성된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 스크립트가 들어 있는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-116">[out] A string containing the generated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] script.</span></span>  
  
 <span data-ttu-id="bbf0f-117">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="bbf0f-117">*HRESULT*</span></span>  
 <span data-ttu-id="bbf0f-118">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-118">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bbf0f-119">Return Value</span><span class="sxs-lookup"><span data-stu-id="bbf0f-119">Return Value</span></span>  
 <span data-ttu-id="bbf0f-120">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-120">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="bbf0f-121">0 값은 메서드 호출이 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-121">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="bbf0f-122">0 이외의 값은 오류가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-122">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbf0f-123">설명</span><span class="sxs-lookup"><span data-stu-id="bbf0f-123">Remarks</span></span>  
 <span data-ttu-id="bbf0f-124">*DatabaseName* 이 비어 있으면 *IsRemote* 는 무시되고 데이터베이스 이름에 보고서 서버 구성 파일 값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-124">If *DatabaseName* is empty then *IsRemote* is ignored and the report server configuration file value is used for the database name.</span></span>  
  
 <span data-ttu-id="bbf0f-125">*Iswindowsuser* 가로 설정 된 경우 사용자 `true` *이름은* \<domain> \\<username 형식 이어야 합니다 \> .</span><span class="sxs-lookup"><span data-stu-id="bbf0f-125">If *IsWindowsUser* is set to `true`, *UserName* should be in the format \<domain>\\<username\>.</span></span>  
  
 <span data-ttu-id="bbf0f-126">*Iswindowsuser* 를로 설정 하면 `true` 생성 된 스크립트에서 사용자에 게에 대 한 로그인 권한을 부여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 하 고, 보고서 서버 데이터베이스를 기본 데이터베이스로 설정 하 고, 보고서 서버 데이터베이스, 보고서 서버 임시 데이터베이스, master 데이터베이스 및 MSDB 시스템 데이터베이스에 대 한 **RSExec** 역할을 부여 합니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-126">When *IsWindowsUser* is set to `true`, the generated script grants login rights to the user for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], setting the report server database as the default database, and grants the **RSExec** role on the report server database, the report server temporary database, the master database and the MSDB system database.</span></span>  
  
 <span data-ttu-id="bbf0f-127">*Iswindowsuser* 를로 설정 하면 `true` 메서드에서 표준 Windows sid를 입력으로 받아들입니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-127">When *IsWindowsUser* is set to `true`, the method accepts standard Windows SIDs as input.</span></span> <span data-ttu-id="bbf0f-128">입력된 표준 Windows SID 또는 서비스 계정 이름은 사용자 이름 문자열로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-128">When a standard Windows SID or service account name is supplied, it is translated to a user name string.</span></span> <span data-ttu-id="bbf0f-129">데이터베이스가 로컬 데이터베이스인 경우 계정은 계정의 지역화된 올바른 표현으로 변환되고</span><span class="sxs-lookup"><span data-stu-id="bbf0f-129">If the database is local, the account is translated to the correct localized representation of the account.</span></span> <span data-ttu-id="bbf0f-130">원격 데이터베이스인 경우 계정은 컴퓨터 계정으로 표현됩니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-130">If the database is remote, the account is represented as the computer's account.</span></span>  
  
 <span data-ttu-id="bbf0f-131">다음 표에서는 변환된 계정과 해당 원격 표현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-131">The following table shows accounts that are translated and their remote representation.</span></span>  
  
|<span data-ttu-id="bbf0f-132">변환된 계정/SID</span><span class="sxs-lookup"><span data-stu-id="bbf0f-132">Account / SID that is translated</span></span>|<span data-ttu-id="bbf0f-133">일반 이름</span><span class="sxs-lookup"><span data-stu-id="bbf0f-133">Common Name</span></span>|<span data-ttu-id="bbf0f-134">원격 이름</span><span class="sxs-lookup"><span data-stu-id="bbf0f-134">Remote Name</span></span>|  
|---------------------------------------|-----------------|-----------------|  
|<span data-ttu-id="bbf0f-135">(S-1-5-18)</span><span class="sxs-lookup"><span data-stu-id="bbf0f-135">(S-1-5-18)</span></span>|<span data-ttu-id="bbf0f-136">로컬 시스템</span><span class="sxs-lookup"><span data-stu-id="bbf0f-136">Local System</span></span>|<span data-ttu-id="bbf0f-137">\<Domain>\\<ComputerName\>$</span><span class="sxs-lookup"><span data-stu-id="bbf0f-137">\<Domain>\\<ComputerName\>$</span></span>|  
|<span data-ttu-id="bbf0f-138">.\LocalSystem</span><span class="sxs-lookup"><span data-stu-id="bbf0f-138">.\LocalSystem</span></span>|<span data-ttu-id="bbf0f-139">로컬 시스템</span><span class="sxs-lookup"><span data-stu-id="bbf0f-139">Local System</span></span>|<span data-ttu-id="bbf0f-140">\<Domain>\\<ComputerName\>$</span><span class="sxs-lookup"><span data-stu-id="bbf0f-140">\<Domain>\\<ComputerName\>$</span></span>|  
|<span data-ttu-id="bbf0f-141">ComputerName\LocalSystem</span><span class="sxs-lookup"><span data-stu-id="bbf0f-141">ComputerName\LocalSystem</span></span>|<span data-ttu-id="bbf0f-142">로컬 시스템</span><span class="sxs-lookup"><span data-stu-id="bbf0f-142">Local System</span></span>|<span data-ttu-id="bbf0f-143">\<Domain>\\<ComputerName\>$</span><span class="sxs-lookup"><span data-stu-id="bbf0f-143">\<Domain>\\<ComputerName\>$</span></span>|  
|<span data-ttu-id="bbf0f-144">LocalSystem</span><span class="sxs-lookup"><span data-stu-id="bbf0f-144">LocalSystem</span></span>|<span data-ttu-id="bbf0f-145">로컬 시스템</span><span class="sxs-lookup"><span data-stu-id="bbf0f-145">Local System</span></span>|<span data-ttu-id="bbf0f-146">\<Domain>\\<ComputerName\>$</span><span class="sxs-lookup"><span data-stu-id="bbf0f-146">\<Domain>\\<ComputerName\>$</span></span>|  
|<span data-ttu-id="bbf0f-147">(S-1-5-20)</span><span class="sxs-lookup"><span data-stu-id="bbf0f-147">(S-1-5-20)</span></span>|<span data-ttu-id="bbf0f-148">네트워크 서비스</span><span class="sxs-lookup"><span data-stu-id="bbf0f-148">Network Service</span></span>|<span data-ttu-id="bbf0f-149">\<Domain>\\<ComputerName\>$</span><span class="sxs-lookup"><span data-stu-id="bbf0f-149">\<Domain>\\<ComputerName\>$</span></span>|  
|<span data-ttu-id="bbf0f-150">NT AUTHORITY\NetworkService</span><span class="sxs-lookup"><span data-stu-id="bbf0f-150">NT AUTHORITY\NetworkService</span></span>|<span data-ttu-id="bbf0f-151">네트워크 서비스</span><span class="sxs-lookup"><span data-stu-id="bbf0f-151">Network Service</span></span>|<span data-ttu-id="bbf0f-152">\<Domain>\\<ComputerName\>$</span><span class="sxs-lookup"><span data-stu-id="bbf0f-152">\<Domain>\\<ComputerName\>$</span></span>|  
|<span data-ttu-id="bbf0f-153">(S-1-5-19)</span><span class="sxs-lookup"><span data-stu-id="bbf0f-153">(S-1-5-19)</span></span>|<span data-ttu-id="bbf0f-154">로컬 서비스</span><span class="sxs-lookup"><span data-stu-id="bbf0f-154">Local Service</span></span>|<span data-ttu-id="bbf0f-155">오류 - 아래를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-155">Error - see below.</span></span>|  
|<span data-ttu-id="bbf0f-156">NT AUTHORITY\LocalService</span><span class="sxs-lookup"><span data-stu-id="bbf0f-156">NT AUTHORITY\LocalService</span></span>|<span data-ttu-id="bbf0f-157">로컬 서비스</span><span class="sxs-lookup"><span data-stu-id="bbf0f-157">Local Service</span></span>|<span data-ttu-id="bbf0f-158">오류 - 아래를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-158">Error - see below.</span></span>|  
  
 <span data-ttu-id="bbf0f-159">[!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)]에서 기본 제공 계정을 사용하고 있고 보고서 서버 데이터베이스가 원격이면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-159">On [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)], if you are using a built-in account and the report server database is remote, an error is returned.</span></span>  
  
 <span data-ttu-id="bbf0f-160">`LocalService` 기본 제공 계정이 지정되어 있고 보고서 서버 데이터베이스가 원격이면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-160">If the `LocalService` built-in account is specified and the report server database is remote, an error is returned.</span></span>  
  
 <span data-ttu-id="bbf0f-161">*IsWindowsUser* 가 true이고 *UserName* 에 제공된 값을 변환해야 하는 경우, WMI 공급자는 보고서 서버 데이터베이스가 같은 컴퓨터에 있는지 또는 원격 컴퓨터에 있는지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-161">When *IsWindowsUser* is true and the value supplied in *UserName* needs to be translated, the WMI provider determines whether the report server database is located on the same computer or on a remote computer.</span></span> <span data-ttu-id="bbf0f-162">WMI 공급자는 로컬 설치 여부를 확인하기 위해 다음 값 목록에 대해 DatabaseServerName 속성을 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-162">To determine if the installation is local, the WMI provider evaluates the DatabaseServerName property against the following list of values.</span></span> <span data-ttu-id="bbf0f-163">일치 항목이 있으면 로컬 데이터베이스이고,</span><span class="sxs-lookup"><span data-stu-id="bbf0f-163">If a match is found, the database is local.</span></span> <span data-ttu-id="bbf0f-164">그렇지 않으면 원격 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-164">Otherwise, it is remote.</span></span> <span data-ttu-id="bbf0f-165">비교는 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-165">The comparison is case-insensitive.</span></span>  
  
|<span data-ttu-id="bbf0f-166">DatabaseServerName 값</span><span class="sxs-lookup"><span data-stu-id="bbf0f-166">Value of DatabaseServerName</span></span>|<span data-ttu-id="bbf0f-167">예제</span><span class="sxs-lookup"><span data-stu-id="bbf0f-167">Example</span></span>|  
|---------------------------------|-------------|  
|<span data-ttu-id="bbf0f-168">"."</span><span class="sxs-lookup"><span data-stu-id="bbf0f-168">"."</span></span>||  
|<span data-ttu-id="bbf0f-169">"(local)"</span><span class="sxs-lookup"><span data-stu-id="bbf0f-169">"(local)"</span></span>||  
|<span data-ttu-id="bbf0f-170">"LOCAL"</span><span class="sxs-lookup"><span data-stu-id="bbf0f-170">"LOCAL"</span></span>||  
|<span data-ttu-id="bbf0f-171">localhost</span><span class="sxs-lookup"><span data-stu-id="bbf0f-171">localhost</span></span>||  
|\<Machinename>|<span data-ttu-id="bbf0f-172">testlab14</span><span class="sxs-lookup"><span data-stu-id="bbf0f-172">testlab14</span></span>|  
|\<MachineFQDN>|<span data-ttu-id="bbf0f-173">example.redmond.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="bbf0f-173">example.redmond.microsoft.com</span></span>|  
|\<IPAddress>|<span data-ttu-id="bbf0f-174">180.012.345,678</span><span class="sxs-lookup"><span data-stu-id="bbf0f-174">180.012.345,678</span></span>|  
  
 <span data-ttu-id="bbf0f-175">*Iswindowsuser* 를로 설정 하면 `true` WMI 공급자는 LookupAccountName를 호출 하 여 계정의 SID를 가져온 다음 LookupAccountSID를 호출 하 여 스크립트에 넣을 이름을 가져옵니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="bbf0f-175">When *IsWindowsUser* is set to `true`, the WMI provider calls LookupAccountName to get the SID for the account and then calls LookupAccountSID to get the name to put in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] script.</span></span> <span data-ttu-id="bbf0f-176">이렇게 하면 사용되는 계정 이름이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유효성 검사를 통과합니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-176">This ensures that the account name used will pass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] validation.</span></span>  
  
 <span data-ttu-id="bbf0f-177">*Iswindowsuser* 를로 설정 하면 `false` 생성 된 스크립트에서 보고서 서버 데이터베이스, 보고서 서버 임시 데이터베이스 및 MSDB 데이터베이스에 대 한 **RSExec** 역할을 부여 합니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-177">When *IsWindowsUser* is set to `false`, the generated script grants the **RSExec** role on the report server database, the report server temporary database, and the MSDB database.</span></span>  
  
 <span data-ttu-id="bbf0f-178">*Iswindowsuser* 가로 설정 된 경우 `false` 스크립트를 성공적으로 실행 하려면 SQL Server 사용자가에 이미 있어야 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="bbf0f-178">When *IsWindowsUser* is set to `false`, the SQL Server user must already exist on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the script to run successfully.</span></span>  
  
 <span data-ttu-id="bbf0f-179">보고서 서버에 보고서 서버 데이터베이스가 지정되어 있지 않은 경우 GrantRightsToDatabaseUser를 호출하면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-179">If the report server does not have a report server database specified, calling GrantRightsToDatabaseUser returns an error.</span></span>  
  
 <span data-ttu-id="bbf0f-180">생성된 스크립트는 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 및 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]을(를) 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="bbf0f-180">The generated script supports [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005, and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbf0f-181">요구 사항</span><span class="sxs-lookup"><span data-stu-id="bbf0f-181">Requirements</span></span>  
 <span data-ttu-id="bbf0f-182">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbf0f-182">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbf0f-183">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bbf0f-183">See Also</span></span>  
 [<span data-ttu-id="bbf0f-184">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="bbf0f-184">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
