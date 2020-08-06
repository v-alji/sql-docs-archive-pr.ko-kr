---
title: ListIPAddresses 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListIPAddresses method
ms.assetid: 7e7cf182-fba0-4604-a474-098461e23e9d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 845f7ba7db02a0b860f966184463580733af0faf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649907"
---
# <a name="listipaddresses-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="a9db7-102">ListIPAddresses 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="a9db7-102">ListIPAddresses Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="a9db7-103">보고서 서버 컴퓨터의 IP 주소를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="a9db7-103">Lists the IP addresses for the report server computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9db7-104">구문</span><span class="sxs-lookup"><span data-stu-id="a9db7-104">Syntax</span></span>  
  
```vb  
Public Sub ListIPAddresses (ByRef IPAddress() as String, _  
    ByRef IPVersion()as String, ByRef IsDhcpEnabled () as Boolean, _   
    ByRef Length as Int32, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListIPAddresses (out string[] IPAddress,   
    out string[] IPVersion, out bool[] isDhcpEnabled, out int length,   
    out int HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9db7-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="a9db7-105">Parameters</span></span>  
 <span data-ttu-id="a9db7-106">*IPAddress[]*</span><span class="sxs-lookup"><span data-stu-id="a9db7-106">*IPAddress[]*</span></span>  
 <span data-ttu-id="a9db7-107">[out] 컴퓨터의 IP 주소 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="a9db7-107">[out] The list of IP address for the computer.</span></span>  
  
 <span data-ttu-id="a9db7-108">*IPVersion[]*</span><span class="sxs-lookup"><span data-stu-id="a9db7-108">*IPVersion[]*</span></span>  
 <span data-ttu-id="a9db7-109">[out] IP 주소의 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="a9db7-109">[out] The version for the IP addresses.</span></span>  
  
 <span data-ttu-id="a9db7-110">*IsDhcpEnabled[]*</span><span class="sxs-lookup"><span data-stu-id="a9db7-110">*IsDhcpEnabled[]*</span></span>  
 <span data-ttu-id="a9db7-111">[out] IP 주소에 DHCP를 사용할 수 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a9db7-111">[out] Indicates whether the IP addresses are DHCP enabled.</span></span>  
  
 <span data-ttu-id="a9db7-112">*길이*</span><span class="sxs-lookup"><span data-stu-id="a9db7-112">*Length*</span></span>  
 <span data-ttu-id="a9db7-113">[out] 메서드에서 반환된 배열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="a9db7-113">[out] The length of the array returned by the method.</span></span>  
  
 <span data-ttu-id="a9db7-114">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="a9db7-114">*HRESULT*</span></span>  
 <span data-ttu-id="a9db7-115">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="a9db7-115">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9db7-116">Return Value</span><span class="sxs-lookup"><span data-stu-id="a9db7-116">Return Value</span></span>  
 <span data-ttu-id="a9db7-117">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a9db7-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="a9db7-118">0 값은 메서드 호출이 성공했음을 나타내고 오류 코드는 호출이 실패했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a9db7-118">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9db7-119">설명</span><span class="sxs-lookup"><span data-stu-id="a9db7-119">Remarks</span></span>  
 <span data-ttu-id="a9db7-120">*IPVersion* 문자열은 V4, V6입니다.</span><span class="sxs-lookup"><span data-stu-id="a9db7-120">*IPVersion* strings are V4, V6.</span></span>  
  
 <span data-ttu-id="a9db7-121">*Isdhcpenabled* 가 이면 `True` *IPAddress* 는 동적 IPAddress입니다.</span><span class="sxs-lookup"><span data-stu-id="a9db7-121">If *IsDhcpEnabled* is `True`, the *IPAddress* is dynamic.</span></span> <span data-ttu-id="a9db7-122">SSL 바인딩에 사용해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9db7-122">It should not be used for SSL bindings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9db7-123">요구 사항</span><span class="sxs-lookup"><span data-stu-id="a9db7-123">Requirements</span></span>  
 <span data-ttu-id="a9db7-124">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9db7-124">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9db7-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a9db7-125">See Also</span></span>  
 [<span data-ttu-id="a9db7-126">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="a9db7-126">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
