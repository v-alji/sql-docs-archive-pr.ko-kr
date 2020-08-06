---
title: SetSecureConnectionLevel 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetSecureConnectionLevel (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetSecureConnectionLevel method
ms.assetid: 0fac7d5e-2670-4657-9439-331e7d93babb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4361f09eb38b3e5650b68ae6f86b7f2266bbf1a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737719"
---
# <a name="setsecureconnectionlevel-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="23a3a-102">SetSecureConnectionLevel 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="23a3a-102">SetSecureConnectionLevel Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="23a3a-103">보고서 서버의 보안 연결 수준을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="23a3a-103">Sets the secure connection level of the report server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23a3a-104">구문</span><span class="sxs-lookup"><span data-stu-id="23a3a-104">Syntax</span></span>  
  
```vb  
Public Sub SetSecureConnectionLevel(Level as Integer, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetSecureConnectionLevel(Int32 Level,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23a3a-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="23a3a-105">Parameters</span></span>  
 <span data-ttu-id="23a3a-106">*Level*</span><span class="sxs-lookup"><span data-stu-id="23a3a-106">*Level*</span></span>  
 <span data-ttu-id="23a3a-107">보안 연결 수준을 나타내는 정수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="23a3a-107">An integer value representing a secure connection level.</span></span>  
  
 <span data-ttu-id="23a3a-108">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="23a3a-108">*HRESULT*</span></span>  
 <span data-ttu-id="23a3a-109">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="23a3a-109">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23a3a-110">Return Value</span><span class="sxs-lookup"><span data-stu-id="23a3a-110">Return Value</span></span>  
 <span data-ttu-id="23a3a-111">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="23a3a-111">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="23a3a-112">0 값은 메서드 호출이 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="23a3a-112">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="23a3a-113">0 이외의 값은 오류가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="23a3a-113">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23a3a-114">설명</span><span class="sxs-lookup"><span data-stu-id="23a3a-114">Remarks</span></span>  
 <span data-ttu-id="23a3a-115">메서드를 호출하면 보고서 서버의 SecureConnectionLevel 속성이 지정된 값으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="23a3a-115">When called, the report server SecureConnectionLevel property is set to the value specified.</span></span> <span data-ttu-id="23a3a-116">값이 0이면 SSL이 해제되어 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="23a3a-116">A value of 0 indicates that SSL is turned off.</span></span> <span data-ttu-id="23a3a-117">값이 1보다 크거나 같으면 SSL이 설정됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="23a3a-117">A value greater than or equal to 1 indicates that SSL is turned on.</span></span>  
  
-   <span data-ttu-id="23a3a-118">값을 설정 하면 보고서 서버 구성 파일의 SecureConnectionLevel 요소가 변경 되 고 `URLRoot` 구성 파일의 요소는 지정 된 *수준이* 1 보다 크거나 같은 경우 "https://"를 사용 하도록 설정 되 고, 지정 된 *수준이* 0 인 경우에는 "http://"로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="23a3a-118">When the value is set, the SecureConnectionLevel element in the report server configuration file is changed, and the `URLRoot` element in the configuration file is set to use "https://" if the specified *Level* is greater than or equal to 1, or "http://" if the specified *Level* is 0.</span></span>  
  
 <span data-ttu-id="23a3a-119">[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]에서 SecureConnectionLevel은 설정/해제가 전환되며 기본값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="23a3a-119">In [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], SecureConnectionLevel is made an on/off switch, default value is 0.</span></span> <span data-ttu-id="23a3a-120">SetSecureConnectionLevel 메서드 API를 통해 전달되는 값이 1보다 크거나 같으면 SSL이 설정된 것으로 간주하고 그에 따라 구성 속성 SecureConnectionLevel이 rsreportserver.config 파일에서 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="23a3a-120">For any value greater than or equal to 1 passed through SetSecureConnectionLevel method API, SSL is considered on and the configuration property SecureConnectionLevel is set accordingly in the rsreportserver.config file.</span></span> <span data-ttu-id="23a3a-121">값 2와 3도 이전 버전과의 호환성을 위해 계속 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="23a3a-121">Values of 2 and 3 are still allowed for backward compatibility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23a3a-122">요구 사항</span><span class="sxs-lookup"><span data-stu-id="23a3a-122">Requirements</span></span>  
 <span data-ttu-id="23a3a-123">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23a3a-123">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23a3a-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="23a3a-124">See Also</span></span>  
 [<span data-ttu-id="23a3a-125">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="23a3a-125">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
