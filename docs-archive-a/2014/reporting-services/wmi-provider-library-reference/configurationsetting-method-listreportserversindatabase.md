---
title: ListReportServersInDatabase 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- ListReportServersInDatabase (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- ListReportServersInDatabase method
ms.assetid: a4bf5968-c46f-484f-a510-65e2dde65a0d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9eaea72c0737124d89c86b55281326073597fb38
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649906"
---
# <a name="listreportserversindatabase-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="5fc8d-102">ListReportServersInDatabase 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="5fc8d-102">ListReportServersInDatabase Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="5fc8d-103">보고서 서버에 보안 정보에 대한 액세스 권한이 있는지 여부에 관계없이 보고서 서버 데이터베이스에 있는 보고서 서버 설치 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc8d-103">Returns the list of report server installations that are present in the report server database, regardless of whether they have access to secure information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fc8d-104">구문</span><span class="sxs-lookup"><span data-stu-id="5fc8d-104">Syntax</span></span>  
  
```vb  
Public Sub ListReportServersInDatabase(ByRef MachineNames() As String, _  
    ByRef InstanceNames() As String, ByRef InstallationIDs() As String, _  
    ByRef IsInitialized() As Boolean, ByRef Length As Int32, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void ListReportServersInDatabase (out string[] MachineNames,   
    out string[] InstanceNames, out string[] InstallationIDs,   
    out Boolean[] IsInitialized,out Int32 Length, out Int32 HRESULT,    
    out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fc8d-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="5fc8d-105">Parameters</span></span>  
 <span data-ttu-id="5fc8d-106">*MachineNames[]*</span><span class="sxs-lookup"><span data-stu-id="5fc8d-106">*MachineNames[]*</span></span>  
 <span data-ttu-id="5fc8d-107">[out] 데이터베이스에서 설치된 보고서 서버의 컴퓨터 이름이 들어 있는 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="5fc8d-107">[out] An array containing the machine names for the report server installations in the database.</span></span>  
  
 <span data-ttu-id="5fc8d-108">*InstanceNames[]*</span><span class="sxs-lookup"><span data-stu-id="5fc8d-108">*InstanceNames[]*</span></span>  
 <span data-ttu-id="5fc8d-109">[out] 데이터베이스에서 설치된 각 보고서 서버의 인스턴스 이름이 들어 있는 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="5fc8d-109">[out] An array containing the instance names of each of the report server installations in the database.</span></span>  
  
 <span data-ttu-id="5fc8d-110">*InstallationIDs[]*</span><span class="sxs-lookup"><span data-stu-id="5fc8d-110">*InstallationIDs[]*</span></span>  
 <span data-ttu-id="5fc8d-111">[out] 데이터베이스에서 설치된 각 보고서 서버의 설치 ID가 들어 있는 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="5fc8d-111">[out] An array containing the installation IDs of each report server installation in the database.</span></span>  
  
 <span data-ttu-id="5fc8d-112">*IsInitialized[]*</span><span class="sxs-lookup"><span data-stu-id="5fc8d-112">*IsInitialized[]*</span></span>  
 <span data-ttu-id="5fc8d-113">[out] 데이터베이스에서 설치된 각 보고서 서버의 초기화 상태가 들어 있는 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="5fc8d-113">[out] An array containing initialization status for each report server installation in the database.</span></span>  
  
 <span data-ttu-id="5fc8d-114">*길이*</span><span class="sxs-lookup"><span data-stu-id="5fc8d-114">*Length*</span></span>  
 <span data-ttu-id="5fc8d-115">[out] 메서드에서 반환된 배열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="5fc8d-115">[out] The length of the arrays returned by the method.</span></span> <span data-ttu-id="5fc8d-116">반환된 모든 배열의 길이는 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5fc8d-116">All returned arrays have the same length.</span></span>  
  
 <span data-ttu-id="5fc8d-117">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="5fc8d-117">*HRESULT*</span></span>  
 <span data-ttu-id="5fc8d-118">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="5fc8d-118">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="5fc8d-119">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="5fc8d-119">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="5fc8d-120">[out] 호출에서 반환되는 추가 오류가 들어 있는 문자열 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="5fc8d-120">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5fc8d-121">Return Value</span><span class="sxs-lookup"><span data-stu-id="5fc8d-121">Return Value</span></span>  
 <span data-ttu-id="5fc8d-122">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc8d-122">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="5fc8d-123">0 값은 메서드 호출이 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5fc8d-123">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="5fc8d-124">0 이외의 값은 오류가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5fc8d-124">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fc8d-125">설명</span><span class="sxs-lookup"><span data-stu-id="5fc8d-125">Remarks</span></span>  
 <span data-ttu-id="5fc8d-126">ListReportServersInDatabase는 보고서 서버에 보안 정보에 대한 액세스 권한이 있는지 여부에 관계없이 보고서 서버 데이터베이스에 있는 보고서 서버 설치 목록을 나열하고 각 설치 정보가 들어 있는 일치하는 배열 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc8d-126">ListReportServersInDatabase lists the report server installations that are present in the report server database, regardless of whether they have access to secure information, and returns a matched set of arrays containing information about each installation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fc8d-127">요구 사항</span><span class="sxs-lookup"><span data-stu-id="5fc8d-127">Requirements</span></span>  
 <span data-ttu-id="5fc8d-128">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fc8d-128">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fc8d-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5fc8d-129">See Also</span></span>  
 [<span data-ttu-id="5fc8d-130">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="5fc8d-130">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
