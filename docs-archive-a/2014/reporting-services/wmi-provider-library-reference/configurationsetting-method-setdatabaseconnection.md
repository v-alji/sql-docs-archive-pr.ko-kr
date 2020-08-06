---
title: SetDatabaseConnection 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetDatabaseConnection (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDatabaseConnection method
ms.assetid: c040aa78-92b8-41e4-9ae2-eff9fcdddc5b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b5c62777edd1fab2b0cb3babc13ab09f7bcf32a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737738"
---
# <a name="setdatabaseconnection-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="206a6-102">SetDatabaseConnection 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="206a6-102">SetDatabaseConnection Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="206a6-103">특정 보고서 서버 데이터베이스에 대한 보고서 서버 데이터베이스 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="206a6-103">Sets the report server database connection to a particular report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="206a6-104">구문</span><span class="sxs-lookup"><span data-stu-id="206a6-104">Syntax</span></span>  
  
```vb  
Public Sub SetDatabaseConnection(Server as String, _  
    DatabaseName as string, CredentialsType as Integer, _  
    Username as String, Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void BackupEncryptionKey(string Server,   
    string DatabaseName, Int32 CredentialsType,   
    string UserName, string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="206a6-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="206a6-105">Parameters</span></span>  
 <span data-ttu-id="206a6-106">*Server*</span><span class="sxs-lookup"><span data-stu-id="206a6-106">*Server*</span></span>  
 <span data-ttu-id="206a6-107">보고서 서버 데이터베이스를 호스트하는 데 사용되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="206a6-107">The name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that is used to host the report server database.</span></span>  
  
 <span data-ttu-id="206a6-108">*DatabaseName*</span><span class="sxs-lookup"><span data-stu-id="206a6-108">*DatabaseName*</span></span>  
 <span data-ttu-id="206a6-109">보고서 서버 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="206a6-109">The name of the report server database.</span></span>  
  
 <span data-ttu-id="206a6-110">*CredentialsType*</span><span class="sxs-lookup"><span data-stu-id="206a6-110">*CredentialsType*</span></span>  
 <span data-ttu-id="206a6-111">연결에 사용할 자격 증명의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="206a6-111">The type of credentials to use for the connection.</span></span> <span data-ttu-id="206a6-112">값은</span><span class="sxs-lookup"><span data-stu-id="206a6-112">Values can be:</span></span>  
  
-   <span data-ttu-id="206a6-113">0 - Windows</span><span class="sxs-lookup"><span data-stu-id="206a6-113">0 - Windows</span></span>  
  
-   <span data-ttu-id="206a6-114">1 - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="206a6-114">1 - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="206a6-115">2 - Windows 서비스</span><span class="sxs-lookup"><span data-stu-id="206a6-115">2 - Windows Service</span></span>  
  
 <span data-ttu-id="206a6-116">*UserName*</span><span class="sxs-lookup"><span data-stu-id="206a6-116">*UserName*</span></span>  
 <span data-ttu-id="206a6-117">보고서 서버 데이터베이스에 연결하는 데 사용되는 계정 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="206a6-117">The account name used to connect to the report server database.</span></span>  
  
 <span data-ttu-id="206a6-118">*암호*</span><span class="sxs-lookup"><span data-stu-id="206a6-118">*Password*</span></span>  
 <span data-ttu-id="206a6-119">보고서 서버 데이터베이스에 연결하는 데 사용되는 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="206a6-119">The password used to connect to the report server database.</span></span>  
  
 <span data-ttu-id="206a6-120">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="206a6-120">*HRESULT*</span></span>  
 <span data-ttu-id="206a6-121">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="206a6-121">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="206a6-122">Return Value</span><span class="sxs-lookup"><span data-stu-id="206a6-122">Return Value</span></span>  
 <span data-ttu-id="206a6-123">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="206a6-123">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="206a6-124">0 값은 메서드 호출이 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="206a6-124">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="206a6-125">0 이외의 값은 오류가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="206a6-125">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="206a6-126">설명</span><span class="sxs-lookup"><span data-stu-id="206a6-126">Remarks</span></span>  
 <span data-ttu-id="206a6-127">*CredentialsType* 매개 변수를 0(Windows)으로 설정하면 *UserName* 및 *Password* 매개 변수를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="206a6-127">When the *CredentialsType* parameter is set to 0 (Windows), the *UserName* and *Password* parameters must be set.</span></span> <span data-ttu-id="206a6-128">*UserName* 매개 변수는 "domain\username" 형식이어야 하며 값은 유효한 Windows 로그온을 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="206a6-128">The *UserName* parameter must be in the form "domain\username", and the value must represent a valid Windows logon.</span></span>  
  
 <span data-ttu-id="206a6-129">*CredentialsType* 매개 변수를 1([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])로 설정하면 *UserName* 매개 변수에 전달되는 값이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인 이름의 요구 사항을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="206a6-129">When the *CredentialsType* parameter is set to 1 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), the value passed in the *UserName* parameter must conform to the requirements of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login name.</span></span>  
  
 <span data-ttu-id="206a6-130">*CredentialsType* 매개 변수를 2(Windows 서비스)로 설정하면 보고서 서버에서 통합 보안을 사용하여 보고서 서버 데이터베이스에 연결하고 *UserName* 및 *Password* 매개 변수는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="206a6-130">When the *CredentialsType* parameter is set to 2 (Windows Service), the report server uses integrated security to connect to the report server database and the *UserName* and *Password* parameters are ignored.</span></span> <span data-ttu-id="206a6-131">보고 서버 웹 서비스는 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 계정 또는 애플리케이션 풀의 계정과 Windows 서비스 계정을 사용하여 보고서 서버 데이터베이스에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="206a6-131">The Reporting Server Web service will use either the [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] account or an application pool's account and the Windows service account to access the report server database.</span></span>  
  
 <span data-ttu-id="206a6-132">SetDatabaseConnection 메서드는 호출되면 지정된 보고서 서버에 대한 구성 파일에 있는 자격 증명과 데이터베이스 정보를 암호화하여 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="206a6-132">When called, the SetDatabaseConnection method encrypts and stores the credentials and database information in the configuration file for the specified report server.</span></span>  
  
 <span data-ttu-id="206a6-133">SetDatabaseConnection 메서드는 보고서 서버에서 지정된 데이터를 사용하여 보고서 서버 데이터베이스에 연결할 수 있는지 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="206a6-133">The SetDatabaseConnection method does not check that the report server can connect to the report server database using the data specified.</span></span>  
  
 <span data-ttu-id="206a6-134">처음 설정하는 경우 ConnectionPoolSize 속성은 ConnectionPoolSize = #Processors \* 75 프로세서를 기반으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="206a6-134">When set for the first time, the ConnectionPoolSize property is set based on the following processors: ConnectionPoolSize = #Processors \* 75.</span></span>  
  
 <span data-ttu-id="206a6-135">SetDatabaseConnection 메서드는 지정된 계정에 권한을 부여하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="206a6-135">The SetDatabaseConnection method does not grant permissions to the specified account(s).</span></span> <span data-ttu-id="206a6-136">보고서 서버 데이터베이스에 액세스하고 결과 스크립트를 실행해야 하는 각 계정에 대해 [GenerateDatabaseRightsScript](configurationsetting-method-generatedatabaserightsscript.md) 메서드를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="206a6-136">You must call the [GenerateDatabaseRightsScript](configurationsetting-method-generatedatabaserightsscript.md) method for each account that requires access to the report server database and run the resulting script.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="206a6-137">요구 사항</span><span class="sxs-lookup"><span data-stu-id="206a6-137">Requirements</span></span>  
 <span data-ttu-id="206a6-138">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="206a6-138">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="206a6-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="206a6-139">See Also</span></span>  
 [<span data-ttu-id="206a6-140">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="206a6-140">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
