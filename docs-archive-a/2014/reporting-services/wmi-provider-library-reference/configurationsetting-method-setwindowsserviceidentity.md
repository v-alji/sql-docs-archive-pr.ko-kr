---
title: SetWindowsServiceIdentity 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetWindowsServiceIdentity method
ms.assetid: 9bbc734c-9e69-48c2-8bec-8abe7c6cc987
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 15d1b7fa5fc6d69a963785cdaf976c80623c47f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737684"
---
# <a name="setwindowsserviceidentity-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="754e2-102">SetWindowsServiceIdentity 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="754e2-102">SetWindowsServiceIdentity Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="754e2-103">보고서 서버 Windows 서비스가 지정된 Windows 사용자로 실행되도록 하고 이 계정에 보고서 서버를 작동하기에 충분한 파일 시스템 사용 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="754e2-103">Makes the Report Server Windows service run as a specified Windows user, and grants this account sufficient file system permissions to allow the report server to operate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="754e2-104">구문</span><span class="sxs-lookup"><span data-stu-id="754e2-104">Syntax</span></span>  
  
```vb  
Public Sub SetWindowsServiceIdentity(UseBuiltInAccount as Boolean, _  
    Account as String, Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetWindowsServiceIdentity(boolean UseBuiltInAccount,   
    string Account, string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="754e2-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="754e2-105">Parameters</span></span>  
 <span data-ttu-id="754e2-106">*UseBuiltInAccount*</span><span class="sxs-lookup"><span data-stu-id="754e2-106">*UseBuiltInAccount*</span></span>  
 <span data-ttu-id="754e2-107">지정된 계정이 기본 제공 Windows 계정인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="754e2-107">Indicates whether the specified account is a built-in Windows account.</span></span>  
  
 <span data-ttu-id="754e2-108">*계정*</span><span class="sxs-lookup"><span data-stu-id="754e2-108">*Account*</span></span>  
 <span data-ttu-id="754e2-109">Windows 서비스를 실행하는 데 사용할 "DOMAIN\alias" 형식의 Windows 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="754e2-109">The Windows account to use to run the Windows service, in the format "DOMAIN\alias".</span></span>  
  
 <span data-ttu-id="754e2-110">*암호*</span><span class="sxs-lookup"><span data-stu-id="754e2-110">*Password*</span></span>  
 <span data-ttu-id="754e2-111">계정의 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="754e2-111">The password for the account.</span></span>  
  
 <span data-ttu-id="754e2-112">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="754e2-112">*HRESULT*</span></span>  
 <span data-ttu-id="754e2-113">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="754e2-113">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="754e2-114">Return Value</span><span class="sxs-lookup"><span data-stu-id="754e2-114">Return Value</span></span>  
 <span data-ttu-id="754e2-115">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="754e2-115">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="754e2-116">0 값은 메서드 호출이 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="754e2-116">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="754e2-117">0 이외의 값은 오류가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="754e2-117">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="754e2-118">설명</span><span class="sxs-lookup"><span data-stu-id="754e2-118">Remarks</span></span>  
 <span data-ttu-id="754e2-119">*UseBuiltInAccount* 매개 변수가로 설정 되어 `true` 있고 보고서 서버가 MICROSOFT 또는 Windows XP에서 실행 되는 경우 [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)] *Name*, *Domain*및 *Password* 매개 변수의 값이 무시 되 고 로컬 시스템 계정이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="754e2-119">When the *UseBuiltInAccount* parameter is set to `true` and the report server is running on Microsoft [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)] or Windows XP, the value of the *Name*, *Domain*, and *Password* parameters are ignored and the Local system account is used.</span></span>  
  
 <span data-ttu-id="754e2-120">*UseBuiltInAccount* 매개 변수를로 설정 하 `true` 고 보고서 서버에서 Windows server 2003를 실행 하는 경우 *도메인* 및 *암호* 속성이 무시 되 고 이름 필드에 "Builtin\NetworkService" 또는 "Builtin\System" 또는 "Builtin\LocalService"가 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="754e2-120">When the *UseBuiltInAccount* parameter is set to `true` and the report server is running on Windows Server 2003, the *Domain* and *Password* properties are ignored, and the name field must contain either "Builtin\NetworkService" or "Builtin\System" or "Builtin\LocalService".</span></span>  
  
 <span data-ttu-id="754e2-121">SetWindowsServiceIdentity 메서드는 보고서 서버 설치 디렉터리에 있는 파일 및 폴더에 대한 파일 사용 권한을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="754e2-121">The SetWindowsServiceIdentity method sets file permissions on files and folders in the report server installation directory.</span></span>  
  
 <span data-ttu-id="754e2-122">*계정* 매개 변수에 지정 된 계정에는 `LogonAsService` Windows의 권한이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="754e2-122">The account specified in the *Account* parameter requires `LogonAsService` rights in Windows.</span></span> <span data-ttu-id="754e2-123">이 권한은 메서드를 통해 지정된 계정에 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="754e2-123">The method grants this right to the specified account.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="754e2-124">요구 사항</span><span class="sxs-lookup"><span data-stu-id="754e2-124">Requirements</span></span>  
 <span data-ttu-id="754e2-125">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="754e2-125">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="754e2-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="754e2-126">See Also</span></span>  
 [<span data-ttu-id="754e2-127">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="754e2-127">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
